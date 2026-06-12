---
title: "Wireless Issue"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by blah569 on 2008-06-22
Okay, so I have installed the RTL8187b Windows 98 driver file, I have made sure that the driver starts whenever I boot into Ubuntu, and I have black listed r81860 Linux driver file.  My wireless card is RTL816b or RTL8187b (I believe it is this one [RTL8187b]).

This is my output for the command (ndiswrapper -l):

```

net8187b : driver installed
	device (0BDA:8189) present

```

I absolutely love Ubuntu, but the only flaw I can see is that I can not get my wireless to work.  Any assistance is appreciated.  Thanks.

---

### Post by Kevbert on 2008-06-22
Please have a look at this [link]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

---

### Post by blah569 on 2008-06-22
> **Kevbert said:**
> Please have a look at this [link]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

Thanks, but I only see "Ethernet Interface" with the command "lshw -C network."  I do not see "Wireless Interface."  I have come to the conclusion that ndiswrapper might not be associating RTL8187b for wireless access.  Might this be the case?

---

### Post by pokipoki08 on 2008-06-22
Please post the output

Check for ndiswrapper status
```
dmesg | grep ndiswrapper
```

Check for wifi interface
```
dmesg | grep wlan
```

Activate your wifi interface (replace X with your interface integer)
```
sudo ifconfig wlanX up
```

Scan available wireless networks
```
iwlist wlanX scan
```

Sometimes, you need to plugin the USB wifi card AFTER you login, in order for it to be loaded & detected.

Are you trying to connect to an open/restricted network? Is it WEP/WPA?

---

### Post by blah569 on 2008-06-22
> **pokipoki08 said:**
> Please post the output

Check for ndiswrapper status
```
dmesg | grep ndiswrapper
```

My output for this is:

```

blah569@blah569-laptop:~$ dmesg | grep ndiswrapper
[   45.530407] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.733896] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   45.733927] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[   45.734439] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[   45.734477] usbcore: registered new interface driver ndiswrapper

```

Check for wifi interface
```
dmesg | grep wlan
```

I receive no out for this.

Activate your wifi interface (replace X with your interface integer)
```
sudo ifconfig wlanX up
```

N / A

Scan available wireless networks
```
iwlist wlanX scan
```

N / A

Sometimes, you need to plugin the USB wifi card AFTER you login, in order for it to be loaded & detected.

Are you trying to connect to an open/restricted network? Is it WEP/WPA?

The Network I would be connecting to does have WEP security, but I do know the WEP key to my wireless internet.
 

The Wireless card is internal, by the way, it came with this computer.

---

### Post by blah569 on 2008-06-22
I do not mean to double post, but I could really use some help.  Thanks.

---

### Post by pokipoki08 on 2008-06-22
```
blah569@blah569-laptop:~$ dmesg | grep ndiswrapper
[   45.530407] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.733896] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but [COLOR="Red"]Windows driver is not 64-bit;bad magic: 010B[/COLOR]
[   45.733927] ndiswrapper (load_sys_files:210): [COLOR="Red"]couldn't prepare driver 'net8187b'[/COLOR]
[   45.734439] ndiswrapper (load_wrap_driver:112): [COLOR="Red"]couldn't load driver net8187b; check system log for messages from 'loadndisdriver'[/COLOR]
[   45.734477] usbcore: registered new interface driver ndiswrapper
```

The driver you are using is incompatible.

What platform of ubuntu are you using? 32/64 bit?

You should use the same wifi drivers that is working in WinXP.

For now, uninstall the driver used in ndiswrapper until you can confirm the version & platform used.

---

### Post by blah569 on 2008-06-22
> **pokipoki08 said:**
> ```
blah569@blah569-laptop:~$ dmesg | grep ndiswrapper
[   45.530407] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.733896] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but [COLOR="Red"]Windows driver is not 64-bit;bad magic: 010B[/COLOR]
[   45.733927] ndiswrapper (load_sys_files:210): [COLOR="Red"]couldn't prepare driver 'net8187b'[/COLOR]
[   45.734439] ndiswrapper (load_wrap_driver:112): [COLOR="Red"]couldn't load driver net8187b; check system log for messages from 'loadndisdriver'[/COLOR]
[   45.734477] usbcore: registered new interface driver ndiswrapper
```

The driver you are using is incompatible.

What platform of ubuntu are you using? 32/64 bit?

You should use the same wifi drivers that is working in WinXP.

For now, uninstall the driver used in ndiswrapper until you can confirm the version & platform used.


I am using a 32-bit Ubuntu (I believe).  I also have Vista on my Windows partition, not XP.

---

### Post by pokipoki08 on 2008-06-22
Locate the wireless driver ([COLOR="Blue"]32-bit WinXP version[/COLOR]) and install it in ndiswrapper.

---

### Post by blah569 on 2008-06-22
I still receieve this:

```

[   45.530407] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   45.733896] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   45.733927] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[   45.734439] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[   45.734477] usbcore: registered new interface driver ndiswrapper

```

Do I need to restart this computer?  Did I not use a 32 bit XP driver?  I used an XP driver, but I do not know if it is 32-bit.  I downloaded the files from [http://www.driverguide.com](http://www.driverguide.com)

---

### Post by pokipoki08 on 2008-06-22
Find out the ubuntu version you are using 
```
uname -ma
```

x86_64 = 64 bit
i386 or i686 = 32 bit

Install the appropriate bit/version of your wireless driver in ndiswrapper. It must be the WinXP version.

Shutdown your PC
Unplug your wireless
Power on PC
Login to Ubuntu
Plug in your wireless
Run those commands I posted earlier (up)

---

### Post by blah569 on 2008-06-22
It tells me that I am using 64 bit.  I do not know where I could find 64 bit drivers.  I shall take a look.

---

