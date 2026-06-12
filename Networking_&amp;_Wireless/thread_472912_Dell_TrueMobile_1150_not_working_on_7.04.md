---
title: "Dell TrueMobile 1150 not working on 7.04"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by rjmarshall on 2007-06-13
I had put another post in the Dell forum, but I'm not getting any response there...

I have a Dell TrueMobile 1150 which works fine under XP.  I installed Ubuntu 7.04 from the livecd and the card worked until I did an update (2.6.20.15 to 2.6.20.16).  So I thought that I would try with the older kernel, but that didn't work.  I even tried reinstalling and I still can't get it to work.

When I do an lshw I see:

lshw -C network
   *-network
            description: TrueMobile 1150 Series PC Card
            product: Version 01.01
            vendor: Dell
            physical id:0
            slot: Socket 1

I don't see it when I do an lspci, but when I do lspcmcia I get:

Socket 1 Device 0:     [-- no driver --]        (bus ID: 1.0)

iwconfig says "lo   no wireless extensions"

I did update the firmware on the 1150 from 6.10 to 8.72, but that didn't help.

If I eject the card, and re-insert it, I see:

pccard: PCMCIA card inserted into slot 1
pcmcia: registering new device pcmcia1.0
hermes @ 00010100: Card removed while waiting for command 0x0021 completion.

But none of the lights come on and NetworkManager still says no network connection.

Is there a way to install and use the XP driver (since it seems to work fine)?

Thanks,

Rob

---

### Post by chili555 on 2007-06-13
Please let us see the output of these terminal commands with the card inserted:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```Thanks.

---

### Post by rjmarshall on 2007-06-13
Hi,

Here's the output...

```

root@rob-laptop:/# lsmod | egrep '(orinoco|hostap|prism2)'
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

But the odd thing is...I tried to install XP on the laptop again, just as a test, but then realized that I only have the XP update CD.  So I rebooted the system and now the interface works like a champ.  I really don't get it...I guess it's just quantum mechanics at work again :)

Thanks,

Rob

---

### Post by chili555 on 2007-06-13
Glad it's working! What we were getting at here is that sometimes too many modules get loaded and it is necessary to blacklist prism2_cs. Looks like it is not an issue here.

---

### Post by rjmarshall on 2007-06-16
Well, I installed the updates yesterday and rebooted, and the network card quit working again.  So I tried a couple of things that didn't help.  Then I decided, as a test, to boot the Windows XP update disk again.  It complained, as expected, that I wasn't updating an existing Windows system and then rebooted.  

Again, when the laptop came up after booting off the XP update, the network card starting working.

At this point I have to assume that something in a register somewhere (some status bit, or something) is not getting cleared/set when doing a reboot with Ubuntu.  But that XP does clear it properly.  Does this sound familiar to anyone?

Thanks,

Rob

---

### Post by rjmarshall on 2007-06-21
Whenever I reboot or shut the laptop off and restart it, lose the wireless connection.  In the kern.log I see:

```
un 20 14:49:39 rob-laptop kernel: [  122.227237] hermes @ 00010100: BAP0 offset timeout: reg=0x8000 id=0xfd0b offset=0x0
Jun 20 14:49:39 rob-laptop kernel: [  122.227333] eth0: Cannot read hardware identity: error -110
Jun 20 14:49:39 rob-laptop kernel: [  122.227395] eth0: Incompatible firmware, aborting
Jun 20 14:49:39 rob-laptop kernel: [  122.227520] orinoco_cs: register_netdev() failed
```

But if I then boot windows for a minute (from the update CD), and reboot, it works fine.

Any ideas?  I really hate having to reboot with XP to get the wireless working.

Thanks,

Rob

---

### Post by timetrap on 2007-10-09
Brand new to the forum . . . But I managed to "modify" the 6.16 Oronico Gold Firmware (an 1150 is a rebranded Gold card) to work on the Dell Truemobile 1150, I just used it on my card so far no problems.

 I thought that if I flashed by own card up to the latest verision 8.74 I would be doing a good thing . . . yeah right . . . anything more than 6.16 will break the monitoring mode of the card. So kismet stopped working for me. GRRR . . . .and since I used a "hacked" firmware to get me to the 8.74 upgrade I was out of luck.

So I decided to "hack" my own firmware from the 6.16 installer.

If you are a little leary about using a hacked firmware on a PCMCIA WLAN card, have no fear.  Here is what I did.

1. Opened the .exe file in a hex editor
2. Overwrote part of a decriptor that limits what cards it will install to
3. Saved
4. Installed

No big deal.

I did NOT touch any of the code that contains the binary portion of the firmware (feel free to run a diff)

One caveat, it is an .exe file so you will have to boot into windows one more time ;-)

So for all of the googlebots out there here is a list of keywords:

DELL Truemobile 1150 firmware downgrade 6.16

Enjoy!

---

