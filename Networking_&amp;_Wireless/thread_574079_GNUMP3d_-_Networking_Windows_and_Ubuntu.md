---
title: "GNUMP3d - Networking Windows and Ubuntu"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by mapleshade on 2007-10-12
I have a laptop running Ubuntu Server 7.04 LAMP CLI.  I have GNUMP3d and Samba installed.  I want to dedicate this laptop to GNUMP3d, but my music files are on my Windows machine.  The files are located in K:\music, the computer's name is HTPC and it's static IP is 192.168.1.3.  The computers are on the same network and I can ping the Windows machine from the laptop, but I don't know how to set GNUMP3d's music directory to the directory on the Windows machine.  I'm guessing it'd be something like root = //HTPC/"something"?

---

### Post by chenel on 2007-12-14
I'm not sure if gnump3d is able to handle Samba addresses, but if it does you would have to
(1) Have the files of the music shared (with no password requirements) to the local network on the windows computer.  You will need to know what the name of the share is (see #2)
(2) You would need to use root = smb://HTPC/*share name*/

If this doesn't work you could also try smb://192.168.1.3/*share name*/ (I've had lots of trouble trying to get samba to recognize windows hostnames in the past).

Hope this helps.


> **mapleshade said:**
> I have a laptop running Ubuntu Server 7.04 LAMP CLI.  I have GNUMP3d and Samba installed.  I want to dedicate this laptop to GNUMP3d, but my music files are on my Windows machine.  The files are located in K:\music, the computer's name is HTPC and it's static IP is 192.168.1.3.  The computers are on the same network and I can ping the Windows machine from the laptop, but I don't know how to set GNUMP3d's music directory to the directory on the Windows machine.  I'm guessing it'd be something like root = //HTPC/"something"?

---

### Post by chenel on 2007-12-14
Just stumbled across this thread - [http://ubuntuforums.org/showthread.php?t=340900](http://ubuntuforums.org/showthread.php?t=340900) - I think this will solve your problem.

cheers.

---

