---
title: "Samba networking of 2 computers."
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by drews_blunted on 2006-11-14
:KS  I have two computers setup with ubuntu edgy installed on both. The first computer is my desktop, it is hooked up to my 4 port hub that my cable modem connects to. I am only allowed 1 ip from my isp so only 1 computer can be online at a time. The second computer is connected to the hub but is not connected to the internet. The second computer is my mythtv box. What i want to be able to do is download stuff on my desktop then browse share or folders on my mythtv box and send it files from my desktop so i can then watch the media files on the mythtv box. Both the computers have samba installed and i can view my own shares while on the individual computers but i cannot view either of the computers from one another. Im not sure if i have a network setup to do this correctly? they are all connected via the hub. 

Can anyone help me figure out how to share files between 2 computers on linux with samba? 

Thanks in advance :)


8)

---

### Post by dmizer on 2006-11-14
1) if they are both linux, DON'T USE SAMBA.  it's a real hastle to get confgiured, it's slow, and causes other problems because it's a protocol that's been reverse engineered to emulate windows network sharing.  use NFS instead.  the 4th link in my sig.  it's a snap to setup and you'll be far less likely to have problems with it as it's a file sharing protocol designed specifically for linux.

2) not many home internet usrs have more than one ip address (i don't).  this does not mean you can't have both computers online at the same time (i've had at least 5 machines online at once).  you can set one machine up with internet connection sharing a.k.a. ICS (requires two network adapters on one machine), or you can purchase a router and set your network up like so:

modem -> pc with ICS -> hub -> boundless quantities of other computers.
or
modem -> router -> boundless quantities of other computers.

you'll also need to arrange your network in one of the above two configurations in order for your computers to share files.  ICS is more painfull, but cheaper.  routers are more expensive, but painless.

---

### Post by drews_blunted on 2006-11-14
Thanks for your post, this seems like what im looking for. I only have a couple more things to ask. 

How do i mount these shares? 
I am not an expert at networking.

i am at the part of your howto that talks about mounting:

> 
to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files


I tryed replacing mydomain.com with my ip address? is this correct?
Also am i right to assume that this will alow me to set my fstab to automaticaly mount shares or folders etc on a remote computer on the network everytime it starts? If so that sounds great and i would like a little more help in figuring this out. Thanks so much.

Also i am assuming i am suposed to replace /files with whatever share of the computer im trying to connect to? so would i replace it with say /home/mythtv or /media/sata ?? im still a little confused about this mounting. Also i am to assume that i need ntp installed on both machines correct?

---

### Post by dmizer on 2006-11-15
okay ... file sharing 101:

in a file sharing situation there are two computers:
1) a [COLOR="Red"]SERVER[/COLOR] which contains the files you desire to share to other computers.
2) a [COLOR="Red"]CLIENT[/COLOR] which is the computer connecting to the server.

always: CLIENT ---> SERVER
never: SERVER ---> CLIENT

**in a group of networked computers, any computer can be _both_ a server and/or a client at any time, as long as they are configured to be so.**

in the case of linux file sharing servers, you will need to indicate which directory contains the files you wish to have available to other computers on your network.

in the case of linux clients, clients desiring to mount shares from a server need to have a location on the client hard drive where the files can be cashed so they will appear when you need access to them (a similar technique as temporary internet files, which allow frequently visited webpages to load more quickly).

now lets look at a concrete example in a network of two computers: **music** and **videos**.

computer "music": contains music
computer "videos": contains videos

[SIZE="4"]scenario 1[/SIZE]
so now, you're sitting at **music**, but you want to watch a movie located on **videos** in the [COLOR="Blue"]/home/drews_blunted/movies[/COLOR] directory.  why get up and walk across the room to watch the movie on the other computer?

you set up **videos** as an NFS _server_ by installing the necessary NFS server software according to the howto, and then placing /home/drews_blunted/movies in the /etc/exports file like so:
```
[COLOR="Blue"]/home/drews_blunted/movies[/COLOR] 192.168.1.1/24(rw,no_root_squash,async)
```
with this command, you are instructing **videos** that the files located in [COLOR="Blue"]/home/drews_blunted/movies[/COLOR] should be made available to all computers located on the network with ip ranges from 192.168.1.1 - 192.168.1.255, and finally, that this directory should be made available so the client computer can both read and write the files in this directory.

now computer **videos** is set up as a server, and the files in [COLOR="Blue"]/home/drews_blunted/movies[/COLOR] are available for viewing by other computers in the network.

