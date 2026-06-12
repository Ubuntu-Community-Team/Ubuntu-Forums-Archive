---
title: "Unable to mount location message"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by loren41 on 2010-08-02
I am trying to make contact with my Windows 7 Professional network from a Unbuntu 10.04 laptop.  When I select Places/Network/Windows Network, I receive the following message:
[INDENT]Unable to mount location
Failed to retrieve share list from server[/INDENT]

Scanning the Forum, I see that many people have had similar problems, but I've found none of the responses helpful.

I need more knowledge, like:

[INDENT]What appl sent this message?
Who has failed to retrieve the list?
The share list is located on the server, is that my Windows PC?
What would make the retrieval fail?[/INDENT]

---

### Post by damianv on 2010-08-02
I am having the same problem. The connection used to work great between the 10.04 laptop and Windows 7 Desktop. The error mentioned in your post just started happening within the last week. It occurs after I click on the Windows Network icon.

---

### Post by JustinR on 2010-08-02
Its a gnome samba/nautilus problem and has supposedly been 'fixed'. Try manually mounting the samba share with:

Applications > Accessories > Terminal
```

sudo mount //COMPUTER_NAME/SHARE_NAME /mnt

```

You can replace /mnt with something else such as /media/ExternalHDD.

---

### Post by damianv on 2010-08-02
I'm not sure if i'm using this command correctly but I just want a mount for the entire device. Not the particular directory within that device. This is how it went...


rolfsmeier@Yoshi:~$ sudo mount //steelrose /steelrose
Mounting the DFS root for a particular server not implemented yet
No ip address specified and hostname not found

---

### Post by johnnytm on 2010-09-18
If you know the ip address of the machine you are trying to mount you can use places--> connect to server --> when it opens use the drop down arrow to select windows share, then type the ip address into the server line. if u have a username and password for the windows machine you will be prompted to enter it. This is the only way I could find a way to access my windows desktop from my Ubuntu laptop. Hope that helps.

---

### Post by prj44 on 2011-11-06
I am at wits' end trying to get my Ubuntu 11.04 to talk to my PC workgroup.  (It used to work...not any more!)

Sometime, I get access, but most times, not.  This is where the fury begins!

When others on the workgroup see the Ubuntu, they are refused access...the ID and PW are rejected.  I have tried an incredible range of things suggested by others on this site, all without any positive resolution.  

I can even get the Windows machine to share files with a Mac for XXDEsake!  But not Ubuntu, any longer.

Am I looking at a full fresh install of U?  Are there error logs I should be checking to try to understand why this is being blocked?

Any suggestions most welcome.  This is unbelievably frustrating...and I am red
uced to a sneaker net.

---

### Post by sandyd on 2011-11-07
Are you using homegroups btw?

If you have homegroups enabled, its not gunna work.

---

### Post by prj44 on 2011-11-08
No Homegroup, just old-fashioned Workgroup.

---

### Post by audiomick on 2011-11-08
You may find some help here

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Morbius1 on 2011-11-08
I'm confused by your post:
> Sometime, I get access, but most times, not.  This is where the fury begins!

When others on the workgroup see the Ubuntu, they are refused  access...the ID and PW are rejected.  I have tried an incredible range  of things suggested by others on this site, all without any positive  resolution.  


Does this have anything to do with the "Unable to mount location" error. That error is usually a Linux permissions error on the server not a Samba issue.

Why not post the output of each of the following commands so people here can asses how you are set up:
```
testparm -s
net usershare info --long
smbtree
hostname
```

---

