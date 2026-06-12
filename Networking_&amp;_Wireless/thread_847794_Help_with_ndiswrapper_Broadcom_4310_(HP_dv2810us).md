---
title: "Help with ndiswrapper Broadcom 4310 (HP dv2810us)"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by thiagopv on 2008-07-02
I can´t connect using my wireless. My computer is a HP dv2810us (AMD 64 bits), i installed the last version of ndiswrapper in Synaptic and used R174291.exe driver (file bcmwl5.inf in the folder DRIVER_US) using ndisgtk. Below follows the output for some commands.

command: **lspci**
[I]
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
[/I]

command: **lspci -n**
[I]
04:00.0 0280: 14e4:4315 (rev 01)
[/I]
command: **lshw -C network**
[I]
WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: MCP67 Ethernet

       vendor: nVidia Corporation

       physical id: a

       bus info: pci@0000:00:0a.0

       logical name: eth0

       version: a2

       serial: 00:1d:72:57:56:11

       width: 32 bits

       clock: 66MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

  *-network UNCLAIMED

       description: Network controller

       product: BCM4310 USB Controller

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:04:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: latency=0
[/I]

command: **ndiswrapper -l**

[I]bcmwl5 : driver installed

	device (14E4:4315) present (alternate driver: wl)

[/I]
I have already inserted the line ¨blacklist wl¨ in /etc/modprobe.d/blacklist

If i try to load ndiswrapper with ¨modpreobe ndiswrapper¨ i receive the following message:

*FATAL: Module ndiswrapper not found.*


I don`t understand why i´m getting this

thiago@thiago-laptop:~$ [B]ifconfig
[/B][i]
eth0      Link encap:Ethernet  Endereço de HW 00:1d:72:57:56:11  

          inet end.: 192.168.1.102  Bcast:192.168.1.255  Masc:255.255.255.0

          endereço inet6: fe80::21d:72ff:fe57:5611/64 Escopo:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1

          pacotes RX:2004 erros:0 descartados:0 excesso:0 quadro:0

          Pacotes TX:1730 erros:0 descartados:0 excesso:0 portadora:0

          colisões:0 txqueuelen:1000 

          RX bytes:1282281 (1.2 MB) TX bytes:312360 (305.0 KB)

          IRQ:252 Endereço de E/S:0x8000 



lo        Link encap:Loopback Local  

          inet end.: 127.0.0.1  Masc:255.0.0.0

          endereço inet6: ::1/128 Escopo:Máquina

          UP LOOPBACK RUNNING  MTU:16436  Métrica:1

          pacotes RX:654 erros:0 descartados:0 excesso:0 quadro:0

          Pacotes TX:654 erros:0 descartados:0 excesso:0 portadora:0

          colisões:0 txqueuelen:0 

          RX bytes:257257 (251.2 KB) TX bytes:257257 (251.2 KB)
[/I]
thiago@thiago-laptop:~$ **iwconfig**
[I]
lo        no wireless extensions.

eth0      no wireless extensions.
[/I]

I think the problem is with the module of ndiswrapper but i don´t know what i should do.

Thanks anybody can try to help me (sorry about my english, i´m from Brazil :))

---

### Post by pytheas22 on 2008-07-02
First of all, try adding these lines to /etc/modprobe.d/blacklist:
```

blacklist b43
blacklist b43legacy
blacklist b43 ssb
blacklist ssb
```

Those drivers are for the PCI versions of the Broadcom chipsets so they shouldn't affect your USB device, but maybe they are interfering for some reason.

Second, do you use a 32-bit or 64-bit kernel?

Third, what is the output of:
```

locate ndiswrapper
```

---

### Post by thiagopv on 2008-07-02
> **pytheas22 said:**
> First of all, try adding these lines to /etc/modprobe.d/blacklist:
```

blacklist b43
blacklist b43legacy
blacklist b43 ssb
blacklist ssb
```

Those drivers are for the PCI versions of the Broadcom chipsets so they shouldn't affect your USB device, but maybe they are interfering for some reason.

Second, do you use a 32-bit or 64-bit kernel?

Third, what is the output of:
```

