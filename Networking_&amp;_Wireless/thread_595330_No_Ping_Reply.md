---
title: "No Ping Reply"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Borsec on 2007-10-28
Hello Ubuntu Users

I am pretty new to the linux world and i kinda have a problem.
My main computer has two onboard Network Adapters Nvidia Nforce 4 / Intel PRO 1000 .
Nvidia pretty much is for the internet usage, where my network cable plugs in.
The other one  should be for some home networking.But that is my problem.I have Ubuntu 7.10 installed on a older computer with 2 network adapters/ realtek chipset ones.
I connected XP and Ubuntu through a switch but i can't get them to work.
If i try to ping one or the other, i simply get "Request Timed Out" from XP and "Destination Host Unreachable"

I can't understand what is wrong.It's just like the "ping" packets won't leave the computer because even if i unplug the cable from my switch it'll still say the same thing.
Even tried to connect them with one cable without a switch, stll no luck.Disconnected the internet and used Nvidia Adapter, gain no luck.Localhost /127.0.0.1 pinging works.
here is my "arp -n" from Ubuntu:

Address 10.10.10.5
HWtype -
HWaddress (incomplete)
Flags Mask -
Iface eth0

Ubuntu is 10.10.10.2 and XP is 10.10.10.5 , submask 255.255.255.0 /with no firewalls .Am i really stupid or there is something wrong?
and at  "arp -n"  shouldn't Address be 10.10.10.2 ?

---

### Post by zek725 on 2007-10-28
networking through a switch? then i guess that's peer-to-peer networking. Make sure you have the right wiring for your ethernet cable. [http://del.icio.us/zek725/networking](http://del.icio.us/zek725/networking)

---

### Post by Borsec on 2007-10-29
thanks for the answer.the problem was..linux it's self.Gutsy 7.10 Server really has some issues that need to be addresed.I now run edubuntu server 7.06 , and kinda works i can now connect to it with Putty etc.now all i have to figure out is Samba.Installed Samba and now i ask you , does it run on it's own @ boot or i have to enable it somehow?i really need to put some files from XP into Ubuntu..or there are other ways to do this?

---

