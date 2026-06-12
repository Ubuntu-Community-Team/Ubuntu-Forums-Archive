---
title: "bash, make share folder and mount share folder"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Beezgetz on 2009-11-23
Hello Ubuntu,

I have been searching for couple of days now, and I found some posts here and elsewhere, but none did the trick.

I have 2 laptops, HP and Dell. 
HP has two 'outside' disks (I am not a native English speaker, so disk that is connected to laptop via usb cable), that have been formatted to ntfs, well long time ago.
Both computers are connected in 'network', via internet switch (again, I do not know the right term, but little box that you can connect 4 computers for internet. I have modem, and router, and than this internet switch box)

I can easily connect from one computer to another using gui. First I make folder shareable, than I go to network (places) and I choose folder(s).

Recently I have been learning bash commands, and I am eager to do this steps via command line.

My first question is, how do I set some folder to be share?
a)from my laptop (ext4 fs)
b) from my outside disk (ntfs)


and second question, how do I mount them?


I have tried 
mount -t smbfs -o user=me, password=xxxx dell:/path/to/share /path/to/mount
mount -t cifs -o user=me, password=xxxx dell:/path/to/share /path/to/mount
mount -t nfs -o user=me, password=xxxx dell:/path/to/share /path/to/mount


mount -t smbfs -o user=me, password=xxxx //dell/path/to/share /path/to/mount
mount -t cifs -o user=me, password=xxxx //dell/path/to/share /path/to/mount
mount -t nfs -o user=me, password=xxxx //dell/path/to/share /path/to/mount

mount -t smbfs dell:/path/to/share /path/to/mount
mount -t cifs dell:/path/to/share /path/to/mount
mount -t nfs dell:/path/to/share /path/to/mount

and many other combinations, but I always get some errors... (I could provide output as well)


If my language is poor, I could try to write in more details, sorry guys..

Thank you!

---

### Post by Sarmacid on 2009-11-23
The information you need is here

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ukripper on 2009-11-23
NFS sharing guide - [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Beezgetz on 2009-11-23
Oi guys,

Thanx for the links, but i stumbled upon those sites before...

I was more hoping that this is 3-4 step adventure.

(As I search the net now, I find this post on every first page of the results, so either I do not know how to search or this has not been elaborated before for ubuntu)


So I kindly ask again, is there some command to make a folder shareable, between two ubuntu computers (let us forget about my outside disks)
(I found Red Hat has 4 step 'solution')

and second question, how do I access shared folder from one (ubuntu) computer to another (ubunu) computer?

both questions are for command line (bash), not for gui.

(please, I heard about feeding/teaching the guy with/to fish, I am busting my head over this for over a week now, and all those pages are not so easy to understand.)

I would really appreciate some command line examples.

Kind regards, Beezgetz

---

### Post by nothingspecial on 2009-11-23
If they are both your computers have you thought about just using ssh?

Or do you want to restrict access to the other computer other than the shared folder.?

---

### Post by Beezgetz on 2009-11-23
Hello!

They are both mine, on same desk.

I just want to be able to make same steps as in gui (my first post), only in shell....

So, make some folder shareable on one laptop, and
connect to that folder from another laptop...
..in shell


I don't know what ssh is, I was directed to mount command on our local ubuntu forum (sLOVEnia), so I picked it up from there...

I am not trying to be an expert, I am a beginner, but I would like to use shell for more day-to-day 'work'...


Kind regards, Beezgetz

---

### Post by nothingspecial on 2009-11-23
If you use ssh, you don`t have to "share the folder". You log in to the other computer. So

```
sudo apt-get install openssh-server openssh-client
```

You may have one or both of these installed already........they keep changing it with every release.

 Then, on the machine you want to connect to, type ```
ifconfig
```. In the section related to your internet connection (eth0 if wired, wlan0 if wireless (probably) find your ip address (listed as internet address).

Then on the other machine type ```
ssh username@ipaddress
```

eg```
 ssh beezgetz@192.168.1.2
```

After you have accepted the warning and typed your password (your password on the other computer), you will be logged into your home directory on the remote computer.

From there use the cd command to access the folder.

---

### Post by Beezgetz on 2009-11-23
Oi man, nothing special, this IS special!!!

So, this is like vnc, for desktop use? I have all acces, not folder by folder via shell - great!

Every day I learn something new! This is great, I will defenitly use this! THANKS!

But, still, I would like just to share some folders, so people that are in 'network' can access data that I put in those folders.
I will search for my answers and get back.

Thanks, Beezgetz

---

