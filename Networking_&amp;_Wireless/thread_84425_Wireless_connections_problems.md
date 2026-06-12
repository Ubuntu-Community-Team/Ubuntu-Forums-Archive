---
title: "Wireless connections problems"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by tk421 on 2005-10-31
Hi,

Im trying to connect with the wireless pcmcia card, but it does not connect. I was OK in the Ubuntu 5.04.

Card seems its working OK (light is on) but it does not connect to access point. It seems to be that Im not using WEP and then configuracion is wrong.

Any ideas to debug and solve the problem?

---

### Post by spd106 on 2005-10-31
Could you tell us what kind of card it is? Can you see any access points? **sudo iwlist wlan0 scan**. Have you checked that the card is still configured and that the details are correct?
If you are using ndiswrapper you will probably have to remove all previously installed drivers and packages then reinstall them.

---

### Post by mit on 2005-10-31
[QUOTE=spd106]**sudo iwlist wlan0 scan**. [/QUOTE]

Thanks for the command. I am building up a nice little book of them now!

---

### Post by Valavien on 2005-11-01
I am having a similar problem.  I managed to get my WUSB54G installed with ndiswrapper and it appears in "Network Setings" but I just can't ping anything or access anything even though it says it's active.

---

### Post by tk421 on 2005-11-01
```
wlan0 No scan results
``` :(

* Access Point is working its an Ovislink Air Live
* PCMCIA wireless card is an WL8000PCM. Its has been recogniced and installed by the system and no ndiswrapper needed. (On Ubuntu 5.04 was working OK)
* Its fresh instalation

---

### Post by spd106 on 2005-11-04
>  PCMCIA wireless card is an WL8000PCM

I'm not familiar with this card. The ovislink website lists it as using a texas instruments chipset. Is this the one that uses the acx111? **lsmod,** should show what driver modules are loaded. Or maybe **dmesg | grep wlan0**.
The wifi hardware list in the wiki shows that similar cards with acx111 can be hit and miss. If it worked on Hoary then it should work on Breezy.:confused: 
Looking on the usually comprehensive [www.linux-wlan.org](www.linux-wlan.org) list, it doesn't appear to be there. So I don't know what to suggest. Maybe look for a newer driver version. Perhaps search for texas instruments based cards that are reported to be working.

---

### Post by tk421 on 2005-11-06
mmm... something is lost ...

```

tk421@ubuntu:~$ dmesg | grep wlan0
[4294706.765000] acx100: allocated net device wlan0, driver compiled against wireless extensions v17 and Linux 2.6.12-9-386
[4294707.101000] creating /proc entry driver/acx_wlan0
[4294707.101000] creating /proc entry driver/acx_wlan0_diag
[4294707.101000] creating /proc entry driver/acx_wlan0_eeprom
[4294707.101000] creating /proc entry driver/acx_wlan0_phy
[4294785.989000] wlan0: no IPv6 routers present

```


```

tk421@ubuntu:~$ lsmod | grep ac
af_packet              20232  2
cpufreq_userspace       4444  1
sony_acpi               5516  0
pcc_acpi               11392  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
ac                      4996  0
snd_ac97_codec         72188  2 snd_via82xx_modem,snd_via82xx
snd_pcm                78344  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd                    48644  14 snd_via82xx_modem,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
acx_pci               122752  0
firmware_class          9472  1 acx_pci
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro

```

Do I need to load module acx100?

```

tk421@ubuntu:~$ sudo modprobe acx100
FATAL: Module acx100 not found.
tk421@ubuntu:~$ sudo modprobe acx111
FATAL: Module acx111 not found.

```

I hope that gives some new ideas ...
I gonna download Ubuntu 5.04 live and I ll post the same commands on that  version .

Just I remember that the lights on the pcmcia card are turn on (Just the power one, not the "Act", that is lighting when is sending/receiveing data)

---

### Post by Lambert on 2005-11-06
from a terminal, what does

```
iwconfig
```

give you?

From the panel have you gone into System>Administration>Networking and set the properties on the card?

---

### Post by tk421 on 2005-11-09
Thats ironic ....

I have loaded Live 5.04, configures wireless and NOW im writting from there ...

**INFORMATION FROM LIVE OF UBUNTU 5.04 WITH WORKING WIRELESS**

```

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"802_11g"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:E0:98:BE:FB:45
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=49/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

```
ubuntu@ubuntu:~$ dmesg | grep wlan0
wlan0: no IPv6 routers present
wlan0: no IPv6 routers present

```


```

ubuntu@ubuntu:~$ lsmod | grep ac
cpufreq_userspace       4572  0
sony_acpi               6280  0
pcc_acpi               11264  0
ac                      4996  0
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
af_packet              20744  0
acx_pci               134816  0

```

Please ... someone with a good idea ...

---

### Post by tk421 on 2005-11-09
Now I have "go back" to Ubuntu 5.10, and this is the output of iwconfig that Lambert requested ...

```

tk421@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STABE5008"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Channel:1  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by K2712 on 2005-11-09
I'm having a similar problem with my Linksys WPC54G v4 card.  Here is my lspci output:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:08:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:08:08.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:09:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

"sudo iwlist wlan0 scan" gives me this:
wlan0               Interface doesn't support scanning

"sudo ifup wlan0" gives me this:
Ignoring unknown interface wlan0=wlan0.

"iwconfig" gives me this:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Can anyone help me please??

---

### Post by TimelessRogue on 2005-11-09
And now I'm back in this boat ... a week after reinstalling Breezy to get to the bottom of this kind of problem.  With me, it's a Linksys WPC11 v3 that was fine from the get-go in Hoary and the initial install of Breezy.  All was well using either wireless or DSL when lo and behold the same situation as before:  wireless was just not there ... for no explicable reason.

Outputs are mostly the same as K2712 aside from system differences.

So now I guess I'm back at it again trying to get wireless up and running with absolutely no idea of why it was knocked offline ...

Why has this become a problem?  Why would a system just not recognize a wireless connection, for instance, after working with no  problems and no system changes?  Hmmmm ...

---

### Post by Lambert on 2005-11-09
tk421:

One thing I notice was the essid's are different. 

> IEEE 802.11b+/g+  [COLOR="Red"]ESSID:"STABE5008"[/COLOR]  Nickname:"acx100 v0.2.0pre8" 
> IEEE 802.11g/b+  [COLOR="Red"]ESSID:"802_11g"[/COLOR]  Nickname:"acx100 v0.2.0pre8"

Go to this [[COLOR="Blue"]page[/COLOR]]("http://www.houseofcraig.net/acx100_howto.php")

About half way down you'll see a section titled [COLOR="Sienna"]Bringing your device "UP"[/COLOR]

See if any of that helps or makes sense. You may though just want to start from the top and read down though.

---

### Post by martymart on 2005-11-13
I have exactly the same problem as K2712 & TimelessRogue. My wireless card has been working fine for some time and then after reboot it just dropped off the face of the Earth!! I can still see the card in the hardware manager but that is all. Why the hell has this happened and what can I do to rectify the problem? Can I run the same network wizard that runs at install?

Thanks for the help,

Martin

---

### Post by TimelessRogue on 2005-11-13
Well, guys, I'm back ... with Breezy:  Episode III.  Yes, for the second time my wireless setup was just dropped ... and I mean dropped with a loud thud!  It's been since my last note on here about this problem that we seem to be having with wireless connections that worked from the get-go after installing Breezy and then seeming to quit functioning with no reasonable explanation ... with several different cards. 

 I spent considerable time over the last three days or so using all the tricks put forth on these boards ... aside from utilizing any tools such as ndiswrapper from outside the default installation of Breezy.  That has been my goal:  to have my Linksys WPC11 v3 up and running from the get go and for the duration but ONLY using the Breezy processes

"From the get-go" has not been the problem ... all is well in that respect with the card being recognized and set up during installation (which means the drivers are there.)  It happens somewhere along the line after that when, inexplicably, the whole thing just stops functioning and is no longer there ... not even to tweak!  It seems to happen after an update of Breezy, be it kernel or otherwise.  Which update I can't say.  Perhaps I should take steps to log updates and malfunction to try to pinpoint the source of the problem but I'm not inclined to do so a this juncture.

So is the answer to the rune to just not update?  That's seems a bit ludicrous, but I may give it a try this time.  But if it happens during one of the update processes, which one, which program and for what reason?  IF I do update, though, I will maybe check the logs to try to figure out what is happening.  The problem with that is that, like this last time as a for instance, all was well in the evening when I shutdown but not well at all when I logged on in the morning.

Am I being stubborn about not using ndiswrapper or some other such manner of setting up wireless?  Perhaps, but I do think we should not have to resort to this method except in the case of an obscure card that is either way older or perhaps so new that the drivers have not made in into Ubuntu yet (which of course raises the question of how do we see to it that new drivers are pumped into the system as soon as possible after release.)

Now ... I know this has not necessarily answered any questions.  But I HAVE let you know what I am doing to help solve this mystery.  Why?  Because I believe in and support Ubuntu and the principles surrounding it.  I also think that for Ubuntu to be useful to and used by the masses, it's got to be easier than this ... not everyone out there is geekish or has the time to fuss with it like some of us do ... and won't.  They want to be able to rely on their inet connections being there when the want them.  They'll just turn away and go back to Windoze or another distribution or whatever.  Open source will never be for the masses if that keeps happening.  Which is really sad since so many of us want it and will use it ... if it's easy to set-up and relatively fool proof ... without any deep tweaking.

PS:  For reference, this has all been on an HP n5000 laptop with a Linksys WPC11 v3 card (which comes up on eth1) using the i386 iso to install and then upgrading to the k7 kernel (only because the i386 is what I initially burned to cd.)

---

### Post by cyrano1917 on 2005-11-14
Hi,

Can you tell me what's in your /etc/network/interfaces ?

---

### Post by TimelessRogue on 2005-11-14
Sure, no problem ... should have done it last night ... and all is still working well even at two other locations.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any

auto eth1

iface eth0 inet dhcp

auto eth0


And this a copy of the results of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Access Point: 44:44:44:44:44:44   Bit Rate:2 Mb/s
          Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


And as I said, eth0 is my DSL connection ...

Good luck.  I'll post here if there are any further problems and try to include the cause and/or correction.

---

### Post by martymart on 2005-11-20
I installed a wired Ethernet card in a Ubuntu machine, and Ubuntu found it and I enabled it in the network connections panel. Every thing seemed to work fine but again the card just disappeared from the network manager and just stopped working after a reboot!! Why do my network cards keep disappearing never to be refound????

---

### Post by Lambert on 2005-11-20
[quote=martymart]I installed a wired Ethernet card in a Ubuntu machine, and Ubuntu found it and I enabled it in the network connections panel. Every thing seemed to work fine but again the card just disappeared from the network manager and just stopped working after a reboot!! Why do my network cards keep disappearing never to be refound????[/quote]

It sounds like your driver is not loading at boot. Find the driver it uses and then add it to /etc/modules

---

### Post by martymart on 2005-11-24
I reinstalled Ubuntu and everything worked fine again, but then the wireless card disappeared again. Thanks for the help Lambert, but how do I add the modules to /etc/modules and where do I find the module? Does anyone know why this might be happening?

Thanks for the help

Martin

---

