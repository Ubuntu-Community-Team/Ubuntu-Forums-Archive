---
title: "vpn reconnect script"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Don_Shifty on 2008-06-29
hi i would like to make the vpn login automatic with a bash script. 

a normal login process lookes like this in the terminal:

shifty@shifty-laptop:~$ sudo vpnc epfl.conf
[sudo] password for shifty: 
Enter password for [email]user@vpn-epfl.epfl.ch[/email]: 
VPNC started in background (pid: 10044)...
shifty@shifty-laptop:~$ 


so i tried the following to make it automatic (never mind the sudo pw):

>#!/bin/bash
>LOGIN="pass123"
>send -- "sudo vpnc epfl.conf"
>expect "Enter password for [email]user@vpn-epfl.epfl.ch[/email]:" {send "$LOGIN\r"} 

it gave me this:
./vpn-reconnect: line 6: send: command not found
./vpn-reconnect: line 7: expect: command not found

what can i do to make it work?
thanx
shifty

---

