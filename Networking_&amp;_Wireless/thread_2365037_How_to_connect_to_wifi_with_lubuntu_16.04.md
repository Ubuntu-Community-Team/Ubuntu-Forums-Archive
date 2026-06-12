---
title: "How to connect to wifi with lubuntu 16.04?"
date: 2017-07-01
forum: Networking &amp; Wireless
---

### Post by fernandoch on 2017-07-01
I have an ipn2220 and I can't figure out how to connect to wifi.

I tried to install ndiswrapper, but then I don't know how to connect to the SSID.

Any help would be appreciated.

---

### Post by praseodym on 2017-07-01
What about the "Network-Manager"? Please run the wireless-script from the sticky thread and show the outputs. Does LAN work?

---

### Post by fernandoch on 2017-07-01
Sorry I missed that post.

Here is the output

[http://paste.ubuntu.com/24998180/](http://paste.ubuntu.com/24998180/)

Any problems?

I have LAN with a cable.

---

### Post by praseodym on 2017-07-01
Wow, haven't seen an InProCOmm card for a while ;)

Try this driver with the installed ndiswrapper

[https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz)

---

### Post by fernandoch on 2017-07-01
Thank you, I installed this one

ipn2220_x32w9xME_mod.inf

But I still don't see the option to setup the wifi.

---

### Post by praseodym on 2017-07-01
Check

```
ndiswrapper -l
sudo ndiswrapper -ma 
```
Reboot and check
```

dmesg | grep ndis
```

---

### Post by fernandoch on 2017-07-01
```
fernando@ubuntu:~$ ndiswrapper -l
ipn2220_x32w9xme_mod : driver installed
	device (17FE:2220) present
neti2220 : driver installed
	device (17FE:2220) present
fernando@ubuntu:~$ 
fernando@ubuntu:~$ sudo ndiswrapper -ma
[sudo] password for fernando: 
module configuration information is stored in /etc/modules.conf
```

Now rebooting again

---

### Post by fernandoch on 2017-07-01
I get this now.

```
fernando@ubuntu:~$ sudo modprobe ndiswrapper
fernando@ubuntu:~$ 
fernando@ubuntu:~$ dmesg | grep ndis
[  294.123507] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  294.133612] ndiswrapper version 1.61 loaded (smp=yes, preempt=no)
[  294.224123] ndiswrapper: driver ipn2220_x32w9xme_mod (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[  294.258896] ndiswrapper: using IRQ 21
[  294.470115] usbcore: registered new interface driver ndiswrapper
[  294.485726] ndiswrapper 0000:00:0a.0 enp0s10: renamed from wlan0
[  294.486301] ndiswrapper: interface renamed to 'enp0s10'
```

---

### Post by praseodym on 2017-07-01
Is it an UEFI or BIOS? For UEFI deactivate secure boot

---

### Post by fernandoch on 2017-07-02
This is BIOS.

What else can I do?

---

### Post by fernandoch on 2017-07-02
Everything seems well installed

```
fernando@ubuntu:~$ ndiswrapper -l
ipn2220_x32w9xme_mod : driver installed
	device (17FE:2220) present
```

How to configure the wifi?

---

### Post by praseodym on 2017-07-02
Reset the BIOS to default, should be F9, save and exit with F10

---

### Post by johndough2 on 2017-07-02
Hi

Does this mean you are using Channel Zero (if it exists)?

enp0s10   14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
                 
          Channel 14 : 2.484 GHz
          Current Channel:0

The network manager can be changed, you could try WICD network manager perhaps.

sudo apt-get install network-manager

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by fernandoch on 2017-07-03
> **praseodym said:**
> Reset the BIOS to default, should be F9, save and exit with F10

Did that, then what?

---

### Post by johndough2 on 2017-07-03
Hi

Have you done this...
[https://help.ubuntu.com/community/NdiswrapperIpn2220](https://help.ubuntu.com/community/NdiswrapperIpn2220)

also earlier thread   ...   [https://ubuntuforums.org/showthread.php?t=1042480](https://ubuntuforums.org/showthread.php?t=1042480)
    File Type: zip inprocomm_ipn2220_v3.07.02.2005.zip
    File Type: gz ipn2220_32_64_all.tar.gz
    File Type: gz ipnworks.tar.gz

Since the "module verification failed: signature and/or required key missing" I would purge the file and search for an alternative, or try and force acceptance of an unsigned package.

These may give clues ... [https://wiki.debian.org/ipw2200](https://wiki.debian.org/ipw2200)

[https://wireless.wiki.kernel.org/en/users/drivers/ipw2200](https://wireless.wiki.kernel.org/en/users/drivers/ipw2200)

---

### Post by fernandoch on 2017-07-03
Yes I have done all that with no success.

I also read that the signature failure was not a problem.

[https://ubuntuforums.org/showthread.php?t=2295691&p=13359760#post13359760](https://ubuntuforums.org/showthread.php?t=2295691&p=13359760#post13359760)

I still click on the network button next to the clock and I don't see how to setup a wifi.

wicd could change that?

---

### Post by johndough2 on 2017-07-04
wicd could change that? 

Yes.

---

