---
title: "[SOLVED] Audio drops on streaming mp3 from smb share to wireless"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by sebbouckaert on 2008-08-05
Hi,

At home we have an old P III 500 MHz, 384 MB RAM, acting as a file and print server, running Kubuntu 6.10 with smb server. It mainly hosts our music and photo collection.

On our other home computers these smb shares are mounted permanently by adding this line to /etc/fstab ```
//192.168.1.120/gedeeld    /media/atlas/gedeeld smbfs  credentials=/root/.smbcredentials,noatime,nobrl,umask=000,uid=1000,gid=1000  0    0

```

Everything is connected by a Linksys DSL modem/router.

Problem acts up when we try to play music on one of the wireless computers. During playback of mp3's, the system hangs for a few seconds, after which it resumes. Tried all sorts of players (Rhythmbox, Banshee, Exaile...) and this happens with normal 128 kbps mp"'s.

I first noticed this on our desktop downstairs, which is connected with an USB wireless Interface (WUSB54G), but lately I found that my Asus eee 900 suffers the same. Weird thing is that under windows XP there is no problem at all.

Is it possible to fine tune smb.conf somehow, or does it have something to do with the wireless drivers in Ubuntu? Can't seem to find much about this on the internet, except for [this old thread]("http://ubuntuforums.org/showthread.php?t=304545").

---

### Post by dmizer on 2008-08-06
For shares between Linux computers, use NFS instead of samba.  NFS is much faster, will cause far fewer issues during transfer, and it's native to Linux.

The howto for configuring NFS on both the server and client is located in my sig.

---

### Post by sebbouckaert on 2008-08-06
Thanks for the tip. I'll look into that very soon when I find the time. 

I guess I'll have to convince my family (and myself) to stop having one leg in Windows and another in Ubuntu, since all our machines are dual boots...Hardest thing will be to tell my wife to "forget about iTunes" lol. 
I guess it's not possible to access a NFS share under Windows?

---

### Post by sebbouckaert on 2008-08-06
Another thought: would it be possible to keep the existing smb configuration and sort of "overlay" the existing shares with NFS? Thus improving access under Ubuntu, but keeping it possible to browse the local network under Windows?

---

### Post by dmizer on 2008-08-06
> **sebbouckaert said:**
> Another thought: would it be possible to keep the existing smb configuration and sort of "overlay" the existing shares with NFS? Thus improving access under Ubuntu, but keeping it possible to browse the local network under Windows?

This would be an ideal solution.  Yes you can do this.

---

### Post by sebbouckaert on 2008-08-07
> **dmizer said:**
> This would be an ideal solution.  Yes you can do this.

So what you say is that I can set up my server to simultaneously share the same shares 

```

```//server/shared //server/user1 //server/user2```

``` both as smb and nfs? No compatibility issues

That would be great.

---

### Post by dmizer on 2008-08-07
I've done it before.  The only issue I ran into was file permissions.

Alternatively, you could try this: [http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by sebbouckaert on 2008-08-08
Great. I'll try to set up the NFS first, and see what will happen then. Hope I don't get too much hassle with the permissions 'cause I'm a total noob on that :confused:
I'll let you know how it works out in a short while.

---

### Post by sebbouckaert on 2008-08-11
Hi,

Due to some other things it took a while but I got it sorted: Our file serving PC was still running on Edgy 6.10 and because I didn't want to go through the hassle of configuring my smb shares all over again I had to do a dist upgrade 3 times (Feisty – Gutsy – Hardy) in order to get things up to date.

Once that was done (took all weekend on that old machine) I used your How To to to set up a NFS share, next to the existing smb shares, and that went quite smooth. Had a small issue with permissions though, so I chmodded 777. That's probably not the most subtle way to solve things, but as I said I'm a permission-noob, and this way we can all read and write the share on our home network.

Once the NFS was mounted, I immediately noticed the speed difference, and best of all: we can now stream music from the server on our wireless connection without any trouble whatsoever!

---

### Post by dmizer on 2008-08-11
That's fantastic. I'm glad to hear you got things working satisfactorily.

Please use the "Thread tools" menu to mark this thread as solved so other people know there is a solution here.  Thank you!

---

