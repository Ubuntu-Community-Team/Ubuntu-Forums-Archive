---
title: "how to install ndiswrapper and what is its purpose?"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by bobetko on 2007-12-25
I am trying to make my (Atheros) AR5007EG wireless to work. 

I am following directions from this thread: [http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007eg+atheros]("http://http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007eg+atheros")

And, I can't install ndiswrapper

This is what I get when I run make:

make -C driver
make[1]: Entering directory `/home/zlatko/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/zlatko/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/zlatko/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/zlatko/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/zlatko/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/zlatko/ndiswrapper-1.5/driver/loader.o
/home/zlatko/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/zlatko/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/zlatko/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/zlatko/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/zlatko/ndiswrapper-1.5/driver'
make: *** [all] Error 2


Can somebody tell me what's wrong. Thanks....

---

### Post by ijason on 2007-12-25
hmm. the purpose of NDIS wrapper is to allow linux to use windows drivers for communication (and other?) hardware. i've seen it almost exclusively used for NICs. 

interesting thing is, that on 7.10, i haven't had to use ndis for any of my network devices... i just had the hardware present when i installed and ubuntu had it's own drivers. 

unfortunately i'm not sure how to solve your ownership problem :confused:

---

### Post by chalewa on 2007-12-25
wait are you tyring to compile ndiswrapper from source?


just grab it from synaptic (search for ndiswrapper) and then to install the windows driver just type in


```
sudo ndiswrapper -i /location/of/windows/driver
```

that will install the driver... i couldn't get the how to you were using to load up on my comptuer for some reason



[http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)

---

### Post by bobetko on 2007-12-25
thanks.. I got it from Synaptic (still don't understand why it doesn't work other way)...

Next thing to do was to execute :

```
pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```

(I previously downladed windows driver for atheros ar5007eg wireless card)

This went fine (I think so), no errors were reported.

After ndiswrapper -l I see:
[B]net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)[/B]

The next step was: (to make sure ndiswrapper loads every time I start ubuntu)
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

This gives me ERROR:
FATAL: module ndiswrapper not found....

What's wrong here? Thanks.

---

### Post by chalewa on 2007-12-25
oh hm..

well it seems as though there is something wrong with ndiswrapper itself... maybe try to uninstall and reinstall?

---

### Post by bobetko on 2007-12-27
I did...

I downloaded ndiswrapper 1.51 and it compiled with no problem....
Installed xp drivers...

now after ndiswrapper -l I get
net5211 : driver installed

but, It seems to me that wireless doesn't work.
If I click on network connection (top right icon) I see only Wired Connection
I tried Radar... Doesn't show anything.

iwconfig gives me:
lo     no wireless extensions
eth0   no wireless extensions

I also noticed, if I click to Administration > Restricted Driver Manager, it tells me my hardware does not need any restricted drivers. Before it was showing something (I believe my wireless card)... So is this good or bad?

My laptop is Acer Aspire 5315 and it has button to activate/deactivate wireless. I sort of think that this button is creating all this trouble.....

Any ideas?

---

