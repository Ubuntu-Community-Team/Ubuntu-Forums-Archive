---
title: "Samba and Symbolic Links"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by kaptainlange on 2007-02-02
This seems to be a tough nut to crack, I've seen several one post threads on this board about this problem.  I've only found one solution that brings up other problems.  Here is the problem.

When mounting a samba share on Linux, symbolic links are not followed with respect to the original link.  For example, on the server you have the directory, Stuff.  It has a link in it called "more stuff" and it links to /something/else.

If you share Stuff, mount it on another Linux machine, the link in stuff will now point to the location /something/else on the local machine instead of the file on the remote machine.  Windows does not have a problem with this, for some reason the client it uses manages to translate the link to an actual file/folder.

The only solution I have found to this is the "unix extensions = no" line for the server's smb.conf.  This however is not a solution as it ends up mounting everything as root, and and you lose all user/group permissions associated with the current files and file creation.

If anyone has a clue as to how to get around this, it would be much appreciated.

---

### Post by mightyteegar on 2007-02-02
Have you tried setting this config variable in the share "Stuff" in smb.conf? :

```
follow symlinks=yes
```

---

### Post by kaptainlange on 2007-02-03
Indeed I have, not to mention I believe this is default for samba?

For whatever reason, Windows behaves as expected, as well as nautilus when doing something like smb://place/share.  For some reason though mounting produces problems.  I've also tried using cifs and smbfs as the type for the mount command, both produce the problem.

---

### Post by .zb on 2007-10-09
echo "0" > /proc/fs/cifs/LinuxExtensionsEnabled
This should help

---

### Post by t0m on 2007-10-18
I got the exactly the same problem with my feisty-server and a gutsy client. any solution for that?

@.zb
it does work then, but only root can access the mounted samba shares, which is not an option.

---

### Post by kwnet.at on 2007-11-17
u have to use the options uid= and gid= to set the correct owner on your local fs,
and mention the rights of the parent directories...

---

### Post by Isterklister on 2007-11-19
Hello,
can you explain more what you mean kwnet.at?

Thanks

---

### Post by Sciamano on 2007-11-29
I'm having the same problem.
Can someone please explain a step-by-step procedure to mount shares with symlinks correctly?
Thanks

---

### Post by xer0x on 2008-01-05
hey, for a moment...  I thought the trick for this one is to add the line:

wide links = no      ; unfortunately this does not work...


unix extensions = no   ; worked for me.   -- make sure you put it in the global section .. and not in a specific share.

---

### Post by Sciamano on 2008-01-08
This is what worked for me; edit the [global] section of /etc/samba/smb.conf this way (correct or add the missing lines):

```
follow symlinks = yes
wide symlinks = yes
unix extensions = no
```

---

### Post by teeks99 on 2008-01-13
> **Sciamano said:**
> This is what worked for me; edit the [global] section of /etc/samba/smb.conf this way (correct or add the missing lines):

```
follow symlinks = yes
wide symlinks = yes
unix extensions = no
```

Did you apply this on the client machine?

I get an error saying that "wide symlinks" is an unknown parameter when I try to do a mount.  

Others mentioned that the unix extensions let other non root users access the mount, is this the case.  Is there somewhere I could get more info on this?

Thanks,
Tom

---

### Post by Sciamano on 2008-01-13
No, I applied it on the server (the computer which has the directories to be shared with others).
I can't answer your other questions. I just know it works for me...

---

### Post by teeks99 on 2008-01-14
Thanks, I did that for me as well.... it works.

There's a better explanation of the options in the bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/134716](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/134716)

Tom

---

