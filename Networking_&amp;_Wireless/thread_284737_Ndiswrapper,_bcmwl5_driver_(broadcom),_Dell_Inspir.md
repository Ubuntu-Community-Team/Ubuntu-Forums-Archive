---
title: "Ndiswrapper, bcmwl5 driver (broadcom), Dell Inspiron e1505"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by xonecas on 2006-10-26
Ok, I have ndiswrapper saying that it is all good, but I can't get it to work, and after some diggin up, I'm thinking that the laptop isn't powering up the wireless card (the led that used to come up on windows is not lit under linux).

Anyone knows some way I can get this working ?

---

### Post by foxy123 on 2006-10-26
> **xonecas said:**
> Ok, I have ndiswrapper saying that it is all good, but I can't get it to work, and after some diggin up, I'm thinking that the laptop isn't powering up the wireless card (the led that used to come up on windows is not lit under linux).

Anyone knows some way I can get this working ?

did you do
```
sudo modprobe ndiswrapper
```?

---

### Post by PixelCloud on 2006-10-26
I switched to the fwcutter


works well

---

### Post by xghstst0riesx on 2006-10-26
fwcutter? what do you mean by that?

---

### Post by foxy123 on 2006-10-27
> **xghstst0riesx said:**
> fwcutter? what do you mean by that?

I think she/he means a native Linux bcm43xx driver...

---

### Post by cvmostert on 2006-10-27
> **foxy123 said:**
> I think she/he means a native Linux bcm43xx driver...

i also went the native route, does not work on bcm43xx mine is a broadcom 4306 wireless card. 

and with the new edgy i can not modprobe ndiswrapper... 

does not find the ndiswrapper.ko

AND i can not install from source because kbuild can not find the build directories... whatever... broadcomm gives me the creeps!

---

### Post by foxy123 on 2006-10-27
> **cvmostert said:**
> i also went the native route, does not work on bcm43xx mine is a broadcom 4306 wireless card. 

and with the new edgy i can not modprobe ndiswrapper... 

does not find the ndiswrapper.ko

AND i can not install from source because kbuild can not find the build directories... whatever... broadcomm gives me the creeps!

I am still using Dapper and but anyway both methods work for me: ndiswrapper and bcm43xx. Though I herd that people have problems with them on Edgy.

Note, that you have to blacklist a native bcm43xx driver if you wnat to use ndiswrapper. To compile ndiswrapper from source you need linux-headers installed. Though you may know it already.

To use a native bcm43xx driver you have to extract firmware using a fwcutter tool. Mind that some Windows drivers do not work with bcm43xx (the driver I have on CD for my wireless card did not, so I had to download another one).

---

### Post by cvmostert on 2006-10-27
> **foxy123 said:**
> I am still using Dapper and but anyway both methods work for me: ndiswrapper and bcm43xx. Though I herd that people have problems with them on Edgy.

Note, that you have to blacklist a native bcm43xx driver if you wnat to use ndiswrapper. To compile ndiswrapper from source you need linux-headers installed. Though you may know it already.

To use a native bcm43xx driver you have to extract firmware using a fwcutter tool. Mind that some Windows drivers do not work with bcm43xx (the driver I have on CD for my wireless card did not, so I had to download another one).

i used fwcutter aswell, no go.. have linux-headers installed but i have the XX.10 and not the XX.7 version... and i think that is why i can not compile... maby i should wait the soulution out.. or go and buy another card... i am borrowing this one...

---

### Post by nbound on 2006-10-27
Ive created a HOWTO for this card here: [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809)

---

### Post by kperkins on 2006-10-27
thanks nbound.
I'd forgotten all the steps, and _thought_ that Ubuntu would do stuff like this automatically when installing ndiswrapper.
And Yahoo!!!! NetworkManager works perfectly now, in Edgy, I can connect to all networks encrypted or not (in Dapper I couldn't connect to unencrypted, because of wpasupplicant)

---

### Post by steveyeager on 2007-01-31
I have just been working with the new 7.04 herd live cd, and it is pretty good.  I understand that the 43xx broadcom native driver is built into the current kernel.  Sure enough, the network configuration tool acknowledged my broadcom wireless card.  However, when I tried to configure it, it crashed the configuration tool.   

Anybody have any thoughts?

---

