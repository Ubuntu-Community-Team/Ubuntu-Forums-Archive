---
title: "Unable to setup bluetooth headset due to snd_bt_sco problem?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by plasticM on 2007-11-04
Hi.

I've been trying to use a sony ericsson headset with my belkin dongle (which seems to work fine) in Gutsy, but I'm getting nowhere.  :(

So far the furthest I've been down any avenues is to try Stéphane Graber's [**[COLOR="Blue"]_gbtsco_[/COLOR]**]("http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/").  Unfortunately the following happens.

I can pair with the headset (by trying to browse it using the bluez bluetooth applet), and I can see it using gbtsco, but when I try to “use as active headset”, I get the following.
```
btsco: no process killed
ERROR: Module snd_bt_sco does not exist in /proc/modules
FATAL: Error inserting snd_bt_sco

(/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Error: control open (hw:1): No such device
Error: Can’t find device. Bail

```
Likewise “sudo modprobe snd-bt-sco” gives:
```
FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Is this an issue with my kernel? Can anyone advise? I’m still pretty new to Linux and certainly haven’t messed with my kernel yet.

Or if anyone has any other suggestions to get the headset up and running I'd be really grateful.

Thanks,

Tim

ps Sorry, this is kind of a cross post with a comment on Stéphane's blog, but I'm not sure how often he checks that and I'm impatient.  :redface:

---

### Post by plasticM on 2007-11-05
Erm.  Bump? 

Can anyone maybe just point me in the right direction?

---

### Post by Evanlec on 2007-11-12
yes, same problem here
using vanilla kernel 2.6.23.1 - is this why?

---

### Post by Truster on 2007-11-15
i also have the same problem here, but only with the realtime-kernel. The module works with generic kernel

---

### Post by Truster on 2007-11-16
I've success. i can now use the snd_bt_sco module after removing the package **linux-backports-modules-2.6.22-14-rt**, so try this in a terminal:

**sudo apt-get remove linux-backports-modules-`uname -r`**

this works... at least on my computer.

Good Luck

---

### Post by plasticM on 2007-11-18
Thanks Truster, that seems to have made progress.  My headset connects and even beeps but I'm still not there.  :(

The process now is:

 - boot up

 - enter "sudo modprobe snd-bt-sco" in a terminal

 - enter "sudo gbtsco" (gbtsco opens)

 - set headset to pair, and "check for new devices" in gbtsco

 - headset shows, select to "use as active headset"

 - headset shows as active headset

And this is where it goes wrong.  I can't see the headset in the Sound Preferences to select it.The sound playback options are:
-autodetect 
-ALC833 Analog
-ALSA
-ESD
-OSS
none of which make any sound issue from the headset. :( There is a "BT headset (Alsa Mixer)" under Mixer Options - Devices, but I can't seem to use it for anything.  Am I missing something obvious?

The other attempt I've made is to use skype anyway.  Skype does make the headset connect, beep once, connection noise (ie quiet static), beep again, disconnect.

If I use skype to try test sounds I get the following:
for default device:
  -    headset connects, beeps once, connection noise (test sound comes from PC speakers), beeps again, disconnects
for "BT Headset (hw:Headset, 0)" or "BT Headset (plughw:Headset, 0)"
   -    headset connects, beeps once, connection noise continues for a while then skype closes (well, crashes I suppose)

I feel like I'm nearly there - the computer's talking to the headset and everything.  It's just not using the speaker on it. :(

Can anyone help?

Thanks for reading,

Tim

---

### Post by Truster on 2007-11-19
i use the command "btsco -r -f xx:xx:xx:xx:xx:xx"

replace the xx with the MAC address from the headset

i only use Twinke, i can select BTSCO as sound device

try asoundconf -list if the BTSCO appers

hope, this helps

---

### Post by sceo on 2007-12-06
exact same behavior as PlasticM - in Gutsy, Plantronics 3XX... i'm so close... it's just that, well, no sound is coming out of the headset - still coming out of the speakers...

---

### Post by hrabeX on 2007-12-08
> **plasticM said:**
> Hi.

I've been trying to use a sony ericsson headset with my belkin dongle (which seems to work fine) in Gutsy, but I'm getting nowhere.  :(

So far the furthest I've been down any avenues is to try Stéphane Graber's [**[COLOR="Blue"]_gbtsco_[/COLOR]**]("http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/").  Unfortunately the following happens.

I can pair with the headset (by trying to browse it using the bluez bluetooth applet), and I can see it using gbtsco, but when I try to “use as active headset”, I get the following.
```
btsco: no process killed
ERROR: Module snd_bt_sco does not exist in /proc/modules
FATAL: Error inserting snd_bt_sco

(/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Error: control open (hw:1): No such device
Error: Can’t find device. Bail

```
Likewise “sudo modprobe snd-bt-sco” gives:
```
FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Is this an issue with my kernel? Can anyone advise? I’m still pretty new to Linux and certainly haven’t messed with my kernel yet.

Or if anyone has any other suggestions to get the headset up and running I'd be really grateful.

Thanks,

Tim

ps Sorry, this is kind of a cross post with a comment on Stéphane's blog, but I'm not sure how often he checks that and I'm impatient.  :redface:

I have exactly the same problem in Gutsy, no linux backported modules installed. Still the same problem with inserting snd_bt_sco module (fatal error) and in gbtsco hw error. lsusb shows me:
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (                                HCI mode)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c044 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
```

---

### Post by sjvdwalt on 2008-01-31
It looks like btsco has been replaced by the newer bluetooth-alsa.  The build.html in /usr/share/doc/bluetooth-alsa details the installation process.  I managed to get my Jabra BT200 working this way, even though there are still a few minor hitches (e.g. the first Skype call works perfectly, on the second the other person receives noise from my side).

Good luck!

---

