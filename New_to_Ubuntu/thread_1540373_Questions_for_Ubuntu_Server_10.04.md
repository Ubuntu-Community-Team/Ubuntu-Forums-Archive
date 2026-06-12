---
title: "Questions for Ubuntu Server 10.04"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Captain Smiley Pants on 2010-07-27
Hey so I'm using this old box as a quick and dirty FTP backup-our-files box for our family. I am going to install an FTP client and assign users and all that fun stuff, but I am using Ubuntu Server in the mean time and I have a quick question:

So, when I install what I want, how can I make sure that the process has started even before I have logged on to the computer? Let's say there is a power failure and someone not so computer literate wants to use the server, all they'd need to do is turn on the computer, wait a minute for it to load everything up, and not have to bother with logging in?

I know that just SCREAMS security issues but I'm very confident in my routers firewall and I'll be adding encryption with the FTP stuff for "just in case".

Thanks!

---

### Post by imbjr on 2010-07-27
> **Captain Smiley Pants said:**
> Hey so I'm using this old box as a quick and dirty FTP backup-our-files box for our family. I am going to install an FTP client and assign users and all that fun stuff, but I am using Ubuntu Server in the mean time and I have a quick question:

So, when I install what I want, how can I make sure that the process has started even before I have logged on to the computer? Let's say there is a power failure and someone not so computer literate wants to use the server, all they'd need to do is turn on the computer, wait a minute for it to load everything up, and not have to bother with logging in?

I know that just SCREAMS security issues but I'm very confident in my routers firewall and I'll be adding encryption with the FTP stuff for "just in case".

Thanks!

Do you even need to assign users? I use NFS on the server and share a directory between the various machines on the network. Anything your family want saving can be merely dropped into the appropriate directory.

To answer you question more directly:the process will be started before anyone can log in - so you are safe.

---

### Post by Captain Smiley Pants on 2010-07-27
Well, I could use NFS, and would be more than willing... But 1: I don't even know how to use it (guess I'll Google it) and 2: they want their own folders and permissions with them, so they can dump their stuff into their folders without other users looking through their stuff and they are not able to look at others.

Can NFS do that?

---

### Post by imbjr on 2010-07-28
> **Captain Smiley Pants said:**
> Well, I could use NFS, and would be more than willing... But 1: I don't even know how to use it (guess I'll Google it) and 2: they want their own folders and permissions with them, so they can dump their stuff into their folders without other users looking through their stuff and they are not able to look at others.

Can NFS do that?

Here's the guide I followed:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Skip to the "NFS Server" section and even then the "Pre-Installation Setup" isn't strictly necessary.

As for permissions, you should be able to tightly control what ppl see. I have a videos directory with my son's videos in it, but under that there's an others subdirectory that only I can go into.

---

