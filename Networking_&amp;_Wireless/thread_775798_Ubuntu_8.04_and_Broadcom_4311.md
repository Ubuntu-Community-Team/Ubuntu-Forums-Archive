---
title: "Ubuntu 8.04 and Broadcom 4311"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by cowboys2010 on 2008-04-30
I have a Compaq Presario C700NR laptop with a Broadcom Corporation BCM94311MCG wlan mini-PCI card. I am also running a fresh install of Ubuntu 8.04. I have done nothing to it. No updates or additional software packages. I am pretty much about to give on getting the card to work. It has caused me over a month of frustration. All of the HOWTOs and other forums on this topic have gotten me nowhere. I know about the Ndiswrapper and the bcm43xx, but they have steered me straight into a dead end.  Any advice? Thanks

---

### Post by revmacd on 2008-04-30
Well, I'm not one of the forum admin guys and I am relatively new to Ubuntu myself but I was having the same problem and I'll tell you how I solved it. 

I started running vmware over my windows. I set Ubuntu up as the guest OS in vmware and when I was setting up the machine it asks how you want the wlan to configure. The button I checked was NAT but it wasn't the default button. Doing that makes the wireless card keep running off windows and it's drivers even when you have the guest os running. I forget what NAT stands for but if you read the dialogue when setting up the guest os you'll get it.

I hope it helped. good luck.

---

