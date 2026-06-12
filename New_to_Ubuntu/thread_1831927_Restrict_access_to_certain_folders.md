---
title: "Restrict access to certain folders"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by psylencer on 2011-08-24
Hi all,

Hoping this is an easy question.  I want to have Thunar or Nautilus open with a restricted view of directories which I specify.  IE I want a Video, Pictures and Recordings directory to be displayed and perhaps the ability to access mounted drives other than SDA ie USB Flash, External HDDs etc.  

Could someone please recommend the best way to do this?

I was thinking use FTP server to define directories I wish to share, and using an FTP client to access the directories but I run into headaches if the user plugs in a USB flash - as it will not automatically be added to the FTP client permissions.

Any ideas?

Thanks in Advance.

---

### Post by androssofer on 2011-08-24
> **psylencer said:**
> Hi all,

Hoping this is an easy question.  I want to have Thunar or Nautilus open with a restricted view of directories which I specify.  IE I want a Video, Pictures and Recordings directory to be displayed and perhaps the ability to access mounted drives other than SDA ie USB Flash, External HDDs etc.  

Could someone please recommend the best way to do this?

I was thinking use FTP server to define directories I wish to share, and using an FTP client to access the directories but I run into headaches if the user plugs in a USB flash - as it will not automatically be added to the FTP client permissions.

Any ideas?

Thanks in Advance.

an unelegant solution tht wud perhaps take some work, but shud do the trick. is create a new user, then restrict access to most of ur files and folders to only be readable to root and perhaps another account? 

so the user could only view their home directory. and any new usbs etc should b ok for them to access aswell.

here is a doc on permissions:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

however, sum1 might hav a btr solution...

---

### Post by psylencer on 2011-08-24
Trouble is all of those folders would have to be under the users home folder.  Which is a problem.  Secondly, the user executing the "command" Browse folders would have to be a different user as is necessary for the system Im working on.  Im guessing I could use SU username thunar or similar, but wouldn't that require me to enter a password?  - Not really the option im looking for.  Also correct me if Im wrong, but wouldn't that user be able to see all the other folders if they were to go up a folder level?

---

### Post by mikejonesey on 2011-08-24
ftp server does not define dirs, think your confusing yourself a little maybe? I'm confused over what you are trying to acomplish.

to enable usb to a user group add a rec to the fstab

please clarify what you need as i'm not too sure...

---

### Post by psylencer on 2011-08-24
I have no doubt I can define folders with an FTP server of which I wish the user to access.    Seems like a complicated solution though.  I was hoping for a way to launch Thunar or similar with restricted access properties.     Ie I want to enable the user to access and see certain folders, not just those which exist within the users home folder.  I do not want the user to even see folders of which they have no rights not access.

Perhaps I need to script my own interface.  Any ideas where I should start?

---

### Post by Wim Sturkenboom on 2011-08-24
Are you talking about a local machine or remote access (the mentioning of FTP makes it confusing)?

If local:
Define a number of groups (one for each directory that you want to protect). Make the users that are allowed to see video a member of the (new) video group, make users that are allowed listen to music a member of the (new) music group etc.

Use
```

chown you:videogroup videodirectory
chown you:musicgroup musicdirectory
...
...

```
You will still have full ownership and only members of the specific groups have read only access with the below code
```

chmod 750 videodirectory
chmod 750 musicdirectory
...
...

```
If you need finer grained control, I think that ACL is the way but others might have better ideas.

---

### Post by psylencer on 2011-08-24
My idea with the FTP was to have a server and client running on the same machine - ie the client connects to the server 127.0.0.1


Does you idea allow for the user to be locked to those directories specified?

---

### Post by Wim Sturkenboom on 2011-08-25
It's not a jail as in ftp if that's what you mean. The user can still snoop around in e.g. /etc and in home directories of other users; the latter can easily be fixed with permissions.

I don't think FTP is the solution on a local system. What would prevent the user to change the 'location' in Nautilus to *_/home/username_* or to *_/etc_* ?

Maybe you can tell us why you want to achieve what you're trying to achieve. Don't you want your kids to watch the movies or ...

---

### Post by psylencer on 2011-08-25
> **Wim Sturkenboom said:**
> 

I don't think FTP is the solution on a local system. What would prevent the user to change the 'location' in Nautilus to *_/home/username_* or to *_/etc_* ?


This is a Kiosk system. I've modified the interface to prevent users from accessing terminal, menus etc. Therefor preventing them from making changes to the system.  One thing I would like them to be able to do is insert a USB drive and allow them to copy their own files to directories which they have the permissions to access.  I don't want them to to be able to see ssytem files, regardless of whether they can view them.

Basically a simple system where users can see connected devices and copy files from those devices to the directories with which they have permission do do so.  

Still thinking FTP is the closest solution - however that doesn't (advice needed) allow connected devices to be accessed as they all have potentially different mount points depending on the media used.

Ie Jack connects a USB stick made my toshiba, would have a different mount point to a 2.5" HDD mounted by jill.

Think of a traditional DVR - one can view and copy files, however they cannot see system directories and files - just the stuff they are meant to see.

---

### Post by androssofer on 2011-08-25
> **psylencer said:**
> This is a Kiosk system. I've modified the interface to prevent users from accessing terminal, menus etc. Therefor preventing them from making changes to the system.

got a plan! which i kinda wanna do myself now(for funs), but dnt know quite how to do the finer details.... and my logic might b a tad flawed, so bare with me! 

so u make a new group, say called "admins" and to that you add your main users, say root and yourself...

then you make another "averageJoes", and add the restricted users (jim and jill? )to that.

then to all the files folders u wanna hide from the averagesJoes, but still want admins to see, u change their group to admins. (can a file/folder belong to multiple groups? if so, add the folders to this group.)

then all the folders u want averageJoes to be able to see change(or add if possible) their group to averageJoes. say like /media (for usbs)

then u recursivly remove read access for "others" on all the stuff u wanna hide from averageJoes

```
chmod -R -r parentFolder/
``` (tho this will remove read access from every1, so it needs to be fixed to only remove read access for "other", so any suggestions?)

tho this might cause havoc on the system. so might wanna get it verified by sum1 who knows wot their doing... or try it on a vm...

the idea behind it is. tht restricted things on the system are not allowed to be read by "others" only by their owner and group. and as their group is part of "admins" only those in tht group can view the restricted stuff. and averageJoes would hav their own folder, plus general stuff like usbs etc but wud b unable to read other files/folders as they arent in admins and "others" arent allowed to read!

---

### Post by Wim Sturkenboom on 2011-08-25
Thanks for clarifying. Have you considered dedicated kiosk solutions? I'm not familiar with that and don't have other solutions.

I did think about apache and only starting a browser at startup and protecting directories with htaccess. But I can not prevent access using *_file:///_* which will show the root file system :(

---

