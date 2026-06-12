---
title: "HOWTO: Intrepid Ibex assign static IP and wireless Internet sharing with Firestarter"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by fairyanto on 2008-12-02
_I use_ : Huawei 220 usb modem with Telkomsel as ISP, Acer notebook with XP already configured and used for client, cross cable to replace switch.

_Setup the modem_ : after setup the II (Intrepid Ibex), plug the modem, II will auto configured, but you must edit the connections to suit your ISP requirement at first by right click the 'tower icon ' at upper panel.
choose the Mobile Broadband, add/edit/fill it as your ISP manual (i checked auto connect also, because I use unlimited account, so no worry with the bill). Click ok and you got online now.

updating II: after got online please update your II first.

_Assign static IP_ : It's little bit tricky and so far there isn't proper help without remove 'network manager' that i can search.
But yesterday I found the conclusion without removing 'network manager' that I worry to amputee my II from sniffing my modem. It's just an easy step.
Right click the 'tower icon ' at upper panel, choose edit connection, click 'wired tab'.
click and **delete 'auto (eth0), yes delete rather than edit** (if you just edit the connection, it will be reset again with the default).
click add then fill the IP s as necessary in my setting was:
IP: 192.168.0.1 , subnet: 255.255.255.0 (netmgr will covert into 24 later) and so on.
Name the conecction as you want (I type 'kucing' because my cat just walk in front of my keyboard at the time : kucing = cat in indonesian). restart II.

_Internet sharing_ : As many ubuntu user suggest for newbie like me, I use Firestarter, simply aptget it or by add/remove, then configure it. you may search the posting about Firestarter if you are not sure what you'll do with this.

Connect the client with cable.. and I got my notebook online.
sorry with my poor english.

warm regards,
Winanda Fairyanto
):P

---

