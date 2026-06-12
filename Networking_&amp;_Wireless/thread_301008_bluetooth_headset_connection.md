---
title: "bluetooth headset connection"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by casaschi on 2006-11-16
Trying to connect to my bluetooth headset on a new Edgy install.

I looked at [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) for guidance

When my headseat is in pairing mode, if try  

  sudo hidd --search

I get totally no output, not even the "No devices in range or visible" that I get when the headset is off.

But if I try 
  sudo hcitool scan
then my headest is recognized
  aa:bb:cc:dd:ee:ff       BT Headset-12

If I try then
  sudo hidd --connect  aa:bb:cc:dd:ee:ff
I get the error message
  Can't get device information: Permission denied

(obviously I replaced the real address of my device with a fake one)

Any hint?

-- Paolo

---

### Post by tarun77 on 2006-11-20
I have the exact same problem except when I try 
> sudo hidd --connect aa:bb:cc:dd:ee:ff
I get 
Can't get device information: Success
but the device didn't connect. If I run this again 
> sudo hidd --connect aa:bb:cc:dd:ee:ff
I get 
Can't get device information: Input/Output Error

Has anyone faced a similar problem and managed to solve it? Any help is much appreciated.

Thanks,
Tarun

---

### Post by casaschi on 2006-11-20
I sorted my bluetooth problem thanks to the suggestions below:
[http://thread.gmane.org/gmane.linux.bluez.user/11012/focus=11012](http://thread.gmane.org/gmane.linux.bluez.user/11012/focus=11012)

Now I can use my headset with Skype...

---

### Post by tarun77 on 2006-11-21
Thanks for the suggestion Paolo.

I followed that thread, installed the bluez-btsco package
> sudo aptitude install bluez-btsco
loaded the btsco module
> sudo modprobe snd_bt_sco
and ran the following command 
> btsco -v aa:bb:cc:dd:ee:ff
This is what I get
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 8 connected
Using interface hci0


Also, I have bluez-passkey-gnome installed but I never get asked for a pin. The device doesn't seem to be connected. What am I missing?

---

### Post by dief-eh? on 2007-01-06
> **tarun77 said:**
> Thanks for the suggestion Paolo.

I followed that thread, installed the bluez-btsco package
> sudo aptitude install bluez-btsco
loaded the btsco module
> sudo modprobe snd_bt_sco
and ran the following command 
> btsco -v aa:bb:cc:dd:ee:ff
This is what I get
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 8 connected
Using interface hci0


Also, I have bluez-passkey-gnome installed but I never get asked for a pin. The device doesn't seem to be connected. What am I missing?

Hi there!

I gather that if your hcid.conf file has security auto, you might not get asked. But at least you have 2 lines that I don't:

btsco -v  00:03:89:53:EC:7F
btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused

How do I connect on a RFCOMM channel?

---

### Post by gardo on 2007-02-23
I'm also getting the RFCOMM connection refused.

#btsco -v  00:BF:5F:65:60:9C
btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused

Has anyone found a workaround for this?

---

### Post by fwendt on 2007-03-13
Hi, I'm having the exact same problem with RFCOMM: Connection refused. I have hade no problems using my phone as a GPRS modem, and I've tried several variants of the /etc/bluetooth/rfcomm.conf file. I get a feeling that the problem lies somewhere else.
The headset is a SonyEricsson HBH-DS970 and I really like it.

---

### Post by Permafrost91 on 2007-09-03
having the same problem here using Gutsy and a Ativa BT-220 headset. any help would be greatly appreciated (knowing of course that Gutsy is not yet stable, but I'm having the same issues under Feisty it seems)

---

### Post by kevinmedina on 2007-09-03
Same problem with a Plantronics headset :-(

```
kevinmedina@ubuntu:~$ sudo btsco -v 00:03:89:E7:BA:8B btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

```

---

### Post by rchille on 2007-09-05
Same problem both when I run from the command line:

```
btsco -v 00:17:F2:9E:24:21
btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused
```

And from gtbso from:
[http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/](http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/)

I'm running the latest Gutsy and this is as far is I've made it with my Jabra BT1080's. I could never get Feisty to even give them a look. Happy that I made it this far with Gutsy, now if we could just get that last little bit... :)

---

### Post by rchille on 2007-09-05
Okay apparently I grabbed the wrong address.

When I switched to the correct one gbtsco connected to the headset and I even got a connect beep to play through it when I ran xmms!!!

Unfortunately, instead of speakers my Jabra BT8010 seems to think that xmms is "calling" it and it goes into phone mode. I haven't able to sort this out, any ideas?

UPDATE:
I tried:
```
aplay -B 1000000 -D plughw:Headset /usr/share/sounds/login.wav
```
from
[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

I got the same behavior. Apparently something is causing the Jabra to think the laptop is "calling" it and it goes it to phone mode instead of headphone mode.

---

### Post by Permafrost91 on 2007-09-05
rchille, you've certainly made it a lot further than I've gotten with mine then ... what exactly does this ```
Can't connect RFCOMM channel: Connection refused
``` error message mean anyways? I haven't been able to even decipher what this error message is about ... maybe knowing what the problem was would help.

I've also tried kdebluetooth but it can't find my headset.

Thirdly, I've heard that the bluetooth kernel modules have changed in Gutsy ... any ideas what that is all about?

---

### Post by rchille on 2007-09-07
Not sure if this will help but here is post from another forum I saw at:
[http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/](http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/)
> 
If you get the message “Can’t connect RFCOMM channel: Connection refused”, you probably aren’t putting in the passkey (typically “0000&#8243; for headsets). You have to run passkey-agent so that when your bluetooth headset asks for the passkey your computer will understand and give you a method for putting that in. Do it like this:

1. Open a new terminal window
2. type: passkey-agent –default /usr/bin/bluez-pin
3. try clicking “Use as Active Headset” again in gbtsco

This time you should see a window pop up where you can put in the passkey. Hope this works!

-TJ

I'm still trying to figure out why my Jabra BT8010 thinks that xmms is calling it instead of putting into into speaker mode. Anyone have a similar experience?

Rob

---

### Post by rchille on 2007-09-10
Good News!

The lasted round of updates for Gutsy solved my problems with my computer putting my Headphones in the wrong mode! (Happily listening to White Stripes as I type this). 

:guitar:

The quality is a little scratchy so some further work is to be done but I think that will wait. I'll just listen to live recordings for a awhile :)

Try the updates (there was a set on both Fri and Sat that included BT) and Good luck!

---

### Post by Leaf on 2007-09-19
I too was getting the RFCOMM: error when I ran  btsco -v 00:00:00:00:00

I opened /etc/bluetooth/rfcomm.conf and filled in the (commented out) lines.

just paired my motorola h605, whoo!

---

