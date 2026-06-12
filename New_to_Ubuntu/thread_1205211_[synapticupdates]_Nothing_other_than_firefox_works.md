---
title: "[synaptic/updates] Nothing other than firefox works"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by GumboLinux on 2009-07-05
im using ubuntu 7.10. I just installed it on this computer and I went to install wine and it never could reload the list of applications. I then tried to use terminal with ```
sudo apt-get install wine
``` it returned no results or recommendations. I cannot use the update manager either. I can go to websites using firefox and have a wired connection which obviously works. here is the lspci result because I know it often helps to be prepared > mikey@mikey-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
mikey@mikey-desktop:~$ 

:mad:

---

### Post by taurus on 2009-07-05
7.10 has expired and no longer supported.  Why don't you install something a little newer like version 9.04?

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by GumboLinux on 2009-07-05
Im trying to but I cant update it and I cant burn a new version to a disk without a burning program which I cannot get without updating package lists -.-

---

### Post by taurus on 2009-07-05
There is already a burning app on your machine, Applications -> Sound & Video -> Brasero Disc Burner.  Otherwise, you can burn the ISO file from nautilus.

---

### Post by austinpsycho on 2009-07-05
i believe *sudo apt-get dist-upgrade* will upgrade your distrobution.. i dont know if it will go from 7 to 9 but its worth a shot

---

### Post by CatKiller on 2009-07-06
> **GumboLinux said:**
> im using ubuntu 7.10. I just installed it on this computer

Since you've just installed it, you won't lose anything by installing a newer version. That would be my recommendation. As has already been mentioned, there is a cd burning application already installed. You should be able to just right-click on the .iso file and select "burn to disk."

Otherwise, since Gutsy is no longer supported, its repositories have been moved to a different server. You can change your existing install to look for updates on the new server by changing your sources.list.

```
sudo nano /etc/apt/sources.list
```(Ctrl-O to save, Ctrl-X to exit)

Change whatever mirror location you have in there to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) and then run ```
sudo apt-get update
``` to refresh the list of available packages from the new server.

Another option is to dist-upgrade to Hardy, which is still supported. Open up your sources.list but instead of changing the mirror location, change each instance of gutsy to hardy. Then run

```
sudo apt-get update
sudo apt-get dist-upgrade
```This will pull in all of the new packages to upgrade you to 8.04 LTS. This will take a while.

---

