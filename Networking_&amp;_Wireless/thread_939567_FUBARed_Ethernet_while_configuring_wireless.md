---
title: "FUBARed Ethernet while configuring wireless"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Jason124 on 2008-10-06
Good evening (in LA at least), I was trying to tackle the task of configuring my Dell 1390 wireless card on a Dell E1505 laptop. All went according to [this]("http://vladgh.com/2008/05/31/dell-wireless-1395-card-and-ubuntu-hardy-heron/") tutorial until I got to sudo rmmod ssb. At which point it said "ERROR: Module ssb is in use by b43" and I restarted. Well, it seems whatever I did, I lost my ethernet connection, and wireless isn't configured.

I'm not a complete stranger in Linux but, I am letting my sense of adventure get to the best of me. Help?

---

### Post by nixscripter on 2008-10-06
Perhaps a simple typing mistake on the part of the author (or a different configuration for you):

> 
Insert these lines ABOVE &#8220;exit 0&#8243; line:
```

    modprobe -r b44
    modprobe -r ssb
    modprobe -r ndiswrapper
    modprobe ndiswrapper
    modprobe ssb
    modprobe b44

```


Change **b44** to **b43** in every case.

---

### Post by Ayuthia on 2008-10-06
> **nixscripter said:**
> 
Change **b44** to **b43** in every case.

Actually, you don't want to change b44 to b43.  If you do that, you will be loading two wireless drivers for your card and they will run into conflicts.

However, can you post the results of lshw -C network and lspci -nn?  Also can you post your /etc/rc.local?  Most likely there is something in this file that is causing the problem.

---

### Post by nixscripter on 2008-10-06
I meant that in the instructions provided, the conflicting driver (which it was trying to remove) was b44. The conflicting driver in his case appears to be b43.

So when the guide says b44 in the quote I mentioned, I would only suggest replacing it with b43, meaning that's what it would remove.

---

### Post by Jason124 on 2008-10-07
Hello and thanks for reading.

A bit of "good" news, I brought my laptop home today and hooked it up to the ethernet here and it works. It could've been that there was a network fluke at my apartment.

I've also removed any modifications I've done to the rc.local file but posted it anyways.


[rc.local]("http://pastebin.com/m123b5a4")

and the output of my lspci -nn can be found [here]("http://pastebin.com/m2e7ab0b1")

---

### Post by Ayuthia on 2008-10-07
My guess is that something was either incorrect in the rc.locl before you removed the script or else something bad happened when ndiswrapper was loaded.  You are one of the few that does need the b44 driver so it looks like b44 or ssb was not loaded back after ndiswrapper was loaded.

You have a 4311 rev 01 card.  Did you try using the b43 driver with it?  If you have, how was it?  Also, the wl driver should work with it also.  Here is the link for the wl driver:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

However, if you have not tried the b43 driver, you might want to do that.  It will help prevent you from having to do any work arounds with ndiswrapper or wl.

If you do want to still use ndiswrapper you should try the following to see what happens (will only last for the session):
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
```
This is the same thing as the script.  Like I mentioned earlier, the b44 driver is the one for your wired card.  That and ssb need to be loaded in order for the ethernet card to work.  To verify that it is loaded:
```
lsmod|grep -i -e b44 -e ssb
```

---

### Post by Jason124 on 2008-10-07
I haven't tried the b43 driver yet, I wasn't sure where to go about configuring it so I just googled it and after reading a few how-tos, just stuck to one. At this point is there anything that needs to be done before attempting b43 drivers? Do i have to wipe the previous driver installs (a la windows) prior to continuing? I don't want to dig myself into a deeper rut.

Update: 

Just tried it and I believe it didn't work. I got to step 4 which is:

> 
4. **Test the new wireless driver**
Now, lets test out our new wireless driver. Enter:
```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko 

``` 

If it worked, and you can see/connect to wireless networks, you'll want to:

I went to the network icon in the upper right and clicked on wireless networks (I'm assuming this is where I go) and it does not list any networks nor does it allow me to add one.

---

### Post by Jason124 on 2008-10-07
double posted

---

### Post by Ayuthia on 2008-10-08
> **Jason124 said:**
> I haven't tried the b43 driver yet, I wasn't sure where to go about configuring it so I just googled it and after reading a few how-tos, just stuck to one. At this point is there anything that needs to be done before attempting b43 drivers? Do i have to wipe the previous driver installs (a la windows) prior to continuing? I don't want to dig myself into a deeper rut.

Update: 

Just tried it and I believe it didn't work. I got to step 4 which is:



I went to the network icon in the upper right and clicked on wireless networks (I'm assuming this is where I go) and it does not list any networks nor does it allow me to add one.

My guess is that the b43 module is still causing the conflict.  Try the following and see if it works:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo modprobe b44
```
What this will do is remove all the conflicting drivers, load the wl module and then load the b44 module (since ssb needs to be loaded after the wl module).

---

### Post by Jason124 on 2008-10-08
> **Ayuthia said:**
> My guess is that the b43 module is still causing the conflict.  Try the following and see if it works:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo modprobe b44
```
What this will do is remove all the conflicting drivers, load the wl module and then load the b44 module (since ssb needs to be loaded after the wl module).

Thanks! Got it working with those 4 lines but I have a small problem. Every time I reboot, I have to rerun those 4 lines in order to get it to work.

I've added blacklist-bcm43 to /etc/modprobe.d with the following 
```

blacklist b43 
blacklist ssb 
blacklist b43legacy

```
and removed ndiswrapper from modprobe.d

I've performed the steps below to make things "permanent" but it doesn't seem to be working.

> **Ayuthia said:**
> 
```
sudo depmod -a
echo wl |sudo tee -a /etc/modules
```
The depmod -a command will update your modules list.  After that, you will be able to automatically load the module in /etc/modules or if you want to load it manually:
```
sudo modprobe wl
```

The ieee80211_crypt_tkip will automatically be loaded when the modprobe wl is done.


---

### Post by Ayuthia on 2008-10-08
> **Jason124 said:**
> Thanks! Got it working with those 4 lines but I have a small problem. Every time I reboot, I have to rerun those 4 lines in order to get it to work.

I've added blacklist-bcm43 to /etc/modprobe.d with the following 
```

blacklist b43 
blacklist ssb 
blacklist b43legacy

```
and removed ndiswrapper from modprobe.d

I've performed the steps below to make things "permanent" but it doesn't seem to be working.

Ok.  Did you also copy the wl.ko file to a place in /lib/modules?  Once you have done that, you can then add the following:
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
This is similar to the ndiswrapper version, but it is located in /etc/modprobe.d instead of /etc/rc.local.  I prefer to have the code there so that it is only used for this module.

Let me know if this works.  If for some reason you lose your wired connection and need it back, just make sure that the wired module is still there and then you can load it back:
```
lsmod|grep -e b44 -e ssb
sudo modprobe b44
```

---

### Post by Jason124 on 2008-10-08
wl.ko is in the /lib/modules/2.6.24-19/wlan folder and yes, the
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
did resolve it. Thanks again!

---

### Post by nixscripter on 2008-10-09
Great. Please mark the thread as solved (under the thread tools menu).

---

