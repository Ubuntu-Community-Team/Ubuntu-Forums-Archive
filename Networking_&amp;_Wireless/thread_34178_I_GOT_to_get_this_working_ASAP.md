---
title: "I GOT to get this working ASAP"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by SuperKev on 2005-05-13
Hi All,

Before you ask, yes, I did do a search but found nothing that told me what I needed or it just didn't make sense to me.

Ok, here's what I need:

I have a windows XP and Ubuntu on a network with a linksys router. What I need, desparately, is to be able to set up printer and file sharing so I can start to use Linux for more than just web and email, and be 'almost' done with windose completely  \\:D/ 

I need some simple instructions in the form of, go to windose and do ABC then go to Ubuntu and do XYZ. I have tried and tried to do this without posting on here about it but I just cannot get it to work, and like I said I need to get this working since the Linux box is set up to be my work station now. I do have samba already installed.

I know you all probably get sick of all us newbies asking these questions so my apologies for my n00bness.

Any help is greatly appreciated.

SK

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=SuperKev]
I have a windows XP and Ubuntu on a network with a linksys router. What I need, desparately, is to be able to set up printer and file sharing so I can start to use Linux for more than just web and email, and be 'almost' done with windose completely  \\:D/.
[/QUOTE]

Hello.

first: read this over

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

second: read this over

[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printer+sharing+windows](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printer+sharing+windows)

third: read this over 

[http://occy.net/printing](http://occy.net/printing)

fourth:

[http://www.ubuntuforums.org/showthread.php?p=161112#post161112](http://www.ubuntuforums.org/showthread.php?p=161112#post161112)

---

### Post by momo66 on 2005-05-13
I probably can help with the network question.  I am also a new user but i now have Linux as my only desktop and networked to a Windows XP machine (my sons PC) and a Powerbook OSX.  

I have both machines mounted to directorys on my linux system.  

Im assuming you can see your other computer on the network.  You need to know the PC name or the IP address of the computer you are trying to access.

this is the command I used to connect to my Powerbook

```
sudo smbmount //Powerbook/Movies /media/powerbook/ -o username=mmccrary
```

the command is smbmout

the second part is the server and share Im trying to mount  //Powerbook/Movies
instead of the server name you could also use the IP address //192.168.1.100/Movies

the third is the directory I want to mount the share to  /media/powerbook/  (I created this directory before using the smbmount command.

the last part is your username and password 

Another example is the command I used to connect to my sons PC

```
sudo smbmount  //masonpc/ /media/masonpc/
```

Didnt have a username or password setup for this one.  Also didnt have a share name so all I needed to use was the server name.  

Let me know if this doesnt work and I will try to help.. I was ready to give up last week myself but now Im glad I didnt.

---

### Post by SuperKev on 2005-05-13
OK,

I don't know how I did it exactly (I think I do) but I got printing to work  \\:D//

BUT... I still can't access files from my XP machine, I tried your example momo but I kept getting 'couldn't resolve mount point' (I'm sure it's just something simple I am just unaware of at the moment)

But one more piece of the puzzle fits now! All I need is access to my windows folders, sound and video and it's a done deal. I almost chucked Linux about a week ago but if I can get these things sorted I'll be a happy linux camper.

Thanks for the help so far

---

### Post by momo66 on 2005-05-17
Sorry its taken so long to respond.  Make sure you include the share name for your drive you are sharing from XP Machine.  I just  named mine C 

so the command should be

```
sudo smbmount //192.168.1.103/c /media/masonpc
``` 

192.168.1.103 is the XP ip address, c is the name of the share


[QUOTE=SuperKev]OK,

I don't know how I did it exactly (I think I do) but I got printing to work  \\:D//

BUT... I still can't access files from my XP machine, I tried your example momo but I kept getting 'couldn't resolve mount point' (I'm sure it's just something simple I am just unaware of at the moment)

But one more piece of the puzzle fits now! All I need is access to my windows folders, sound and video and it's a done deal. I almost chucked Linux about a week ago but if I can get these things sorted I'll be a happy linux camper.

Thanks for the help so far[/QUOTE]

---

