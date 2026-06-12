---
title: "Orinoco wireless recently stopped working..."
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by elistar on 2008-07-14
Hi all,

Long-time reader, first-time poster here. I'm having a bit of trouble with my wireless, and am hoping someone out there could possibly help.

This is all very similar to this thread, but I've tried the fix suggested with no results.

My situation: 

I'm running Xubuntu 8.04 (auto-updated from 7.10 back in April) with its built-in Lucent/Agere (8.1 firmware) wireless card. It worked fine until about a week ago, when after a reboot, it would no longer give me an IP.

a) Orinoco drivers are loaded (orinoco, orinoco_cs, hermes, psmcia and pcmcia_core)

b) Potential conflicting drivers (prism*, hostap) are neither blacklisted nor loaded (lsmod | grep prism; lsmod | grep host) give no results. 

c) ifconfig shows the interface eth1 with correct MAC address but no  IP address. It also shows eth0 (wired internet) with an IP from the same router, and two Avahi addresses.

d) When I start up, iwconfig shows the interface eth1 with a blank ESSID and correct MAC address for the access point. I can set essid (sudo iwconfig essid Blahblah) to my hidden ESSID, and iwconfig then shows the right ESSID. 

e) sudo iwlist eth1 scan reports no results

f) I'm not using any encryption on the router or the laptop.

g) dhclient fails to get an IP address ("No DHCPOFFERS received.")

h) I tried static IP but didn't work either.

i) ping 192.168.0.1 doesn't get a response from the access point.

j) I can convince the gnome nmapplet (nm-editor?) that it's connected at 87% strength, but iwconfig never reports an association with an access point. 

k) I've tried the following options to the kernel loading: noapic nolapic acpi=off apm=on. It didn't solve the problem.

Results from lshw -C network are:
```

  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:85:c8:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.4 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:56:ba:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b

```

And finally (as per the suggestion in the thread linked above), the results of cat /proc/interrupts show a bunch of stuff sharing IRQ11: 

```

           CPU0       
  0:    1304813    XT-PIC-XT        timer
  1:      17936    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:        192    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:          1    XT-PIC-XT      
  7:          1    XT-PIC-XT      
  8:          3    XT-PIC-XT        rtc
  9:        574    XT-PIC-XT        acpi
 10:          1    XT-PIC-XT      
 11:     143415    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2, yenta, yenta, eth0, ALI 5451, pcmcia0.0
 12:        119    XT-PIC-XT        i8042
 14:      55989    XT-PIC-XT        ide0

```

But adding "exclude irq 11" (and/or exclude irq 3, just for fun) has no effect on the interrupts used. 

Finally, I have a workaround: plug in my Microsoft Wireless card, which uses the Orinoco drivers, and I get internet (on eth2). (This card also shows up as two entries in lshw -C network...)

My eternal gratitude to anyone who has any ideas... I'm completely stumped!

- elistar

---

### Post by dmizer on 2008-07-14
recently, my orinoco card has been causing problems with my wireless router.  i can use it once, and then my router will not allow the orinoco card to connect.  it also causes other problems like DNS resolution.

it may be unique to my situation, but i do know that simply rebooting the router fixes the problem.  it's easy to do, and it's worth a try.

if that fixes your problem, you may want to see if you can find some updated firmware for your router.  it may also be a bug in the orinoco driver.

---

### Post by elistar on 2008-07-14
Thanks for the quick response, dmizer. Tried it - and unfortunately no luck. 

