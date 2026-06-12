---
title: "Wake On Lan (WOL) doesn't work with 3c905c"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by Alef Auman on 2006-12-14
Hello,

Wake On Lan doesn't work for the following on board NIC card in a HP VL400 computer :
01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

I've tried already with the following :
1)
Add the following to /etc/modules
3c59x options=0x408

2)
Add the following to /etc/modules
options 3c59x enable_wol=1

but without success.

I've the same machine but with windows xp installed on it, and there it works.
Wake on Lan is enabled in the BIOS

Some outputs
```

alef@FIRSTLOOK-UB:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes
alef@FIRSTLOOK-UB:~$ 

```

I don't have the following lines
[INDENT][/INDENT]Supports Wake-on: g
[INDENT][/INDENT]Wake-on: g
and this is not a good sign.
Maybe the driver is not good in Ubuntu?


Does somebody have some other ideas?

With kind regards
Alef

---

### Post by Alef Auman on 2006-12-16
In the meantime I've experimented further with the Wake On Lan. I've found that the WOL works only in the following situation:
	Connect the power supply to the computer
	Then send the magic packet and the commputer will start

In the following situation it will not work
	Do a shutdown but leave the power supply connected
	Send the magic packet but the computer doesn't start

So to solve the problem I've to cut off the power supply and connect the power supply again.

---

### Post by skf2610 on 2006-12-21
i have 3c905c-tx-m (pci version). the problem was exactly the same, but it works for me now.   this is what i did:

-- edit the file 3c59x.c located in /usr/src/linux/drivers/net/
-- add one command acpi_set_WOL(dev); at line number 3134 just before pci_disable_device(VORTEX_PCI(vp)); the codes looks like following

...
...
       if (VORTEX_PCI(vp)) {
                pci_set_power_state(VORTEX_PCI(vp), PCI_D0);    /* Go active */
                if (vp->pm_state_valid)
                        pci_restore_state(VORTEX_PCI(vp));
                acpi_set_WOL(dev); /* WOL  - workaround */
                pci_disable_device(VORTEX_PCI(vp));
        }
...
...

-- recomile the module

and before shutdown i remove the module from the memory

modprobe -r 3c59x

i add this line to the shutdown script, just before "halt" command.
i am not an expert, but this works just fine for me. btw i use global_enable_wol=1 instead of enable_wol=1 and ethtool will "not" show the line "Wake-up=..."

---

### Post by LotsOfPhil on 2007-02-11
> **skf2610 said:**
> i have 3c905c-tx-m (pci version). the problem was exactly the same, but it works for me now.   this is what i did:

-- edit the file 3c59x.c located in /usr/src/linux/drivers/net/
-- add one command acpi_set_WOL(dev); at line number 3134 just before pci_disable_device(VORTEX_PCI(vp)); the codes looks like following

...
...
       if (VORTEX_PCI(vp)) {
                pci_set_power_state(VORTEX_PCI(vp), PCI_D0);    /* Go active */
                if (vp->pm_state_valid)
                        pci_restore_state(VORTEX_PCI(vp));
                acpi_set_WOL(dev); /* WOL  - workaround */
                pci_disable_device(VORTEX_PCI(vp));
        }
...
...

-- recomile the module


I don't have this file (or even a /usr/src/linux directory). And I don't know how to recompile the module. Can you help?

---

### Post by xlr8or on 2007-03-08
I have the same 3c905c card and it works for me now. I had to take the next steps:

1.) Connected network card with mobo with wol cable

2.) Enabled **wake on lan** in the **BIOS**

