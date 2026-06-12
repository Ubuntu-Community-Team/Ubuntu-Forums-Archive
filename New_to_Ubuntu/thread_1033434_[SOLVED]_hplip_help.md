---
title: "[SOLVED] hplip help"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by hellomoto on 2009-01-07
Heya im trying to install my HP printer (which has been working via hplip b4 i reinstalled my OS) but i get the following error durring early installation.

```

Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
\error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
error: Command failed. Re-try #1...

```

I have checked to see if the CD-ROM source is enabled but all it says is on the GUI: "To install from a CDROM insert a disk into the drive." how do I disable it?

I have had no trouble using apt-get to install software on this machine up untill now.

---

### Post by Titan8990 on 2009-01-07
Post the contents of /etc/apt/sources.list

---

### Post by kestrel1 on 2009-01-07
What version of Ubuntu are you using?
In 8.04 go to system - administration - software sources & check under the Third Party Software tab

---

### Post by hellomoto on 2009-01-07
Here is my sources list:

```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free

```

I am using 8.04

---

### Post by Irony on 2009-01-07
You are not making much sense. If Ubuntu 8.04 is installed you don't need the cd - thus your list can look like this;

```
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free
```

You could uncomment the backports if you want to see more programs. Note hit the reload button to update everything.

Check the model of your printer and check which hplip version it needs;

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

or just compile the latest source;

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

If the ubuntu repositories have the correct hplip drivers then just install from there from synaptic.

---

### Post by hellomoto on 2009-01-07
I have never had to compile hplip from source to get my printer working. 

When i run sudo apt-get update... i now get the following error:

```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://gb.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

any ideas? Will this effect hplip installing correctly?

---

### Post by Irony on 2009-01-07
Is your internet connection working, i.e. can you browse websites?

---

### Post by kestrel1 on 2009-01-07
He's on here so I would guess the Internet is working, unless he has another machine.

---

### Post by Titan8990 on 2009-01-07
Comment out your first line to remove the CD from your sources list:

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

needs to be:

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

---

### Post by hellomoto on 2009-01-07
my internet is working but I am using wvdial through a PPP connection and not through network manager. 

I have uncommented the CDROM option but it doesn't help with hplip.

When I run apt-get now i get the following error:

```

W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

---

### Post by hellomoto on 2009-01-07
Result! :P

To fix the update problem I had to search for a better mirror. I did this via synaptic. 

I also uncommented CDROM in my repository list... 

Ran hplip -- sorted. 

Many thanks for all your help everyone. :)

---

### Post by Captain_tux on 2009-01-07
This solution worked perfectly for me without the need to compile anything. Just a little attention to detail as you're installing and everything should be fine:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Here's the thread the link came from: 

[http://ubuntuforums.org/showthread.php?t=813149&highlight=5180](http://ubuntuforums.org/showthread.php?t=813149&highlight=5180)

---

### Post by Irony on 2009-01-07
I mentioned compiling only if he needed the latest hplip (my printer requires 2.8.7 which is not in 8.04 repositories).

Tux, the link you supplied to the hplip site is actually to an automatic compiler.

---

### Post by Captain_tux on 2009-01-07
> **Irony said:**
> I mentioned compiling only if he needed the latest hplip (my printer requires 2.8.7 which is not in 8.04 repositories).

Tux, the link you supplied to the hplip site is actually to an automatic compiler.

Yes... which worked beautifully for both my laptop and desktop.

---

