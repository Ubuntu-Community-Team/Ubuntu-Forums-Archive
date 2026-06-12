---
title: "SFTP access without limitations"
date: 2020-06-18
forum: Networking &amp; Wireless
---

### Post by itsshowtime on 2020-06-18
Hi guys,

I am tasked with configuring a server for SFTP and rsync access, sounds easy enough... Right?...

The rsync runs over SSH, just like SFTP does. I configured the Ubuntu server (in fully offline environment) for SSH access and rsync and then proceeded by adding the following config that you can retrieve in 99% of the SFTP Ubuntu tutorials:
```

[COLOR=#000000][FONT=Consolas]Match group [/FONT][/COLOR][COLOR=#1990B8][FONT=Consolas]sftp
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]ChrootDirectory /home
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp[/FONT][/COLOR]

```

This basically does what it says it does and pay attention to the fact that we are limiting the SSH access to the /home directory and limiting the only SSH based access to SFTP. This works like a charm for SFTP access to the specific directory. It does however limit all SSH access to the specified directory only and to make matters worse it limits all SSH access to the use of SFTP commands only.

Obviously rsync will not be allowed using this configuration and even without the ForceCommand you can still not properly use rsync as it requires access to different directories that are not present in any user's home folder.

So, that's not an issue, let's remove the ForceCommand and ChrootDirectory and continue. Oh wait, SFTP doesn't work anymore?? Okay let's look up other tutorials/guides that explain how to configure Ubtunu for SFTP access, and pick out one that doesn't use the ForceCommand or ChrootDirectory config changes. Oh wait, there are none such guides??

Okay guys, either I am stupid and missing something here? Or There is really no way to configure SFTP and any other type of SSH based access to the same server? Let's hope this is me being stupid.

Any help on this would be very appreciated!


Cheers :popcorn:

---

### Post by TheFu on 2020-06-18
ssh and sftp are enabled by default before you changed anything, at least they always have been on 16.04 and earlier.

The **Match** stanza goes from that point to the next **Match** or the end of the file. Let me test something .... 

```
Subsystem       sftp    /usr/lib/openssh/sftp-server
Match User thefu-test
   ChrootDirectory /home
   X11Forwarding no
   AllowTcpForwarding no
   ForceCommand internal-sftp

```

So, the error I see when trying ssh thefu-test@regulus is:
```
/bin/bash: No such file or directory
```
That's because the ChrootDirectory doesn't have /bin/ access which is necessary for a login where bash is the default shell. Some setup is required. [https://www.tecmint.com/restrict-ssh-user-to-directory-using-chrooted-jail/](https://www.tecmint.com/restrict-ssh-user-to-directory-using-chrooted-jail/) has steps.

For sftp, it is easier to setup because their is an internal-sftp server available: [https://www.tecmint.com/restrict-sftp-user-home-directories-using-chroot/](https://www.tecmint.com/restrict-sftp-user-home-directories-using-chroot/)

The code above has to go at the end of the sshd_config file.  I've tested it using a 20.04 desktop as the server and a 16.04 client.

---

