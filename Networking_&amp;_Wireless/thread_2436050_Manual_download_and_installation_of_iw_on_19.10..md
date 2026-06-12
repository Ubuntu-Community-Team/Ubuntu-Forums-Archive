---
title: "Manual download and installation of iw on 19.10."
date: 2020-01-30
forum: Networking &amp; Wireless
---

### Post by yetimon_64 on 2020-01-30
My situation is I have just successfully installed an Ubuntu Eoan 19.10 server image onto an SD card and booted it up on a raspberry pi 4. I have no worries with the actual installation but DON'T have any access to internet via ethernet. My 2 options are usb tethering (which is failing miserably due to the android phone defaulting to file transfer during the boot process of the pi) and a WPA2 wireless hotspot on the android phone.

I can easily connect to a wpa2 wireless hotspot from the CLI, which I have done many many times, but am missing the package "iw" in this installation. This is the only block to me getting the pi online and getting a DE installed.

Normally I'd go to the ubuntu packages site and go to one of the mirrors listed however no mirrors are listed and a notice to use a package manager is posted there instead [[COLOR=#0000FF]--the ubuntu package download page for iw_5.3-1_arm64.deb--[/COLOR]]("https://packages.ubuntu.com/eoan/arm64/iw/download") (link)

I have managed to get a debian download of that file but am a bit reluctant to use it, I would prefer to use the ubuntu archives for this but it seems to be blocked for some unknown (to me) reasons.

Does anyone know where I could source a deb file from the ubuntu eoan repositories for "iw_5.3-1_arm64.deb"?
Also I'd be interested to find out why the ubuntu packages site no longer shows download mirrors for getting such packages like they used to.

TIA, yeti.

**Edit: update:** I managed to get the android phone to default to tethering but still didn't work, no network still.
                    Some good news; the downloaded debian "iw" package has exactly the same md5 hash as listed on the ubuntu     packages site so I'll give it a go.

---

### Post by yetimon_64 on 2020-01-30
Marking as solved.

The debian package for iw, with the same md5 hash as the ubuntu packages site, worked fine. I simply wrote the debian installer package to the micro sd card, plugged the micro sd into the pi and booted. Then used "sudo dpkg -i iw_5.3-1_arm64.deb" to install it. Then proceeded to connect to the wpa2 wireless hot spot as I usually do from the console. Network was working and the system could be updated. So my issue for this thread is solved.

Still interested to find out ...
> ... why the ubuntu packages site no longer  shows download mirrors for getting such packages like they used to.
... if anyone has information on this.

Finally: I didn't end up getting a working DE as yet, will have to troubleshoot some more and if necessary open another question thread later. Yeti.

---

### Post by deadflowr on 2020-01-30
> ... why the ubuntu packages site no longer shows download mirrors for getting such packages like they used to.
Arm packages are in the ports repository. (ports.ubuntu.com)
The default archives (archive.ubuntu.com) only holds amd64 and i386 packages.
[s]I do not know if there are any mirrors for the ports repository.[/s]
scratch that, I did find [this thread]("https://askubuntu.com/questions/428698/are-there-alternative-repositories-to-ports-ubuntu-com-for-arm") and the listed mirror still exists:
[https://launchpad.net/ubuntu/+mirror/ftp.tu-chemnitz.de-archive]("https://launchpad.net/ubuntu/+mirror/ftp.tu-chemnitz.de-archive")

Though I'm not sure why no show for any of those archives in the mirror listing page.
I don't see any armXX  packages with mirrors, though all the amd64 and i386 versions do.

---

### Post by yetimon_64 on 2020-01-30
Ah yes "arm64", it makes sense the main two, amd64 and i386, are on the mirrors. I suppose the most used would need the mirrors in use. I was actually thinking of amd64 that I'd seen on the mirrors in the past not arm64, my mistake there. Thanks deadflowr.

---

