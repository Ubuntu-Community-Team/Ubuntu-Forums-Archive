---
title: "Help!! ( absolute beginner )"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by MedeX on 2009-09-15
Hi.. i just installed ubuntu 9.04 on my machine it is Intel 915 .. Erm the graphic card is 82915gl/gv sound card is realtek ac3 hd audio... just thought to give it a try on this machine.. ubuntu is sharing hd with xp... 


Issues are huh i dont knw how and frm where to install drivers for  **THE GRAPHICS AND SOUND CARD**... 
I thought i can do that by connecting to the network but... Ubuntu identifies that there is a mobile broadband connection it thn configures it as well and am getting connected as well but not even a single application can access the network dont knw whats the deal.....


I really want to use ubuntu coz umm i heard that its like prototype?? ANywayz plz help me guyz.... :-s

---

### Post by mapes12 on 2009-09-15
Hi and welcome to the forum

Is your question about your wifi network connection problem?

You may want to change the title of your thread to something like "Help with wifi connection". Others will then be able to pick up your thread quickly.

Meantime, go to Applications>Accessories>Terminal and type ```
lspci
```press enter 

But if you have a USB wifi device change it to ```
lsusb
``` and post the output back here.

---

### Post by MedeX on 2009-09-15
Thanx for the help but basically i need help in  installing drivers for my graphics and sound card :confused:

---

### Post by nothingspecial on 2009-09-15
> **MedeX said:**
> Thanx for the help but basically i need help in  installing drivers for my graphics and sound card :confused:

Is your sound not working?

Is your display not working?

In most cases the sound and graphics cards are already installed.

In your menu go to system > administration > hardware drivers and see if any graphics drivers are in there.

If your sound is not working go applications > accessories > terminal and type ```
aplay -l
``` and post the output back here.

For your wireless please type ```
sudo lshw -C network
``` and post the output here.

With this information hopefully someone can help you.

---

### Post by Bradtek on 2009-09-15
> **MedeX said:**
> I really want to use ubuntu coz umm i heard that its like prototype?? ANywayz plz help me guyz.... :-s

wtf ? :confused:

---

### Post by muteXe on 2009-09-15
Rofl this thread is messed up :)
I'm completely confused.

---

### Post by 3rdalbum on 2009-09-15
> **MedeX said:**
> Hi.. i just installed ubuntu 9.04 on my machine it is Intel 915 .. Erm the graphic card is 82915gl/gv sound card is realtek ac3 hd audio... just thought to give it a try on this machine.. ubuntu is sharing hd with xp... 


Issues are huh i dont knw how and frm where to install drivers for  **THE GRAPHICS AND SOUND CARD**...

They are already present.

For your mobile broadband problem, you might need to add some DNS addresses. Right-click the network manager, click Edit Connections, go to Mobile Broadband and click on your connection. Click the Edit button, go to IPv4 Settings tab, change the method to "Automatic (PPP) Addresses Only" and add the following to the DNS field:

```
208.67.222.222, 208.67.220.220
```

That will use the free OpenDNS servers. You will need to disconnect and reconnect for the change to take effect, I believe. When you have a connection, find out your ISP's DNS addresses from your ISP's website, and put them in instead of OpenDNS.

---

### Post by MedeX on 2009-09-15
Thanx alot 3rd album... :) yup you were rite they are all installed i just needed to install some plugins ...  Now am able to connect my bb and huh i am just lovin it :guitar: 

Thnx all for your help...

P.s!! @ BRADtek buddy i heard that lol how wud i knw i ve just started using it... btw you can clarify why you said so " WT F " haha!! :popcorn:

---

