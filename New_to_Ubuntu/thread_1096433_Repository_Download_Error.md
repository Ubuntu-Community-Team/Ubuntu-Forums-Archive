---
title: "Repository Download Error"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Chessa on 2009-03-14
Ok, I keep getting an error message when I open Update Manager "Could not download all repository indexes".  Here are the issues it's highlighting:

```
GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz  404 Not Found

Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/hardy/http://ppa.launchpad.net/banshee-team/ppa/ubuntu/binary-i386/Packages.gz  404 Not Found

Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Help?  I've tried searching for similar situations, but I'm really really new and having a hard time understanding similar solutions/situations and how they relate to this.  I'm happy to use the Terminal if you can tell me exactly what to type (and a short explanation of what it's doing, so I can figure it out next time) - I'm really new, like I said.

I've tried removing Firestarter, thinking maybe it was blocking some of them, but I still get the error.  I've also tried switching software servers, and it's happened at three different servers. so that doesn't appear to be the issue either.  Oh, and it's been happening for 8 days, if that's important.

Thanks in advance.

---

### Post by taurus on 2009-03-14
1.  Go into System -> Administration -> Software Sources and remove the check mark for the CDROM.

2.  You need GPG key for ppa.launchpad.net.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding) a PPA to your Ubuntu repositories

---

### Post by Chessa on 2009-03-15
> **taurus said:**
> 1.  Go into System -> Administration -> Software Sources and remove the check mark for the CDROM.

2.  You need GPG key for ppa.launchpad.net.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding) a PPA to your Ubuntu repositories

Thanks, taurus.  Ok, so I unchecked the cd-rom.  I also got the banshee ppa and medibuntu key to work.  However, I can't get this message to go away.  I don't understand - is there a generic key for Ubuntu Hardy I'm supposed to have?  Or for launchpad?  I've searched and searched, but I'm just lost as to where to find this particular key.  Here's the message:

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
```

When I check my authentication tab in Software Sources, I see that I have a key for Ubuntu Archive Automatic Signing Key and one for Ubuntu CD Image Automatic Signing Key - both are from 2004.  Are these out of date, or...I just can't figure it out.  I'm trying, I swear! ;)

---

### Post by Chessa on 2009-03-15
Ok, nevermind, I figured it out, YAY!

I used the directions from this thread [http://ubuntuforums.org/showthread.php?t=1046158]("http://ubuntuforums.org/showthread.php?t=1046158"), post #4 in particular. I just subbed the last 8 digits of the error key for the 8 digits listed in that post, and now no more errors. 

Hooray!

---

