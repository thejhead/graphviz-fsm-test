![Alt text](https://g.gravizo.com/source/svg/custom_mark10?https://raw.githubusercontent.com/thejhead/graphviz-fsm-test/main/README.md)
<details> 
<summary></summary>
custom_mark10
    digraph BGP_FSM_CONNECT {
        rankdir=LR;
        pad=".25"
        nodesep="1"
        ranksep="1"
        CONNECT
        OPENSENT
        ACTIVE
        OPENCONFIRM
        IDLE
        CONNECT_END [label="CONNECT"]
        { rank=same OPENSENT, ACTIVE, OPENCONFIRM, IDLE, CONNECT_END}
        node [shape=record]
        TRANSITIONS [label="<t0>BGPOpen_with_DelayOpenTimer_Running|<t1>DelayOpenTimer_Expires|<t2>TcpConnectionFails|<t3>Tcp_CR_Acked|<t4>TcpConnectionConfirmed|<t5>NotifMsgVerErr"]
        IDLE_TRANSITIONS [label="<t0>ManualStop|<t1>BGPHeaderErr|<t2>BGPOpenMsgErr|<t3>AutomaticStop|<t4>HoldTimer_Expires|<t5>KeepaliveTimer_Expires|<t6>IdleHoldTimer_Expires|<t7>BGPOpen|<t8>OpenCollisionDump|<t9>NotifMsgVerErr|<t10>NotifMsg|<t11>KeepAliveMsg|<t12>UpdateMsg|<t13>UpdateMsgErr"]
        CONNECT_TRANSITIONS [label="<t0>ConnectRetryTimer_Expires|<t1>TcpConnection_Valid|<t3>Tcp_CR_Invalid"]
        {rank=same TRANSITIONS IDLE_TRANSITIONS CONNECT_TRANSITIONS}
        node [shape=record]
        DELAY_OPEN_TIMER_ACTIONS [label="<a0>DelayOpenTimer(RUNNING)|<a1>DelayOpenTimer(NOT RUNNING)"]
        DELAY_OPEN_ACTIONS [label="<a0>DelayOpen(TRUE)|<a1>DelayOpen(FALSE)"]
        CONNECT -> TRANSITIONS:t0 [arrowhead=none]
        TRANSITIONS:t0 -> OPENSENT
        CONNECT -> TRANSITIONS:t1 [arrowhead=none]
        TRANSITIONS:t1 -> OPENCONFIRM
        CONNECT -> TRANSITIONS:t2 [arrowhead=none]
        TRANSITIONS:t2 -> DELAY_OPEN_TIMER_ACTIONS:a0 [arrowhead=none]
        TRANSITIONS:t2 -> DELAY_OPEN_TIMER_ACTIONS:a1 [arrowhead=none]
        DELAY_OPEN_TIMER_ACTIONS:a0 -> ACTIVE
        DELAY_OPEN_TIMER_ACTIONS:a1 -> IDLE
        CONNECT -> TRANSITIONS:t3 [arrowhead=none]
        CONNECT -> TRANSITIONS:t4 [arrowhead=none]
        TRANSITIONS:t3 -> DELAY_OPEN_ACTIONS:a1[arrowhead=none]
        TRANSITIONS:t4 -> DELAY_OPEN_ACTIONS:a1[arrowhead=none]
        DELAY_OPEN_ACTIONS:a1 -> OPENSENT
        CONNECT -> TRANSITIONS:t5 [arrowhead=none]
        TRANSITIONS:t5 -> DELAY_OPEN_TIMER_ACTIONS:a0 [arrowhead=none]
        TRANSITIONS:t5 -> DELAY_OPEN_TIMER_ACTIONS:a1 [arrowhead=none]
        DELAY_OPEN_TIMER_ACTIONS:a0 -> IDLE
        DELAY_OPEN_TIMER_ACTIONS:a1 -> IDLE
        CONNECT -> IDLE_TRANSITIONS [arrowhead=none]
        IDLE_TRANSITIONS -> IDLE
        CONNECT -> TRANSITIONS:t4 [arrowhead=none]
        TRANSITIONS:t4 -> DELAY_OPEN_ACTIONS:a0[arrowhead=none]
        DELAY_OPEN_ACTIONS:a0 -> CONNECT_END
        CONNECT -> TRANSITIONS:t3 [arrowhead=none]
        TRANSITIONS:t3 -> DELAY_OPEN_ACTIONS:a0[arrowhead=none]
        DELAY_OPEN_ACTIONS:a0 -> CONNECT_END
        CONNECT -> CONNECT_TRANSITIONS:t0 [arrowhead=none]
        CONNECT_TRANSITIONS:t0 -> CONNECT_END
        CONNECT -> CONNECT_TRANSITIONS:t1 [arrowhead=none]
        CONNECT_TRANSITIONS:t1 -> CONNECT_END
        CONNECT -> CONNECT_TRANSITIONS:t2 [arrowhead=none]
        CONNECT_TRANSITIONS:t2 -> CONNECT_END
    }
custom_mark10
</details>
