---
title: "[Howto] Easily use wireless in Ubuntu 8.04"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by chunchengch on 2008-05-10
Here is a easy way to use wireless in Hardy, wish it is helpful to you.

1. Install package hardinfo to see if Hardy catch your wireless controller/card, if it does, congratulation! 

[COLOR="Red"]$ sudo apt-get install hardinfo[/COLOR]

in the screenshot, you can see my wireless controller is detected. 

[ATTACH]69478[/ATTACH]

2. If you have wireless switch on your notebook, turn it on before you power on the notebook.

3. Left-click on the Network Manager icon on the top panel, select one of the wireless networks detected and check it.

4. If you have firestarter installed, it is better to have it installed, then go to the [COLOR="Blue"]Preferences > Firewall > Network Settings[/COLOR], select [COLOR="Red"]Wireless device (wlan0)[/COLOR] in both [COLOR="Green"]Internet connected network device[/COLOR] and [COLOR="Green"]Local network connected device[/COLOR].

OK! now you should be able to use wireless to surf internet.

---

### Post by itzig on 2008-05-12
hmm, I can see my card in harinfo, but no connection is shown in networks manager. why's that?

---

### Post by chunchengch on 2008-05-13
> **itzig said:**
> hmm, I can see my card in harinfo, but no connection is shown in networks manager. why's that?

first, do you unplug your wired connection? wireless connection will not show in networks manager if wired connection is still plugged.

second, is there wireless switch on your notebook? and do you turn it on?

---

### Post by itzig on 2008-05-14
thanks, but I do not have a switch on that card. I tried unplugging the wired connection andrestarted, but still, it won't connect, and it won't show a connection in the manager, but I know there is one here!?
I am using the Linksys WPC54G Card

---

### Post by chunchengch on 2008-05-15
> **itzig said:**
> ... but I know there is one here!?...

maybe you should try it in other public places...

---