(FWIW, the router is a Netgear WGR614v5. It happily hands out an IP to iPhones, PSPs, iPod touches, my Wii, Nintendo DSs, my Linksys router with DD-WRT, my wife's laptop, etc... many of which grabbed IPs after I reset it.)

I'm beginning to suspect that my problem is related to this bug  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/79398]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/79398") since I'm getting the same type of message (quote from the bug page:)

```

My Vodafone 3G datacard, Novatel Wireless Merlin U630 PCMCIA modem doesn't work in feisty.

In dapper inserting the card works as expected:

Jan 15 13:20:38 ubuntu kernel: [4297888.937000] pccard: PCMCIA card inserted into slot 0
Jan 15 13:20:38 ubuntu kernel: [4297888.937000] pcmcia: registering new device pcmcia0.0
Jan 15 13:20:38 ubuntu kernel: [4297888.938000] pcmcia: registering new device pcmcia0.1
Jan 15 13:20:38 ubuntu kernel: [4297889.006000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

But in Feisty Herd 2 it has an error:

Jan 15 13:53:03 pechin3 kernel: [ 411.318328] pcmcia: request for exclusive IRQ could not be fulfilled.
Jan 15 13:53:03 pechin3 kernel: [ 411.318339] pcmcia: the driver needs updating to supported shared IRQ lines.
Jan 15 13:53:03 pechin3 kernel: [ 411.361612] serial_cs: serial8250_register_port() at 0x03f8, irq 3 failed
Jan 15 13:53:03 pechin3 kernel: [ 411.361921] pcmcia: request for exclusive IRQ could not be fulfilled.
Jan 15 13:53:03 pechin3 kernel: [ 411.361925] pcmcia: the driver needs updating to supported shared IRQ lines.
Jan 15 13:53:03 pechin3 kernel: [ 411.403842] serial_cs: serial8250_register_port() at 0x02f8, irq 3 failed
``` 

Now, since sudo pccardctl ident reports the following:

```

Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"
Socket 1:
  no card

```

I think I *should* be able to force the orinoco driver to use a different IRQ, but I can't seem to make it work. Any suggestions on what to type (and where)? I've added 

```
module "orinoco_cs" opts "irq_list=3,4,5,6,7"
```

to /etc/pcmcia/config.opts, with no luck, but will keep trying other things...

- elistar

---

### Post by dmizer on 2008-07-14
> **elistar said:**
> I think I *should* be able to force the orinoco driver to use a different IRQ, but I can't seem to make it work. Any suggestions on what to type (and where)?

try the pci=routeirq boot option.

---

### Post by elistar on 2008-07-14
You're fast! Thanks again...

I actually tried that around the time that you suggested it - after I saw the note in dmesg. Unfortunately, it didn't have any effect on my problem. (I didn't have any noticeable effect at all, actually - but I didn't save the old dmesg to run diff on.) 

(An aside: when I add "pci=routeirq" to the /boot/grub/menu.lst options, I put it in quotes. Does that matter? Should I have omitted the quotes?)

Is there any way to force Ubuntu to install an older kernel (say, 2.6.12)? Other than that, I'm just about out of ideas.

-elistar

---

### Post by dmizer on 2008-07-14
> **elistar said:**
> You're fast! Thanks again...
lol, a product of being bored ;)

> **elistar said:**
> (An aside: when I add "pci=routeirq" to the /boot/grub/menu.lst options, I put it in quotes. Does that matter? Should I have omitted the quotes?)

you should have omitted the quotes.

i usually suggest editing grub via the boot menu first, so that you can test settings before making them permanent.  that way if you mess up by putting a space where one should not be, and bork your boot, all you have to do is reboot to clear the error.

---

