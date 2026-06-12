---
title: "How do I add Libre Office to my software sources in Lucid"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Catbells on 2011-05-05
As I don't know what I'm doing, I have my software sources set to only suggest LTS upgrades and am still on Lucid Lynx.  I like the background of Libre Office (developers from OpenOffice and freer licensing) and would like to make the switch.  the Libre Office web site recommends using Ubuntu Software Centre but I can't find the package in Ubuntu Software Centre or in Synaptic Package Manager.  I can't find the source in LibreOffice.org.

Does anyone know what the source for LibreOffice is so that I can add it to System > software sources?

---

### Post by andymorton on 2011-05-05
You can find it here. 

[http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/](http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/)

andy :)

---

### Post by Catbells on 2011-05-05
Thanks for that quick reply Andrew.  It was clear and easy to follow.

Just a shame that either LibreOffice isn't ready for Lucid Lynx or, my machine has something not quite suitable about it.  The output from my terminal is quoted below.  It sounds pretty negative to me.

I've got the repository added which is what I asked originally.

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libreoffice-gnome: Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~lucid1) but it is not going to be installed
                     Depends: libreoffice-gtk but it is not going to be installed
E: Broken packages

---

### Post by el_koraco on 2011-05-05
Run 

```
dpkg --configure -a
```

then ```
sudo apt-get install -f
```

Then try to install again. 

Sometimes you have to repeat this in order to fix everything.

---

### Post by Catbells on 2011-05-05
I don't know how to get superuser privilege (it sounds like it's for someone who knows more about linux than me).  I did once look at going in as Root user, but decided that it was there to protect people like me from damaging their system.
> rosemary@rosemary-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
rosemary@rosemary-laptop:~$ sudo apt-get install -f
[sudo] password for rosemary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnustep-base-common libavahi-compat-libdnssd1 gnustep-base-runtime
  libgnome-device-manager0 gnustep-gui-common libftgl2
  libaccess-bridge-java-jni gnustep-back0.16 libboost-thread1.40.0
  libaccess-bridge-java libgnustep-gui0.16 libtorrent-rasterbar5
  gnustep-back0.16-art libsdl-ttf2.0-0 libmikmod2 libgnustep-base1.19
  gnustep-common gnustep-gpbs libsdl-mixer1.2 gnustep-back-common
  libboost-filesystem1.40.0 libobjc2 gnustep-gui-runtime ca-certificates-java
  libboost-system1.40.0 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
rosemary@rosemary-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by el_koraco on 2011-05-05
Sorry, I missed that one. Run 

```
sudo dpkg --configure -a
```

You get superuser privileges with "sudo".

---

### Post by Catbells on 2011-05-06
Many thanks for all your help El Koraco.

I've tried a few times but I'm still getting unhelpful messages about it depending on various packages such as libreoffice-core and libreoffice-writer that aren't going to be installed.  This happens when I try in Terminal and when I try in Synaptic Package Manager.  It would be nice, if the messages explained why they're not going to be installed but, they don't.

Is it time to put a bug report on LibreOffice in Launchpad?

---

### Post by Paddy Landau on 2011-05-06
I understand that you cannot install Libre Office and Open Office at the same time in Lucid.

I uninstalled Open Office before installing Libre Office, and that worked.

---

### Post by Catbells on 2011-05-06
I hadn't thought of that, Paddy!  Synaptic Package Manager had said that it was going to remove OpenOffice packages but it didn't occur to me to do it myself.  LibreOffice is downloading as I type.  Thank you for your help.

---