but we're not done, we actually want to watch the movie on computer **music**.  to do that, you need to set up **music** as an NFS client.  now it's necessary to install the NFS client software according to the howto, and then provide a location for the cashed NFS files from **videos** to cashe so we can have access to them on demand.  so we create a directory in [COLOR="Green"]/media[/COLOR] called [COLOR="Green"]/media/from_videos[/COLOR]:
```
sudo mkdir [COLOR="Green"]/media/from_videos[/COLOR]
```
now computer **music** (as a client) can mount computer **videos** (as a server) like so:
```
sudo mount **videos**.ip.address.here:[COLOR="Blue"]/home/drews_blunted/movies[/COLOR] [COLOR="Green"]/media/from_videos[/COLOR]
```
with this command you are telling **music** to look on computer **videos** for files located in the folder [COLOR="Blue"]/home/drews_blunted/movies[/COLOR] (on **videos**) and cashe them locally in the [COLOR="Green"]/media/from_videos[/COLOR] folder.

[SIZE="4"]scenario 2[/SIZE]
later on in the evening, you're sitting at **videos**, but you want to watch an mp3 located on **music** in the [COLOR="Blue"]/home/drews_blunted/mp3[/COLOR] directory.  why get up and walk across the room to listen to the mp3 on the other computer?

so instead, you install NFS server software on **music** and place /home/drews_blunted/mp3 in the /etc/exports file like just like we did in scenario 1:
```
[COLOR="Blue"]/home/drews_blunted/mp3[/COLOR] 192.168.1.1/24(rw,no_root_squash,async)
```

now **music** is set up as a server, and the files in [COLOR="Blue"]/home/drews_blunted/mp3[/COLOR] are available for viewing by other computers in the network.

and just like scnario 1, we actually want to listen to the mp3 on computer **videos**.  so now **videos** has to be set up as an NFS client, and will also require a location to cashe the files from **music**.  so, create a directory in [COLOR="Green"]/media[/COLOR] called [COLOR="Green"]/media/from_music[/COLOR]:
```
sudo mkdir [COLOR="Green"]/media/from_music[/COLOR]
```
finally, computer **videos** (as a client) can mount computer **music** (as a server) like so:
```
sudo mount **music**.ip.address.here:[COLOR="Blue"]/home/drews_blunted/mp3[/COLOR] [COLOR="Green"]/media/from_music[/COLOR]
```

so now, with the above in mind, i hope it should be apparent that: if you want both computers to see files from the other, you will have to set up both computers as both server and client.  furthermore, and perhaps most importantly, i hope that you understand WHY you need both server and client on both machines, as well as gained a little more understanding of how computer file sharing functions.

---

### Post by drews_blunted on 2006-11-18
Alright i think i almost have this im just having some problems with my ip and computer name?

So far i have tryed connecting my client computer to connect to my server, and i have been typing in the following:

sudo mount drew.192.168.1.100:/media/sata /media/sata/drew

/media/sata is the folder on computer 1 i want mounted at locatation /media/sata/drew on computer 2. 

Drew is my username so i think thats what i need for my computer name or user? 

Also i am just trying to connect to the ip ifconfig told me in the console? 

Also now i have the computers networked via a router with a hub built in.

Let me know if im doing this right or what im doing wrong? :-|

---

### Post by dmizer on 2006-11-18
well, if you've configured both server and client correctly, you shouldn't have to worry about a user name.  your server will be filtering according to ip address, so if the computer does not belong to your network, it won't be able to view the share.

so ...
```
sudo mount 192.168.1.100:/media/sata /media/sata/drew
``` 
should do the trick if your server is configured correctly.

---

### Post by drews_blunted on 2006-11-18
Awsome!! Everything is working how it should!

This is a real cool feature i now have. I can setup my mythtv backend and access videos from it using the frontend from anywhere in my house over my wireless network!

Thanks for your help again! you sure wrote me alot of good information!!

---

### Post by dmizer on 2006-11-18
on the client computer, do this:
```
rpcinfo -p 192.168.1.100
```
do you have firestarter installed?

---

### Post by danbuffington on 2006-11-21
I'm trying to set up a *simple* home server to share and backup files onto.

When I try to make the 'shared' folder become shared, I get this error:

files@waddle:~$ ls
Desktop  Examples  files  shared
files@waddle:~$ /shared 192.168.1.1/24(rw,no_root_squash,async)
bash: syntax error near unexpected token `('
files@waddle:~$ 

{looking forward to Feisty Fawn's simplified networking :) }


Any ideas?

---

### Post by dmizer on 2006-11-21
not too sure what you're trying to do there.  you have to put this line:
```
/shared 192.168.1.1/24(rw,no_root_squash,async)
```
in a file.  specifically /etc/exports

please take another very close look at the howto, and if you have more problems please post in the howto thread so others trying to figure it out can find all their answers in that thread rather than having to search the entire forum. 

this IS simplified networking.  you should take a look at the howto's for setting up samba.  ugh.

---