locate ndiswrapper
```

Ok, the blacklist that you suggest were already inserted.
I'm using a 64 bit kernel.

long list...
thiago@thiago-laptop:~$ locate ndiswrapper
/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper/bcmwl5
/etc/ndiswrapper/bcmwl5/14E4:4311.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4311:0007:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4311:0008:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4312.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4312:0007:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4312:0008:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4315.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4315:000B:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318:0005:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4318:0006:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319:0005:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4319:0006:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0001:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0002:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0003:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0004:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:0001:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:0002:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:0003:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4324:0004:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4328.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4328:0009:1028.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4328:000A:1028.5.conf
/etc/ndiswrapper/bcmwl5/bcmwl5.inf
/etc/ndiswrapper/bcmwl5/bcmwl564.sys
/home/thiago/.local/share/Trash/info/ndiswrapper.2.ko.trashinfo
/home/thiago/.local/share/Trash/info/ndiswrapper.2.trashinfo
/home/thiago/.local/share/Trash/info/ndiswrapper.3.trashinfo
/home/thiago/.local/share/Trash/info/ndiswrapper.ko.trashinfo
/home/thiago/.local/share/Trash/info/ndiswrapper.trashinfo
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-1.9
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-utils-1.9
/usr/share/doc/ndiswrapper-common/AUTHORS
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/README
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-utils-1.9/AUTHORS
/usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/README
/usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/copyright
/usr/share/man/man8/ndiswrapper-1.9.8.gz
/usr/share/man/man8/ndiswrapper.8.gz
/var/cache/apt/archives/ndiswrapper-common_1.50-1ubuntu1_all.deb
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb
/var/lib/dpkg/info/ndiswrapper-common.list
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-utils-1.9.list
/var/lib/dpkg/info/ndiswrapper-utils-1.9.md5sums

---

### Post by pytheas22 on 2008-07-03
It looks like the ndiswrapper module is nowhere to be found on your system.  Maybe you only installed one of the two ndiswrapper packages (thsi shouldn't have been possible but maybe something weird happened)?  I would try this:

```
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install ndiswrapper* ndisgtk
```

then install the Windows driver inside ndiswrapper again.  After that, you can try:
```

sudo modprobe ndiswrapper
```

and hopefully it will work.

Also, please remember that you need to use a 64-bit version of the Windows driver if you use a 64-bit Linux kernel.  Otherwise it definitely won't work.

---

### Post by itsjustarumour on 2008-07-03
Hi Thiagopv,

Perhaps it was the Hardy updates that broke your wireless?  I've posted on this here:

[http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)

Kind Regards,

itsjustarumour

---

### Post by pytheas22 on 2008-07-03
> Perhaps it was the Hardy updates that broke your wireless? I've posted on this here:

[http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)

I don't think these issues are related.  The original poster was trying to use ndiswrapper to drive his card, not the b43 driver contained in linux-restricted-modules.  But your problem definitely seems legitimate in its own right.  I've replied in your thread and hopefully we can straighten things out.

It's also useful to know that this card should normally work with the b43 driver, so ndiswrapper isn't necessary (although it should work just as well).

---

### Post by itsjustarumour on 2008-07-03
Guys - sorry for that - and thanks Pytheas for posting on my other thread  :-)

---

### Post by thiagopv on 2008-07-03
Itsjustarumour, no, I didn't installed these kernel updates yet.

I tried what Pytheas22 asked me to do, remove and reinstall ndiswrapper again, fine. But when i try to install the windows driver...

[I]thiago@thiago-laptop:~$ **ndiswrapper -i /home/thiago/driver/DRIVER_US/bcmwl5.inf**
couldn't open /home/thiago/driver/DRIVER_US/bcmwl5.inf: Arquivo ou diretório inexistente at /usr/sbin/ndiswrapper-1.9 line 219.
[/I]
this happened before and i've installed the driver using ndisgtk, the problem maybe here...

thanks for you patience guys

---

### Post by thiagopv on 2008-07-03
Sorry, my Ubuntu speaks Portuglish or Englese
*...mwl5.inf: Arquivo ou diretório inexistente at /u...* means file or directory inexistent

---

### Post by pytheas22 on 2008-07-03
> I tried what Pytheas22 asked me to do, remove and reinstall ndiswrapper again, fine. But when i try to install the windows driver...

thiago@thiago-laptop:~$ ndiswrapper -i /home/thiago/driver/DRIVER_US/bcmwl5.inf
couldn't open /home/thiago/driver/DRIVER_US/bcmwl5.inf: Arquivo ou diretório inexistente at /usr/sbin/ndiswrapper-1.9 line 219.

First, you need to be root to install the Windows driver and it doesn't look like you are.  Try:
```

**sudo** ndiswrapper -i /home/thiago/driver/DRIVER_US/bcmwl5.inf
```

But that doesn't explain the nonexistent-file message.  Are you sure that you typed the correct location of the file?  What does this tell you:
```

ls -R /home/thiago/driver
```

Also, be sure that you are installing the 64-bit version of the Windows driver!  it's very important

---

