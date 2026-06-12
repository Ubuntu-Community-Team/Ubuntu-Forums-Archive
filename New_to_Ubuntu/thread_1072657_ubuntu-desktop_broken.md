---
title: "ubuntu-desktop broken?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-02-17
Per:

Skype at the

Ubuntu Documentation > Community Documentation > Skype 
[https://help.ubuntu.com/community/Skype#Message:%20%22Problem%20with%20...%22](https://help.ubuntu.com/community/Skype#Message:%20%22Problem%20with%20...%22)

I read to kill pulseaudio

I tried this, but received a package BROKEN error:

ubuntu-desktop

how do I determine which error and how to correct it?


mark@Lexington-19:~$ killall pulseaudio
mark@Lexington-19:~$ sudo aptitude remove pulseaudio
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are [B]BROKEN:
  ubuntu-desktop [/B]

---

### Post by uberg on 2009-02-17
i can't remember how to that from apt-get offhand but try running Synaptic (gksu synaptic or from the System/Administration menu).  Under edit in the Synaptic program there is a fix broken package button.  Give that a try.
Joe

---

### Post by whoop on 2009-02-17
ubuntu-desktop is a metapackage and pulsaudio is a dependency. So I really wonder how you could fix that.

---

### Post by Mark_in_Hollywood on 2009-02-17
Yikes:

mark@Lexington-19:~$ killall pulseaudio
pulseaudio: no process killed
mark@Lexington-19:~$ sudo aptitude remove pulseaudio
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  pulseaudio 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1339kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: pulseaudio but it is not installable
The following actions will resolve these dependencies:
[B]
Remove the following packages:
ubuntu-desktop[/B]

Leave the following dependencies unresolved:
libpulsecore5 recommends pulseaudio
Score is -81

---

### Post by LowSky on 2009-02-17
ubuntu-desktop being broken shouldn't be a big deal, infact it breaks easily and the system really doesn't normally mind. 
Ubuntu-desktop is only a meta-package, basiclaly a place holder. That package points to other packages, namley everything gnome related and installed onto an Ubuntu machine from default. It will break if you remove any part of its normal setup, like Fire-fox or pulseaudio

---

### Post by uberg on 2009-02-17
i notice on the instruction page that it says to install esound after uninstalling pulseaudio.  Have you done that? Sounds like that this is the replacement for pulseaudio.  Maybe that fixes the problem?

---

### Post by Mark_in_Hollywood on 2009-02-17
> **uberg said:**
> i notice on the instruction page that it says to install esound after uninstalling pulseaudio.  Have you done that? Sounds like that this is the replacement for pulseaudio.  Maybe that fixes the problem?

I haven't been able to SAFELY remove pulseaudio, as I keep receiving a BROKEN error about: gnome-desktop.

I've read where this can seriously hurt the OS. I must avoid that.

---

### Post by dzark on 2009-02-17
As Whoop mentioned earlier, ubuntu-desktop is a 'Meta-package'. It is not actually a program, a file, or anything except a link to a whole lot of packages. So by installing the package 'ubuntu-desktop' you end up installing a whole bunch of other stuff, including printing, screensavers, wireless tools, and among them - 'PulseAudio'.  By removing one of the 'sub-packages' it is no-long complete and breaks. Big deal? Not at all.

If you want to see what the subpackages (dependencies) of ubuntu-desktop are, type 
```

sudo aptitude show ubuntu-desktop
``` into a terminal.

---

### Post by Mark_in_Hollywood on 2009-02-17
OK, but look what it said at the bottom:

mark@Lexington-19:~$ sudo aptitude show ubuntu-desktop
[sudo] password for mark: 
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.124
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 53.2k
Depends: acpi, acpi-support, acpid, alacarte, alsa-base, alsa-utils, anacron,[I removed the names of 1001 packages]

Description: The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system 
 
**It is also used to help ensure proper upgrades, so it is recommended that it not be removed.**

If I believe what you say that removing it is not a BIGGIE, then why am I warned not to? This isn't rhetorical, I'm happy to let aptitude remove it, but I must not hurt the OS in so doing. Thanks.

---

### Post by dzark on 2009-02-17
Due to most of us being volunteers, and the incredible variations of software possible in ubuntu, to ensure the highest possible chance of a successfull distribution upgrade...

Over many years on many boxes, I've only seen it only once, and that was a while ago, where a distribution upgrade failed, and was fixable by installing ubuntu-desktop. I guess with so many packages, a dependency here or there may get missed, and this reduces the chance a little..

Dont use a cellphone while driving, dont smoke, etc ;)

---

### Post by Mark_in_Hollywood on 2009-02-17
As I said at the top I was doing this to fix Skype. I think I said that.

This resolved the problem:

Howto solve all PulseAudio-related issues in Ubuntu
[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)


Thank you, community, for your support.

I miss marking posts as: SOLVED.

---

