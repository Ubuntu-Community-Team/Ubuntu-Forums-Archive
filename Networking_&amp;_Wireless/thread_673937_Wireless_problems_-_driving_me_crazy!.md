---
title: "Wireless problems - driving me crazy!"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by jasonbell on 2008-01-21
Hi,

I have recently switched from Fedora to Ubuntu.  I must say it is working out well, so few problems with Ubuntu compared to Fedora.

However, my wireless is causing me pain, and I need it for work.

I have a Lenovo T60 with a Intel® PRO Wireless 3495ABG.
I am running Ubuntu 7.10 (2.6.22-14-generic).

The wireless was a bit flaky after install - kept popping up asking me for the WEP key in an endless loop and never connected.  Sad thing is it worked perfectly on Fedora 7, but not Fedora 8. 

I googled around and found I should not be using the ipw3945 but the iwl3945.  So I gave this a bash:

sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe iwlwifi_mac80211
sudo modprobe iwl3945

It did make things better, no more endless loop, and it can connect, but rarely.  More often than not it does not work.

I decided to upgrade the iwlwifi to latest version 1.2.23.  Probably good to note at this point I am a bit of a Linux beginner.  I can follow instructions to solve problems but may not always know what they mean :-)

So, anyway, seems I need the latest version of mac80211.  So I downloaded that first and tried to install.  

Following the instructions I ran "make patch_kernel" and it seemed to work fine.

I changed to directory: cd /lib/modules/$(uname -r)/build
Then "make menuconfig".  Seems nothing needed to change there so I backed out without making any changes.

Next part is where I hit the wall.  "make modules" does this:
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

I googled the error and it shows up a lot, but with no good explanation.  What is the problem?  Have I done something wrong?  Or, am I missing something?

Any help will be appreciated.  Not having wireless makes life very difficult.

Thanks,
Jason

---

### Post by ubutufan on 2008-01-21
Hi Jason
I can't really figure out why you have a problem with Gutsy and 3945. It works out of the box.

Here is what I would suggest, in case you are ready to go for a new "clean" install.

Go to [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and install wicd.
It handles wireless like a charm no matter the encryption. And likewise it handles the wired connections

---

### Post by jasonbell on 2008-01-22
Thanks for your help.  I will give it a go.

Meanwhile, I am still interested in the problem: make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c'

Any ideas?

---

### Post by Haise on 2008-01-22
Doesn't work out of box for me, either.  :(

I'm hoping an update gets released soon to fix it...

---

### Post by ubutufan on 2008-01-22
Jasonbell, I am not sure about this. You may be getting this message because the kernel headres are prepared so this step maybe unnecessary. Again I am not sure.

Have you tried wicd?

Also post here the contents of your file /etc/network/interfaces

---

### Post by jasonbell on 2008-01-22
Wicd did not work either unfortunately.  Still could not see my wireless, I had more luck with network manager.

Strange.  I am not too concerned, in two weeks I am getting a new laptop and might have more luck with that one.  But I like Ubuntu a lot and it is a shame wireless is letting it down - for me at least.  

I have googled and searched and poked and prodded all I can.  I need an expert to help me get this thing working.

/etc/network/interfaces

auto lo
iface lo inet loopback

---

### Post by Haise on 2008-01-22
I tried wicd; it hangs on "obtaining IP address" for like, 10 minutes and then reports it can't get one.  I'm on a Lenovo x60 running Gusty.  (I've also tried this on Kubuntu 7.10, Kubuntu 7.04, and Feisty as well; it always just sits there waiting for an IP address).

My interfaces file only contains the loopback, as well.  The network I'm trying to connect to is unencrypted.

---

### Post by ubutufan on 2008-01-22
The contents of the interfaces file is ok. This is what it should be.
I wish I could help. My 3945 was immediately recognised and ipw3945 driver loaded at install time.
You should try also the following posted by kevdog
[http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog](http://ubuntuforums.org/showthread.php?t=571188&highlight=kevdog)


I take it that you have checked that in the restricted drivers menu, the wireless is enabled.

---

### Post by Haise on 2008-01-22
Naturally.  It can scan and read packets in promiscuous mode, but it just seems to be broken for actually *connecting* to anything.

I guess it's back to Vista so I can get work done. :P

---

### Post by jasonbell on 2008-01-22
I have checked the restricted drivers menu and it is enabled but says not in use since I changed from ipw3945 to iwl3945, and since then it has been more stable and can at least connect sometimes.

---

### Post by Haise on 2008-01-22
My problem was fixed by using ndiswrapper with the lenovo supplied drivers.

Not a great fix, but at least I'm not in Vista. :)

---

