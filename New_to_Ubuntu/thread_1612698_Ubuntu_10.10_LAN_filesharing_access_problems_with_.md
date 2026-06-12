---
title: "Ubuntu 10.10 LAN filesharing access problems with Vista and NAS"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by noodleking on 2010-11-03
Hi,
I'm a Linux/Ubuntu novice and I'm trying to get to grips with file/folder sharing on a LAN, between Ubuntu, Vista, XP and a NAS.

Before installing Samba, I had access to the NAS and the folders I was sharing on the Vista (but it showed nothing about "Workgroup"). I wanted to share files from the Ubuntu, so I installed Samba and Ubuntu magically discovered my NAS and windows shares on the "WORKGROUP" and their shares that I had access to before. I entered the username-password for the accounts I'd set-up for such access and everything was working fine. Then, I logged out of Ubuntu, booted into Vista, used the same shares and server, did some work on Vista and closed the system down.

The following day, I booted into Ubuntu and could no longer access any of the shares on the NAS or the other Vista on the LAN (neither the ones under WORKGROUP, nor the other ones). Nothing was available under network at all. And WORKGROUP was empty. Even so, the other Vista could access my Apache webserver on Ubuntu, but it could no longer access the public folder I'd set-up on Ubuntu.

Eventually I had to reboot the Vista and the NAS so that Ubuntu rediscovered the folders on both system.

What I'm wondering about is 1) why did Ubuntu lose the shares? 2) is there anyway of permanently mounting the shares so that programmes within Ubuntu (including Terminal) can navigate to it within their own file-browsing systems 3) Why do I have "WORKGROUP" shares (which I presume is my Ubuntu logging into that domain) as well as the regular shares I had before 4) what is the best way to set-up a robust File-server on Ubuntu, either with my current Ubuntu Desktop Edition or with Ubuntu Server Edition.

btw. I'm using Ubuntu Maverick, I upgraded from 10.4, rather than doing a clean reinstall (I have not had any other problems with it).

---

### Post by bioterror on 2010-11-03
/etc/samba/smb.conf does have this value

```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```

Replace that WORKGROUP with your desired workgroup name and then do ```
sudo service smbd restart
```

Sometimes I cant neither see shares, but I hammer refresh few times and I can once again see the shares.

Mystical thing that is.

---

### Post by HaggisSupper on 2010-11-22
I ran into very similar problems when trying to connect Ubuntu 10.10 netbook edition to a share on a NAS.

The solution was to change the name resolution order as described at [http://ubuntuforums.org/showthread.php?t=1082148&page=9](http://ubuntuforums.org/showthread.php?t=1082148&page=9)

This worked for me. Can't help you with your other requests i'm afraid.

---

