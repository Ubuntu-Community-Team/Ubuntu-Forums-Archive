---
title: "Is it possible to configure Ubuntu as workstation client in Windows domain network?"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by CroEragon on 2007-02-02
In my school there is course called "Creative Computing". In first session teacher asked us "What you wanna do in this class?" Since teacher is not programmer or something like that, we were left with choice of Front Page and Powerpoint unless someone suggest something else. I suggested "Introduction to Linux and Open source" and we agreed about it. Since we are getting some new computers, some of old ones would go to that and we would install Linux. Only problem is that i dont know if you can configure Ubuntu to work with Windows Server domain network(that' what we got in school) as workstation in same or similar way as XP does.

So, does anyone know is it possible to configure ubuntu to acts as worksrtation in same manner as XP do, that means restricting some things as Terminal and doing centralized control, same as in Windows. If not possible to mix Linux with Windows, then can we set up small server for linux that would do same. i know i'm ascking impossible, but there is small hope it is possible. 

Hope dies last!:D

---

### Post by Palmstroem on 2007-02-02
In the Linux world the package of choice to communicate to Windows computers is called **Samba**. Just install Ubuntu, then install smbclient if it does not already come with the default installation, and you should be able to connect to your other Windows PCs.

The other way round i.e., making the Linux box control all the Windows PCs, is also possible with the Samba package. If you want this, you can install the whole Samba suite, configure the smb.conf file (that is the hardest part!) and be happy...

Enjoy!

---

### Post by koenn on 2007-02-02
No. 
re Palmstroem : samba provides access to Windows shares, i.e. shared directories. The Linux pc's would be able to access shared folders on Windows systems, but would not be part of the "domain". Samba (server) in turn can act as an NT4 style domain controller, but that is in no way comparable to a Windows 2k or later Adctive Directory Domain. 

I don't think tou can join linux desktyop machines to an (Active Directory) Domain. Even so, they can't be retricted by Group Policy Objects (eg compulsary computer and network configuration, limited access to command promt, etc ... ) because although these policies are created on the server, they need the Windows registry to be implemented on the 'client' computers. There's no Windows Registry on a linux computer. 

There are some alternatives to Microsoft's Active Directory - 
For a quick introduction, you could read this :
[http://users.pandora.be/mydotcom/howto/linux/migration03.htm](http://users.pandora.be/mydotcom/howto/linux/migration03.htm)

---

### Post by irongeek on 2007-02-05
Well, you can make a Linux box authenticate against Active Directory via kerberos and winbind. It's easier to do in OpenSUSE than in Ubuntu. Heres some info on doing it in Ubuntu:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