3.) Created a file called "**network**" in **/etc/modprobe.d/**

4.) added a line: **options 3c59x global_enable_wol=1**

5.) reboot

6.) shutdown -h now

7.) Send a magic packet and the server starts...

This works for me, **even though ethtool still won't work and gives you the known response!** 
I didn't have to recompile anything :)

Hope it helps you too!

---

### Post by moon2js on 2007-03-08
> **xlr8or said:**
> 
1.) Connected network card with mobo with **wol cable**


Does anyone have a hint at where I can find one of these wol cables? It's a three-pin ATX misc cable that I can't find at any computer store. Does it have a specific name?

---

### Post by LotsOfPhil on 2007-03-08
I think they are called "Remote wake-up cables" [http://search.live.com/results.aspx?q=%22remote+wake-up+cable%22&sourceid=Mozilla-search&form=CHROME](http://search.live.com/results.aspx?q=%22remote+wake-up+cable%22&sourceid=Mozilla-search&form=CHROME)
At least that's what 3com calls it.

I assume your NIC needs this? Just making sure.

---

### Post by moon2js on 2007-03-09
Yeah, I have an older system (circa 1999) and, although the Intel mobo, 3com NIC, and BIOS all support WOL (in theory and documentation), it doesn't have the cable. It's kinda silly ordering it online because with shipping it's more expensive than a brand new NIC (although a brand new NIC might not work with my old mobo WOL-wise).

---

### Post by Mr. C. on 2007-03-09
> **moon2js said:**
> Does anyone have a hint at where I can find one of these wol cables? It's a three-pin ATX misc cable that I can't find at any computer store. Does it have a specific name?

I have one on my hands right now, still bagged.  I believe it came from my 3c980tx card.

PM me your name/address, and if its cheap enough, I'll toss it in an envelope and mail it to you.

MrC

---

### Post by LotsOfPhil on 2007-03-12
xlr8or, it works! Thanks a lot.

---

### Post by moon2js on 2007-03-23
> **xlr8or said:**
> I have the same 3c905c card and it works for me now. I had to take the next steps:

[snip, hardware all set!]

3.) Created a file called "**network**" in **/etc/modprobe.d/**

4.) added a line: **options 3c59x global_enable_wol=1**

5.) reboot

6.) shutdown -h now

7.) Send a magic packet and the server starts...

This works for me, **even though ethtool still won't work and gives you the known response!** 
I didn't have to recompile anything :)

Hope it helps you too!

Sadly, it didn't work for me.  I've got a 3Com 3c905C-TX/TX-M and my "ethtool eth0" output is exactly the same as Alex's in the first post.

Before coming here and trying xlr8or's advice, I followed [Chris Tucker's WOL howto thread](http://ubuntuforums.org/showthread.php?t=234588), but "ethtool -s eth0 wol g" gets a "Cannot get current wake-on-lan settings: Operation not permitted
  not setting wol"

Any one have any idea how I can properly enable WOL as a module option or trouble shoot?

---

### Post by Mr. C. on 2007-03-23
Operation not permitted is telling you that you don't have privilege to perform that operation; it must be done as root.  Use:

```
sudo ethtool -s eth0 wol g
```

MrC

---

### Post by moon2js on 2007-03-23
Oops. I forgot sudo when I was getting output to post, but even with the sudo, I still get:

```
$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: [B]Operation not supported
  not setting wol[/B]
```

I tried to enable wol by putting "options 3c59x global_enable_wol=1" in /etc/modprobe.d/network (as described earlier) and also by appending it to /etc/modprobe.d/options, but no luck so far. Is my syntax wrong?

Anything else I can try?

---

### Post by Mr. C. on 2007-03-23
The enable_wol, and global_enable_wol options have been in the 3c59x driver since 2001.

Can you show output from :
```

lspci
sudo ethtool -i eth0
ifconfig -a
sudo lshw -class network

```

Also, did you enable WOL in your BIOS ?
MrC

---

### Post by moon2js on 2007-03-23
Yeah, BIOS has it set. In fact, it powers up after power loss (plugging in), which I switched on in the BIOS, too.

Does the syntax or where you put it make a difference? I tried "global_enable_wol=1" (as described earlier) and then permutated with or without "global" and with or without "=1" in /etc/modprobe.d/network.

```
james@werewolf:~$ **lspci**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (                                              rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (re                                              v 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0f.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/U                                              ltra66) (rev 01)
00:10.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 6c)
00:11.0 Communication controller: 3Com Corp, Modem Division WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon                                               7500]
james@werewolf:~$ sudo **ethtool -i eth0**
Password:
driver: 3c59x
version:
firmware-version:
bus-info: 0000:00:10.0
james@werewolf:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:DA:11:B7:86
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe12:b885/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7193 errors:0 dropped:0 overruns:1 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2357351 (2.2 MiB)  TX bytes:42700 (41.6 KiB)
          Interrupt:9 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

james@werewolf:~$ sudo **lshw -class network**
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@00:10.0
       logical name: eth0
       version: 6c
       serial: 00:50:da:12:b8:85
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                                              00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full                                               ip=192.168.1.97 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1400-147f iomemory:e8020000-e802007f irq:9

```

---

### Post by Mr. C. on 2007-03-23
Darn, the one thing I was looking for was the driver version.

Please report output from:

```
uname
dmesg | grep 3c59x
```

MrC

---

### Post by moon2js on 2007-03-23
This is an Edgy server/xubuntu install.

```
james@werewolf:~$ uname
Linux
james@werewolf:~$ dmesg | grep 3c59x
[17179596.580000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
```

Come to think of it, you're probably looking for kernel info, not just "Linux":
```
james@werewolf:~$ uname -a
Linux werewolf 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Liux
```

---

### Post by Mr. C. on 2007-03-23
You should be able to add the line below to the existing file: /etc/modprobe.d/options 

options 3c59x enable_wol=1

or create your own file in /etc/modprobe.d

The boot on power-loss option is not related to WoL.  Your system must be put into the correct state upon power down, so that the NIC retains power.  Here are some threads that might provide some answers:

[http://www.beowulf.org/archive/2006-December/017042.html](http://www.beowulf.org/archive/2006-December/017042.html)
[http://ubuntuforums.org/showthread.php?p=1547189](http://ubuntuforums.org/showthread.php?p=1547189)
[http://www.nvnews.net/vbulletin/showthread.php?t=70384](http://www.nvnews.net/vbulletin/showthread.php?t=70384)

There have been no WoL related changes in the 3c59x driver from your version to the current 2.6.20.4 kernel, so it is unlikely that the driver is a problem.  Most likely, your system is not in the correct ACPI power state.

MrC

---

### Post by dirk_k on 2007-04-22
removing the '-i' from the /etc/init.d/halt script worked for me (3c905C-TX/TX-M on intel 440BX)
i got this from:
[http://ubuntuforums.org/showpost.php?p=1737164&postcount=21]("http://ubuntuforums.org/showpost.php?p=1737164&postcount=21")

---

### Post by jis on 2007-05-22
> **Mr. C. said:**
> Darn, the one thing I was looking for was the driver version.

Please report output from:

```
uname
dmesg | grep 3c59x
```

MrC

Well, I've got some version shown here:
```
$ sudo ethtool -i eth0
Password:
driver: 3c59x
version: LK1.1.19
firmware-version:
bus-info: 0000:00:0f.0

```

Linux kernel version is 2.6.15-28-386.

```
$ dmesg | grep 3c59x
[   58.413021] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html

```

I have added line "options 3c59x enable_wol=1" in /etc/modprobe.d/options and in /etc/modprobe.d/network, removed the '-i' from the /etc/init.d/halt, but no help. The NIC led powers off on 'shutdown -h now'. The led does not power off if I press power button soon after reboot, and switches on, if I pull the power cord of and plug it back in. Magic packets don't wake the system even if the target NIC led is powered when sending the packet. BIOS has PME Wakeup events enabled, there is no explicit Wake on LAN setting in the BIOS setup of this Compaq Deskpro EP series PC.

---

### Post by jis on 2007-05-23
In [http://knowledgebase.3com.com](http://knowledgebase.3com.com) I found in solution "3C90x Family - How to disable Remote Wake-Up". If I understood it right, the NIC could be configured to wake up system at 
1. Magic Packet Wake-up
2. Ping Wake-up
3. ARP Wake-up
4. Link State Change Wake-up

But does configuring that require using MS Windows?

---

### Post by rick128 on 2007-06-19
> **xlr8or said:**
> I have the same 3c905c card and it works for me now. I had to take the next steps:

1.) Connected network card with mobo with wol cable

2.) Enabled **wake on lan** in the **BIOS**

3.) Created a file called "**network**" in **/etc/modprobe.d/**

4.) added a line: **options 3c59x global_enable_wol=1**

5.) reboot

6.) shutdown -h now

7.) Send a magic packet and the server starts...

This works for me, **even though ethtool still won't work and gives you the known response!** 
I didn't have to recompile anything :)

Hope it helps you too!

It works great with my 3com 3c905c card. Thanks to xlr8or.:D

---

### Post by jis on 2007-06-19
I still wonder why mine doesn't work. I did find only PME Wakeup events setting in BIOS, but it seems to have no effect.  Specs about the computer:  [http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=96269&targetPage=http%3A%2F%2Fh20000.www2.hp.com%2Fbc%2Fdocs%2Fsupport%2FUCR%2FSupportManual%2FTPM_dsk-107c-0498%2FTPM_dsk-107c-0498.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=96269&targetPage=http%3A%2F%2Fh20000.www2.hp.com%2Fbc%2Fdocs%2Fsupport%2FUCR%2FSupportManual%2FTPM_dsk-107c-0498%2FTPM_dsk-107c-0498.pdf)
(See also my previous posts.)

---

### Post by AnythingBut on 2007-06-19
I'm having the same problem as you are Jis.  I've tried everything in this thread with no luck.  I have a 3c905C-TX/TX-M [Tornado] (rev 78) integrated on the motherboard of a Dell Optiplex GX240.  "Remote Wake Up" is enabled in the BIOS.

Is there a way to double check that the wol option we are setting is indeed being set?

---

### Post by rick128 on 2007-06-20
I am quite new to linux. I just follow what xlr8or has posted and it works right away.
About the BIOS, mine is to set the "Wake up by PCI"  ON and no need for a wol cable.
I have tried  this on Windows to make sure it can boot up normally before switch to linux.

:KS

---

### Post by jis on 2007-06-20
rick128, maybe Windows configured the NIC so that remote wake-up works in linux, too? (I have only Xubuntu Dapper in the machine so I cannot try it first in Windows.) Did you use the wakeonlan software to wake up? What about the LED of the NIC; are they powered before you apply remote wake-up? All LEDs are off in my system, if the WOL cable is removed, unlike when WOL cable is attached. (See, my previous [post.]("http://ubuntuforums.org/showpost.php?p=2703373&postcount=20"))

Newer system don't need the cable, see an Intel.com page about remote wake-up problems: [http://www.intel.com/support/network/sb/cs-008459.htm](http://www.intel.com/support/network/sb/cs-008459.htm)

My NIC model is 3c905C-TX/TX-M [Tornado] (rev 74) according to lspci command.

(I have posted about the issue also in a [HP support forum]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1129671&admit=-682735245+1182321086409+28353475").)

FWIW, in my [motherboard spec]("http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=96269&targetPage=http%3A%2F%2Fh20000.www2.hp.com%2Fbc%2Fdocs%2Fsupport%2FUCR%2FSupportManual%2FTPM_dsk-107c-0498%2FTPM_dsk-107c-0498.pdf") it is said (in chapter 4.2.6) that "This system complies with the PCI Power Management Interface Specification (rev 1.0). The PCI Power Management Enable (PME-) signal is supported by the 440EX/BX chipset and allows PCI peripherals to initiate the power management routine."

P.S. In chapter 4.2 it is told that for detailed information about the PCI bus opertation, refer to the PCI Local Bus Specification Revision 2.1. Doesn't it tell you that it is not PCI 2.2 compliant bus and thus does not support remote wake-up without the WOL cable?

---

### Post by tenwiseman on 2007-09-25
Hi

Thought I'd relate my success with getting a 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74) PCI card working on an IBM PC 300PL model 6862-140 (Pentium II-350MHz) with Xubuntu 7.04 Feisty Fawn (alternative)

This PC has an on-board Intel 8255x Ethernet PCI (10/100) adaptor that supports WOL but for some reason I couldn't get it to reliably start from a WOL packet sent after a software initiated shutdown. If the machine was powered off with the on/off switch then WOL would work - but loading the e100 driver kills WOL & scripting "ethtool -s eth0 wol g" didn't fix that.... so I abandoned using the onboard adaptor and installed a 3Com PCI card with a 3-wire WOL cable.

BIOS settings are APM & ACPI enabled, Wake on LAN enabled, Wake on PCI disabled. The onboard ethernet adaptor is disabled by setting the motherboard dip switch 6 (ethernet disable) to ON.

I followed xlr8or's settings here but no WOL packet results...

[Quote= xlr8or]
2.) Enabled wake on lan in the BIOS

3.) Created a file called "network" in /etc/modprobe.d/

4.) added a line: options 3c59x global_enable_wol=1
[/Quote]

.... Until I did the following line to rebuild initramfs

sudo /usr/sbin/update-initramfs -u

This worked for me ;-)

--
Adrian C

---

