---
title: "Can't connect my bluetooth headset anymore"
date: 2017-10-18
forum: Networking &amp; Wireless
---

### Post by Dread Knight on 2017-10-18
I've upgraded from 17.04 to 17.10 recently and I can't connect my bluetooth headset anymore, although pairing works. I did unpaired the device and tried again, but no luck.
Tested this in Gnome-Shell and KDE, no luck in either desktop environment.
Any suggestions on how to debug / fix this would be appreciated.

---

### Post by dino99 on 2017-10-18
first step: use info on the net
[https://duckduckgo.com/?q=ubuntu+bluetooth&t=canonical&ia=qa](https://duckduckgo.com/?q=ubuntu+bluetooth&t=canonical&ia=qa)

---

### Post by JGJones on 2017-10-18
Having the same issue but with my mouse - a Logitech MX Master. The laptop is an HP Spectre 13 and everything on this works well on 17.04.

Upgraded to 17.10 today. Logitech MX Master no longer connects and it is extremely difficult to get this to sync. I've managed via turning bluetooth on and off multiple times to get the mouse to connect and it works for about 5 seconds. It state it is still connected, but the mouse stop working.

As for the rfkill command:

```
$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
59: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Nothing is blocked

To confirm that my MX Master mouse is actually paired:

```

$ bluetoothctl 
[NEW] Controller 00:C2:C6:DA:9F:02 spectre [default]
[NEW] Device D7:61:62:DC:77:7E MX Master
Agent registered
[bluetooth]# devices 
Device D7:61:62:DC:77:7E MX Master
[bluetooth]# paired-devices 
Device D7:61:62:DC:77:7E MX Master

```

Flawlessly on 17.04
"Broken" on 17.10 - I'm a bit stuck on what else to look at to debug this. I'll have a look in the system logs and see if anything shows there.

---

### Post by dino99 on 2017-10-18
Maybe use gtkorphan & bleachbit (as root) to clean the system; then reboot and check journalctl about warning/error

---

### Post by JGJones on 2017-10-18
After looking a bit, I see there's the hci* tools (ie hcidump) which I have used.

After getting my MX Master mouse to finally connect and it is working, I am able to use the mouse - however as mentioned, this last only a coupla of seconds.

This is the output of hcidump from when I was moving the mouse to when it stopped working at the end:

```

> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xe0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xd0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xe0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xb0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xe0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xa0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xd0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xe0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x01 0xd0 0xff 0x00 0x00 
> ACL data: handle 3585 flags 0x02 dlen 14
    ATT: Handle notify (0x1b)
      handle 0x0031
      value 0x00 0x00 0x00 0xa0 0xff 0x00 0x00 

<< at this point - mouse stop working >>

> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
< HCI Command: LE Set Scan Enable (0x08|0x000c) plen 2
    value 0x00 (scanning disabled)
    filter duplicates 0x00 (disabled)
> HCI Event: Command Complete (0x0e) plen 4
    LE Set Scan Enable (0x08|0x000c) ncmd 1
    status 0x0c
    Error: Command Disallowed
< HCI Command: LE Set Scan Enable (0x08|0x000c) plen 2
    value 0x00 (scanning disabled)
    filter duplicates 0x00 (disabled)
> HCI Event: Command Complete (0x0e) plen 4
    LE Set Scan Enable (0x08|0x000c) ncmd 1
    status 0x0c
    Error: Command Disallowed
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189
> HCI Event: Vendor (0xff) plen 7
> HCI Event: Vendor (0xff) plen 189

```

I can't see anything to signify why it might have stopped working. I can confirm that it is not a fault with my mouse as I have a Dell Precision laptop running Ubuntu 16.04 LTS and the mouse is able to work flawlessly with that.

---

### Post by JGJones on 2017-10-18
I don't use gtkorphan/bleachbit (I do keep the system as clean as possible and I did reset my Gnome desktop after upgrading to 17.10).

Nothing in journalctl nor in syslog etc. 

This is frustrating as I can see the mouse working for a few seconds before it'll randomly stop and there's nothing to suggest why. It will say it is still connected. I turned off the mouse and the system say it is still connected.

---

### Post by Dread Knight on 2017-10-18
> **dino99 said:**
> first step: use info on the net
[https://duckduckgo.com/?q=ubuntu+bluetooth&t=canonical&ia=qa](https://duckduckgo.com/?q=ubuntu+bluetooth&t=canonical&ia=qa)

It's saying it's not blocked.

> **dino99 said:**
> Maybe use gtkorphan & bleachbit (as root) to clean the system; then reboot and check journalctl about warning/error

Just tried bleachbit as root, did a clean. Can't even find gtkorphan, oh well.

Device kinda connects at times, device itself doesn't say that, but it shows as connected on my PC, though it's not listed in the audio devices, so I can't play anything through my headset.
Also when selecting the bluetooth headset from the bt devices list, the "Connection On/Off" button is kinda problematic, not working at all at times, hmm...

---

### Post by wildmanne39 on 2017-10-20
Moved to Networking and wireless since 17.10 has been released!

---

### Post by Dread Knight on 2017-10-23
Bump, still can't use my bluetooth headset...

---

### Post by jeremy31 on 2017-11-15
What model headset as I can use my Sony headset in Ubuntu 17.10 although I do need to use a modified pyhton script from github to get it to use A2DP rather than HSP/HFP audio

---

### Post by Dread Knight on 2017-11-15
> **jeremy31 said:**
> What model headset as I can use my Sony headset in Ubuntu 17.10 although I do need to use a modified pyhton script from github to get it to use A2DP rather than HSP/HFP audio

Yeah, I've read about cases like that, mostly because of the mic if I recall right...
The headset model is Bluedio T2+

---

