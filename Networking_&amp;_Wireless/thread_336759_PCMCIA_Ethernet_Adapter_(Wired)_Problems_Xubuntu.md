---
title: "PCMCIA Ethernet Adapter (Wired) Problems Xubuntu"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by fusiachi on 2007-01-12
Edit: *Resolved*

Hi,

I've been using Ubuntu for a few months now, and have really started to fall in love with it.  My mother recently got a ghetto-old laptop, but the win98 install wasn't quite right...  I've since installed a copy of xubuntu, and want to get her up and running on the internet.  For some reason, though, the PCMCIA card I bought isn't detected.  I'm guessing this distro doesn't have the right drivers built in out of the box?  

Anyway, there was a driver disc w/the card, so I popped it in.  Keep in mind I'm a bit of a linux newb.  It had a directory labeled "linux" with drivers included for red hat 6.2 and 7.0.  Will these work?  And if so, how the heck do I get them installed?

The readme says

> 
1. Login as root.

2. Copy realtek_cb.o into /lib/modules/2.2.16-22/pcmcia
     "cp realtek_cb.o into /lib/modules/2.2.16-22/pcmcia"

3. Reference config contents, and add it into pcmcia/config

           #
           # Device driver definitions
           #

          device "realtek_cb"
          class "network" module "cb_enabler", "realtek_cb"

          #
          # CardBus Cards
          #

          card "10/100 CardBus Card
          manfid 0x0000, 0x021b
          bind "realtek_cb"

4. Restart the cardmgr
         
          "/etc/rc.d/init.d/pcmcia restart

5. Logoff root



Well, I haven't the slightest how to login to root in xubuntu.  I don't feel as if I should have to, anyways.  Much less have my mother accidentally do so in the future.  Secondly, I'm not too familiar with the command line, and my attempts to cp said file have been met with failure.  Also, editing the /pcmcia/config isn't working.  I'm guessing that's a problem with permissions?

Anyway, when it comes down to it, I can't get this stinkin' thing to work.  I'd greatly appreciate any help the community could offer.  If you need more information (and based on the little I've offered), just ask, and I'll try to figure out what you need to know.

Thanks for your time.

-Wade

---

### Post by dmizer on 2007-01-12
how long ago did you purchase that card?  those redhat drivers are ancient.  you might as well toss that cd in the trash.

what is the make and model of the card?  it may be as simple as blacklisting a conflicting module.

also ... with the wired card attached, open the commandline and type:
```
lspci
```
and post the results.  this will give us chipset information about your pcmcia card.

---

### Post by fusiachi on 2007-01-12
Ordered the card from newegg about 2 weeks ago.

It's on the generic side - Encore ENP832-TX-PC.

lspci info:

> 
00:00.0 Host Bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI Bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP Bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface:  Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller:  Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge:  Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00:0 VGA Compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 **Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL-8139/8139C/8139C+ (rev 10)**



Thanks in advance for any help.

---

### Post by fusiachi on 2007-01-12
I don't know if this is in line with forum etiquette, but I'm going to *bump* the above post in hope of support.

---

### Post by fusiachi on 2007-01-13
I'm thinking using the packaged windows drivers w/ndiswrapper might work; but this isn't a wireless card.  Nor would I have a clue how to get it working.  Thoughts?

---

### Post by fusiachi on 2007-01-13
Been trying to get this working for a while now.  Tried installing the XP drivers on the cd w/ndiswrapper.  Now, when I use the command ```
ndiswrapper -l
``` I get the following output:
> Installed ndis drivers: 
fethcb driver present, **hardware present**

To me, that looks like a positive result.  All the same, I don't know how to tell if my ethernet card is really being detected?  Sorry for all the posts, I just figured this might be the only place I'd find an answer.

Edit: Also, is there perhaps a conf file somewhere to edit that might help?  Anyway, I don't really have a clue.  Hopefully someone else does.  Thanks again.

Second edit: Also, the card lights up nice when an ethernet cable is plugged in.  If that has anything to do with... anything.

---

### Post by dmizer on 2007-01-14
ndiswrapper can work for some wired ethernet cards, but i don't think you need it.

you say you get lights when an ethernet cable is plugged in.  what's the output of ifconfig?  from the looks of things, your card should work.

---

### Post by fusiachi on 2007-01-15
Well, it shows up in ifconfig now as eth0.  Of course, that still doesn't make it usable to me for some reason.  A config file somewhere maybe would fix it?

---

### Post by dmizer on 2007-01-15
okay ... post the contents of /etc/network/interfaces

---

### Post by fusiachi on 2007-01-15
Think you're on to something.

> 
# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp



auto eth0


---

### Post by dmizer on 2007-01-15
first, move "auto eth0" to above the "iface eth0 inet dhcp" line.

restart networking with:
```
sudo /etc/init.d/networking restart
```
then do an ifconfig to see if you pulled an ip.

---

### Post by fusiachi on 2007-01-16
Not getting an ip.  Furthermore when I did ```
sudo /etc/init.d/networking restart
``` I got (and this is slightly abridged) 
> 
Listening on LPF/eth0/00:10:60:76:aa:84
Sending on  LPF/eth0/00:10:60:76:aa:84
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
NO DHCPOFFERS received.
No working leases in persistent database - sleeping.

So I'd guess something is going wrong at that point?  Anyway, thanks in advance for all your troubleshooting.

---

### Post by dmizer on 2007-01-16
try:
```
sudo dhclient eth0
```

if that doesn't help, try connecting with a static ip address.  don't worry about the fact that your router is dhcp, you still should be able to pick an ip within the dhcp range, and connect.

if that doesn't work, try rebooting your router (power off, wait, then power on).  what brand and model of router do you have?  is there a firmware update available?

i can't find anything that indicates your card shouldn't work in linux/ubuntu.

---

### Post by fusiachi on 2007-01-16
No luck.

Actually, I'm not connecting to a router.  Just swapping the cat5 back and forth between a tower and the laptop.  Using a Sprint 645 series DSL modem.

---

### Post by dmizer on 2007-01-16
you should still be able to reboot the modem (power off, power on), as well as plug in static ip settings.

modems don't handle cable swapping between computers nearly as well as routers do.

humm, that modem is frequently used for pppoe, is your service straight dsl, or is it adsl with pppoe?  (ie, in windows, do you have to plug in a username and password to get connected?)

---

### Post by fusiachi on 2007-01-16
No username/password.  And I restarted the modem both w/ and w/o a static IP set within the range (in this case I tried 192.168.1.3).

I'll give it another shot.

---

### Post by fusiachi on 2007-01-16
Okay, this was most definitely a PEBKAC situation.  After restarting the modem again, it was a no-go.  But then I looked at the ethernet cable and saw that it wasn't quite seated right.  Now, it's working like a charm.  Posting from a previously non-functional laptop.  Thanks for walking me through so much troubleshooting, dmizer.  Learned a lot about (x)ubuntu in the process of trying to find a solution.  

-Wade

---

### Post by dmizer on 2007-01-16
that's really fantastic!  glad we got it sorted.  enjoy.

---

