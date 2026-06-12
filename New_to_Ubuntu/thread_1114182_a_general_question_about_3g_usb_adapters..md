---
title: "a general question about 3g usb adapters."
date: 2009-04-02
forum: New to Ubuntu
---

### Post by techno-mole on 2009-04-02
hello, i have a general question about usb 3g adapters (as you can get from vodafone, orange etc) the kind that you would use on a laptop or notebook for internet access.

the question being how well do these run on linux (ubuntu)? do they need any software ? or are they plug and play kind of thing ?

i have another small question regarding usb devices in general.

basically does the system keep a log of every usb device thats plugged in ? and where might i find the logs, and also does it log devices that have been plugged in even if they arent plugged in al
t the time ?

cheers

---

### Post by cptrohn on 2009-04-02
> **techno-mole said:**
> hello, i have a general question about usb 3g adapters (as you can get from vodafone, orange etc) the kind that you would use on a laptop or notebook for internet access.

the question being how well do these run on linux (ubuntu)? do they need any software ? or are they plug and play kind of thing ?

i have another small question regarding usb devices in general.

basically does the system keep a log of every usb device thats plugged in ? and where might i find the logs, and also does it log devices that have been plugged in even if they arent plugged in al
t the time ?

cheers

I'm not sure about all of them, but I do know that the Novatels work with linux.... EVDOforums is a great place for finding out about each products capabilities.

---

### Post by popuptarget on 2009-04-02
Techno,

   Just popped in a USB 3G verizon on my 'buntu just to see and answer your question.  I have a Verizon 3G express card already configured that did not need software so to answer your question. Yes it seemed to just work.  I disconnected the express card, plugged in the usb and reaquired the network. Matter of fact I am writing to you on the usb3G.  As for the log I will have to look around for that.

Popup

---

### Post by philinux on 2009-04-02
/var/log/messages 

This file shows usb devices being plugged in and registered and being unplugged.

---

### Post by dje on 2009-04-02
huawei e160g from 3 UK worked out of the box in intrepid for me

---

### Post by sailor2001 on 2009-04-02
I have a real cheap AN 802.11g USB adapter that I think I paid about $19.95 for and it works great on windows and Ibex

---

### Post by lemmy999 on 2009-04-02
Huawei E270 and Vodafone hsdpa sim ( both from Ebay) works well for me in the UK.No configuring needed, network manager just works!:p

---

### Post by GeorgeVita on 2009-04-02
Hi **techno-mole**, about 3g modems:

At first you must determine the real manufacturer and model of the modem and not the "masked" Provider name.

A source to see if a modem works directly in Ubuntu 8.10 is the file:
**file:///usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**
copy paste the above as an internet address to Firefox.

Search for **Huawei** or **MF628** (for a manufacturer or a model)

Note that often models of the the same manufacturer appear as a basic modem of the same manufacturer (ex. Huawei E170 is like E220).

...searching to this forum is always a source!

Regards,
George

---

### Post by ulfj on 2009-04-02
I've been trying to get a verzion usb720 to work but not having any luck but refuse to give up.Others have gotten the same device to work so it can be done,I'll just keep on plugging away.

---

### Post by Sealbhach on 2009-04-02
Huawei E220 works as well, network manager knows what to do.


.

---

### Post by cornish12 on 2009-04-09
I'm using E160G from 3 and and it works great with Ubuntu. Speed is slower than expected but that I guess is variable.

---

### Post by MaxCordell on 2009-06-12
(Posting in the UK, Ubuntu newbie) Running Ubuntu  9.04
Vodafone USB mobile broadband works just fine.  Just plug in and go.  Reading these threads I was worried that installation would be too technical and "under the hood" but Ubuntu takes care of it for you.  It recognises the presence of a USB mobile broadband, asks which provider and which tarriff you're on and away you go.
It seems that the time taken to connect is much faster with Ubuntu than with Windows, and could it be signal strength is stronger? That doesn't make sense, but the signal strength indicator suggests it is so. 
 
One warning: the USB is loaded with mini programs that run under Windows, for SMS messaging and for topping up your account.  You lose these with Ubuntu.  So to top up you'll need either to plug the USB into a Windows machine, or register your USB at the Vodafone website, after which you can access their website and pay by credit card online.

---

