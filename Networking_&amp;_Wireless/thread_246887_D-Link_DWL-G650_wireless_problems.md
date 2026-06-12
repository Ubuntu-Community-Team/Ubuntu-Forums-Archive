---
title: "D-Link DWL-G650 wireless problems"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by TrIde2188 on 2006-08-29
Right i have tried - due to a friends help - tried many linux distros but so far i have not been able to get my wireless card - it is in the name, rev C3 - working, only one light is on blinking every 10 seconds or so... Any help/tips would be helpful

Thanks in advance

-TrIde

---

### Post by funchords on 2006-08-29
That should work right out of the box with Dapper Drake.  

Try this command in a terminal window:

**sudo iwconfig**

---

### Post by TrIde2188 on 2006-08-29
okay i tried that ... it says
lo no wireless extensions.

sit0 no wireless extensions


but before ... the wireles card was as i siad blinking once eveyr 10 seconds wlel only one of the two lights was

now its juston all the time whichi guess is a good thing? lol

the other light tho (to say its connected ) isnt

---

### Post by funchords on 2006-08-30
Hmmm.  Try these:
[B]
sudo ifconfig ath0 up
sudo ifup ath0
sudo iwconfig ath0[/B]

If that doesn't get you online, then try these and post the results:

[B]dmesg | grep ath
lspci | grep Network[/B]

---

### Post by tturrisi on 2006-08-30
The card should have an Atheros chipset which meaqns you must install the linux-restricted-modules for your kernel.  Run Synaptic, enable universe & multiuniverse repositories & install the trestricted package that matches your kernel.

---

### Post by TrIde2188 on 2006-08-30
okay i did the

sudo ifconfig ath0 up
sudo ifup ath0
sudo iwconfig ath0

but i changed ath0 for sit0 seeing as thats what mine is lol.

sudo ifup sit0 gave 
Ignoring unknown interface sit0=sit0

and after the last one i still got

sit0   no wireless extension

after typing
dmesg | grep athi got this

[4294737.787000] ath_hal: module license 'Proprietary' taints kernel.
[4294737.818000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294737.895000] ath_rate_sample: 1.2
[4294737.949000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294737.980000] ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

then i replaced the ath with sit and got

[4298678.056000] Disabled Privacy Extensions on device c2855400(sit0)

i typed 

lspci | grep Network

it just went back to the command line

---

### Post by TrIde2188 on 2006-08-30
> **tturrisi said:**
> The card should have an Atheros chipset which meaqns you must install the linux-restricted-modules for your kernel.  Run Synaptic, enable universe & multiuniverse repositories & install the trestricted package that matches your kernel.

Yea im doing that atm

but .. then what im sliughtly confused as to what to do with it ? =/ sorry if the answer is smack bang in my face lol

---

### Post by funchords on 2006-08-30
My safest guess:  After you install it, reboot the system so that the device can be detected.  

Let me know...

---

### Post by TrIde2188 on 2006-08-30
Rebooted -
still only onelight not flashing on the card itself
ifconfig produced -
lo 
thats it =/
sudo iwconfig produced

lo no wireless extensions

sit0 no wireless extensions

no sign of the wireless card anywhere =/

---

### Post by tturrisi on 2006-08-30
sit0 is NOT your wifi interface.  sit0 is a network extension that has to to with ip6.

dmesg says what's up:  
ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

did you install the correct linux-restricted-modules?  It MUST be the package that matches the kernel you are booting with.  If you boot with kernel-2.6.1.25 then you need the restricted package of same name, etc. for other kernels.

---

### Post by TrIde2188 on 2006-08-30
Ah right ok

i only have one in the synaptic package manager

well i typed in the search linux restricted

it came up with
package:                                isntalled version
linux-restricted-modules-2.6.12-9-386   2.6.12.4-11
linux-restricted-modules-386            2.6.12.16
linux-restricted-modules-common         2.6.12.4-11

---

### Post by tturrisi on 2006-08-31
open a terminal & type:
uname -r
post the result here.

---

### Post by TrIde2188 on 2006-08-31
uname -r
=
2.9.12-9-386

---

### Post by tturrisi on 2006-08-31
look on back of the card, what is the model along with version # ?
(dlink made the 650G using 4 different chipsets!

---

### Post by TrIde2188 on 2006-08-31
didnt find a "model umber" so ill give all nsets of numberslol

FCC ID:   KA22004042015-1
P/N:      DWLG650EU.C3
S/N:      DR7414B004261
MAC ID:   001195B8E16C
H/W Ver.: C3
F/W Ver.: 4.11

---

### Post by tturrisi on 2006-08-31
ok. hardware version c3, so your card does have an atheros chipset.
By any chance does your laptop have a led light and/or button for wifi?  Some laptops' wifi led is also a button, as on some acer models.

---

### Post by TrIde2188 on 2006-08-31
Erm looked around the laptop itself and there doesnt seem to be any sign of a button/light =/

---

### Post by TrIde2188 on 2006-08-31
nudge? =/ =]

