---
title: "issues with wifi card"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by killerhotdude on 2013-12-03
[COLOR=#222225][FONT=Arial]ok heres my problem:[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]i just install androidx6 on my hp pavilion dv7 laptop and then installed ubuntu 13.4 also with windows 7.[/FONT][/COLOR]
[COLOR=#222225][FONT=Arial]i configured gub to allow boot of all os/s but heres my main issue[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]in windows 7 i have to start hp connection manager in order to have access to my wifi card so i have wifi ther... androidx86 4.1 jelly i relly dont have to do anything other then turn on wifi to access it but in my ubuntu 13.4 it wont allow me to use my wifi adapter says its hard blocked from rfkill and i used like 4 different wifi cards and still no luck.[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]so why in android which is also linux based i can use my wifi cards but not in ubuntu?[/FONT][/COLOR]

[COLOR=#222225][FONT=Arial]ps in the network menu it says hardware switch turned off even thou its turned on


and how can i get my wifi card to work in ubuntu[/FONT][/COLOR]

---

### Post by jboyette on 2013-12-04
go to the command line, and type rfkill list. Look for the devices that say blocked, then type (sudo if you get permission denied)  rfkill unblock <device>.  That will allow the network card to work.

---

### Post by killerhotdude on 2013-12-04
heres my output for the list command

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

heres wafter i ran the command

root@naru-HP-Pavilion-dv7-Notebook-PC:/home/naru# rfkill unblock all
root@naru-HP-Pavilion-dv7-Notebook-PC:/home/naru# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


any more suggestions?

---

