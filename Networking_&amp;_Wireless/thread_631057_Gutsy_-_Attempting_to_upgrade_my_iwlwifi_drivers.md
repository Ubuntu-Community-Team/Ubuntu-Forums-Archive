---
title: "Gutsy - Attempting to upgrade my iwlwifi drivers"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by [Neurotic] on 2007-12-04
Hi all,

I've been having serious crashed with my Intel AGN card, ever since I started using WEP encryption on my home network.

While I am going to try switching it to WPA encryption to see if it could help, I've been trying to upgrade my iwlwifi drivers to see if that makes a difference.

Following the guide here:
[http://www.intellinuxwireless.org/?p=mac80211&n=HOWTO-mac80211](http://www.intellinuxwireless.org/?p=mac80211&n=HOWTO-mac80211)

For the 1st part of the process, I can get all the way to hte point that is:

```
% make modules modules_install
```

When I run this, I have the following output:

```
mark@synesthesia:/lib/modules/2.6.22-14-generic/build$ sudo make menuconfig
scripts/kconfig/mconf arch/i386/Kconfig


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

mark@synesthesia:/lib/modules/2.6.22-14-generic/build$ sudo make modules modules_install
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
mark@synesthesia:/lib/modules/2.6.22-14-generic/build$ 
```

I can't for the life of me find any information on asm-offsets.c and where I can get it from / what package to install to make it available.

If anyone could give me a hand, I'd be happy to document how to upgrade your iwlwifi drivers for other people's usage.

Failing all this, if it doesn't work, I will switch back to using ndiswrapper, because I can't have my machine doing a hard crash randomly when my wireless is working.

Thanks for your time guys.

---

### Post by smyrman on 2007-12-04
I don't know if this will help you, but there is how-to for debian on this page:
[http://www.nanonanonano.net/linux/debian/iwlwifi]("http://www.nanonanonano.net/linux/debian/iwlwifi")

Debian and ubuntu beeing quite simular, I guess one could make some changes, and make it work.

For instance you can skip this:

 deb [http://www.backports.org/debian](http://www.backports.org/debian) etch-backports main contrib non-free

And instead try to just enable the ubuntu bacports rep. (either edit /etc/apt/sources.list, or enable it width help of the graphical menus [Settings>Administrations>Software Sources].) 

Here you do not install the mac80211 again. You just install the new drivers for iwlwifi. I hope this will help you.

**PS!** I haven't testet this jet.. (But I will)

---

### Post by [Neurotic] on 2007-12-04
I'm pretty sure this is an old article, as it refers to iwlwifi 1.1.18, and the latest snapshot these days is 1.2.22.

Previously I know you didn't have to recompile the kernal with mac80211, but I believe with the newer version you do, as is described on the HOWTO for the iwlwifi drivers.
[http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

So I still am reasonably sure that I will need to recompile kernel with the latest max80211 snapshot, to make sure that the new iwlwifi drivers work properly.

Thanks for the input never the less, and I am happy to be proved wrong! :oD

---

### Post by [Neurotic] on 2007-12-06
bump

Please tell me someone, somewhere has upgraded their iwlwifi drivers?

---

### Post by Jeff_From_VA on 2007-12-07
I haven't but am considering it - I can't get ndiswrapper working right, it hangs on modprobe ndiswrapper, and my wifi performance sucks bad in gutsy - 15-25kbps

---

### Post by [Neurotic] on 2007-12-07
Interesting fact - I just changed my network from WEP encryption to WPA, and it seems pretty solid at the moment, I haven't had a drop out yet, or a hard crash.

I'm going to assume that WPA probably had a bit more work done on it, as WEP is relatively easy to crack.

So maybe a solution all around is to change the encryption on your network.

---

### Post by [Neurotic] on 2007-12-07
Nope.. I lied.

Seems to be more stable... but still experiencing hard crashes.

I've yet to experience one when I'm booted into my XP dual boot, so it doesn't seem to be a hardware problem.

---

### Post by crumja on 2007-12-09
I've had good success following this guide:

[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)

Just modify the links to the sources to be the latest ones.

---

### Post by [Neurotic] on 2007-12-09
@crumja - I notice this guide doesn't cover compiling the kernel?

Does that mean I can skip that step?

---

### Post by Ronin324 on 2008-01-16
Well I have been trying to upgrade my iwl4965 drivers as well as the mac subsystem following the guides on the Intel Linux Wireless page. I have a few minor issues that look like they may have been corrected in the newer releases.  

[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

While trying to build the mac80211 subsystem I have run into the same problems seeing this error message.

```
make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.
```

I see that others have run into this problem. 

Well I was not sure if the mac subsystem needed to be upgraded as well as the iwl drivers since mac80211 is all ready loaded I just tried to install those drivers. I was able to compile them apparently successfully but i am not able to get them to load. I ran a make install and rebooted the system and ran modinfo iwl4965 and am still running the 1.1.17 driver.

Hopefully someone will have some tips regarding these problems since I have searched and goggled this one to death. Maybe one of the Ubuntu Gurus could make a guide covering this subject.

---

### Post by mcade on 2008-01-30
AHHH!  I'm having the same issues.  Have a new Thinkpad T61 with the 4965 AGN card. Things work okay on my lamo home wireless network, but when I try to connect to the WPA PEAP mschapV2 network at school, it seems that something bad happens to my wireless drivers... I *think* they crash, but I'm not sure how to know... anyway, searched around and saw somewhere that the iwlwifi drivers that came with gutsy don't like my card and/or the type of encryption I'm trying to use ... but there is supposed to be a fix in the newer version...

blah blah blah tried to upgrade, followed instructions on intellinuxwireless.org got the same "can't find asm-offsets.c" when running %make modules modules_install on the mac-80211 bit...

I just want to be on the universities encrypted network like all the smarmy windows users... Is that so much to ask?  :confused:

I guess I should also tell you that I'm running the x86_64 kernel...

---

### Post by kegobeer on 2008-01-30
> **mcade said:**
> AHHH!  I'm having the same issues.  Have a new Thinkpad T61 with the 4965 AGN card. Things work okay on my lamo home wireless network, but when I try to connect to the WPA PEAP mschapV2 network at school, it seems that something bad happens to my wireless drivers... I *think* they crash, but I'm not sure how to know... anyway, searched around and saw somewhere that the iwlwifi drivers that came with gutsy don't like my card and/or the type of encryption I'm trying to use ... but there is supposed to be a fix in the newer version...

blah blah blah tried to upgrade, followed instructions on intellinuxwireless.org got the same "can't find asm-offsets.c" when running %make modules modules_install on the mac-80211 bit...

I just want to be on the universities encrypted network like all the smarmy windows users... Is that so much to ask?  :confused:

I guess I should also tell you that I'm running the x86_64 kernel...

If you installed Gutsy, then mac80211 is already running.  If you did a "sudo modprobe mac80211", and you didn't get an error message, then you don't need to compile the mac80211 module.  In order to compile the mac80211 module, you need to compile a completely new kernel - that's why you are getting that error message.

Skip the mac80211 stuff, and just continue with the HOWTO.

---