---

### Post by funchords on 2006-08-31
> **tturrisi said:**
> ok. hardware version c3, so your card does have an atheros chipset.
By any chance does your laptop have a led light and/or button for wifi?  Some laptops' wifi led is also a button, as on some acer models.

This is a PCMCIA/Cardbus card, so there won't be a button or a Fn key.  Plug it into the slot and it's on.  Nothing to enable.

---

### Post by TrIde2188 on 2006-08-31
its on... theres a green lgiht but when used in dads laptop... 

theres two lights flashing simultaneously (sp?) to show the live internet connection
this is one light on its own on all the time =/

---

### Post by funchords on 2006-08-31
sit0 is something else.  Ignore it.  I promise.

> **TrIde2188 said:**
> 
after typing
dmesg | grep athi got this

[4294737.787000] ath_hal: module license 'Proprietary' taints kernel.
[4294737.818000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294737.895000] ath_rate_sample: 1.2
[4294737.949000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
**[4294737.980000] ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)**

Okay, this is why it's not working right out of the box.  I'm not sure how to proceed, yet.

I'd sure like to see if there are any dmesg entries between that first line and that last line (and maybe just a couple lines before and after).

Probably the easiest way to do this is to issue these commands:

[B]dmesg > ~/dmesg.txt
*myeditor* ~/dmesg.txt[/B]

(replace *myeditor* with your favorite editor, such as kate or gedit)

Then locate a line that matches the data in that top line, and cut and paste the line(s) before/within/after that section that you think probably apply to that network card.

---

### Post by funchords on 2006-08-31
Another output I'd like to see is 

cat /var/log/syslog | grep "cardmgr"

This should report entries/removals/detections from the PCMCIA slot.

---

### Post by tturrisi on 2006-09-01
google turns up very little on:
 ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
but has some references to the acer laptops' wifi on-off buttons, which is why I asked about it.

---

### Post by spd106 on 2006-09-01
First I would suggest obtaining the 6.06.1 updates. Download the CD if you are unable to connect directly. Make sure you dist-upgrade and have the ubuntu-desktop installed. Maybe the 2.6.15-26 kernel + restricted drivers will work.

If it still doesn't work could you try building madwifi-ng from source? The latest version 0.9.2 seems to work well with my G650 H/W:C2 There are a lot of dependancies though gcc, make, linux-headers etc. The wiki has a howto.

---

### Post by TrIde2188 on 2006-09-01
Yea iv ehad some help last night, im gonna get a friend to help me compile the madwifi0ng source, and i have gcc-4.0 but it doesnt want that it seems to only work/want gcc-3.4 =/

---

### Post by AllenGG on 2006-09-01
Thanks to some of the posters here I was able to get the "D-Link DWL-G520" working right out of the box.
Process, did "uname -r" got kernel version, 
ckecked to make sure same "restricted modules" installed,
then to; System>Aministration>Window Wireless Drivers
and "Configure Network"
3 choices:
Wireless Connection,  ath0 > activate
Properties: checked Enable this connection
then (my) Network name  ESSID ..............
then Connection Settings> Configuration>DHCP
note, I had removed the network cable previously
other 2 choices were: Ethernet Connection eth0
and Modem Connection PPP0
still needs a little tweaking but works as well as the cable via eth0
Allen:cool:

---

### Post by TrIde2188 on 2006-09-01
> **spd106 said:**
> First I would suggest obtaining the 6.06.1 updates. Download the CD if you are unable to connect directly. Make sure you dist-upgrade and have the ubuntu-desktop installed.

As i think i said at the begining, i have not got enough ram to run the dapper drake live cd to install..thats why i used breezy badger because there was a "install only" iso

oif i had the "install only" iso for dapper drake that would be very helpful =]

---

### Post by spd106 on 2006-09-02
> **TrIde2188 said:**
> As i think i said at the begining, i have not got enough ram to run the dapper drake live cd to install..thats why i used breezy badger because there was a "install only" iso

oif i had the "install only" iso for dapper drake that would be very helpful =]

What's wrong with the alternate CD? It has the text-based installer and all the up-to-date debs. All they did was rename the live cd 'desktop' as it contains the new live installer. That way it's much simpler for new user to install. The old install CDs are now labelled 'alternate'. I would provide a link but it's better to find a local mirror and the main cdimage site only seems to have the DVD.

---

