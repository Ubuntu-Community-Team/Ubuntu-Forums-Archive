---
title: "Netgear Wg511 Drivers"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by j.ingham06 on 2007-03-11
Where can I get drivers for my Netgear WG511 (v2) which will work with linux. I have no method of getting online unless I shutdown and run XP, so most tutorials I try and use fall over when it tries to connect to the internet half way through. I have a Dell Latitude D600.

Thanks

---

### Post by foofi22 on 2007-03-12
Hi

I too have a WG551v2 card made in China (I assume yours is also made in China, if you are not sure just look on the underisde of the card)  Anyway after much aggravation I have got my card working on a Dell 250N (this computer sucks btw).  Exactly how far have you got through the tutorials?  Have you got the green light blinking?  I used the mrv8000 drivers with ndiswrapper 1.8

---

### Post by conjur3r on 2007-03-12
Unfortunatley, the WG511 version requires you to use ndiswrapper as foofi22 has mentioned.  If you had obtained the WG511T version, you would have had wireless support natively with Linux.

---

### Post by chili555 on 2007-03-12
If you do not have a working Internet connection, you can use another computer which is connected to the Internet to download the following packages.

For Edgy Eft (6.10)
   1.  [http://packages.ubuntu.com/edgy/misc/ndiswrapper-common](http://packages.ubuntu.com/edgy/misc/ndiswrapper-common)
   2.  [http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8)
   3.  [http://packages.ubuntu.com/edgy/net/ndisgtk](http://packages.ubuntu.com/edgy/net/ndisgtk) 
   4.  [http://mirrors.kernel.org/ubuntu/pool/universe/u/unshield/unshield_0.5-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/u/unshield/unshield_0.5-3_i386.deb)
   5.  [http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.1-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.1-1_i386.deb)

      Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:
```
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb
sudo dpkg -i unshield*.deb
sudo dpkg -i cabextract*.deb
```

Then you need the .inf file. The easiest way is to go to Netgear's support page and download the driver for your exact version. V1, v2 v3, etc. use different or improved chipsets, so grabbing the wrong file will not work.

Here is a post about the process to get the .inf file out of the driver file for a v1 card. Your process will be very similar. [http://www.ubuntuforums.org/showthre...ighlight=WG511](http://www.ubuntuforums.org/showthre...ighlight=WG511)

Run ndisgtk, put the .inf in place, bring up and configure your wireless interface and surf!

---

### Post by j.ingham06 on 2007-03-12
Cheers for the replies! I'll have a shot in a minute! :)

---

### Post by vandelejo on 2007-03-12
After many hours of frustration with the same problem, I purchased a WL-107g adaptor. It worked right out of the box. No ndiswrapper/exotic operations:) .

---

### Post by j.ingham06 on 2007-03-12
hey chili555, I did what you said, but after trying this line
```
sudo dpkg -i --force-depends ndisgtk_*.deb
```

It showed this...
```
Creating database ... 88240 files and directories currently installed.
Preparing to replace ndisgtk 0.6-0 ubuntu1 (using ndisgtk.deb)...
Unpacking replacement ndisgtk
dpkg: ndisgtk: dependencey problems, but configurating anyway as you request.
  ndisgtk depends on ndiswrapper-utils; however: package ndiswrapper-utils is not installed.
Setting up ndisgtk(0.6-0 ubuntu1).
```
(I had to write this by hand so there may be one odd error in there...)

I'm assuming that the ndiswrapper utils is not installed, but when I ran that (before) it said they were installed.

Thanks for helping...

---

### Post by chili555 on 2007-03-12
And did you get the card installed, configured and connected? Are you posting from Ubuntu?

---

### Post by j.ingham06 on 2007-03-12
```
ndisgtk depends on ndiswrapper-utils; however: package ndiswrapper-utils is not installed.
```

Isn't this a problem? ANd no :P Im stuck on the installing of ndiswrapper :(

---

### Post by j.ingham06 on 2007-03-13
Turns out I need to buy a new PCMCIA Wireless reciever anyway. Any suggestions to ubuntu frienldy cards? I'm a fan of Netgear but I've read that all their cards aren't linux friendly!

---

### Post by dnchari on 2007-03-14
Hey Chili555, I had the same problem as  j.ingham06, I have installed everything and try to configure do I need to use ascii while configuring? I am unable to connect to internet, mine is USB wireless adaptor(Hawking)....please help me

thanks in advance

---

