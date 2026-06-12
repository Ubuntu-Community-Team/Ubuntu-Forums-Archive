---
title: "Setting up Sitecom WL-012 with wlan-ng?"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by filipebrandao_ on 2007-03-17
This is my problem...
After a long unsucessful time trying to instal linux-wlan-ng and all the dependeces needed , i realized that that app comes on the cd in a deb package with all the dependeces...so I installed linux-wlan-ng deb . Now my problem is to configure it for my usb adapter (Sitecom WL-012)!!Can someone help me please?

If I installed it manually , i know that i should write:
./Configure   on the console and tap y or n accordingly to my needings.

Thanks in advance and sorry if I mispelled something ;-)

---

### Post by filipebrandao_ on 2007-03-18
I've been following [this tutorial]("http://ubuntuforums.org/showthread.php?t=121393") and a good progress has been done.

Now my problem is :
In the final step of the tutorial, when i have to write on the console:
ifup wlan0

this is what happens:
SEE CaptureEcra.png on the attachments

I also tried to reset using:
modprobe prism2_usb prism2_doreset=1
and a similiar error apeared! SEE CapturaEcra-1.png on the attachments.

Help me please!

---

### Post by filipebrandao_ on 2007-03-18
i have done a thing that i forgot , and now the error is a little different.

Here is what i've done that is on the 6th step of the tutorial:

> All of these issues are cured by creating a file /etc/wlan/shared.prism2 with the following contents:

#!/bin/bash
prism2_fwload ()
{
/bin/true
}

prism2_mibset ()
{
/bin/true
}

I'll refresh this post right after i get a screenshot of the error! be right back :)

EDIT:

Screenshot uploaded!!!Check out CapturaEcra-2.png on the attachments!

---

### Post by tormod on 2007-03-19
You'll need to replace the udev rule in /etc/udev/rules.d/ and the wlan-udev.sh in /etc/wlan/ with the attachments from [https://launchpad.net/bugs/29706](https://launchpad.net/bugs/29706).

If firmware loading is not working for you, it would be helpful if you "confirm" this bug, and if the patches make it work, report that as well.

---

### Post by filipebrandao_ on 2007-03-19
> **tormod said:**
> You'll need to replace the udev rule in /etc/udev/rules.d/ and the wlan-udev.sh in /etc/wlan/ with the attachments from [https://launchpad.net/bugs/29706](https://launchpad.net/bugs/29706).

If firmware loading is not working for you, it would be helpful if you "confirm" this bug, and if the patches make it work, report that as well.
First of all, thanks for helping me :)

I did that and it continues the same:

> 
root@ubuntu-desktop:~# ifup wlan0

[: 84: -f: unexpected operator
: not foundlan.conf: 85: 
: not foundhared.prism2: 3: {
: not foundhared.prism2: 4: /bin/true
: not foundhared.prism2: 5: }
: not foundhared.prism2: 6: 
: not foundhared.prism2: 8: {
: not foundhared.prism2: 9: /bin/true
: not foundhared.prism2: 10: }
.: 17: Can't open /etc/init.d/functions
Failed to bring up wlan0.

root@ubuntu-desktop:~# modprobe prism2_usb prism2_doreset=1

WARNING: Error inserting p80211 (/lib/modules/2.6.17-10-generic/linux-wlan-ng/p80211.ko): Invalid module format

---

