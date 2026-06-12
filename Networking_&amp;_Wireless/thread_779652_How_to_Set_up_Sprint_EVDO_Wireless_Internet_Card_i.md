---
title: "How to Set up Sprint EVDO Wireless Internet Card in Ubuntu"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by lyndaj70 on 2008-05-02
Hello, all!

I am not sure where to post this, but I just managed to install a Sprint wireless usb evdo internet card on my fiancee's laptop using an easy tutorial directly from Sprint.  

I had tried several of the other tutorials out there, the ones that used gnomePPP and added scripts to your system, and this one is "really" easy and it works.  The only change I would make to it is instead of going to Add/Remove programs to install KPPP, I would go straight to synaptic and get it there, to make sure you don't get the KPPP4, which I could not get to work.

I did get an error on the first step of modprobing usbserial (said it was already loaded), but I continued tofollow the tutorial step by step and it installed so easily!  

Here is the link to the tutorial (a pdf file):

[www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf]("www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf")

It actually works quite well, and as a result of this card my n00b fiancee is now attempting to switch to Ubuntu from Windows (he hates Vista).  We'll see what happens!

Peace!
Lynda

---

### Post by acorn22 on 2008-05-08
I also have a Sprint card and the directions are actually really good. Only problem is I can't connect to the internet to apt-get kppp.

What do I do?

---

### Post by lyndaj70 on 2008-05-08
> **acorn22 said:**
> I also have a Sprint card and the directions are actually really good. Only problem is I can't connect to the internet to apt-get kppp.

What do I do?


You will have to go somewhere you can connect to the internet via another method, like ethernet (dsl) or dial-up or wifi.  I have tried to get the card to work without kppp without success....

Hope this helps,
~Lynda

---

### Post by SukiKreg on 2008-07-01
Hello, I am a new ubuntu user and slow in the head at that. I have gotten to  KPPP add a new account. When I click on the create a new account the KPPP Create new account pops up. However it locks up and I cannot click on wizard or cancel and the manual seup box does not even appear. I am using the Novatel U720 USB....  Any ideas?

---

### Post by SukiKreg on 2008-07-01
Figured I should add some things. 1. The EVDO has already been activated on a windows machine.. I am using the newest version of UBUNTU and I have a inspiron 1501 laptop.

Thanks
Suki

---

### Post by SukiKreg on 2008-07-02
I tried doing the whole thing over again but now when I type in the sudo modprobe -r usbserial I get a fatal module -r not found.....

Some stupid questions.  Should I do the the whole thing with the modem plugged in or unplugged? Does that matter? This is my only internet access so I have to borrow my neighbors wifi until I get this going.... All help would be appreciated it.  The big issue is the KPPP I think, like I said previous when I click on new it seems to lock up with the wizard and cancel unclickable and the manual box missing.

THANKS

---

### Post by lyndaj70 on 2008-07-03
> **SukiKreg said:**
> I tried doing the whole thing over again but now when I type in the sudo modprobe -r usbserial I get a fatal module -r not found.....

Some stupid questions.  Should I do the the whole thing with the modem plugged in or unplugged? Does that matter? This is my only internet access so I have to borrow my neighbors wifi until I get this going.... All help would be appreciated it.  The big issue is the KPPP I think, like I said previous when I click on new it seems to lock up with the wizard and cancel unclickable and the manual box missing.

THANKS

hokay.... first off, have the sprint modem plugged in when you start... I don't believe the usbserial modprobe will work otherwise....  While setting it up can you go anywhere where you can connect to the Internet via ethernet?  I noticed a conflict with my wifi card and had to turn off wireless networking to set up the modem.... can you run Synaptic and see which version of KPPP you are running?  I could only get it to run with the version recommended with the tutorial on the pdf...  I looked and there's specific tutorials out there for your card, but they seem a tad too complicated even for me to follow.... this same tutorial should work for your card, as Ubuntu doesn't so much look at model as type of device, and it should detect one modem same as the other provided it detects it, which I am pretty sure it should...  Also Sprint will attempt to walk you through it over the phone if we can't help you here....  They are very Linux-friendly...

Hope this helps, I will keep looking for a better tutorial for you!

Peace,
Lynda

---

### Post by lyndaj70 on 2008-07-03
Found in another forum that the same tutorial will work with your card... You can go here to read it:  [http://www.linuxquestions.org/questions/linux-wireless-networking-41/novatel-wireless-ovation-u720-and-linux-531408/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/novatel-wireless-ovation-u720-and-linux-531408/")

Hope this helps!
~Lynda

---

### Post by lyndaj70 on 2008-07-03
Here's another tutorial:

[http://ubuntuforums.org/archive/index.php/t-366229.html]("http://ubuntuforums.org/archive/index.php/t-366229.html")

Which I found in this tutorial:

[http://www.radparker.com/2007/11/asus-eee-pc-and-sprint-evdo-easy.html]("http://www.radparker.com/2007/11/asus-eee-pc-and-sprint-evdo-easy.html")


Will add more links if I find them...
Peace,
~Lynda

---

### Post by lyndaj70 on 2008-07-03
Disable wireless networking when you start this.. for some reason there's a conflict...  It will register on your system as an old-fashioned modem, not a wireless connection so it will not show up on your network connections, and you will open kppp to logon to the internet.. when you want to use wifi unhook the sprint card then enable your wireless... 

After you get it set up, you disable wireless, plug in the card, fire up kppp, and tell it to connect using that modem..

---

### Post by dragonlord2598 on 2008-07-11
I have a AMD-64 bit laptop and can not install kppp or kpplogview pls help

---

### Post by lyndaj70 on 2008-07-11
> **dragonlord2598 said:**
> I have a AMD-64 bit laptop and can not install kppp or kpplogview pls help

If you have the 64-bit version of ubuntu you may have to go with the 32-bit to get the programs....  64-bit while great doesn't seem to have as many programs available...

---

### Post by SukiKreg on 2009-01-04
I am back, I lost that laptop shortly after posting. Similar problem. Still have a U720 Novatel USB Sprint modem. Using a HP mini 1030nr with Ubuntu 8.04 netbook remix.  Ubuntu would not allow me to install Kppp for some reason. so I had to install Gnome PPP. I played around with it using the sprint pdf as a guide and I got it to recognize the modem and dial out. The modem blinks and I eventually get a connection but I cannot surf the web. I took some screen caps I hope this helps.  What am I doing wrong?
[IMG]http://web.qx.net/tomhamilton/connectdetails.png[/IMG]
[IMG]http://web.qx.net/tomhamilton/connectdetails.png[/IMG]

---

### Post by SukiKreg on 2009-01-07
Bada Bump

---

### Post by Mach1US on 2009-01-15
If your card does not work out of the box you my try some of those tweaks:

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

