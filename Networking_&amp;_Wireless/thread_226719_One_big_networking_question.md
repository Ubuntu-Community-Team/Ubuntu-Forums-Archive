---
title: "One big networking question"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by aglc2005 on 2006-07-31
Ok, so this may be a little complicated and I am not totally sure what all I can or cannont do, so I am going to give what I am trying to accomplish and any help would be greatly appreciated.

I have a desktop which I am going to be setting up so that the other five computers in my appartment will have access to for music so we can store the music on this one desktop, and everyone in my appartment will use this for music. It would be nice if I can still use it as my personal computer as well so that I don't have to run my laptop all the time, but that is not a nessecity. Also if possible I would like to have access be read only and the person has to sign into the computer before access is granted. The reason for the read only is so that they don't just dump all of their stuff on the computer and so that anyone that may be over for a visit won't be able to mess it up. The next problem that I am seeing is that the only computers running Linux at all are this desktop and my laptop (both Ubuntu). So how would I set it up so that the other computers running Windows (all XP) will also have access?

Thanks in advance for anyone willing to help me.:D And I think that is all, lol

Edit: Also is there a way to log/view who is logged in for security purposes?

---

### Post by mips on 2006-07-31
Sounds like you are in need of SAMBA. Just do a search here for samba and I'm sure there are guides in the howto section as well.
OR
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Samba website should you want more, [http://www.samba.org/](http://www.samba.org/)

---

### Post by aglc2005 on 2006-07-31
Cool, sounds simpler than what I had thought, thanks for the help

---

### Post by aglc2005 on 2006-08-23
Ok I have my samba set up, I'm having problems with the windows partition though. Here is my code

```

[global]
workgroup = Mshome
netbios name = andrewslaptop
valid users = f******
[homes]
guest ok = no
read only = yes
[Windows_Music]
path = /media/hdc1/Document\ and\ Settings/Andrew/My\ Documents/My\ Music
comment = Windows Music
read only = yes
guest ok = no
[Linux_Music]
path = /home/andrew/Music
comment = Linux Music
read only = yes
guest ok = no

```

The asteristcs are there in the users name for a reason I am sure anyone can guess. Is there anything wrong? My Linux_Music works fine, but the Windows_Music does not.

---

### Post by Ankton on 2006-08-23
check your windows path i think u have forgotten an 's' on the word document ;)

Hope this helps

---

### Post by aglc2005 on 2006-08-25
> **Ankton said:**
> check your windows path i think u have forgotten an 's' on the word document ;)

Hope this helps

Ahh yes I did, lol, I ended up just moving the entire folder to (in windows) C:\Windows_Music. But its funny how I got so mad over this not working and all that the problem was was a stupid s.

I have one more question about this, is there a way to check the status of the share, like the number of people connected, what is being accessed or anything like that?

---

### Post by Ankton on 2006-08-25
you can do it in windows xp by opening - control panel > administrative tools > computer management expand system tools and shared folders, you can figure the rest out from there ;)

---

### Post by aglc2005 on 2006-08-27
> **Ankton said:**
> you can do it in windows xp by opening - control panel > administrative tools > computer management expand system tools and shared folders, you can figure the rest out from there ;)

Ok here is a little confusing puzzle, the windows was working fine (I'm running my samba in Ubuntu just for clarity) and had the other computers set up and connected, then a couple days no one computer that is connected to the samba can find the Windows folder i had het up, but the Linux folder that is set up works fine.

---

