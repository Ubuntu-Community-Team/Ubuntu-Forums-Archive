---
title: "Freezes after login"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by strunkbunch on 2009-01-02
I used a live CD to install in windows. I tried using from live CD and it kept locking up. Installed it and after login locks up on tan screen with mouse pointer or black screen with working mouse pointer. I saw a post on install issues where there is a similar issue and this is the response:

[I]I found the answer by looking around the forums some more. 

In the fail safe terminal I uninstalled compiz and it booted fine. 

Originally Posted by jerrylamos View Post
Any number of us are having problems with 8.10 compiz. My thinkpad gets a black or tan screen instead of a desktop. The workaround in Launchpad Bug #259385 is:

boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If later on you want to try compiz you can install it with Synaptic. As of today compiz still freezes my pc. The "official" fix is blacklisting some graphics hardware so that compiz won't start.

Jerry

p.s. might help if you listed your hardware[/I]

He had a Dell 2400 I have a Dell Dimensions 2350 and a Netgear wireless card. I want to know if I do this will it effect windows at all? I would like to try Ubuntu but as of yet no such luck.

---

### Post by cmnorton on 2009-01-02
My first thought is this is a graphics problem. You thought this as well, because you removed compiz. I also suggest booting into recovery mode and running dpkg-reconfigure xserver-xorg. Take all default responses, except consider consider other lower graphical configurations. Also consider replacing any propietary driver with vesa, until you can boot normally. 

Then you could try replacing the vesa driver with the driver that will support your advanced graphics. These days that is usually nvidia..

---

