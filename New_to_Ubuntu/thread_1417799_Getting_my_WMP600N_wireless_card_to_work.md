---
title: "Getting my WMP600N wireless card to work"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by CampDrex on 2010-02-27
The card recognizes the wireless network in my home but will not connect. Is there a quick solution? Running newly installed 9.10 on a new machine with Win 7 installed (dual boot).:p

---

### Post by CampDrex on 2010-02-27
I guess it's back to step 1. Reload ubuntu 9.10 to see if network will recognize and stay on line. What's funny is that I can see my network and networks all around my house but it won't stay on line......

---

### Post by ercferret18 on 2010-02-27
you could try making sure the wireless switch is on

---

### Post by CampDrex on 2010-02-27
The Linux machine recognizes the network and I'm posting on the windows machine. Pardon my noobiosity but to which switch are you referring?

---

### Post by ercferret18 on 2010-02-27
sometimes there is a hot key (like Fn+F2) that you can press to activate wireless, and it won't work unless this switch is pressed.

---

### Post by CampDrex on 2010-02-28
PackerFan I think you have it all wrong. My wireless card is a PCI card installed in a desktop. I have a Linksys WMP600N PCI card and when in NM it looks and sees my network name it just won't connect. I have re-installed 9.10 and even removed the Windows partition so the machine is only running ubuntu. That has not improved the  situation. I think there may be something simple that will get me going but a hotkey is not it.

---

### Post by bkratz on 2010-02-28
> **CampDrex said:**
> PackerFan I think you have it all wrong. My wireless card is a PCI card installed in a desktop. I have a Linksys WMP600N PCI card and when in NM it looks and sees my network name it just won't connect. I have re-installed 9.10 and even removed the Windows partition so the machine is only running ubuntu. That has not improved the  situation. I think there may be something simple that will get me going but a hotkey is not it.

Look at post 17 in this thread and pay attention to the type of encryption, it may be your problem too.

[http://ubuntuforums.org/showthread.php?p=8650314&highlight=WMP600N#post8650314](http://ubuntuforums.org/showthread.php?p=8650314&highlight=WMP600N#post8650314)

---

### Post by CampDrex on 2010-02-28
> **bkratz said:**
> Look at post 17 in this thread and pay attention to the type of encryption, it may be your problem too.

[http://ubuntuforums.org/showthread.php?p=8650314&highlight=WMP600N#post8650314](http://ubuntuforums.org/showthread.php?p=8650314&highlight=WMP600N#post8650314)
I'm going to give this a try...

---

### Post by CampDrex on 2010-03-06
I am still struggling with this but not giving up yet. I have read where ndiswrapper may help. (I am such a noob) I am trying to check through all of the configuration information for my card. What is the most frustrating thing is that the card is communicating and can see my and other local wireless networks. I KNOW I am soo close...

---

### Post by bkratz on 2010-03-06
> **CampDrex said:**
> I am still struggling with this but not giving up yet. I have read where ndiswrapper may help. (I am such a noob) I am trying to check through all of the configuration information for my card. What is the most frustrating thing is that the card is communicating and can see my and other local wireless networks. I KNOW I am soo close...

Please copy/paste the outputs of the following back here:

sudo lshw -C network
iwconfig

The first command will require your password which will not be echoed to you, it is LSHW in lowercase and C in upppercase.
The terminal is located at Applications>>Accessories>>Terminal.

---

### Post by vprajapati on 2010-03-06
> **CampDrex said:**
> The card recognizes the wireless network in my home but will not connect. Is there a quick solution? Running newly installed 9.10 on a new machine with Win 7 installed (dual boot).:p

If u have installed the pci wireless card in ur desktop, u will have to be installed the wireless card driver.
The driver cd comes with the wireless card, so plz install that one.
install ndiswrapper Linux kernel module  from sysneptic package manager.

Vijay Prajapati,
Gemstone, 2ghz, 3gb ram

---

### Post by bkratz on 2010-03-06
Found another good thread

[http://ubuntuforums.org/showthread.php?t=1423100](http://ubuntuforums.org/showthread.php?t=1423100)

---

### Post by CampDrex on 2010-03-07
bkratz, Thanks for your kind concern. I finally just physically moved the system to a wired location, got the network to recognize my machine and I am sure the multitude of positive feedback on the WMP600N will prove true. This ia a new machine with Karmic loaded with nothing else so there is no reason for it not to work once I am updated!! Famous last words... I will close the thread SOLVED within the next day or two... FLW...;)

---

### Post by CampDrex on 2010-03-07
I read that post and it sounds as though he had my problem. I will go back there when it's time. Thanks again!

---

### Post by CampDrex on 2010-03-07
I'd like to say something highly technical and full of pith as are some of the more experienced posts. The simple solution was to configure the system for a wired connection if available, update and install the WMP600N and configure. I was not an instant "on" with my wired connection but the configuration is straightforward and took no time.
The wireless card was an instant "on" OOB. What a relief!

Thanks to bkratz for the helpful links they will come in handy I am sure.

---

### Post by bkratz on 2010-03-07
Congratulations! Glad to see you got everything going.

---

