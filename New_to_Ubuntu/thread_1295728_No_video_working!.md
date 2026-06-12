---
title: "No video working!"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by beano0528 on 2009-10-19
I still can't get my plugins working!:mad:  I have tried flash player 10 and 9.  I have changed firefox to 3.5.3.  All my plugins are installed, but nhl.com, stlouisblues.com, and even youtube not working!  I am dieing here!  Huge Blues fan that watches games online and needs any help I can get.  I am getting desperate!

---

### Post by mcooke1 on 2009-10-19
Install opera

---

### Post by beano0528 on 2009-10-19
> **mcooke1 said:**
> Install opera
Ok.  What is opera and where/how do I install it?

---

### Post by pgar23 on 2009-10-19
Check out this blog about Opera, how to install, how to install the flsh and java plugins, and it even includes a fix if you should have problems with your video...I personally prefer Opera over firefox anyday.

---

### Post by beano0528 on 2009-10-19
> **pgar23 said:**
> Check out this blog about Opera, how to install, how to install the flsh and java plugins, and it even includes a fix if you should have problems with your video...I personally prefer Opera over firefox anyday.
Link not working man.

---

### Post by pgar23 on 2009-10-19
[http://www.ubuntugeek.com/how-to-install-opera-web-browser-in-ubuntu-including-flashjava-plugins.html](http://www.ubuntugeek.com/how-to-install-opera-web-browser-in-ubuntu-including-flashjava-plugins.html)

---

### Post by beano0528 on 2009-10-20
Well how do I know what operating system I am using?  I know Linux, but which version?

---

### Post by philinux on 2009-10-20
> **beano0528 said:**
> I still can't get my plugins working!:mad:  I have tried flash player 10 and 9.  I have changed firefox to 3.5.3.  All my plugins are installed, but nhl.com, stlouisblues.com, and even youtube not working!  I am dieing here!  Huge Blues fan that watches games online and needs any help I can get.  I am getting desperate!

Ok first off lets see what plugin are installed.
In firefox address bar type this.
```
about:plugins
```

Post back what it says about flash.

---

### Post by halitech on 2009-10-20
also, what video card do you have?

post the results of
```
lspci
```

also, more details about your system, cpu, amount of ram, internet connection, etc

---

### Post by beano0528 on 2009-10-21
> **philinux said:**
> Ok first off lets see what plugin are installed.
In firefox address bar type this.
```
about:plugins
```Post back what it says about flash.
Already done that.  Says its enabled.
**Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

---

### Post by beano0528 on 2009-10-21
> **halitech said:**
> also, what video card do you have?

post the results of
```
lspci
```also, more details about your system, cpu, amount of ram, internet connection, etc
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Dougie187 on 2009-10-21
> **beano0528 said:**
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

What's this return (from a terminal)

```
apt-cache policy swfdec-mozilla
```

If that says it is installed, maybe try this.
```
sudo apt-get autoremove --purge swfdec-mozilla
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by beano0528 on 2009-10-21
> **Dougie187 said:**
> What's this return (from a terminal)

```
apt-cache policy swfdec-mozilla
```If that says it is installed, maybe try this.
```
sudo apt-get autoremove --purge swfdec-mozilla
sudo apt-get install ubuntu-restricted-extras
```
You are freakin' awesome!  I have been trying to fix this for about a week now and it has been driving me crazy!  I tried the first one and it said it was installed so I tried the second one, restarted firefox and it is working!  So what exactly did that code do?

---

### Post by Dougie187 on 2009-10-21
Well, you were using the open source version of flash, not the "non-free" version. So the first one removed the open source version of flash. Then the second one installed a standard packaged called "ubuntu-restricted-extras" which is a compilation of flash, java, and codecs that are not free.

---

