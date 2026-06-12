---
title: "DWL-G630 HW:E2, FW: 5.00 / Ubuntu 8.04"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by TheSwede86 on 2008-10-04
Hello!

First of all let my apologize for any bad english since I am not a native english speaker. Furthermore let me apologize if this matter has been discussed in another thread, I have scoured the internet and found similiar problems but not any that helped me.

I am a beginner at Linux (and Ubuntu) so please explain things in a step by step manner.

Ubuntu 8.04
D-Link PC-Card DWL-G630 HW:E2 FW: 5.00

As per my understanding this uses Ralink RT61 drivers and this is what I have done:

Downloaded the latest drivers from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) this is the driver RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)

Is this even the correct driver for my card? It says "PCI/mPCI/CB" and CB = CardBus = PC-Card? This is the only driver that says "RT61" which I think is the correct driver.

So I unpack these at my desktop and go in the Terminal and give the following commands:

While standing in "Module":
cp Makefile.6 ./Makefile (since I according to "Uname -a" have kernel 2.6)

Don't do step 3 in the "ReadMe" since I don't have the kernel 2.4

Then I write "make all" and get the following error:

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/mittnamn/Skrivbord/2008_0723_RT61_Linux_STA_v1.1.2.2/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/mittnamn/Skrivbord/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/mittnamn/Skrivbord/2008_0723_RT61_Linux_STA_v1.1.2.2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

Translation:

skrivbord=Desktop
mittnamn=username

Please help me, I love this OS but I have sat for the entire day trying to figure this out and scouring different similiar threads but it never worked for me.

Best Regards & Thanks in advance - TheSwede86

---

### Post by roelpeeters on 2008-10-04
Hi,

I was just wondering. I've been reading some wiki's and they speak of executing just 'make' in the Module directory instead of 'make all'. Have you tried this? Giving the make all command may 'make' more than needed. Otherwise you might want to check the forums of ralink.
Edit: I just took the last version of the driver from rt2x00.serialmonkey.com. I have always had good experiences with their driver for the rt61 chipset. I could build it without any problem on 8.04 hardy.
Edit2: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

---

### Post by TheSwede86 on 2008-10-04
> **roelpeeters said:**
> Hi,

I was just wondering. I've been reading some wiki's and they speak of executing just 'make' in the Module directory instead of 'make all'. Have you tried this? Giving the make all command may 'make' more than needed. Otherwise you might want to check the forums of ralink.
Edit: I just took the last version of the driver from rt2x00.serialmonkey.com. I have always had good experiences with their driver for the rt61 chipset. I could build it without any problem on 8.04 hardy.
Edit2: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

Thank you for your answer.

Tried both "make" and "make all", will try with your link and report.

EDIT:

That driver seemed to compile but gives me this message, any ideas on how to fix it or if I am just going to ignore it?

!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully

---

### Post by roelpeeters on 2008-10-04
The solution is to call 'strip rt61.ko', then do a 'sudo make install'.

---

### Post by TheSwede86 on 2008-10-04
> **roelpeeters said:**
> The solution is to call 'strip rt61.ko', then do a 'sudo make install'.

I get this is this a normal message:

*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...

If not where is the old config that I should check?

If this is a normal step then what should I do next?

In the "ReadMe" it says:

    4. Check your install (load module, bring interface up and scan):
          # modprobe rt61 [debug=<mask>]

How do I load the module?

---

### Post by roelpeeters on 2008-10-04
Sorry for the late reply. The loading of the module is done with 'sudo modprobe rt61'. Then check with 'dmesg' what the system has done. You can use also 'iwconfig' which will show you what wireless interfaces have been loaded.
What does 'iwconfig' show you?

Edit: you should see an interface with the name similar to ra0.

BTW: the lines starting with *** from the script is only the script reporting what it is doing. Everything you have seen is normal.

---

### Post by TheSwede86 on 2008-10-04
> **roelpeeters said:**
> Sorry for the late reply. The loading of the module is done with 'sudo modprobe rt61'. Then check with 'dmesg' what the system has done. You can use also 'iwconfig' which will show you what wireless interfaces have been loaded.
What does 'iwconfig' show you?

Edit: you should see an interface with the name similar to ra0.

BTW: the lines starting with *** from the script is only the script reporting what it is doing. Everything you have seen is normal.

No problem at all, I am really grateful for your help.

(Did a complete re-install of Ubuntu, had some difficulties)

Now I get this after sudo make install:

WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.24-19-generic/extra/rt61.ko

and when trying the sudo modprobe rt61 command I get this:
FATAL: Error inserting rt61 (/lib/modules/2.6.24-19-generic/extra/rt61.ko): Invalid module format

Strange, I think that the symtab och strtab warning didn't appear at my last attempt (before my reformating)

iwconfig gives me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg might help you:

rt61: module has no symbols (stripped?)

But I should have stripped it right?

Btw this guy seem to have the same error message but some how gets passed it, you see any helpful info in this?

Its in german but the Terminal speaks for itself:
[http://tiri.li/wissen/wireless/rt2x00-rt61-wireless-in-ubuntu-804-hardy](http://tiri.li/wissen/wireless/rt2x00-rt61-wireless-in-ubuntu-804-hardy)

---

### Post by roelpeeters on 2008-10-05
Could you try a 'modinfo rt61' ? This to see what information is stored in the rt61.ko. Another thing you might try is to run the following command again 'sudo /sbin/depmod -a'. This should update the dependencies between different kernel modules.
Another thing you could try is 'sudo insmod /lib/modules/2.6.24-19-generic/extra/rt61.ko'. This basically does the same as modprobe, however, you have to specify the path.

---

### Post by TheSwede86 on 2008-10-05
> **roelpeeters said:**
> Could you try a 'modinfo rt61' ? This to see what information is stored in the rt61.ko. Another thing you might try is to run the following command again 'sudo /sbin/depmod -a'. This should update the dependencies between different kernel modules.
Another thing you could try is 'sudo insmod /lib/modules/2.6.24-19-generic/extra/rt61.ko'. This basically does the same as modprobe, however, you have to specify the path.

ubuntu@ubuntu-laptop:~$ modinfo rt61
filename:       /lib/modules/2.6.24-19-generic/extra/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS 2008093011
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     EF2829A6630C943579E4B38
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:
vermagic:       2.6.24-19-generic SMP mod_unload 586
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           ifname:Network device name (default wlan%d) (charp)


Will try your other commands now and get back to you

Edit:

Here they come:

ubuntu@ubuntu-laptop:~$ sudo /sbin/depmod -a
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.24-19-generic/extra/rt61.ko
ubuntu@ubuntu-laptop:~$

and

ubuntu@ubuntu-laptop:~$ sudo insmod /lib/modules/2.6.24-19-generic/extra/rt61.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/extra/rt61.ko': -1 Invalid module format

dmesg still seem to say:

[ 7458.540952] rt61: module has no symbols (stripped?)

---

### Post by roelpeeters on 2008-10-05
It seems like it has loaded it, since you have a wlan0 in your iwconfig list. You might want to try to configure it to use it in your network (here I refer to the other site that you already found).
In addition, you could try to rebuild the module using the steps we did before but do not do the 'strip' command.

---

### Post by TheSwede86 on 2008-10-05
> **roelpeeters said:**
> It seems like it has loaded it, since you have a wlan0 in your iwconfig list. You might want to try to configure it to use it in your network (here I refer to the other site that you already found).
In addition, you could try to rebuild the module using the steps we did before but do not do the 'strip' command.

If I run "iwlist wlan0 scan" I get different acesspoints so I guess it works now but now its just the problem that I can't connect to my own acesspoint :D

But I'm almost there, a BIG thanks for all your help :D

EDIT:

Now I get it working!!! BUT my connection freezes after a random period of time while surfing on any WLAN, why might that be?

Also is it possible to "unstrip", to revert the the settings before making the strip command?

Can I fully uninstall the driver, if so then how I can't seem to find it.

Thanks in advance & Best Regards - TheSwede86

---

### Post by roelpeeters on 2008-10-11
No problem, glad it worked for you. As far as I know there is no way to unstrip, since basically what happens is that the information that is 'stripped' is thrown away, and therefore you are not able to undo the strip. The only thing would be to make the module again.

You can uninstall the driver with the following code:
First:
```

sudo ifconfig wlan0 down

```
Then
```

sudo rmmod rt61

```

This will remove the driver for this instance. If you installed the driver in /etc/modules (you should see a line with rt61 in the file /etc/modules); then you can remove it simply by removing the line with 'rt61' from that file.

Why it freezes, is hard to say. You might want to check your 'dmesg' or other log files to see if you can find any errors. I know that under heavy load (like a lot of downloading, torrents, http downloads together) the wireless connection may drop. 

Hope this helps,

Roel

---

