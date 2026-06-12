---
title: "Going mobile with SSH Private keys"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by kd5ftn on 2007-10-17
I have two SSH servers running, each using public/private key DSA authentication. I have password authentication disabled.

Home - Windows Server 2003 - OpenSSH
School - Ubuntu 7.04 - OpenSSH

I can connect to my SSH servers from untrusted windows machines by using PortaPuTTY and keeping my private keyfile on a USB thumbdrive. The setup is similar to [ this tutorial here]("http://ubuntuforums.org/showthread.php?t=383053"). 

However, I'd like to be able to also connect from MacOS X clients. The problem is, I can't just copy my id_dsa file to the thumbdrive and use the -i command, since OpenSSH demands that my keyfile be be private:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/Volumes/NICKS_STUFF/MacPortableApps/SSH-VNC/keyfile/id_dsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.


So, is there anyway that I can SSH into my servers from an untrusted mac host without using password authentication?

---

