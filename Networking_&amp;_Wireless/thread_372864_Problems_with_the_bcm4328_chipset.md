---
title: "Problems with the bcm4328 chipset"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by oyvinvo on 2007-02-28
For some reason I got this working at the first try on my ferrari 1005 and 32-bit install of ubuntu now. Here's how:

First I installed ndiswrapper utils.
```
sudo aptitude install ndiswrapper-utils-1.9
```

Then I downloaded the windows driver from acer support and unzipped them. 
```
wget ftp://ftp.work.acer-euro.com/notebook/ferrari_1000/driver/WLan%20Driver%20802.11n%20Rel.%204.80.28.7.zip
unzip WLan\ Driver\ 802.11n\ Rel.\ 4.80.28.7.zip

```

Next step is to make ndiswrapper use this windows driver.
```

cd 80211n
sudo ndiswrapper -i bcmwl5.inf

```

Which gave me this ouput.
> 
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2


ndiswrapper should now tell you that the device is present,
```
sudo ndiswrapper -l
```
> 
bcmwl5 : driver installed
        device (14E4:4328) present


Next step is to add an alias.

```
sudo ndiswrapper -m
```
> adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

Now try modprobe it and it will hopefully work as it did for me:)
```
sudo modprobe ndiswrapper
```

Last you should add ndiswrapper to /etc/modules so it will load ndiswrapper on startup.
Just use your favourite editor and add a new line at the bottom of the file and type in: ndiswrapper
save and close the file.


> I've been trying to get my wireless card on my Acer Ferrari 1005 to work for some days now. At this point I've installed the drivers with ndiswrapper. The driver I used can be obtained here ( [link]("ftp://ftp.work.acer-euro.com/notebook/ferrari_1000/driver/xp/WLan%20Driver%20802.11n%20Rel.%204.80.28.7.zip") ) and it is the latest available from acer. 
ndiswrapper -l gives me this:
```
acid@nami:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

however iwconfig doesn't seem to recognise my card.
```
acid@nami:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

So I check my dmesg to see if there had been any errors, but it told me everything was a'okay.
```
acid@nami:~$ dmesg | grep ndiswrapper
[   67.631460] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[   67.661339] usbcore: registered new driver ndiswrapper
```
depmod -a && modprobe ndiswrapper gives no output.

So now I'm kinda stucked and turning to you guys. Any useful tip or help would be much appreciated.

---

### Post by Metaljaz on 2007-02-28
So, you did try to bring up the driver by typing:
 sudo depmod -a
 sudo modprobe ndiswrapper

If you got no error messages then the driver should have been loaded.

If this is not the thread that you followed look through this one to see if you missed something. Click on the OS version you are using:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by oyvinvo on 2007-02-28
That's right, I don't get any errors. I've looked into the fwcutter aswell but it wouldn't accept the windows driver. I'm currently installing the 32bit version of ubuntu hoping that the 32 bits drivers will be nicer to me;p

---

### Post by oyvinvo on 2007-02-28
Apperantly the drivers from acer is just 64bits:( Tried with this [howto]("http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper") but ndiswrapper -l doesn't say that the hardware is present. Guess that's because the howto seems to be for bcm4318 and I have bcm4328.

Guess I'll try with the fwcutter again then.

edit:
fwcutter didn't do me any good either. It's so strange about the windows drivers. 
I have a bcmwl5.inf, bcmwl5.sys and a bcmwl564.sys .... This inf file seems to be referring to the bcmwl564.sys which is the 64 bits driver.

---

### Post by jesterfred on 2008-03-22
I have a Dell Precision M6300 with the exact same Broadcom wireless card.  When using Gutsy 64 bit, I am able to successfully install ndiswrapper and Broadcom driver.  Once installed, I can surf away.  Following the exact same procedure with the same driver files under Hardy (Beta) results in the behavior described above.  No errors reported.  ndiswrapper -l gives:

> bcmwl5 : driver installed
  device (14E4:4328) present (alternate driver: ssb)
But I get no wlan0 device.  iwconfig only lists:

> lo        no wireless extensions.
eth0      no wireless extensions.
(Also, I don't know what the reference to ssb above means)

---

