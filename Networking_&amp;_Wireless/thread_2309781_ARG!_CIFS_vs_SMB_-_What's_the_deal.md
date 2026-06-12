---
title: "ARG! CIFS vs SMB - What's the deal?"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by jeremiahlange on 2016-01-13
Ok, so I run windows 10 and have an Ubuntu VM running on it for my dev environment. My project files are on the Windows 10 machine, so I setup a CIFS share and auto-mount it to access them and run my dev environment from my Ubuntu VM. It's very convenient, except for one issue. Latency. I can copy large files over the cifs share at very good transfer rates, but latency per file is not good, which causes a problem when there are 100's of small project files that need to be loaded up. Even just straight copying all these small files from the CIFS share to the local vm takes forever (But I can tranfer a multi-gigabyte file extremely quickly. I did some digging around and found that newer versions of SMB, like 2 and 3, are much more efficient and CIFS is based off of SMB v1. However when I try to apt-get install smbfs, I get a message that reads something along the lines of SMBFS is obsolete, use cifs-utils. I'm really scratching my head here. How do I mount a SMB share using a higher version?

---

### Post by Morbius1 on 2016-01-13
I'm kind of lost here on the description of the problem.

If you are mounting a Windows share using cifs ( from cifs-utils ) and want to change the default version of SMB that's being used you need to add the "vers" parameter:

From man mount.cifs:
> vers=
           SMB protocol version. Allowed values are:

           ·   1.0 - The classic CIFS/SMBv1 protocol. This is the default.

           ·   2.0 - The SMBv2.002 protocol. This was initially introduced in Windows Vista Service Pack 1, and Windows Server
               2008. Note that the initial release version of Windows Vista spoke a slightly different dialect (2.000) that is not
               supported.

           ·   2.1 - The SMBv2.1 protocol that was introduced in Microsoft Windows 7 and Windows Server 2008R2.

           ·   3.0 - The SMBv3.0 protocol that was introduced in Microsoft Windows 8 and Windows Server 2012.

           Note too that while this option governs the protocol version used, not all features of each version are available.

I guess the biggest thing that confuses me is if the Ubuntu machine is a VM guest  ( and I'm assuming here that you mean VirtualBox ) on a Win10 host why are you not using VBox's shared folder mechanism.

---

### Post by jeremiahlange on 2016-01-13
Sorry, for the confusion. One problem I have is that I don't understand is why I see all this articles saying "don't call it CIFS, CIFS is ancient history, it's SMB....". If CIFS is based off of an old version of SMB, why when I try to install SMBFS am I getting a message that it is obsolete and to use CIFS??
I was able to get smb v 3 working (i think) using the vers option. Interestingly, this was not in the man pages of multiple online sources including this one: [http://manpages.ubuntu.com/manpages/jaunty/man8/mount.cifs.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/mount.cifs.8.html)
Enabling smb 3 seems to have made a significant difference in copying tons of small files, but doesnt seem to help my dev environment performance much. This is puzzling

Regarding my VM, its a guest using VMWare Player, which does have a feature to share a directory from the Host. Unfortunately, there is an issue with long file paths (greater than 255 char i believe). Even though windows supports greater than 255 char path (or whatever the number is), it doesnt work, I found one source that mentioned old API's dont work with the larger file paths, so perhaps this is a vmware programming oversight. Do you know if VirtualBox has the same issue? I'd give it a shot. Although I'm a little skeptical, I've used virtualbox years ago on mac and it was a little buggy and slow.

---

### Post by Morbius1 on 2016-01-13
As for the man pages don't rely on web sources. Open a terminal and type:
```
man mount.cifs
```
You will get the man pages relevant to whatever version of Ubuntu you are using at the moment.

In regards to the long file paths and VBox I don't know. I'm a rather hierarchical user and have subfolders upon subfolders ( to what I thought was an insane level ) but I don't think I've ever reached anything near a 255 character limit.

As for CIFS vs SMB and smbfs, the irony here is that smbfs was actually a much older system and what replaced it was CIFS which brought with it the ability to use SMB2 and SMB3.

---

### Post by bab1 on 2016-01-13
> **jeremiahlange said:**
> Sorry, for the confusion. One problem I have is that I don't understand is why I see all this articles saying "don't call it CIFS, CIFS is ancient history, it's SMB....". If CIFS is based off of an old version of SMB, why when I try to install SMBFS am I getting a message that it is obsolete and to use CIFS??

I was able to get smb v 3 working (i think) using the vers option. Interestingly, this was not in the man pages of multiple online sources including this one: [http://manpages.ubuntu.com/manpages/jaunty/man8/mount.cifs.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/mount.cifs.8.html)

FWIW; context is everything.  The names CIFS and SMB are applied to many things.  The term CIFS was originally used by Microsoft when it first updated the SMB(1) protocol.  Later on they moved back to using the term SMB.  None of this means anything when you are referring to the Ubuntu "packages" you are installing.  

The terms smbfs and cifs-utils are Ubuntu package names, not protocol names.  The package smbfs was used for earlier versions of Ubuntu.  Later versions of Ubuntu use the package cifs-utils.  The package is updated with the latest versions of the Microsoft protocol.  The package also includes the SMB/CIFS utilities.  This also includes the man pages that @ Morbius1 referred to.  

The web based man page you linked to is for is for the 2009 version of Ubuntu and is in the earlier smbfs package  I use Ubuntu 14.04 LTS and the URL for that man page shows the vers option.  See [**here**]("http://manpages.ubuntu.com/manpages/trusty/man8/mount.cifs.8.html").

---

### Post by jeremiahlange on 2016-01-14
Thanks for the clarity! I should know by now to only trust the MAN pages from the terminal (I've only been using Linux on and off for 15 years...)
As much as performance is improved with SMB 3.0, it's really disappoint that running the webserver off the cifs share is so stinking slow. GET ... is like 6000ms (compared to 24000+ ms with smb 1.0), :(

---

