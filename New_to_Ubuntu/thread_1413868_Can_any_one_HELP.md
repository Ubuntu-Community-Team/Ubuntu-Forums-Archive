---
title: "Can any one HELP?"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Dubbz0112 on 2010-02-23
im stuck i need help i have just installed my drivers for my wifi sorces and i need to config the settings for my network i think its saying wlan0 disabled?????:confused:

---

### Post by koba101 on 2010-02-23
first of all....posting I need help as a subject usually won't attract much help.  second, you need to clarify the problem...what version are you using? h/w specs...  maybe on the panel, right clicking on the network icon and enabling wireless would be appropriate...though this is just a shot.

maybe do an ifconfig wlan0 and see what appears

---

### Post by Dubbz0112 on 2010-02-23
sorry ill do that and get it for you

---

### Post by Dubbz0112 on 2010-02-23
my version is 9.10 installed through wubi



Link encap:Ethernet  HWaddr 00:14:a5:2d:2e:09  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by kitschl on 2010-02-23
You can provide details about your configuration that will help us help you. 

Are you using a laptop or a desktop?
[INDENT]--If it's a laptop, is there an external switch for your wireless card? Is it switched on?[/INDENT]
Is your wireless device built-in, or did you install it yourself? Is it PCI or USB? Do you have the model of your self-installed wireless device?
Have you done any research on your wireless device in Ubuntu? Example: Google "enable wireless intel 5300agn ubuntu 9.10 karmic"

Like koba101 said, subject lines like "need help" don't attract much attention. Everybody needs help. "need help" makes people wonder if you can be helped. 

This is good reading, will help you in the future:
[http://catb.org/~esr/faqs/smart-questions.html]("http://catb.org/~esr/faqs/smart-questions.html")

---

### Post by Iowan on 2010-02-23
Post results (from a terminal) of **sudo lshw -C network** - which should show information about your interface(s). **ifconfig -a** will show if interfaces have IP address - and other settings.

---