### Post by elistar on 2008-07-15
Well, now I know about quotes. Still no luck, unfortunately (and I checked dmesg to find 

```
[14255.765459] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified

```

...so I think it worked. Any idea why the pcmcia module is assigning everything IRQ 11 (even 16-bit devices), despite my urging? When I insert the Microsoft card (MN-520; using an Intersil chip), it gets assigned IRQ 11. Both devices are running through the PCMCIA bridge, so why does only the external card obey the rules? (And yes, these questions are mostly rhetorical...)

Here's hoping you're still bored tomorrow.

Best,
elistar

---

### Post by dmizer on 2008-07-15
well, if pci=routeirq didn't work for you, then i don't think you have an irq problem because that would most likely have fixed it.

i don't think everything is actually bound to irq 11, just the pcmcia socket and related sockets are bound to irq 11, which seems natural.  remember, the serial_cs module loaded on irq 3:
```
Jan 15 13:53:03 pechin3 kernel: [ 411.361612] serial_cs: serial8250_register_port() at 0x03f8, irq 3 failed
Jan 15 13:53:03 pechin3 kernel: [ 411.361921] pcmcia: request for exclusive IRQ could not be fulfilled.
```

given that error, you might consider blacklisting the serial_cs module in /etc/modprobe.d/blacklist by adding this line at the end:
```
blacklist serial_cs
```

---

### Post by elistar on 2008-07-15
Hi again - sorry for any confusion; the serial port binding at IRQ3 was just quoted from the bug report at launchpad. I don't actually have a serial driver loaded at all.

On my system, if I insert my PCMCIA CDROM drive, it gets assigned IRQ 3; if I insert the Microsoft Wireless card it also gets assigned IRQ 3 (can't do both at the same time, since there's only one slot). Without either those cards inserted, my USB ports, ethernet, sound card, and the internal PCMCIA slot are all at IRQ 11, as follows. 

Before inserting Microsoft Wireless card:

```

           CPU0       
  0:    2556452    XT-PIC-XT        timer
  1:       6485    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:        624    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:          1    XT-PIC-XT      
  7:          3    XT-PIC-XT      
  8:          3    XT-PIC-XT        rtc
  9:       1432    XT-PIC-XT        acpi
 10:          1    XT-PIC-XT      
 11:      95558    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2, yenta, yenta, eth0, ALI 5451, pcmcia0.0
 12:        149    XT-PIC-XT        i8042
 14:      40149    XT-PIC-XT        ide0

```

And after:

```

           CPU0       
  0:    2671104    XT-PIC-XT        timer
  1:       8143    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:        635    XT-PIC-XT        pcmcia1.0
  4:          1    XT-PIC-XT      
  5:          1    XT-PIC-XT      
  7:          3    XT-PIC-XT      
  8:          3    XT-PIC-XT        rtc
  9:       1471    XT-PIC-XT        acpi
 10:          1    XT-PIC-XT      
 11:     100410    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2, yenta, yenta, eth0, ALI 5451, pcmcia0.0
 12:        149    XT-PIC-XT        i8042
 14:      40443    XT-PIC-XT        ide0

```

Even though the two cards are apparently both 16-bit cards, according to pccardctl status:

```

Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"

```

Thus, my suspicion that this is new behaviour from the something in the pcmcia subsystem. Also, happy to be wrong, but running out of ideas.

If I do 'sudo pccardctl eject 0' then pcmcia0.0 gets dropped from IRQ 11, but as soon as I ask for reinsertion, it show up again.

Finally, if it helps at all, I can set the essid and mode (and other settings) on the internal card, but if I try to set the channel, I get the following error:

```

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Device or resource busy.

```

Standard output from iwconfig is:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Homsar"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

(Thanks again.)

- elistar

---

### Post by elistar on 2008-07-15
Ahh... never mind. I just compared (manually) some old kernel logs from the end of June to my current dmesg. The internal card has been getting IRQ11 forever - even back when it was working. I'm now officially at a loss. 

Any brilliant ideas? Anyone? :)

Beginning to think that the card may just have died...

- elistar

---

### Post by dmizer on 2008-07-15
yes, i really didn't see anything unusual about the irq settings, and booting with the pci=routeirq basically confirmed that.

can you do a scan?
```
sudo iwlist eth1 scan
```

do you have any other wireless access points you can test?

---

### Post by elistar on 2008-07-16
Hi dmizer,

Sorry for the delay - work intervened with my wireless quest. I *cannot* do a scan with the internal wireless card; it returns a blank list. My other card reveals several nearby access points, some of which are unlocked. I've tried associating with them (setting the essid to match) with no luck. 

Thanks for all your help... 

- elistar

---

### Post by elistar on 2008-07-16
Just in case it's of any help to anyone:

```

sudo iwlist eth1 scan
eth1      No scan results

```

And moments later (with eth2, the Microsoft card):

```

sudo iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:15:E9:D5:B4:50
                    ESSID:"rmpl"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level:19/153  Noise level:16/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
          Cell 02 - Address: 00:1C:10:A9:3A:06
                    ESSID:"Soniouze"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Signal level:24/153  Noise level:14/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:19:7E:12:E2:32
                    ESSID:"the game grid"
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Signal level:20/153  Noise level:14/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
          Cell 04 - Address: 00:1B:63:2C:5E:EA
                    ESSID:"Pearson"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Signal level:21/153  Noise level:14/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 05 - Address: 00:1B:11:4A:D5:D7
                    ESSID:"CherylsPlace"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:16/153  Noise level:12/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
          Cell 06 - Address: 00:18:F8:C0:EF:42
                    ESSID:"mikE"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:15/153  Noise level:13/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:1C:F0:F6:4A:9E
                    ESSID:"rodboy"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Signal level:41/153  Noise level:13/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 08 - Address: 00:1E:58:30:14:F9
                    ESSID:"Your Mom Goes to College"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:20/153  Noise level:15/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
          Cell 09 - Address: 00:13:46:F2:72:0A
                    ESSID:"ElmiraNet06"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Signal level:27/153  Noise level:15/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

```

