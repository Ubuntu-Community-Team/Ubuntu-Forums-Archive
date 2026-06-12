---
title: "atheros Wifi range is very short."
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by theheadlessrabbit on 2008-11-21
ok, i am having a bizarre wireless problem that i can't seem to figure out.

i have a 'fugitsu lifebook series A' laptop, with a dual boot WinXP and ubuntu.

my atheros wifi card works fine in windows, but in ubuntu, its range is severely limited.

on a fresh install, ubuntu sees my card without a problem, and 2-3 signals are detected automatically, (mine and the neighbor's) 
when i hit the icon, I see the signal name, signal strength, and whether or not it's protected.  everything looks like it's working perfectly. 

but when i try to connect to any of the networks, it doesn't work.  it tries to connect for 5 minutes or so, then gives up. and says 'unable to connect'

this is the weird part: if i am sitting right beside my wireless router, everything works fine.  as soon as i get more than 1-2 meters away, and the signal drops bellow 90% (approx.) it stops working.

this happens in versions 7.10, 8.02, and 8.10.  i've tried ndis wrapper on 8.02 and 8.10, with no change.

i know it's not a hardware thing, because I'm sitting a good 10 meters away from the router as i type this (in winXP).

what is going on, and how do i fix it?

---

### Post by raiwo on 2008-11-21
* have only one solution for this one: use ndiswrapper. I have used atheros card & madwifi drivers for a year now and have not been able to find any other solutions forthis one. My singal strength is about 20-30% lower when using madwifi drivers than in vista or when using ndiswrapper  *

---

### Post by theheadlessrabbit on 2008-11-21
> **theheadlessrabbit said:**
> this happens in versions 7.10, 8.02, and 8.10.  **i've tried ndis wrapper on 8.02 and 8.10, with no change**.


ndis wrapper makes no difference in this case.  when i am right beside the router, wireless works fine both before and after i install ndiswrapper.    skype, pidgin, firefox, etc. all work flawlessly.

but, as soon as i take 2 steps away from the router. the network craps out, and stops working.  pidgin disconnects, firefox wont load any webpages, etc.

keeping my computer beside the router at all times is not an option.

---

### Post by pyrotech on 2009-03-01
Found any solution to this?

I have the same problem in jaunty.. 
Lousy wireless-signal.
And if the reception-level goes below 50 %, Ubuntu refuses to send\receive anything..

---

### Post by davym on 2009-03-01
I don`t know if this will help,but when i setup my main pc upstairs using xp i found i got a  better signal just by turning my router on its side it went from good to excellent.(Linksys 54g

Good Luck.


I am new to ubuntu recently put it on laptop,i am so impressed i am thinking of putting it on main pc dual boot.

---

### Post by theheadlessrabbit on 2009-03-01
> **pyrotech said:**
> Found any solution to this?

I have the same problem in jaunty.. 

I've tried just about every wifi solution on this site and nothing works. 
the only solution I have found is going back to windows XP.

I love Ubuntu, but I need my wireless to work.  this issue is a deal breaker for me.

---

### Post by Crafty Kisses on 2009-03-01
If you have the Atheros AR242X card this has actually been solved with a newer driver for this card, you can download it right [here.]("http://file-hosting.site-hosts.net/eeepc/madwifi-nr-r3366+ar5007.tar.gz") Once you have it installed compile it from source and install it, and your wireless card should work a lot better. So copy this folder to wherever you want when you're done downloading. Remember you need the build-essential package, but run these commands in these steps and you should be fine:
```
sudo apt-get install build-essential
cd /home/username/foldername
tar xzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007/
make
sudo make install
```
Once you have done that in order, the new driver should be compiled and you want to reboot by running the following:
```
sudo shutdown -r now
```
Once you have rebooted you should be good to go and your wireless should work a lot better.

---

### Post by theheadlessrabbit on 2009-03-01
thanks for the help, I really appreciate someone taking the time to actually read what I wrote and give a proper response. 

but my card is the AR5006EXS.  would that same solution work?

---

### Post by Ice Dragon on 2009-08-05
I had similar issues with an atheros wireless in my laptop, this command resolved the issue for me in Ubuntu 9.04

> sudo apt-get install linux-backports-modules-jaunty

---

