---
title: "How hard can it be?"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by thered on 2007-11-16
All I want to do is share files between my laptop and desktop.  Both running Ubuntu 7.10

I can see both on the network.  I set folders to be shared. I've set permissions on folders. I can see folders...but... when i click on the folder it tells me it is empty or may have been deleted.  Won't let me view files or access them. They are both part of same 'workgroup'

Shares a samba shares.  I've tried nfs too without success.

I read various postings on here but most want to share with windoze Pcs.

I'm sure I'm missing something silly, but can't tie it down.

Any ideas?

---

### Post by taurus on 2007-11-16
Install ssh-server on one machine and you can ftp in from the other.

---

### Post by thered on 2007-11-16
Taurus: Surely there's a more elegant solution... ;)

---

### Post by Phurious on 2007-11-16
Did you . . .
```
sudo smbpasswd -a <USER>
```
?

---

### Post by thered on 2007-11-17
Phurious:  No I don't think I did. I've only used the various GUIs to set it up, or try and set it up.

Pray elaborate, where and when and on what do I use this command.

---

### Post by Phurious on 2007-11-17
Here is a good tutorial that helped me:

[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")

---

### Post by thered on 2007-11-17
Phurious:  Wonderful my friend, that turned on all the lights!!! 8)

Network filesharing up and running. :)

Thank you very much.

---

### Post by thered on 2007-11-17
For those who come after, here's a quick how to:

Samba network:

Set up workgroup:

System>Admin>Network

Select connection then general tab - give Pc a hostname - leave domain blank.

System>Admin>Shared folders

General properties tab and give network a name e.g. Workgroup (default is MS Home)



Open terminal

```
sudo gedit /etc/samba/smb.conf
```

Find line with 'browsable' and remove comment mark and make it:

browseable = yes

Find line below with 'writeable' in remove comment mark and make it

writeable =yes

SAVE and close file.



Setup samba server password:
```

sudo smbpasswd - a usernameofchoice (doesn't **have** to be your ubuntu one)
```

terminal will ask for samba password - type it in

terminal will ask you to confirm it.

Restart samba server:

```
sudo /etc/init.d/samba reload.
```

Terminal should confirm with [OK]

Share folders:

pick or create folders to share.

Right click on folder and select share...

In dialog box select windows network and either remove tick in 'read only' box or not.

Right click on each folder and select 'properties' click on 'permissions' tab and select Create and Delete files for all

---

### Post by HermanAB on 2007-11-17
Samba is a very complex system and will always be hard to get to work.  If you are new to networking, install Filezilla server and client (it is cross platform Linux/Windows) and use that till you are more comfortable with Linux networking.

Cheers,

Herman

---

### Post by Hollowman on 2007-11-17
Ok, I have been trying to figure this out for 2 years.  I followed the video and still no luck.  My set up is as follows.   

Two Ubuntu 7.10 boxes connected to a linksys vonage router.  I have installed the samba packages, altered my smb.conf file and added a user under sbpasswd just like the video and thread shows.  I have set up a shared folder just like it the video. 

When I open up Networking and look under windows network, nothing shows.  Not my local shared folder or anything.  

What am I doing wrong.  

I have been using Ubuntu for 2 years now but  have never figured out how to file share between by two computers.  

Any help would be greatly appreciated.   

Thanks,

Hollowman

---

### Post by Phurious on 2007-11-17
Could be a permissions issue.  Try this on the machine you are sharing the folder from:

```
sudo chmod 777 </PATH/SHARED_FOLDER>
```

Then see if you can browse the folder from the network.

Also, did you install smbfs at the same time you installed samba?

---

### Post by thered on 2007-11-17
hollowman: Have you installed the firewall, Firestarter?  If so you will have to tell it to allow connections from IP addresses on you LAN.

---

### Post by kesomir on 2007-11-18
I would absolutely recommend the 2nd posters suggestion.

on each machine: aptitude install ssh

then when you wish to access files on the other, open nautilus and enter ssh://USERNAMEON OTHER BOX@IPOFOTHERBOX

Quick, painless and encrypted :)

---

### Post by liniaal on 2007-11-18
> **Hollowman said:**
> Ok, I have been trying to figure this out for 2 years.  I followed the video and still no luck.  My set up is as follows.   

Two Ubuntu 7.10 boxes connected to a linksys vonage router.  I have installed the samba packages, altered my smb.conf file and added a user under sbpasswd just like the video and thread shows.  I have set up a shared folder just like it the video. 

When I open up Networking and look under windows network, nothing shows.  Not my local shared folder or anything.  

What am I doing wrong.  

I have been using Ubuntu for 2 years now but  have never figured out how to file share between by two computers.  

Any help would be greatly appreciated.   

Thanks,

Hollowman

duh, i don't think that another ubuntu box would show up under "windows network" ? but ok. greatest thing i've learned lately for sending files in between my laptop and my pc is scp :guitar: blazing fast (seems faster than ftp), secure, and simple. scp -r works as well, of course.

---

### Post by Hollowman on 2007-11-18
Wow, thanks for all the replies.  I will try all the suggestions and let you know if I get any where.    This is what I love about the forums.    


Hollowman

---

### Post by thered on 2007-11-18
Hollowman: All I can say if you follow the video that phurious linked to, is that it works.  The only thing it fails to mention is setting of permissons.

I can swap files, I can open and create files across the network in Gedit and open office and save them to both Ubuntu machines.

I can create folders.

I don't need to do anymore, but I'm sure most things will work

---

### Post by Hollowman on 2007-11-19
I got it to work.  The issue came down to my firewall blocking the samba share.  As soon as I turned off the firewall, every thing worked just like the video.   I'm happy, more importantly, my wife is happy (she has been dogging me to figure this out for 2 years).  Now I just need to get firestarter to allow my samba to run.  

Thanks for all the help.  


Hollowman

---

