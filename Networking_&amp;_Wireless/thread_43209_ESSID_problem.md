---
title: "ESSID problem"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by Chrus on 2005-06-21
Hey peoples. Im new here... so before i start ill give a quick intorduction of myself. The nemes Chris... Im from Sydney Australia. Currently studying Networking (which is ironic cos the problem im having at the moment is a networking problem). Ive been meaning to get into Linux for ages, but up untill now, I havent found any distro that I liked enough to use as a full time opperating system.

Anyway... back to my question.

Ive just installed Ubuntu (from what ive seen so far, it looks like a great distro) and installed and set up NDISWRAPPER for my wifi. Now ive put in all the stuff like ESSID, wep key, etc... but its not working. First problem is that its not coming on at all. In the GUI it says its activated, but there are no lights on on my network card.

Second problem is that even though ive put in the ESSID (ive tried in both the GUI and at command line), but when i do an "iwconfig" it tells me i dont have an ESSID.

Any help would be greatly appreciated.

Thanks in advance.
Chrus.

---

### Post by stonecrest on 2005-06-21
[QUOTE=Chrus]but there are no lights on on my network card.[/QUOTE]

Do you mean that the power light is off as well? If that is the case, then ndiswrapper has not been correctly installed and/or set up. Type ndiswrapper -l to make sure that you have loaded the card's drivers. When you type "sudo modprobe ndiswrapper" is when your card should power on - if it isn't, check the log files to see if there is an error msg anywhere.

---

### Post by Chrus on 2005-06-21
Yeah... Im not getting any lights at all.

Whats with the sudo??? do i need that??? I only did "modprobe ndiswrapper"...

---

### Post by Chrus on 2005-06-24
*bump*

Still havent got it working. Anyone have any suggestions???

---

### Post by fizgig on 2005-06-24
you need sudo to modprobe.  type **lsmod |grep ndis **to see if it is indeed loaded.  If so, make sure the drivers are there with the aforementioned ndiswrapper -l.

In the future, more info is helpful.  The type of network card you're using, the response from the computer to each command you give it, perhaps the output from **lspci **and so forth.

---