- elistar

---

### Post by dmizer on 2008-07-17
humm, it appears as though the orinoco card is able to perform a scan, it's just not sensitive enough to find any networks.

if you boot to an older kernel do you still have the trouble?

---

### Post by elistar on 2008-07-17
Hi again,

The oldest kernel I have on the machine is 2.6.20 (from the original 7.04 install) - and behaviour is identical with that, 2.6.22, or an earlier build of 2.6.24 (I seem to have about 6 different 2.6.24 kernels). 

I admit I haven't tried all possible combinations of pci=routeirq, noapic and acpi=off with the older kernels - but I never used those options in the first place, and the card was working until about noon on July 8th.

Given the age of this machine (P3M-750), I think compiling an older kernel is a bit too large a project for me to chew on at this point.

- elistar

---

### Post by dmizer on 2008-07-17
next thing i would do then, is to test the card in a windows machine.  if you had kernels back to 7.04 and you tried them all, then there's obviously no need for you to compile any kernel.

i'll see if i can dig up my own orinoco card and test it, but i expect that the antena in your card has been severed or damaged in some way because everything else seems to be working fine.

---

### Post by elistar on 2008-07-29
It's tough to test in a Windows machine, since it's the built-in card. I could reinstall Windows, but since the CD is an external PCMCIA drive (bootable, but confuses most linux installs), so this would involve a day or two of pain.

An interesting new development (in case you're still reading this): I picked up a faster IBM X30 laptop for cheap, and threw Xubuntu on there. Install worked fine, including setting up my wireless card. As soon as I rebooted into Xubuntu, Wireless was gone. Same built-in wireless as my Portege; exact same symptoms. I think that something was done to Xubuntu recently that's broken the communication with this card... outside of the kernel? 

I'm going to try to get things working on the X31 (different distros, Ubuntu 6.06, etc.) to see if I can isolate what the problem is... will post again if I find a solution.

- elistar

---

### Post by dmizer on 2008-07-29
I'm still reading this.  I have not yet found my own orinoco card, but I will make a concerted effort to do so this evening.

Try disabling NetworkManager? [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

Edit:
Found it (I really had to dig :o)

```
$ lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:ab:11:f2:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.4 ip=192.168.0.2 multicast=yes wireless=IEEE 802.11b
```

```
$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:90:CC:0F:5D:7C
                    ESSID:"shinkansen"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Signal level:64/153  Noise level:16/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
```

```
$ ping www.google.com
PING google.navigation.opendns.com (208.67.219.231) 56(84) bytes of data.
64 bytes from www.google.com (208.67.219.231): icmp_seq=1 ttl=48 time=131 ms
```

```
~$ head -n1 /etc/issue
Ubuntu 8.04.1 \n \l
```

Still suggest you disable NetworkManager as linked above.  I don't seem to have any problems with the orinoco driver itself.

---

### Post by elistar on 2008-09-09
A post-mortem for anyone who might stumble across this thread:

First, a huge thank-you to dmizer, who had the patience of a saint. Without his help, I might have started to question my own sanity.

The Orinoco card works fine. A combination of problems with two computer caused my issues:

[LIST=1]
[*]On the Portege 2000 (since sold), the external switch to enable/disable wireless got jammed - even though it appeared to be 'on', it was stuck off. Interestingly, the switch doesn't disable the card itself, but just the antenna. After discovering that (while cleaning the computer for sale) and using some compressed air and a small blade, everything started working again.
[*]On the ThinkPad X30 (currently for sale), there was an almost-identical wireless card installed, but *the built-in antenna that runs around the screen had never been connected*. Discovered this one while opening the computer up to replace the wireless card with a new one, and found the two connectors for the antenna still sitting in a little anti-static pouch glued to the motherboard. Plugged the connectors in, and it started working.
[/LIST]

**Conclusion**: if your Orinoco card seems to suddenly stop seeing networks, chances are ***very strong*** that it's an antenna issue, since the drivers appear to be fine, error messages about shared IRQs etc. notwithstanding.

I've now moved on to a Dell C640 laptop (1400x1050 screen) with an Orinoco card, and it works just fine. :-)

- elistar

---

