---
title: "Is Samba the best option?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by lud666 on 2008-08-10
I need to share files between an Ubuntu and a Kubuntu box over the network, it seems like Samba would do what I need.  Is it the best option if I don't need windows compatibility?

---

### Post by Baerun on 2008-08-10
I have the same question because I am using Samba right now but was wondering if there is a better alternative. I do want windows compatibility however.

---

### Post by andrewdodsworth on 2008-08-10
I'm very new to Ubuntu but have used SuSE for a long while. There is a very neat way to browse between Linux systems using Konqueror (KDE file manager) - in the location bar type fish://<remotemachinename>. It uses ssh behind the scenes to transfer data so after entering a valid username and password you can browse the remote filesystem as if local. Although Konqueror is KDE you can also  install it in Ubuntu - it instals various KDE core libraries. You obviously have to have sshd running on the remote system for this to work.

For Windows compatability then Samba is the best option. I have a mixed environment so I run my main production server as a Samba PDC and therefore tend to use Samba as a matter of course as most Linux machines have the capability to connect to Samba out of the box.

---

### Post by scorp123 on 2008-08-10
> **andrewdodsworth said:**
>  There is a very neat way to browse between Linux systems using Konqueror (KDE file manager) - in the location bar type fish://<remotemachinename>.  This will not work "out of the box" on Ubuntu because OpenSSH-Server is not installed per default. To make this work you'd have to install it first on the target machine:  ```
sudo apt-get install openssh-server
```

And yes, the method you describe with "fish://" works for KDE. GNOME users would have to use "**ssh://remoteusername@remotemachine**" in Nautilus ... or they could simply use the "**Places > Connect to Server**" menu and then select **SSH** as connection method (in the "Service Type" drop-down list).

In a pure Linux environment there would be no need for Samba then.

---

