---
title: "File sharing among local accounts is not working for me, help!"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by javierdl on 2014-02-11
[FONT=arial][COLOR=#333333]What I've done:[/COLOR]
[/FONT]
[LIST=1]
[*][FONT=arial]I installed "libpam-smbpass". Restarted.[/FONT]
[*][FONT=arial]Opened the Properties window of the drive (partition) where the folder I want to share is located.[/FONT]
[*][FONT=arial]In its Share tab, checked "Share this folder", and "Allow other to create..."[/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]Next, went to the other Ubuntu account to test it. The drive in question no longer pops up a window for me to enter the admin password. It just does nothing. Namely it doesn't open up.[/COLOR]
[COLOR=#333333]What am I missing?
[/COLOR]
Btw, when I first attempted to share the folder, Ubuntu asked me if I wanted to install Samba, so I got it installed at this moment, then I restarted.


JDL

[COLOR=#333333]Thanks guys,[/COLOR]
[COLOR=#333333]JDL[/COLOR][/FONT]

---

### Post by tfrue on 2014-02-11
In Linux, you don't usually have to restart your computer when you finish installing/updating software/packages, you just restart their service. For example, to restart Apache you type: sudo service apache2 restart, which will then update as needed, or: sudo service samba restart, to restart the samba service.

With Samba, you define share and set options, like authentication and permissions, and share your defined shares on your LAN.

But I will go over a generic install, first we will need to install  Samba (Which you've already done), then edit the config file, then restart the Samba services and we  should be good!

```
sudo nano /etc/samba/smb.conf
```
Scroll all the way to the bottom and type:
Don't type the text in the parenthesis.
```

[NewShare}
comment= My New Share
path= /path/to/directory (Can be any path, ex. /home/chris/share)
browseable= yes
writeable= yes
guest ok= yes
read only= no
```

Press "ctrl+x", and possibly type "yes" if it ask, to save the file.

That will make an open share that anyone can access and put/take  anything from it. We can lock it down and make it more secure if you  want, just let me know and I will show you how to do that.

Now we need to restart the samba service, type:
```
sudo service smbd restart

and

sudo service nmbd restart
```

Here is a free online book of Samba that gets pretty detailed, so I would recommend looking over it,
[http://oreilly.com/openbook/samba/book/index.html](http://oreilly.com/openbook/samba/book/index.html)

That should get you up and running with a Samba defined share that  anyone can access when they connect to your LAN, let me know if you have  any troubles and I will help!

Good luck,
Chris

---

### Post by tfrue on 2014-02-11
I was researching this more, and found a more up to date book for Samba that uses version 3:
[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)

---

### Post by bab1 on 2014-02-11
> **javierdl said:**
> [FONT=arial][COLOR=#333333]What I've done:[/COLOR]
[/FONT]
[LIST=1]
[*][FONT=arial]I installed "libpam-smbpass". Restarted.[/FONT]
[*][FONT=arial]Opened the Properties window of the drive (partition) where the folder I want to share is located.[/FONT]
[*][FONT=arial]In its Share tab, checked "Share this folder", and "Allow other to create..."[/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]Next, went to the other Ubuntu account to test it. The drive in question no longer pops up a window for me to enter the admin password. It just does nothing. Namely it doesn't open up.[/COLOR]
[COLOR=#333333]What am I missing?
[/COLOR]
Btw, when I first attempted to share the folder, Ubuntu asked me if I wanted to install Samba, so I got it installed at this moment, then I restarted.


JDL

[COLOR=#333333]Thanks guys,[/COLOR]
[COLOR=#333333]JDL[/COLOR][/FONT]

There are many ways to share a folder using Samba.  Some are easier than others.  You are limited to non-root created shares (and the underlying directory) when you create Samba usershares (created using the GUI).  This provides a method for a user to share directories under their home directory (/home/<user>).   In fact this is why Samba developers created usershares in the first place.

If you want to share a directory that is outside of your home directory then you need change the permissions of that folder.  I'm not sure that a *"Share this folder", and "Allow other to create..." * command on a directory that you do not own or have permissions is allowed.  I have all of my "public shared data" stored at /srv/samba.  I used chmod and chgrp using sudo to create the proper ownership and permissions.  Once that is done you can either create the share with the GUI or create a share by editing the /etc/samba/smb.conf file.

I mention this so you understand that the are 2 ways to do what you want to do.  For a noobie I would create the share in my home directory.  Something like /home/<user>/samba/<directory_to_be_shared> would work.  Then use the GUI to create the usershare.  

The traditional method requires that you understand sudo and permissions/ownership issues and the willingness to directly edit the smb.conf file to create the share.  If you want to do this that I think [this is appropriate]("http://www.jonathanmoeller.com/screed/?p=4169") for your use.

The book that @tfrue has recommended is way out of date (2003) and mostly about Samba v2.  The second release of the book was at the time when Samba v3 was being introduced.  We are now at Samba v3.6.  The book is not inaccurate, but it is outdated.  It will have no information about SMB2 or SMB3 and the client package is now cifs-utils rather than smbfs.  It is also mind numbing for someone who is just starting out.  It is more like a reference book rather than a tutorial.  In my opinion it's nice to have but it only make sense once you have a general idea how it all works anyway.

Whichever method ( _usershares_ or _traditional edit_ of the smb.conf) we are here to help you.

---

### Post by deadflowr on 2014-02-11
By locally, do you mean on the same machine or over a network?

Edit: Nevermind, I didn't notice this is the networking sub-forum.
But it seems strange that when you first tried sharing and it asked to install samba, that it didn't ask to also install the libpam-smbpass package as well.
Those usually install together.(when using the share this folder method)

---

### Post by bab1 on 2014-02-11
> **deadflowr said:**
> ...it seems strange that when you first tried sharing and it asked to install samba, that it didn't ask to also install the libpam-smbpass package as well.

Those usually install together.(when using the share this folder method)

I think that libpam-smbpass started to be installed from 12.10 or 13.04 on.  I have 12.04 on this workstation and it is not installed, even with Samba usershares being used.

```
ls -l /var/lib/samba/usershares
total 8
-rw-r--r-- 1 bab bab 117 Dec  6 17:41 2013_pix
-rw-r--r-- 1 bab bab 113 Jan  3 12:09 2014_pix

```

---

### Post by Morbius1 on 2014-02-12
@bab1, Once again my apologies for my intrusion but this has to be fixed somehow because it's showing up all over the place .........
> **tfrue said:**
> 
```
[NewShare}
comment= My New Share
path= /path/to/directory (Can be any path, ex. /home/chris/share)
browseable= yes
writeable= yes
guest ok= yes
read only= no
```

Press "ctrl+x", and possibly type "yes" if it ask, to save the file.

[COLOR=#0000cd] That will make an open share that anyone can access and put/take  anything from it.[/COLOR]


You do realize that as a general mini howto if someone follows your post verbatim it will not do what I've highlighted in blue, right? You are missing 1 and depending on how the folder being shared is used on the local server itself possibly 2 steps. 

The other thing that's wrong with that post is that you've completely ignored the fact that the user created a Samba Usershare as bab1 pointed out. If he did that and also followed your post we a situation where we have 2 different share definitions in 2 different places both telling samba to share the same folder and they may or may not conflict with each other forcing a cleanup by removing one or the other share.

---

### Post by bab1 on 2014-02-12
> **Morbius1 said:**
> @bab1, Once again my apologies for my intrusion but this has to be fixed somehow because it's showing up all over the place .........

You do realize that as a general mini howto if someone follows your post verbatim it will not do what I've highlighted in blue, right? You are missing 1 and depending on how the folder being shared is used on the local server itself possibly 2 steps. 

The other thing that's wrong with that post is that you've completely ignored the fact that the user created a Samba Usershare as bab1 pointed out. If he did that and also followed your post we a situation where we have 2 different share definitions in 2 different places both telling samba to share the same folder and they may or may not conflict with each other forcing a cleanup by removing one or the other share.

No apologies needed.  I only skimmed the reply when I saw that @tfrue recommended a book that is obviously outdated.  My response was directed to  the OP's points for the most part.  

I have come to the conclusion that I (we) can't cure all the incorrect responses.  My wife says that if I continue to "tilt at windmills" I will become a bitter old man.  I have to admit though -- the Barbarians are at the gate!  :D

---

### Post by tfrue on 2014-02-12
> You do realize that as a general mini howto if someone follows your post  verbatim it will not do what I've highlighted in blue, right? You are  missing 1 and depending on how the folder being shared is used on the  local server itself possibly 2 steps. 

I don't think you realize it does make an open share. I just opened my server and created a share using the defined parameters and it worked. I will say that I did fail to mention changing the permissions on the /path/to/share, but other than that, that is what I missed. Perhaps I did give a bad example as you would have to uncomment the share home folder in the smb.conf file, but that open share works.

Another thing you could do rather than call me out, is to post the corrections of the one or two mistakes that I made.

Let me reiterate what I already posted in my first post, one thing I did fail to mention is that I don't know how to use the GUI version of Samba, so I did neglect the OP, but I was giving a generic installation on how to use Samba. > [COLOR=#0000ff]But I will go over a generic install[/COLOR], first we will need to  install   Samba (Which you've already done), then edit the config file,  then  restart the Samba services and we  should be good!Also, if you have been reading all the post that are coming up everywhere you would've noticed that I have stated many times I don't know or understand the GUI version of Samba. 

> The other thing that's wrong with that post is that you've completely  ignored the fact that the user created a Samba Usershare as bab1 pointed  out. If he did that and also followed your post we a situation where we  have 2 different share definitions in 2 different places both telling  samba to share the same folder and they may or may not conflict with  each other forcing a cleanup by removing one or the other share.
Also, did you notice that bab1 posted the  samba usershare information after I posted the generic installation? As I should've mentioned in my first post, I don't know how to use the GUI version of Samba, but I do know how to use the CLI version. I did neglect the OP, and you are right we don't want two shares pointing to the same share so isn't that why we come together to help everyone? The reason I'm here is to help others while learning just as much because I don't know it all and what you did was not beneficial to anyone.

> I have come to the conclusion that I (we) can't cure all the incorrect responses.
You're right, but isn't that what this community is here for? I've used Linux for a little over a year now, I certainly don't know everything nor a great deal of things about it, but I'm learning just like everyone else because no one is an expert in every field.

---

### Post by Morbius1 on 2014-02-12
The original post said this:
> Opened the Properties window of the drive (partition) where the folder I want to share is located.
In its Share tab, checked "Share this folder", and "Allow other to create..."
The user just created a Samba Usershare - this has nothing to do with bab1's post.

If your objective was to create a guest share that allows anyone to add to, remove from, and edit all of it's content your post will not work. If you change permissions on the shared folder but leave the share definition as it is it will not work. If you want to see how it's done using the traditional way you should look at one of bab1's posts like this one under *** Public Share ***: [http://ubuntuforums.org/showthread.php?t=2200700&p=12915098#post12915098](http://ubuntuforums.org/showthread.php?t=2200700&p=12915098#post12915098)

But you know what? After reading the original post again:
> Next, went to the other Ubuntu account to test it. The drive in question no longer pops up a window for me to enter the admin password. It just does nothing. Namely it doesn't open up.
admin password? Other user account?

Um ... There's a good chance it's just me but I don't think this is a network file sharing question. I think he is trying to create a shared folder that all local users have access to not users across the lan. Or it's a partition that's not automounting and there are concurrent users trying to access it, or .....

---

### Post by deadflowr on 2014-02-12
> **Morbius1 said:**
> 
Um ... There's a good chance it's just me but I don't think this is a network file sharing question. I think he is trying to created a shared folder that all local users have access to not users across the lan. Or it's a partition that's not automounting and there are concurrent users trying to access it, or .....

I thought that too, until I realized the post is in the networking sub-forum.
But, it's probably best to wait for any response from the OP before drawing conclusions on what exactly is going on.

---

### Post by bab1 on 2014-02-12
> **tfrue said:**
> ... I will say that I did fail to mention changing the permissions on the /path/to/share, but other than that, that is what I missed. Perhaps I did give a bad example as you would have to uncomment the share home folder in the smb.conf file, but that open share works.

Writing to a public forum should make one think of all the possibilities.  This isn't like raising your hand in class to answer the question.  This stuff is read by the OP and all those that follow.  Either you get it ALL right or don't answer the original question.  There is no sorta right.  :-(
> 
Another thing you could do rather than call me out, is to post the corrections of the one or two mistakes that I made.

I would say @Morbius1 has!  On both the mental and technical concerns.  Both @Morbius1 and I have been contributing to this forum for over 5 years we have seen folks who sorta knew what they were talking about to others that have trouble even understanding the most basic concepts.  From my point of view the person who thinks they know everything is the most dangerous, especially when it turns out they only know part of the solution.
> 
Let me reiterate what I already posted in my first post, one thing I did fail to mention is that I don't know how to use the GUI version of Samba, so I did neglect the OP, but I was giving a generic installation on how to use Samba. Also, if you have been reading all the post that are coming up everywhere you would've noticed that I have stated many times I don't know or understand the GUI version of Samba. 

Well..., then why even attempt to answer the OP's question if you don't know "don't know or understand the GUI version of Samba".  Your quote not mine.
> 
Also, did you notice that bab1 posted the  samba usershare information after I posted the generic installation? As I should've mentioned in my first post, I don't know how to use the GUI version of Samba, but I do know how to use the CLI version. I did neglect the OP, and you are right we don't want two shares pointing to the same share so isn't that why we come together to help everyone? The reason I'm here is to help others while learning just as much because I don't know it all and what you did was not beneficial to anyone.

I responded because your answer was inadequate and not relative to to the OP's question.  If you have even been partially correct as a response to the original question I would have let you continue without posting anything.
> 

You're right, but isn't that what this community is here for? I've used Linux for a little over a year now, I certainly don't know everything nor a great deal of things about it, but I'm learning just like everyone else because no one is an expert in every field.

Don't learn at some forum posters expense and don't hide behind the "community" thing.  The community will be better served if you are more complete and accurate with your answers. Say less, learn more.  Only speak to what you really understand *fully * and be damn sure you are complete.   If you answers were part of a simple test you would get a D from me.

---

### Post by bab1 on 2014-02-12
> **Morbius1 said:**
> ...

Um ... There's a good chance it's just me but I don't think this is a network file sharing question. I think he is trying to create a shared folder that all local users have access to not users across the lan. Or it's a partition that's not automounting and there are concurrent users trying to access it, or .....

From my point of view the OP was trying to share the folder using Samba usershares.  This doesn't mean that this is really best for what he is trying to accomplish.  However, even if there is only one machine with multiple users, you certainly can mount a Samba share on one host as both the Samba server and it's client.

At this point we are truly OT.  Until we hear from @javierdl we really won't know.

---

### Post by tfrue on 2014-02-12
@bab1, I agree, maybe I shouldn't have posted since I don't fully understand the GUI concept; but I'm certainly not hiding behind the "community" thing. I came to this site to give back what I learned through my studies and research.

My goal with responding to this post and any post in this forum is to educate others and help, I neglected the OP and didn't realize it and there are tons of better ways of letting someone know rather than calling them out in such a vague way.

So to really summarize a huge post that I was about to write, I will say thank you @bab1, because what you posted was something I can actually learn from. I will pay better attention to the OP rather than being fixed on a solution. Thanks, again.

---

### Post by Iowan on 2014-02-12
Thread has drifted off-topic...
Anyone notice that the OP hasn't been back?

---

### Post by javierdl on 2014-02-16
First off, sorry I took so long to come back. Secondly thanks a million to all that came to help.

Morbius1,
> "[COLOR=#000000]Um ... There's a good chance it's just me but I don't think this is a network file sharing question.[/COLOR]"

Sorry I wasn't more accurate with the description of my situation. Correct, I am not connected to other PCs in a LAN, nor I'm interested in sharing across the internet. I'm just trying to share a folder in a separate HDD to a 2nd Ubuntu user with her own account.

Hours ago I replaced the content of smb.conf with 

[NewShare]
comment= My New Share
path= /media/javierdl/2BackUp
browseable= yes
writeable= yes
guest ok= yes
read only= no

But I guess either I miss something or it might have conflicted with my sharing it via the GUI too, or both, I don't know, because after rebooting nothing has changed, and now that I went to check the once modified smb.conf file now is back to its original content.
Should I remove all the sharing I did via the GUI, then modify the smb.conf file again?

JDL

---

### Post by bab1 on 2014-02-16
> **javierdl said:**
> First off, sorry I took so long to come back. Secondly thanks a million to all that came to help.

Morbius1,


Sorry I wasn't more accurate with the description of my situation. Correct, I am not connected to other PCs in a LAN, nor I'm interested in sharing across the internet. I'm just trying to share a folder in a separate HDD to a 2nd Ubuntu user with her own account.

If you have only one PC then you don't need Samba.  What you do need is a separate directory that both users have access to.  
> 
Hours ago I replaced the content of smb.conf with 

[NewShare]
comment= My New Share
path= /media/javierdl/2BackUp
browseable= yes
writeable= yes
guest ok= yes
read only= no

None of this is needed.  In fact you can remove the Samba server from the PC.
> 

But I guess either I miss something or it might have conflicted with my sharing it via the GUI too, or both, I don't know, because after rebooting nothing has changed, and now that I went to check the once modified smb.conf file now is back to its original content.
Should I remove all the sharing I did via the GUI, then modify the smb.conf file again?

JDL
Forget about Samba and the smb.conf file.

Where is the data you want to share stored at the present time?

---

### Post by Morbius1 on 2014-02-17
I have three other questions if that's ok.

If the folder being shared is at /media/javierdl/2BackUp then that's the problem. You can set "2BackUp" to have permissions of 777 such that everyone and your Uncle Bob will have access but the system uses an ACL ( access control list ) on /media/javierdl that will prevent anyone other that javierdl from getting access to it.

If 2BackUp is the mount point of a partition on this "separate HDD" you referenced it would be better if the partition was mounted one level higher on the hierarchy like /media/2BackUp so my questions are:

(1) Is this an internal HDD or an external ( as in USB ) HDD?
[COLOR=#0000cd]*I really don't like the idea of automounting USB drives in fstab - eventually someone will yank it out without a proper unmount and all h-e-double-toothpick will ensue.*[/COLOR]

(2) Do you already have an entry in /etc/fstab for this partition? If so post the output of the following command so we can see how it's set up:
```
cat /etc/fstab
```
(3) How is it formatted - ext4? ntfs? ....

[SIZE=1]*Oddly enough samba can be used to circumvent this issue by using a "force user" in the share definition but using samba to share a folder on the same machine is too perverse logically  - even for me :p*[/SIZE]

---

### Post by javierdl on 2014-02-17
Bab1, 
good! That's great news! I suppose I'll have to learn Samba eventually, but for now I have enough just searching for the right video-card drivers while still being a rookie at Linux/Ubuntu.

Morbius1,

[COLOR=#000000](1) It is an internal HDD.[/COLOR]

[COLOR=#000000](2) Do you already have an entry in /etc/fstab for this partition? 

I don't. I went to that folder and it's empty.

If so post the output of the following command so we can see how it's set up:
[/COLOR]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=add39c55-b321-4ba7-a1f2-e72956419e89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=658541ef-bf29-463a-b875-4300bcc7c63c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[COLOR=#000000](3) How is it formatted - 
[/COLOR]
NTFS


[COLOR=#000000]
[/COLOR]

---

### Post by Morbius1 on 2014-02-17
Then what I would do is the following:

[1] Make a permanent home for this partition to live in:
```
sudo mkdir /media/BackUp
```
[2] Edit fstab as root:
```
gksu gedit /etc/fstab
```
[3] Use the following template and changing the actual UUID number add it to the end of fstab:
```
UUID=DA9056C19056A3B3 /media/BackUp ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```
[COLOR=#0000cd]*To find the correct UUID number for your ntfs partition run the following command:*[/COLOR]
```
sudo blkid -c /dev/null
```
[4] If the partition is already mounted unmount it:
```
sudo umount  /media/javierdl/2BackUp
```
[5] Then run the following comand to test for errors in fstab and if there are none mount the partition to /media/BackUp:
```
sudo mount -a
```

Notes:
umask=000 will make it accessible to all local users. If you want to make it more restrictive we can do that.
By addining it to fstab it will always mount to /media/BackUp automatically at boot.

---

### Post by bab1 on 2014-02-17
> **Morbius1 said:**
> I have three other questions if that's ok.


...

(2) Do you already have an entry in /etc/fstab for this partition? If so post the output of the following command so we can see how it's set up:
```
cat /etc/fstab
```
(3) How is it formatted - ext4? ntfs? ....

[SIZE=1]*Oddly enough samba can be used to circumvent this issue by using a "force user" in the share definition but using samba to share a folder on the same machine is too perverse logically  - even for me :p*[/SIZE]

I'm on the road today.  I think this is just a matter of setting up the directory so all have access and some common group.   How about 2775 permissions and the users in the ***group named users***.

---

### Post by Morbius1 on 2014-02-17
> **bab1 said:**
> I'm on the road today.  I think this is just a matter of setting up the directory so all have access and some common group.   How about 2775 permissions and the users in the ***group named users***.
You can certainly restrict write access to the "users" group or any other group if you wish:
```
UUID=DA9056C19056A3B3 /media/BackUp ntfs defaults,nls=utf8,umask=002,gid=100,windows_names 0 0
```
There's no need for a "2" ( setgid ) since all permissions are immutable and inherit the permissions of the mount when ntfs is mounted in Linux. You just have to remember to add yourself to that group.

---

### Post by bab1 on 2014-02-17
> **Morbius1 said:**
> 
...

There's no need for a "2" ( setgid ) since all permissions are immutable and inherit the permissions of the mount when ntfs is mounted in Linux. You just have to remember to add yourself to that group.

Yes, I missed the formatting.  I saw internal HDD and figured it was EXT formatted.

---

