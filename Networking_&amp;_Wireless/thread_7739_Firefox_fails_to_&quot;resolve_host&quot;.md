---
title: "Firefox fails to &quot;resolve host&quot;"
date: 2004-12-10
forum: Networking &amp; Wireless
---

### Post by canwopit1 on 2004-12-10
Hello everyone.

I'm completely new to the world of Linux, though (with the help of a friend) I've been able to install a couple of other distros, Mandrake 10.0 SuSe 9.2 Pro. Recently, I went to a Linux workshop (that ran for a day) and the people there suggested I try using Ubuntu and... I love it! Especially how fast it is. I can't wait to make it my only operating system!

Though, I have a problem that I can't seem to solve, even if I've looked at other threads and forums. I realise that this may sound stupid, but I can't connect to the internet - I'm using win2k for that. Everytime I try, Firefox "fails to resolve host". My system is an Asus L3800C series laptop with a P4 processor and 512MB RAM. My wireless network card (D-link dwl-650+) is in working order, all lights are on. I tried modifying some of the network settings in the system manager, but I can't find any related to the "channel" or the "BSS/IBSSID", the wireless network card uses.

I would be grateful if anybody could give me some advice concerning my problem.

Cheers.

---

### Post by wulf on 2004-12-11
[QUOTE=canwopit1]Hello everyone.

I'm completely new to the world of Linux, though (with the help of a friend) I've been able to install a couple of other distros, Mandrake 10.0 SuSe 9.2 Pro. Recently, I went to a Linux workshop (that ran for a day) and the people there suggested I try using Ubuntu and... I love it! Especially how fast it is. I can't wait to make it my only operating system!

Though, I have a problem that I can't seem to solve, even if I've looked at other threads and forums. I realise that this may sound stupid, but I can't connect to the internet - I'm using win2k for that. Everytime I try, Firefox "fails to resolve host". My system is an Asus L3800C series laptop with a P4 processor and 512MB RAM. My wireless network card (D-link dwl-650+) is in working order, all lights are on. I tried modifying some of the network settings in the system manager, but I can't find any related to the "channel" or the "BSS/IBSSID", the wireless network card uses.

I would be grateful if anybody could give me some advice concerning my problem.

Cheers.[/QUOTE]
 I doubt your problem is with Firefox; I'm assuming that nothing on your system connects to the Internet.

How is your connection set up? Laptop to wireless network card to ??? to Internet Service Provider to Internet?

I'm using a laptop with an ethernet cable going to a 5-port switch, linking to a Zoom ADSL ethernet modem. When I had problems the other day I used the *ping* command to establish that I could 'see' the modem but not anything beyond it. Later on, when I got to work, I checked the ISPs "service status" page and, sure enough, there had been some problems with their network earlier in the day.

In troubleshooting your problem, I think the first step is to work out whether your laptop is having a problem seeing your local network (there should be something on there you can ping) or if it can get around find locally but is having problems routing further afield (in which case it could be that your DNS entries need checking).

Wulf

---

### Post by canwopit1 on 2004-12-16
Thanks for the advice on tackling the problem. Over the past few days, I've been changing various values, within the Gnome network manager, to see whether or not I could ping my router. The network is setup in the following way: laptop to wireless access point, which then connects to the router and, that, to the ISP. Everytime I ping the router, I get a list of "answers", which goes on and on, from the router's IP, and not the usual 4.

That's still the reason why I'm wondering if there aren't any commands that would allow me to specify: 1) the frequency/channel to which to set my NIC; 2) the Medium Access Control number of my wireless access point, so the NIC can automatically recognize it.

Thank you again for the advice.

Cheers.

---

