---
title: "[Feisty Fawn] NO CARRIER for Smartlink modems (Toshiba Satellite M100 laptop)"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by lowbat on 2007-04-27
Hi all,

I've recently installed Feisty Fawn (release 7.04) on my Toshiba Satellite m100 laptop and so far had an almost flawless setup experience. The majority of devices on this laptop worked perfectly out of the box (Intel 3945 wireless a/b/g, Realtek chipset soundcard). The only annoying thing that occured after installation was the default ATI drivers that wont boot the system into X (had to resort to vesa drivers using "dpkg-reconfigure xserver-xorg"). Eventually I managed to install the proprietary ATI drivers (xorg-driver-fglrx) and upon reboot was greeted with feisty's pretty Gnome UI :).

So here is my progress so far with Feisty:
> Intel 3945 wireless a/b/g --> worked out of the box (played very nice with network manager)
> Realtek chipset soundcard --> worked out of the box
> Bluetooth --> detected by Feisty but havent checked it out yet
> SD card reader --> from Texas Instruments, heard that it works quite well under Feisty
> ATI Mobility Radeon X1300 --> didnt work out of the box (see earlier part of the post)
> Toshiba 120 GB SATA HDD --> works rather well. The HDD makes a horrible clicking sound everytime I shutdown the system; apparently the SATA HDD spin down bug is still apparent in Feisty :( (it started back in Edgy). I managed to find a workaround for this issue at launchpad.
> Fingerprint recognition module --> detected by Feisty, but I have no idea how to test it...
> Suspend/hibernate and resume --> worked flawlessly out of the box. This really made me a happy Ubuntu laptop user! :)
> Toshiba software modem --> Somewhat working. THIS is my main issue :confused:...

So now everything seems to be going quite well for Feisty on the Satellite M100, except for the Smartlink modem. In my experience the modem worked flawlessly both under Dapper and Edgy. I was able to dial-in to my ISP and establish a connection without any hitch using wvdial. This is basically what I did to get the modem working under Feisty (I did the same steps as in Dapper & Edgy):
1. installed the sl-modem-daemon package (sudo apt-get install sl-modem-daemon)
2. edited /etc/default/sl-modem-daemon with the following:
SLMODEMD_DEVICE=hw:0,6 #got the device ID from "aplay -l"
SLMODEMD_COUNTRY=INDONESIA #Where I'm from :)
3. ran "sudo /etc/init.d/sl-modem-daemon restart" to reload the Smartlink module into the kernel
4. ran "sudo wvdialconf". wvdial successfully detected the modem and initialized the proper configuration (I checked the resulting wvdial.conf under Feisty; its the same as in Dapper & Edgy)
5. added my ISP details to wvdial.conf
6. ran "wvdial myISP" (did the same in Dapper & Edgy)

... and voila, I get a constant stream of error messages indicating NO CARRIER! Even reloading the Smartlink module (sudo /etc/init.d/sl-modem-daemon restart) wont get rid of the error... Rebooting Feisty does not fix it either. I get the NO CARRIER error everytime I try to dial-in to my ISP! This issue has never occured to me under Dapper nor Edgy using the same laptop :(. I'm now even considering donwngrading Ubuntu back to Dapper just to get my internet connection back...Can anyone confirm this Smartlink modem issue under Feisty? Better yet a solution? :)

Cheers,

lowbat

---

### Post by netboy541 on 2007-04-29
i'm getting this same problem on my Toshiba A45-S120 laptop.

Modem looks good, takes AT commands, and as soon as I try to use an ATDT command, it immediately comes back with a NO CARRIER, instantly making the software think something is wrong...

I'm looking into it, but I really have no idea where to start......

Worked like a champ under edgy tho. :(

UPDATE:

It appears I get this error when I put my laptop in suspend or hibernate.
I restarted, and it worked like a champ.

Refer to this:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/39259](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/39259)

---

### Post by handaxe on 2007-05-20
Try  this: in /etc/default/sl-modem-daemon change "SLMODEMD_DEVICE=hw:0"  to "SLMODEMD_DEVICE=modem:0" .

HA

---

### Post by mulvila on 2007-06-02
I was having this problem yeasterday with my lap-top when I tried to use the modem first time after shifting to Feisty. This morning I reinstalled sl-modem  package from synaptic and now the modem worked well.

My /etc/default/sl-modem-daemon file is like this:
```
SLMODEMD_DEVICE=auto
SLMODEMD_COUNTRY=USA
FORCESTART=0

```
I live Finland, though. Hope this helps (reinstall sl-modem package or changing the DEVICE to auto).

---

