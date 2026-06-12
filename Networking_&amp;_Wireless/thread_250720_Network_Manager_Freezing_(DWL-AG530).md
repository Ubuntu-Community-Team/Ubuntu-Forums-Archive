---
title: "Network Manager Freezing (DWL-AG530)"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by oddmind on 2006-09-04
Hi everyone. I just followed a guide 
([http://ubuntuforums.org/showthread.php?p=1425763](http://ubuntuforums.org/showthread.php?p=1425763))
that I found on these forums about using ndiswrapper to setup a wireless conection with atheros cards. It just so happens I ahve the exact same model as the guy who posted the guide.

Anyhow, after I was done, ndiswrapper returned the thumbs up sign

```
oddmind@gilliam:~$ ndiswrapper -l
Installed ndis drivers:
neta3ab driver present, hardware present
```

Anyhow I couldn't connect to firefox after I rebooted so I looked back at the guide which told me to fiddle with System>Administration>Network

It said wireless hadn't been configured to i clicked configure and it froze on the stopwatch/hourglass.

It did this several times, so i checked around a couple fo threads and they had done the following.

Changed the Kernel line in /grub/menu.lst to

```
title		Ubuntu, kernel 2.6.12-9-amd64-generic Default (irqpoll)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro [COLOR="Red"]irqpoll[/COLOR] quiet splash
initrd		/boot/initrd.img
savedefault
boot
```

and the video driver line in xorg.conf to

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
#       Option		"UseFBDev"		"true"
        [COLOR="Red"]Option          "DisableIRQ"[/COLOR]
EndSection

```

I wasn't sure about the "UseFBDev" thing so i commented it out. i wasn't sure if i could have more than one option line, or how to put more than one option in there.

Anyhow, I'm running an AMD Athlon 64 3500+ with a Radeon x800 GTO2 and a D-link Air Premier DWL-AG530, and Ubuntu Breezy Badger.

If you need this information, here is what iwconfig returns

```
oddmind@gilliam:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Access Point: 00:00:00:00:00:00   Bit Rate:0 kb/s
          Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

I've also tried to install wifi radar from the add programs manager but it says that it cant do soemthing with repositories or some crap, I might have to download it on my xp partition.

If you know anything I can do to make wifi work please help :]

thanks

---

### Post by tturrisi on 2006-09-05
You do not need to use ndiswrapper w/ Atheros chipset cards.  All you need to do is enable the Universe & multi-universe repositores in /etc/apt/sources.list (remove # symbols) or enable via synapytic configs.  Then install the linus-restricted-modules that match your particular kernel.  The madwifi driver for atheros chipsets is in that package.  Ndiswrapper works but you will lose some of the better features of the card, such as monitor mode.

---

