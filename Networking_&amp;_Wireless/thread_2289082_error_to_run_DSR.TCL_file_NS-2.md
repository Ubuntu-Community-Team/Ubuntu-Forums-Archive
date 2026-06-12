---
title: "error to run DSR.TCL file NS-2"
date: 2015-08-01
forum: Networking &amp; Wireless
---

### Post by hina3 on 2015-08-01
can anybody pls help me to solve this error
following is error:
```

hina@ubuntu:~/Desktop$ ns DSR.TCL
can't read "val(x)": no such variable
    while executing
"$ns namtrace-all-wireless $namtrace $val(x) $val(y)"
    (file "DSR.TCL" line 10)


 and the code is 

#-------Event scheduler object creation--------#



set ns              [new Simulator]

#Creating trace file and nam file 

set tracefd       [open dsr.tr w]

set windowVsTime2 [open win.tr w] 

set namtrace      [open dsr.nam w]    



$ns trace-all $tracefd

$ns namtrace-all-wireless $namtrace $val(x) $val(y)



# set up topography object

set topo       [new Topography]



$topo load_flatgrid $val(x) $val(y)



create-god $val(nn)



# configure the nodes

        $ns node-config -adhocRouting $val(rp) \

                   -llType $val(ll) \

                   -macType $val(mac) \

                   -ifqType $val(ifq) \

                   -ifqLen $val(ifqlen) \

                   -antType $val(ant) \

                   -propType $val(prop) \

                   -phyType $val(netif) \

                   -channelType $val(chan) \

                   -topoInstance $topo \

                   -agentTrace ON \

                   -routerTrace ON \

                   -macTrace OFF \

                   -movementTrace ON

                   

      for {set i 0} {$i < $val(nn) } { incr i } {

            set node_($i) [$ns node]      

      }



# Provide initial location of mobilenodes

$node_(0) set X_ 5.0

$node_(0) set Y_ 5.0

$node_(0) set Z_ 0.0



$node_(1) set X_ 490.0

$node_(1) set Y_ 285.0

$node_(1) set Z_ 0.0



$node_(2) set X_ 150.0

$node_(2) set Y_ 240.0

$node_(2) set Z_ 0.0



# Generation of movements

$ns at 10.0 "$node_(0) setdest 250.0 250.0 3.0"

$ns at 15.0 "$node_(1) setdest 45.0 285.0 5.0"

$ns at 110.0 "$node_(0) setdest 480.0 300.0 5.0" 



# Set a TCP connection between node_(0) and node_(1)

set tcp [new Agent/TCP/Newreno]

$tcp set class_ 2

set sink [new Agent/TCPSink]

$ns attach-agent $node_(0) $tcp

$ns attach-agent $node_(1) $sink

$ns connect $tcp $sink

set ftp [new Application/FTP]

$ftp attach-agent $tcp

$ns at 10.0 "$ftp start" 



# Printing the window size

proc plotWindow {tcpSource file} {

global ns

set time 0.01

set now [$ns now]

set cwnd [$tcpSource set cwnd_]

puts $file "$now $cwnd"

$ns at [expr $now+$time] "plotWindow $tcpSource $file" }

$ns at 10.1 "plotWindow $tcp $windowVsTime2"  



# Define node initial position in nam

for {set i 0} {$i < $val(nn)} { incr i } {

# 30 defines the node size for nam

$ns initial_node_pos $node_($i) 30

}



# Telling nodes when the simulation ends

for {set i 0} {$i < $val(nn) } { incr i } {

    $ns at $val(stop) "$node_($i) reset";

}



# ending nam and the simulation 

$ns at $val(stop) "$ns nam-end-wireless $val(stop)"

$ns at $val(stop) "stop"

$ns at 150.01 "puts \"end simulation\" ; $ns halt"

proc stop {} {

    global ns tracefd namtrace

    $ns flush-trace

    close $tracefd

    close $namtrace

exec nam dsr.nam &

exit 0

}



$ns run



# How to run the program:



$ns dsr.tcl


```

#snapshot of the program:

---

