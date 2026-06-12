---
title: "Understanding Avahi"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by gewitty on 2007-04-23
Can anyone give me a plain English guide to Avahi? Having installed Feisty a couple of days ago, I now find that the network settings page offers me three configuration options for my wireless network: Static, Auto, or Local Zero Conf. Auto was the original setting and this still works (although I had to switch SSID broadcast back on before it could detect the network). When I select Zero Conf, the network still seems to be recognised by WIFi Radar, but the connection doesn't work.

I would like to use Avahi to enable printer sharing and networking with other machines, but having searched around for a Dummies Guide To Avahi, I came up with nothing.

I did download the Avahi Zero Config Browser app. But that leaves me none the wiser either. When I run this, all I get is an Avahi Discovery window which is completely blank. A message at the bottom says, 'No service currently selected'.   

This looks as if it should be a pretty useful utility, but without any clue as to how it works I'm stymied.

---

### Post by ssam on 2007-04-23
[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf) has a bit of information.

the confusing bit is that zeroconf is actually several different things that can work together.

the option in the network settings, is to let zeroconf be in charge of choosing an IP address for you. If you have a router on the network you probably don't want this. The name resolution and service discovery can work independently.

---

### Post by gewitty on 2007-04-23
Thanks Sam. That link helped.

---

### Post by meezilbug on 2008-05-27
I've just installed Ubuntu 8.04, and I'd like to use my printer that is connected to an Apple Airport Express using Bonjour.  I need step by step instructions on how to do this.  I am an avid Mac person, so I am spoiled by having things done for me. :) I decided to venture into the world of Linux, and this is my first stab at it.  Please help my experience be a great one!!  Thank you in advance!!

---

