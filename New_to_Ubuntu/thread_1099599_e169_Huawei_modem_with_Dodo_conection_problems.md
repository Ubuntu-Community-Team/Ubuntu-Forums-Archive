---
title: "e169 Huawei modem with Dodo conection problems"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by wytewing on 2009-03-18
Hi :(

I have just got a new E169 Huawe: modem from Dodo (Optus) (Australia).

I am having trouble getting it to stay connected to the network. I have a slightly older modem though the same model that is with Optus, and it works fine. Yet when I set up PPP with what we were told to in the init strings it just connects then disconnects and keeps repeating the process.

I got the second modem on a lite plan so I could use it when away from my wireless network at home. I know enough to disable my network connection so I am at my wits end as to what else to try.

Any suggestions would be greatly appreciated. I am sure I am not the only Aussie here using Dodo with ubuntu.

Thanks in advance,

Wytewing

---

### Post by kingswood71 on 2009-06-19
hope this helps...
Connection H169 modem to Dodo network in Australia on 8.1

1.plug the usb in.
2.network manager will see it as an E622.
3.Select next etc.
4.select optus 3G
5.itw ill try to connect but cant.
6.Open up edit connections.
7.Mobile broadband, optus 3G edit connections
8.in APN type dodolns1
9.in the PPP tab, select Pap only, then select auto connect. Apply.
10.It will now connect.
11.You most likely will not be able to get firefox to work, so...
12. open up edit connections again and delete and DNS numbers in the ipv4 setting.
13.Open up a terminal and type.. sudo gedit /etc/resolv.conf
14.delete the DNS numbers there and replace with 208.67.222.222 and 208.67.220.220.
15.save this.
16.Now disable ipv6. Open a terminal and type sudo gedit /etc/modprobe.d/aliases
17.find the ipv6 line and type off before the ipv6.
18.Now new terminal and type sudo gedit /etc/modprobe.d/blacklist
19.type in blacklist ipv6 , #ipv6 and ipv6 off.
20.Save this.
21.For extra surety, open new terminal then type. Sudo gedit /etc/modprobe.d/bad_list
22.add to bad list #ipv6, ipv6 and ipv6 off.
23.Save file.
24.Reboot computer.

This should work...worked for me!

Good luck
Rohan

---

