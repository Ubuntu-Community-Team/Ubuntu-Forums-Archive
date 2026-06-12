---
title: "Sharing Hell (Samba)"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by rahulthewall3000 on 2008-05-13
So, here goes. I had sincerely hoped that this issue would be fixed with Hardy and therefore today I installed hardy, just to see whether this works or not. In the process, I removed my gentoo installation in the hope that the only issue that I had with Ubuntu would be removed. And that was sharing. I don't understand this but sharing my external hard drive has never been possible with Ubuntu. So, here is the smb.conf file that I use with gentoo (it worked there). I would be glad if someone could tell me what is the problem here. And the external hard drive is fat32.

```

[global]
    server string = samba @ wall
    security = SHARE
    domain master = yes
    preferred master = yes
    encrypt passwords = false
    obey pam restrictions = yes
    passdb backend = tdbsam
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
    hosts allow = 10.100. 10.50. 127.
    syslog = 0
    max log size = 1000
    dns proxy = no
    invalid users = root
    admin users = rahul
    write list = rahul


[Music]
    comment = Music Collection
    path = /media/WALL/Music/
    guest ok = yes

[Movies]
    comment = Movie Collection
    path = /media/WALL/Movies
    guest ok = yes

[Videos]
    comment = Videos and Series
    path = /media/WALL/Videos
    guest ok = yes

```

So when I go to smb://wall I see the three folders that I have shared. but when I try to open them, it tells me:
```

Unable to mount Location
Failed to mount Windows share

```

---

### Post by Iowan on 2008-05-13
I haven't crossed over to Hardy yet, so I speak from Gutsy (actually, my Samba server is running Breezy...)
I presume your external hard drive is mounted as /media/WALL?

---

### Post by rahulthewall3000 on 2008-05-14
Dude, wall is my computer name, hence smb://wall while WALL is the name of my hard drive.

---

### Post by swells5 on 2008-05-19
exact same problem.
I did manage to get my documents folder working so that I had access from other ubuntu 8.04 desktop by R clicking the folder in nautilus and choosing sharing options and checking the first two choices - share this folder and allow others to write in this folder. From my other desktop when I open documents - it asks for my password and opens and allows me full read write access. When I log in as another user, it asks for the password and without my password - it will not open. So far so good. But, my music and photos folder are as you say "Unable to mount location - failed to mount windows share".

---

### Post by rahulthewall3000 on 2008-05-28
I am back to gentoo, I see no reason to use Ubuntu if sharing does not work.

---

### Post by Iowan on 2008-05-28
@rahulthewall3000
Sharing works - although it IS more of a challenge on Hardy. Use what works for you...

@swells5
Check the permissions on your music and photos folder. Is Samba denying access to you or your other user (or both)? Posting your **/etc/samba/smb.config** might help.

---

### Post by rahulthewall3000 on 2008-05-29
> **Iowan said:**
> @rahulthewall3000
Sharing works - although it IS more of a challenge on Hardy. Use what works for you...


Sorry, but have to disagree. I have never been able to share my external hard drive using Ubuntu - starting right from the days of edgy. As for the challenge, I enjoy challenges, and have made a lot of efforts to make sharing work but all in vain. 
So, when I say sharing does not work - I mean it. (I mean no offense here, just stating my point of view :) )

Cheers
Rahul

---

