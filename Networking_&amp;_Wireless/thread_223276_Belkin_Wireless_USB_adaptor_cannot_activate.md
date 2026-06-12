---
title: "Belkin Wireless USB adaptor cannot activate"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by geroy on 2006-07-26
hi,
ive recently downloaded and installed Ubuntu, and i must say i love it so far!
1 problem i am having, is setting up my wireless. I have a Belkin 54g wireless USB adapter. It is visible in the network connections window, but when i attempt to active it, the system locks up, and i have 2 reboot.
I have also tried using my windows driver, and NDISwrapper, which tells me the hardware is present, but still, which i try and active the device it crashes the pc and i have 2 restart!

I have ruled out that i have a faulty USB stick, as i have more than 1, and i get the same problem with the others.

Anyone got any ideas what my problem is?](*,) 

thanks in advance :) :)

---

### Post by Mark_R on 2006-08-23
Same problem here. Did you get it working?

---

### Post by jimlockerd on 2006-09-06
Belkin usb wireless adaptor.
I had it working yesterday but I reinstalled ubunto for a reason and havent gotten it to do anything since except crash the system when it goes active. I was not using ndiswrapper.  I believe it crashes when it sees the network.
Jimlockerd

---

### Post by Pat Mustard on 2007-06-25
> **jimlockerd said:**
> Belkin usb wireless adaptor.
I had it working yesterday but I reinstalled ubunto for a reason and havent gotten it to do anything since except crash the system when it goes active. I was not using ndiswrapper.  I believe it crashes when it sees the network.
Jimlockerd

Hi

I guess this was a while back, but today I am having the same problem!

I had a Belkin usb wireless adapter working on Feisty.
Reinstalled Ubuntu and now plugging in the adapter causes the system to crash.

Did you ever get a solution to this?

---

### Post by Austin_KW on 2007-06-25
> **Pat Mustard said:**
> Hi

I guess this was a while back, but today I am having the same problem!

I had a Belkin usb wireless adapter working on Feisty.
Reinstalled Ubuntu and now plugging in the adapter causes the system to crash.

Did you ever get a solution to this?

The hang/crash is usually due to multiple drivers trying to manage the adapter, what model and version is the adapter?

---

### Post by Pat Mustard on 2007-06-26
Hi Austin_KW

Thanks for responding. :-)

I am using a Belkin wireless-G USB adapter F5D7050, not sure of the version off hand.

I previously had it working using the serialmonkey rt73 replacement driver.

I finally got it working on the fresh install last night.  From reading the forums I got the impression that it might be caused by other drivers so I removed and blacklisted all the drivers that serialmonkey covers, completed the rt73 setup and eventually coaxed it into working. :D

I'm glad it all works but I can't quite figure out why this didn't happen before?

Thanks

---

### Post by Austin_KW on 2007-06-26
Glad you got it working, 
> I'm glad it all works but I can't quite figure out why this didn't happen before? Probably a timing issue where the 'correct' working driver got in first.

---

### Post by carusoswi on 2008-02-24
> **Pat Mustard said:**
> Hi Austin_KW

Thanks for responding. :-)

I am using a Belkin wireless-G USB adapter F5D7050, not sure of the version off hand.

I previously had it working using the serialmonkey rt73 replacement driver.

I finally got it working on the fresh install last night.  From reading the forums I got the impression that it might be caused by other drivers so I removed and blacklisted all the drivers that serialmonkey covers, completed the rt73 setup and eventually coaxed it into working. :D

I'm glad it all works but I can't quite figure out why this didn't happen before?

Thanks

So, my Belkin N1 worked fine under Feisty.  Under Gutsy, it will lock up the computer no matter when I plug it in.  If I boot while the adapter is plugged in, the boot process stalls right after it queries the adapter (I can see the adapter light flash as it should during boot-up, then, the boot stalls).  If I boot ubuntu first, then plug in the adapter, the adapter light flashes (as it should) and, from then on, the computer is locked up.  I have to reboot.

The adapter works fine from XP, so, I know it isn't a hardware problem.

How do I check for competing drivers and how do I disable them in Gutsy?

Thanks.  I've pretty much stayed away from Ubuntu until I can get this problem sorted out.

Caruso

---

### Post by Austin_KW on 2008-02-24
To check which usb drivers are loaded  and used by usbcore
```

lsmod | grep usbcore 
```
You want to see rt73, 
but not rt2570, rt2500usb or rt73usb

However it may be dificult to check as the may not be loaded until you plug the adapter in and if it hangs it is a bit catch 22.

Make sure that your /etc/modprobe.d/blacklist  contains the lines
blacklist rt2500usb
blacklist rt73usb
blacklist rt2570

---

### Post by carusoswi on 2008-02-24
> **Austin_KW said:**
> To check which usb drivers are loaded  and used by usbcore
```

lsmod | grep usbcore 
```
You want to see rt73, 
but not rt2570, rt2500usb or rt73usb

However it may be dificult to check as the may not be loaded until you plug the adapter in and if it hangs it is a bit catch 22.

Make sure that your /etc/modprobe.d/blacklist  contains the lines
blacklist rt2500usb
blacklist rt73usb
blacklist rt2570

How do you make the vertical line after lsmod?  I cannot find that on the keyboard.  I can copy and paste the command, but would like to know how to type it.

Thanks for the reply.

I just installed Ndiswrapper version 1.52 - no change in the status of my problem, though.

Caruso

---

### Post by Austin_KW on 2008-02-24
Depends on your keyboard on my uk laptop the 'unix pipe symbol' is a broken vertical line from shift '\'

Also you might try an older tarball, see the post from dannyboy79 on [http://ubuntuforums.org/showthread.php?t=400236&page=75](http://ubuntuforums.org/showthread.php?t=400236&page=75) I have see reports that the older tarball worked for somepeople who had hang problems.

Also dont forget to blacklist rt73 if you are using ndiswrapper or vice-versa

---

### Post by carusoswi on 2008-02-24
> **Austin_KW said:**
> To check which usb drivers are loaded  and used by usbcore
```

lsmod | grep usbcore 
```
You want to see rt73, 
but not rt2570, rt2500usb or rt73usb

However it may be dificult to check as the may not be loaded until you plug the adapter in and if it hangs it is a bit catch 22.

Make sure that your /etc/modprobe.d/blacklist  contains the lines
blacklist rt2500usb
blacklist rt73usb
blacklist rt2570

I added these lines to my /etc/modprobe.d/blacklist.

No change in the behavior of my setup.

I should note that the system doesn't exactly lock-up.  I can still pull down menus.  It's just that nothing will load.  I cannot open a terminal window, the timer circle just spins its dots endlessly until I reboot.  I can open Mozzilla, but it cannot connect (via my ethernet connection).  Same spinning dots.

If I open 'network', the dots spin for a while, then, the network "icon" at the lower left task bar disappears.

So, basically, I cannot do anything until I reboot.

That's what I mean by freezing or locking up.

I appreciate your attempts to help me.  Let me know if you have additional suggestions.

Caruso

---

