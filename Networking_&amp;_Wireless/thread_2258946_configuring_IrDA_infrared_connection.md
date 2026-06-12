---
title: "configuring IrDA infrared connection"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by timeofday on 2014-12-31
Is anyone still knowledgeable on IrDA infrared connections between laptops and other devices?


I have an HP 6910p laptop with an IrDA infrared port, and Ubuntu 14.04.1 installed. I have an old IR networking device (HP NetbeamIR) hooked up to my router via ethernet, which I would like to connect to my laptop via IR. My ultimate goal is to use the internet via IR. I have irda/utils and IrNET configured, etc.; the Netbeam definitely sees my laptop (light blinks when laptop is pointed toward it, stops blinking when laptop is pointed away).  I've tried two approaches -- IrNET and IrLAN -- with no success.


**IrNET:**


The result of "cat /dev/irnet" is:
Found 000cc000 (HP NetBeamIR) behind fe40a5c8 {hints 41-00}


To connect to the Netbeam, I tried these two approaches:


pppd /dev/irnet 9600 local noauth nolock


pppd /dev/irnet 9600 local noauth nolock connect-delay 0 idle 10 connect "echo addr 000cc000"


However, the result of "cat /proc/net/irda/irnet" is:
IrNET server - IrDA state: running, stsap_sel: 10, dtsap_sel: 00


In other words, there is no IrNET socket appearing.  I see no other evidence of a connection.


**IrLAN:**


modprobe irlan access=2


then:


sudo ifconfig irlan0 10.0.0.1 netmask 255.255.255.0 broadcast 10.0.0.255


But then I get this message:


SIOCSIFFLAGS: Cannot assign requested address




So I don't know what I'm doing wrong.  Is there an IrDA expert out there who could give me a hand?  (I've searched the Ubuntu forums already without finding any answers.)

---

