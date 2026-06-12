---
title: "Update problem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by andjen on 2009-03-22
I'm a very new user just getting to grips with Ubuntu.

You know the symbol at the top of the screen that appears from time to time to tell you that new updates are available? Well, mine now appears as a grey exclamation mark and when I hover over it I get the message that there is a network problem (although everything seems fine) and the instruction to click on the icon and then click 'Check' when the Update box appears.

Whenever I do this it downloads 80 of 81 files and then comes up with the following error message:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24CFailed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Anyone know how can I resolve this problem?

Andjen

---

### Post by drs305 on 2009-03-22
You can prevent the CD-ROM error by unticking it in Synaptic: Settings, Repositories, Ubuntu Software. It's in the bottom section most likely and is searched for any time you do an update if it is ticked. If it isn't listed there or for other CD's, look under the "Third Party" tab for the CD reference and untick it.

As for the other message, Launchpad has started adding security keys. Run this command to add the key to your system:
```

gpg --keyserver keyserver.ubuntu.com --recv C5E6A5ED249AD24C     
gpg --export --armor C5E6A5ED249AD24C | sudo apt-key add -
sudo apt-get update

```

---

### Post by BGFG on 2009-03-22
Try System>>Administration>>Software Sources, On the first page in the bottom area, is the cd rom checked ? If so, un-check it and try to update again.

edit:late post :) drs305 has you covered

---

### Post by andjen on 2009-03-23
My thanks to you both.

That seems to have solved it!

---

