---
title: "LAN between windows XP and Ubuntu Linux 6.06"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Verminoz on 2006-11-26
The title is pretty self-explanable. I have my pc running Ubuntu Linux and a laptop running windows XP. I also have a DSL modem and an access point (to communicate with the laptop) both of which are connected to a switch. The Ubuntu box is also connected to the switch.
I managed to access the laptop using the Linux box but the laptop (WinXP) cannot "see" the Linux box in the LAN. ](*,) 
Any ideas? Is the problem in my linux box or in the laptop?

Thanks in advance! :)

---

### Post by shin on 2006-11-26
To actually see it, you should set your AP properly with port forwarding.

For example:
if switch has private ip 192.168.1.1, then it 'gives' the following IPs to stuff plugged to it:
desktop 192.168.1.2
AP 192.168.1.3

and AP private ip has 192.18.1.1
laptop 192.18.1.2

then set port forwarding on AP
e.g.
incoming 21 forward to 192.18.1.2

now when you set a ftpd on laptop and try to connect 192.168.1.3 (AP's IP from switch) you will be forwarded to 192.18.1.2 (laptops private ip, normally only reachable from AP)

I hope that helps.

EDIT:
Just noticed that you want to achieve the opposite.
That's different.
AFAIK you cant get to private IP assigned by switch from the laptop to which AP assignes IP.
You need to get your public IP, and contact through it with proper port forwarding on switch.
when switch forwards port 21 to your desktop, then when you try to connect from your laptop (or actually, anything else) to your public IP port 21, then you will be forwarded by switch to your desktop.

---

