---
title: "how to install guest additions in Fedora guest in Virtualbox?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by powel212 on 2009-07-28
Running Fedora 11 64Bit in Virtualbox and was wondering how to install guest additions?

Any help is appreciated.

Powel

---

### Post by ggaaron on 2009-07-28
Run virtual machine, select Devices->Install guest additions, download additions (they will automount in guest). Then run a terminal in guest, go to CD dir, su to root and run ./VBoxLinuxAdditions-x86.run if all went well then restart virtual machine. You'll need some packages in guest - gcc and kernel-devel for example - install script will tell you what you need.

---

### Post by chrisinspace on 2009-07-28
Check out the tutorial here:

[http://fedorasolved.org/Members/realz/VB_Guest_Addition](http://fedorasolved.org/Members/realz/VB_Guest_Addition)

One additional step.  I have found that between steps 3 and 4, you sometimes have to run:

```
m-a prepare
```

---

### Post by powel212 on 2009-07-28
Thanks guys.

running my updates now... will advise when that is done.

Thanks again.

ps. Ubuntu forum is king.

Powel

---

### Post by powel212 on 2009-07-28
> [http://fedorasolved.org/Members/realz/VB_Guest_Addition](http://fedorasolved.org/Members/realz/VB_Guest_Addition)

That worked the magic.

Thanks again guys.

BTW while we're on the subject of Fedora;

What is the native network share folder control application in Fedora. I installed system-config-samba on the fedora guest but it seems to be bypassed. I used system-config-samba to set up one share folder, "~/public" and turned off the firewall but after entering the user name and password for the fedora share I have full access to the entire root folder on the fedora guest. Why?

Any help is appreciated.

Powel

---

### Post by chrisinspace on 2009-07-28
Samba is designed more for sharing files/folders between Linux and Windows machines.  Look into NFS for sharing between 2 Linux installations.

---

