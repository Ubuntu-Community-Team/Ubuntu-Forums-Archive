---
title: "networking adapter"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by dazed and confused on 2005-11-12
All right guys, I need a step by step walk through as to how to install my networking adapter.  I have a belkin wireless g PCI network card.  I am a complete noob to linux, but installed breezy so I could learn my way arround, I am great with all versions of windows, but linux is like a forign language to me.  Pleaese walk me through.

---

### Post by Lambert on 2005-11-12
More is needed about the card to see if there is a native linux driver or we have to use ndiswrapper with the windows drivers.

First, open a terminal (Applications>Accesories>terminal) and type in this..

```
sudo lshw -C network
``` 
then come back and post the output here.

[COLOR=DarkRed]sudo[/COLOR] gives you admin/superuser priveledges
[COLOR=DarkRed]lshw -C network[/COLOR] will list info about your hardware

if you want you can type  in the search field your belkin model and see what others have posted about this card.

if find you have to use ndiswrapper you can follow instructions [[COLOR=Blue]here[/COLOR]]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu"). The steps here are done on the command line.

If you have internet access to this machine while logged in to ubuntu, you can download an app called [COLOR=DarkRed]ndisgtk. [COLOR=Black]If you don't know how to install an app then go [COLOR=Blue][here. ]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")

[COLOR=Black]Once installed you can click System>Admin>windows wireless drivers

Have your windows drivers handy and click through the prompts.

Once you have a driver installed you click on System>admin>network, find the wireless device, highlight, click on properties, enter your network info, click ok, then click activate.



[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by dazed and confused on 2005-11-12
I know that my adapter does not have any native linux drivers.  Running the command  through the termanal resulted in 2 headings, one labeled "format can be" and the other was "options can be", both had several options below them.  I will try and work with ndiswrapper.

---

### Post by dazed and confused on 2005-11-12
My card is a belkin F5D7000 Rev.3.  ndiswrapper will not read the files of my CD drive, where shopuld I put the .inf file so ndiswrapper will read it?

Thanks 
D&C

---

### Post by dazed and confused on 2005-11-12
Never mind guys.  I moved the .inf file, ndiswrapper worked, and I am now posting through linux.:D

---

