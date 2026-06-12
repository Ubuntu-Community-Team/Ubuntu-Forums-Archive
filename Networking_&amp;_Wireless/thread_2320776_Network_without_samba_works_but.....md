---
title: "Network without samba works but...."
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by Hadden89 on 2016-04-17
I always thought Samba was a prerequisite to access to any windows share (same home LAN).
But everything works well without it. PcManFM ask me credentials, I'll put them and I'm in.
Most of shared folders work fine, some list very few files (when it supposed to be several in there).
I'm on lubuntu 15.10.

First question: why shares works? (for knowledge, I'm happy for this xD)
Second question: why most of files are not listed in some folders?

(p.s.: there's a thread similar to this I did some days ago, but there I had samba installed, so opened a new one)

---

### Post by bab1 on 2016-04-17
> **Hadden89 said:**
> I always thought Samba was a prerequisite to access to any windows share (same home LAN).
But everything works well without it. PcManFM ask me credentials, I'll put them and I'm in.
Most of shared folders work fine, some list very few files (when it supposed to be several in there).
I'm on lubuntu 15.10.

First question: why shares works? (for knowledge, I'm happy for this xD)
Second question: why most of files are not listed in some folders?

(p.s.: there's a thread similar to this I did some days ago, but there I had samba installed, so opened a new one)
Post the output of this terminal command```
pgrep -l mbd
```

---

### Post by Hadden89 on 2016-04-18
no output with command

---

### Post by bab1 on 2016-04-18
> **Hadden89 said:**
> no output with command
You need SMB/CIFS to share files with Windows.  In most cases this means Samba will be involved.  The package is also named samba.  You can show that package with this command```
dpkg -l samba
```...post that output here.

---

### Post by Hadden89 on 2016-04-18
Ok, I've installed samba, and launched the command said before

```
hadden@hadden-box:~$ pgrep -l mbd
23060 smbd
23085 smbd
23150 smbd
23156 nmbd

```

---

### Post by bab1 on 2016-04-18
> **Hadden89 said:**
> Ok, I've installed samba, and launched the command said before

```
hadden@hadden-box:~$ pgrep -l mbd
23060 smbd
23085 smbd
23150 smbd
23156 nmbd

```
Samba is based on client/server architecture.  I think just the Samba client is installed by default.  What we don't know is whether the **cifs-utils ** package was installed.  I'm pretty sure that it is installed now.  You can check with this```
dpkg -l cifs-utils
```

So we have kind of backed into the answer to your questions.  Samba is required, even if it is just the client portion.  You always need the Samba server to "serve" files to clients  Most likely you needed **cifs-utils** to have read and write abilities.

At this point it's up to you to configure these 3 things:
[LIST=1]
[*]Linux and Samba users
[*]The file system that the share data resides on
[*]The Samba share definitions
[*]
[/LIST]

---

### Post by Hadden89 on 2016-04-19
> **bab1 said:**
> whether the **cifs-utils ** package was installed
It wasn't yet. I did it. Should I install also smbclient and winbind? (suggested)

> **bab1 said:**
> Linux and Samba users
So add my user to sambashare group

> **bab1 said:**
> The file system that the share data resides on
It's ntfs, so maybe I need also ntfs3g support?

> **bab1 said:**
> The Samba share definitions
Ok, should I add all the shares (win-server + ubuntu-client) or only the ones which must be shared with windows?

---

### Post by bab1 on 2016-04-19
Hold on here a second.  The original questions have been answered, correct?  

I thought the data being shared is **not** local to the Lubuntu host.  Aren't these shares created on your Windows machine? 

There is no need for smbcient if you are not going to use the command line to access shares.  You do not need winbind at all unless you are using Samba as a Domain Controller (DC).

The other questions are not relevant if you are only using Samba as a client.

---

### Post by Hadden89 on 2016-04-19
> **bab1 said:**
> using Samba as a client.
I think it's the case.
My only and main problem with samba/shares is about missing files (that are present and shared between the systems) in some of the folders I go to.
Eg: in some folder (audio type in this case) where I've 2000+ shared files (win), I only see 3-30 files from lubuntu 15.10); in some other folders (image type) where I've an amount of files similiar, the problem doesn't happen.

---

### Post by bab1 on 2016-04-19
> **Hadden89 said:**
> I think it's the case.
My only and main problem with samba/shares is about missing files (that are present and shared between the systems) in some of the folders I go to.
Eg: in some folder (audio type in this case) where I've 2000+ shared files (win), I only see 3-30 files from lubuntu 15.10); in some other folders (image type) where I've an amount of files similiar, the problem doesn't happen.
I agree.  That should not happen.  In fact I have a shared directory that is only music files and they all show up.  The same for video and picture files.

So maybe this is a Windows problem.  Normally the client software does not interfere with the servers abilities.  The only thing that the client might have that could block the share would be a firewall.  I do not run firewalls on any of my hosts in the local network.  My firewall is an edge device (i.e. the router).  Samba is not blocked at all in my local network. 

Is NetBIOS over TCP (NBT) enabled on the Windows file share server?

---

### Post by Hadden89 on 2016-04-20
I have firewall only on windows server, but all traffic in local network is set as trusted (192.168.1.x ranges) and I don't think the router blocks the ports or the network should fail completely.
The netbios on windows was set on "auto" so I put to "enabled" so I'll see if change somethings.
After samba install, I see lubuntu client from windows network but its shares are not fully functional yet (as not set).
Tried also to share full C: (system drive) and does the same (missing files)
Sharing full D: (not system disk) works.
On windows (which is quite strange) the attributes of music folder had some hidden/system.
Removed with cmd.exe in administrator mode in the folder
```
attrib -r -s -h +i /s /d
```
However nothing changed.

---

