---
title: "trojan"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by cross1010 on 2009-07-22
i have both windows and kubuntu in my sys .my windows has been infected by trojan . what should i do to remove it . will it affect my kububntu... help

---

### Post by izizzle on 2009-07-22
Antivirus? Try AVG. No, it will not affect your Kubuntu install at all.

---

### Post by lvleph on 2009-07-22
I would suggest ClamAV while running Kubuntu. You can use this to scan for viruses while in Kubuntu. This way you can be more sure that you are catching things.

---

### Post by Elep.Repu on 2009-07-22
Or, copy your files over, reinstall both windows/kubuntu

---

### Post by cross1010 on 2009-07-23
what is clamAV

---

### Post by philcamlin on 2009-07-23
its a virus cleaner

it will remove your windows viruses if the drive is mounted :)

sudo aptitude install clamav clamav-daemon clamav-freshclam
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)
follow this guide

---

### Post by brookie on 2009-07-23
for winxp systems i use spybot search and destroy as well as norton or any other anti virus. reboot into windows safe mode with networking 

(hit f8 key while booting on most machines) and run the scans while in safe mode. some viruses cannot be detected on normal boot but will be detected in safe mode.

make sure and update the antiviirus/spyware databases before scanning. some antivirus progams will not catch what another one will so i used to have to run multiple tools when removing viruses and spyware. 

also, a good idea is to download ccleaner or another reguistry cleaner and clean up the registry after cleaning out the virus. 

good luck and watch what you click on.
brook

---

### Post by Zorael on 2009-07-23
I've gotten excellent detection results using Prevx, but you need a subscription to make it actually *clean* anything. Detection is free.

Regardless, with a setup of Spybot SoD, HiJack This, and AVG or Avast, you should be able to get rid of it. Then you can install Prevx and let it scan your drives, just to be extra sure.

Oh, and NoScript. ;3

---

### Post by Crunchy the Headcrab on 2009-07-23
I've never had a trojan on my own windows system but I've cleaned up many for others.  It's important to keep windows up to date, run an antivirus and use safe web practices (no p**n or gambling, careful with p2p and torrents).

Having said that, I wouldn't know if I had anything on my system now because I've made the switch entirely to Linux and don't scan for viruses/trojans.

---

### Post by Sef on 2009-07-23
> Or, copy your files over, reinstall both windows/kubuntu


Reinstalling Windows would be a last case senario.   As has been pointed out already, no need to reinstall Kubuntu as it will not affect it.

---

### Post by desireangel on 2011-07-15
Hi 
got a question I have Ubuntu Linux and like to install spybot but the new version wont let me any suggestions??? Thanks Rosy

---

### Post by westie457 on 2011-07-15
> **desireangel said:**
> Hi 
got a question I have Ubuntu Linux and like to install spybot but the new version wont let me any suggestions??? Thanks Rosy
Hello and welcome to the Forums.
Here are some links about viruses and how Ubuntu/Linux deal with them (if that is the right terminology).

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Spybot is a Windows program and as such will not run under Linux/Unix operating systems. However it should be installed and run under Wine. This is available from the repositories (an older stable version) or _[here]("http://www.winehq.org/")_ for more up to date versions and information.

---

