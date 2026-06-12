---
title: "New linux 4965agn drivers"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by carpex on 2007-06-12
Hi, as anyone tried the new Intel Wireless 4965agn drivers for Linux (from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)) with Feisty? Any luck? Anyone tried on a 64 bit install?

Anxious to hear your answers. I'm a bit nervous installing this one since the ndiswrapper install I tried previously prevented my system to boot...

CP

---

### Post by carpex on 2007-06-12
By the way, I found debs here:

[http://sidux.com/debian/pool/non-free/i/iwlwifi-4965-ucode/](http://sidux.com/debian/pool/non-free/i/iwlwifi-4965-ucode/)

Update: these are debs for uCode images only. They don't install the driver.

CP

---

### Post by reidbold on 2007-06-12
I'm having no luck building from source. When I get to the part about testing the build ([http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)) the 'load' script throws up a syntax error. I'll try the debs.

Debs: Driver loads with no errors, no wireless devices recognized.

---

### Post by JoePits on 2007-06-13
> **carpex said:**
> By the way, I found debs here:

[http://sidux.com/debian/pool/non-free/i/iwlwifi-4965-ucode/](http://sidux.com/debian/pool/non-free/i/iwlwifi-4965-ucode/)

CP

omg u r my savior

---

### Post by renerey on 2007-06-13
hey guys, has anyone tried this iwlwifi driver yet? i believe it's not just the iwlwifi driver that needs to be installed. you also have to install the mac80211 before it? has anyone been successful doing both? please let me know. thanks. 

i haven't have time to do it myself. i guess this weekend i'll try.

---

### Post by carpex on 2007-06-13
I don't think you need to install the mac80211, I think this is already part of Feisty. I tried installing the debs, and the installation works but drivers don't seem to get loaded or activated, although $modprobe  iwlwifi does work. 

Update: the debs only install the uCode images, not the drivers.

Hope somebody can figure this one out...

CP

---

### Post by renerey on 2007-06-13
just a thought, is mac80211 is running in your modules? i think it is needed to run the iwlwifi driver. do a lsmod. if mac80211 is not there then you would need to have it loaded in your modules. run $modprobe mac80211. hope this works out.

---

### Post by carpex on 2007-06-13
Renerey, yes, mac80211is running. And lsmod even mentions:

Module                  Size  Used by
iwlwifi                96412  0 
mac80211              192388  1 iwlwifi

So, I guess this part of it works ok...

But running ifconfig wlan0 up   doesn't work.

CP

---

### Post by renerey on 2007-06-13
im going to try it on mine now too... i just need to disable my ndiswrapper. i'll let you know if i have any luck.

edit
after much looking into and googling stuff for this, this is what i got so far.
[http://kerneltrap.org/node/7704](http://kerneltrap.org/node/7704)

in the link above, the new mac80211 and iwlwifi would be included in the new kernel 21 or 22. definitely the 22.

@carpex
i guess you need the new mac80211 loaded in your modules and not the one included with feisty.

---

### Post by srini91 on 2007-06-14
I tried the manual compile steps on a fresh install of 7.04.  I got as far as running "load", but it kept throwing syntax errors about unexpected parentheses.

What I did, from roughly fresh install was:

1. build the mac80211 against /lib/modules/.../build (had to pass custom parameters for SHELL and KSRC) and did the make  kernel_patch - but I didn't recompile the kernel itself, as I figured it already had mac80211; we just need the sources?

2. build the iwlwifi, again passing custom params; the build seem to work ok

3. load fails with shell syntax error

I gave up for now, but I hope that helps someone out.  

As for alternatives, I don't want to use NDISWrapper because it locks you out if you don't turn off your wireless before logging out!  I guess I'll wait til kernel 2.6.22+.

---

### Post by carpex on 2007-06-14
@srini91  Did you try $modprobe iwlwifi ? Did you build both the uCode images and the drivers?

CP

---

### Post by rye_ on 2007-06-16
hi,

I've tried several different tacks in employing this driver.

=> building from source (can't build mac80211)
=>applying .deb packages (outdated)
=>building .deb files from .rpm files (newest)

From all this methods I failed to get a response.  My knowledge of the linux kernel is very, very limited.
I wonder if it may not be possible to directly apply some of the required packages with the existing kernel.
Could somebody with more knowledge could clarify this?

Ryan

---

### Post by vronp on 2007-06-19
Has anybody tried the steps listed in this HOWTO ???

[http://ubuntuforums.org/showthread.php?t=396204&highlight=4965&page=3](http://ubuntuforums.org/showthread.php?t=396204&highlight=4965&page=3)

---

### Post by rye_ on 2007-07-05
Hi all,

I've got it working using zoltan's guide and updating to the gutsy kernel.
see the following page;

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

---

