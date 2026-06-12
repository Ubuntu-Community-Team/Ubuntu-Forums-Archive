---
title: "Upgrade Manager+Software Centre Hanging-up"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by robert-drury on 2011-07-17
Dear Ubuntu team,
Both Upgrade Manager and Ubuntu Software Centre both Hang-up forever during initialisation both suspiciously at the 50% marker. (See two attachments included.)
If I recall, I think I went into Upgrade Manager-Settings and browsed about, I not re-call making any particular changes, I was happy to keep to the defaults, or maybe I changed something and changed it back again, or so. I believe the TEMP file/s some how got corrupted '/tmp/tmp1MA6yF'.
In DOS & Windows I would just just go in and delete all temp files in the temp directory and let the programs rewrite their temp files again, but in Linux, Is that the best solution?  - What do you think?
I assume, I go into Terminal, run SUDO to get root access, the delete file command (whatever the command is, check in help, etc) and trash the file "./tmp/tmp1MA6yF" and any other, what I believe to be, offendingly corrupted files.
Maybe, you've got a whole piece on this subject somewhere, maybe I need to read the manual, where ever it may be.
So far, you at Ubuntu Forum have done a FANTABULUS job for me! 
Last time I complained about poor support for NAS boxes, and the next upgrade seemed to have fixed it! Also I like using Shutter to snapshot the screen so that you can see my problem, "one picture tells a thousand words" (With me, you get two pics and two thousand words, nearly!)
 - Thanks a bundle for all! -- Robert.

---

### Post by philinux on 2011-07-17
Hi Robert,

Open a terminal from Apps>Accessories and use these commands.

```
sudo apt-get update && sudo apt-get upgrade
```

Use copy and paste this into the terminal.

Post back any errors.

---

### Post by robert-drury on 2011-07-17
Thaks, phillinux for reply to my probem:[B]Upgrade Manager+Software Centre Hanging-up [Absolute Beginners 17/07/11 at 11:47
[/B] 			
 			 			 		   		 		 		you sugest:  sudo apt-get update && sudo apt-get upgrade
I get error:
robert@Robert-PCi7:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for robert: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
PLEASE HELP ME MORE. My password is my log-in password.

again:
robert@Robert-PCi7:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
robert@Robert-PCi7:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-doc apt-transport-https apt-utils curl gnome-user-guide gstreamer0.10-tools libcurl3
  libcurl3-gnutls libgstreamer0.10-0 libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-impress libreoffice-l10n-common
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math libreoffice-style-human
  libreoffice-writer libvirt0 python-libvirt python-uno qemu-common qemu-kvm software-center
  sun-java6-bin sun-java6-jdk sun-java6-jre thunderbird thunderbird-globalmenu tomboy ttf-opensymbol
  uno-libs3 update-manager update-manager-core ure
44 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 152 MB/159 MB of archives.
After this operation, 12.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
robert@Robert-PCi7:~$
  I abort here in case I am stepping out of tune here.
Tks for all - Robert

---

