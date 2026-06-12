---
title: "Can't get my home server to work without chmod 777"
date: 2024-01-21
forum: Networking &amp; Wireless
---

### Post by phobos84 on 2024-01-21
Hello everyone.  I did a search and didn't find an answer that quite matched my situation so I figured I would just make a thread and ask.

So I built a computer with Ubuntu 22.04.3 LTS.  I have three hard drives in this computer.  A small M2 that has the OS installed and two WD Red 4tb internal drives.  These drives are used for a small family server.  One of them is for movies and basic public sharing.  The other is full of private data for each user for things like tax documents and phone pictures.  None of the primary SSD is shared.  Well to do this I have been reading the Samba.org manual.  Specifically chapter six.  This is the one I'm talking about [https://www.samba.org/samba/docs/using_samba/ch06.html](https://www.samba.org/samba/docs/using_samba/ch06.html).

With this manual I was able to get my network up and running the way I wanted.  But in chapter six one of the instructions it teaches you to do is to chmod 777 the directory that is to be shared.  I tried skipping this step and sure enough it wouldn't work without it.  Since getting it to work with the chmod 777 command I have tried to change it to other permission levels but nothing else works.  Even chmod 766 made it fail to connect.  So I'm kind of at a loss.  Maybe I'm over thinking it.  Maybe for a home network with no web hosting chmod 777 isn't a big deal.  But everything you read on the internet says how horrible that command is so I figured I would ask here.

So this is my samba.conf file

```
#======================= Global Settings ====================================
[global]
workgroup = WORKGROUP
server string = Linux Shares
netbios name = gunroom
security = user
username map = /etc/samba/smbusers
map to guest = bad user
guest account = nobody
dns proxy = no
#======================= Share Definitions ===================================
[Movies]
path = /mnt/67642963-5223-41a9-8b5f-939d171828d0/Server1/Media/Video
available = yes
valid users = %U %G
write list = %U %G
browsable = yes
public = yes
writable = yes
guest ok = yes
read only = no
printable = no
locking = no
strict locking = no

[Public Drive]
path = /mnt/67642963-5223-41a9-8b5f-939d171828d0/Server1/Public Drive
available = yes
valid users = %U %G
write list = %U %G
browsable = yes
public = yes
writable = yes
guest ok = yes
read only = no
printable = no
locking = no
strict locking = no

[Documents Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive
available = yes
valid users = chad jen simon
write list = chad jen simon
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[Chad Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Chad Drive
available = yes
valid users = chad
write list = chad
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[Jen Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Jen Drive
available = yes
valid users = jen
write list = jen
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[Lolly Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Lolly Drive
available = yes
valid users = lolly chad jen
write list = lolly chad jen
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[Silas Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Silas Drive
available = yes
valid users = silas chad jen
write list = silas chad jen
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

[Simon Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Simon Drive
available = yes
valid users = simon chad jen
write list = simon chad jen
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no
```

This was made following the Samba.org guide.  Then I entered

```
sudo chmod 777 /mnt/67642963-5223-41a9-8b5f-939d171828d0

sudo chmod 777 /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa
```

again this was done following the instructions in the Samba guide in chapter 6.  

So my question is should I change it to something else?  It works perfectly right now.  But for whatever reason as soon as I change that to anything other than 777 it stops working correctly.

Thanks for any advice.

---

### Post by Morbius1 on 2024-01-21
Let's take the least convoluted share definition:
> [Documents Drive]
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive
available = yes
valid users = chad jen simon
write list = chad jen simon
browsable = yes
public = no
writable = yes
guest ok = no
read only = no
printable = no
locking = no
strict locking = no

*[COLOR="#0000FF"]Note: Samba will see that share definition this way:[/COLOR]*
> [Documents Drive]
locking = No
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive
read only = No
strict locking = No
valid users = chad jen simon
write list = chad jen simon
*[COLOR="#0000FF"]Note2 : Makes little sense to have a valid users list = write list on a writeable share since by definition all valid users will be on the "write list" anyway.[/COLOR]*

*** /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa does not have to be 777. It can be 775, 755, it can even be 711. 

It does have to be an odd number however since that will allow others to "traverse" that folder to get to what is beyond it.

*** /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive can be 777 but it's not a requirement.

If you were to put chad , jen, and simon in say a "documents" group then make that directory have group ownership = documents:
```
sudo chown :documents '/mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive'
```
You can set the shared folder to have 775 or even 770 permissions.

And set your share definition to allow only that group:

> [Documents Drive]
locking = No
path = /mnt/01a9fbf5-5f5b-41d3-aa09-36aa35f6ccfa/Documents Drive
read only = No
strict locking = No
valid users = @documents


Sorta kinda depends on what you want - in this example - chad , jen, and simon to be able to do.

As an aside Samba will always have less than or equal control over who can access a given share. Linux may allow everyone access ( 777 ) but if I use "valid users = morbius" only I will be able to access that share as a samba network client.

---

### Post by phobos84 on 2024-01-21
Wow that's a lot simpler.  Thank you.  I'll give this a try and see what it does.

---

### Post by phobos84 on 2024-01-21
That did it.  Thank you.  I'm still learning and have a lot to figure out yet.  The problem I think was that I didn't realize that the chmod number had to be odd.  I kept trying even numbers like 766 or 764 and didn't realize in this situation it wouldn't work.

---

### Post by SeijiSensei on 2024-01-22
They are odd because they need to turn on the "execute" bit which permits entering subdirectories. 

[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-understanding-linux-file-permissions](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-understanding-linux-file-permissions)

You might find symbolic permissions easier to grasp. For instance "711" is the same as "u+rwx,g+x,o+x" giving execute permissions to group members and everyone, but granting full permissions to the directory's owner.

---

