---
title: "NIS problem"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by smcilroy01 on 2007-08-20
I've been been using NIS on a small home network (3 machines, 4 users) running Suse.
Wanting to try the Ubuntu experience I loaded Kubuntu 7.04 x86_64 on one of the NIS clients, dual booting with Suse 10.2. I don't use DHCP, the computers have static IP addresses.  Now the problem is that I can't login using an NIS login, only as a local user.

The NIS user list appears on the login screen and also in various utilities eg as permitted users for file-sharing. 

*ypcat passwd* and *sudo ypcat shadow.byname* show the NIS users as expected

If I'm logged in as the local user, I can *su * to any of the NIS users, but if I then try to *sudo* or* su*, the password isn't recognised.

All of the above lead me to believe that the problem is with the password authentication rather than NIS but at this point I'm out of my depth.
If I go back to Suse, everything works as before. Could there be some incompaability between the NIS server on Suse and the client on Kubuntu? I thought that NIS and NFS would be distro agnostic.

Can anyone tell me what the problem is and hopefully how to fix it?

Apologies if this should have been in Absolute Beginners

---

### Post by mrpeenut24 on 2007-09-05
I'm in the same boat.  We're running an OpenBSD server with the NIS server and authentication works fine on Suse, but when I try to authenticate on Ubuntu, it fails.  ```
ypcat passwd
``` shows all of the users, so I know the files are loaded, I just can't authenticate.  I followed the howto here: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) but now I'm stuck trying to authenticate.  Any ideas?

Thanks!

---

### Post by mrpeenut24 on 2007-09-10
I believe I found what it was.  SuSE has libpam-unix2 (or similar) pre-installed but ubuntu doesn't.  This package allows Ubuntu to authenticate against a passwd file using blowfish.  After I installed this file, I was able to use Ubuntu on an NIS server hosted on OpenBSD.

---

