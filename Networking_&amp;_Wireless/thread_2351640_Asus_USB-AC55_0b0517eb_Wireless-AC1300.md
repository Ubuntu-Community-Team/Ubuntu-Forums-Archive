---
title: "Asus USB-AC55 0b05:17eb Wireless-AC1300"
date: 2017-02-05
forum: Networking &amp; Wireless
---

### Post by collin2012 on 2017-02-05
Hello, I purchased a usb wifi AC dongle that works well with Windows but want to use too on Ubuntu. I'm using Ubuntu 16.04 LTS 64 bits and found [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210) that comments that it has beeb tested mostly on ubuntu 64 bits 15.10. Tried it but didn't worked. Additionaly also tried ndiswrapper inserting .inf files from Windows 7 and also couldn't make it to work.

Have any on tried and successfully make it work?
Any help or guide will be greatly appreciated.
Thanks

---

### Post by jeremy31 on 2017-02-05
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2017-02-05
From here:

[https://wikidevi.com/wiki/ASUS_USB-N10_v2](https://wikidevi.com/wiki/ASUS_USB-N10_v2)

the chipset seems to be Ralink mt7610u. Try this PPA
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms
```

---

### Post by collin2012 on 2017-02-06
> **praseodym said:**
> From here:

[https://wikidevi.com/wiki/ASUS_USB-N10_v2](https://wikidevi.com/wiki/ASUS_USB-N10_v2)

the chipset seems to be Ralink mt7610u. Try this PPA
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms
```


Thanks for the help praseodym. Not sure how did you got the chipset due to [https://wikidevi.com/wiki/ASUS_USB-AC55](https://wikidevi.com/wiki/ASUS_USB-AC55) describes another one, but in reality what's important is that with the easy code you sent me it works. Now I got a $14.29 AC usb dongle working in Ubuntu.:D

---

### Post by praseodym on 2017-02-07
0b05:17eb from the headline. The chipset showed it. Please look at the right side of that link "ID"

---

### Post by collin2012 on 2017-02-11
Additional to
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms
The default network manager works, but can't maintain constant throughput, specially sending data. I noticed it when casting.
To workaround I installed wicd
sudo apt-get install wicd

And worked as it should. Not sure if it's just a setting that is the difference, but works now for me.

---

### Post by jim1000111 on 2017-02-15
Hello, I have the same asus ac1300 adapter, I can not get it working following these instructions.
I am not familar with dkms and unsure how to continue.

---

### Post by mörgæs on 2017-02-17
Please post the commands that you run and their result.

---

### Post by praseodym on 2017-02-17
Just run

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms
```
and reboot

---

### Post by jim1000111 on 2017-02-18
Hello praseodym,

I've done that but still cannot find my wireless adapter or the mt7610u module.
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms
```

---

### Post by jeremy31 on 2017-02-18
Is Secure Boot enabled in BIOS?  That will prevent the module from being able to be used

---

### Post by jim1000111 on 2017-02-18
Hello, no secure boot is disabled, and the bios is running in legacy mode.

---

### Post by jim1000111 on 2017-02-18
I was just able to load the module, using sudo modprobe mt7610u and add the wireless to edit connections.But still no wireless showing.

---

### Post by jeremy31 on 2017-02-18
We might as well try the driver in the original posters link
```
sudo apt-get install git build-essential linux-headers-generic
```
```
git clone https://github.com/jurobystricky/Netgear-A6210.git
```
```
cd Netgear-A6210
```
```
make
```
```
sudo make install
```

Reboot

---

### Post by jim1000111 on 2017-02-18
Many thanks jeremy31, that has given me wireless in Network Manager, I will now check it out if it is working I'll mark this thread as solve again. Thank You!

---

### Post by jim1000111 on 2017-02-18
I am able to connect at 2.4 Ghz but not 5 Ghz, will just keep working on it many thanks again for getting me this far!
Am on 2.4 right now.

---

### Post by jeremy31 on 2017-02-18
I don't know how to fix the 5Ghz.  If you have a kernel update you will need to compile and install the module again, when you notice it doesn't work at all after a reboot
```
cd Netgear-A6210
make clean
make
sudo make install
```

Then reboot

---

### Post by jim1000111 on 2017-02-18
OK, I will keep your info in mind, and regards the 5 Ghz I'll just work away at it. Many Thanks again. The 2.4 is working really well!

---

### Post by hfillipsveen on 2017-07-30
hey guys! tried the command you posted here. but it didnt work
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install mt7610u-dkms

this comes up when i tried the last command
root@kali:~# sudo add-apt-repository ppa:hanipouspilot/rtlwifi
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 93, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Kali/kali-rolling
root@kali:~# sudo apt-get update
Hit:1 [http://mirrors.dotsrc.org/kali](http://mirrors.dotsrc.org/kali) kali-rolling InRelease
Reading package lists... Done
root@kali:~# sudo apt-get install mt7610u-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mt7610u-dkms

---

### Post by collin2012 on 2017-10-10
My hard drive failed and had to do a clean install using 16.04LTS, and did the steps in which I was successful before only and got the adapter to work, but 5ghz deprecated.
Clean install didn't work.
Not sure if I had some setup that helped on lower versions. Summary it works only using max N signal, which is to slow for me. Will continue researching and testing due to I'm going to get a new HDD, I will test will lower version and if works will upgrade from there to replicate what I had working before.
That is an idea to test, hope it helps somebody else.

Correction, did further tests and I needed to update what I was usuing to review the wifi Linssid, and for some reason the chrome browser reports using speedtest.net half or less download speed using the same site on Firefox. So the steps on previous post works fine even without Wicd that is my personal preference.

---

### Post by pokerdetroit on 2017-10-14
> **jeremy31 said:**
> We might as well try the driver in the original posters link
```
sudo apt-get install git build-essential linux-headers-generic
```
```
git clone https://github.com/jurobystricky/Netgear-A6210.git
```
```
cd Netgear-A6210
```
```
make
```
```
sudo make install
```

Reboot

Thank you worked perfect!!

---

### Post by hydros63 on 2018-05-01
Hello I am new to this forum. I purchased the Asus AC-55 usb adapter and none of the steps worked for me.  I keep getting an error. Anyone else still having this issue? Any help would be greatly appreciated.

---

### Post by mörgæs on 2018-05-01
Please post the exact steps you have taken and the exact results.

---

### Post by nightpatrol on 2018-08-21
Hello, this adapter, dont working in Ubuntu 18.04. [COLOR=#000000]How to fix it? 
[/COLOR][URL="https://ubuntuforums.org/showthread.php?t=2398259&highlight=asus+usb+ac55"]asus+usb+ac55
[/URL]
[COLOR=#212121][FONT=arial]This option also does not work.[/FONT][/COLOR]

[COLOR=#212121][FONT=arial]This option also does not work[/FONT][/COLOR]

---

### Post by nightpatrol on 2018-08-21
Hello, this adapter, dont working in Ubuntu 18.04. [COLOR=#000000]How to fix it? 
[/COLOR]https://ubuntuforums.org/showthread.php?t=2398259&highlight=asus+usb+ac55

[COLOR=#212121][FONT=arial]This option also does not work.[/FONT][/COLOR]

---

### Post by coffeecat on 2018-08-23
Back to sleep, ancient thread. Thread closed.

@nightpatrol, if you need help with your wireless adapter, please start your own thread, and post the information requested in [this sticky](https://ubuntuforums.org/showthread.php?t=370108).

To anyone else wanting help with the same or similar device, you won't get any by hijacking an old thread marked solved. That's why I've closed this one. Please start your own threads.

---

