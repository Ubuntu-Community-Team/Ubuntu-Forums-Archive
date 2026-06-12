---
title: "Accessing MacOSX Home Folder in Ubuntu."
date: 2009-11-27
forum: New to Ubuntu
---

### Post by renegadespork on 2009-11-27
I have an extensive library of movies/music in my home folder in OSX, but I can't seem to access them in Ubuntu. I can mount my "Macintosh HD" fine, but when I navigate to my home folder, most of the sub folders are locked ("Music" "Pictures" "Movies" "Desktop" "Library" etc).

I went into OSX (10.5 Leopard) and changed the permissions on these folders (and all of their contents) for "everyone" to "read and write". However, when I try to access them back in Ubuntu, they are still locked. Any suggestions?

---

### Post by jrrader on 2009-11-27
This is more of a Mac issue than an Ubuntu issue.  Try asking in the [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328") forum and you're more likely to get the help you need.

---

### Post by coffeecat on 2009-11-27
> **renegadespork said:**
> I went into OSX (10.5 Leopard) and changed the permissions on these folders (and all of their contents) for "everyone" to "read and write". However, when I try to access them back in Ubuntu, they are still locked. Any suggestions?

When you mean access, do you mean simply copy them off, or do you mean modify/write to them in some way? Because you'll only be able to read them in Ubuntu. Your Leopard HD will almost certainly be formatted with the journalled version of hfs+, for which there are only read-only drivers in Linux. You can write to non-journalled hfs+ in Ubuntu, but it's exceedingly unlikely that your Leopard HD is non-journalled.

But if you can't access the files even for a read, that's curious. One problem would be that your Mac UID and Ubuntu UID will be different. For the first created user the UID in Ubuntu is 1000. Iirc, it's 501 in MacOS. Whatever, it's different. But by changing the permissions to read and write for everyone - which was basically a chmod - you should have made the Unix-permission system allow you read access in Ubuntu.

If you can't access the files even read-only, have you tried accessing them with a root Nautilus? That's a bit of a blunt hammer, but it might work. From a terminal...

```
gksudo nautilus
```If you manage to copy them that way, you'll have to chown them to your ownership once they're on your Ubuntu partition, since they'll now be owned by root.

**Edit:** just had another thought. I use an external HD formatted hfs+ unjournalled to transfer large files from MacOS to Ubuntu. It's just a data partition with folders of my own choosing and I've occasionally run into permissions problems - sometimes not. The permissions that MacOS sets seem to vary according to what mood it's in. :? Anyway, if I'm remembering this correctly, I found that I had to modify the permissions for the whole hierarchy of folders that my files were in before I could navigate up the folder tree without hindrance in Ubuntu. Which means that you might have to do the same for your home in MacOS - which would be a very bad idea. Something else to think about.

> **jrrader said:**
> This is more of a Mac issue than an Ubuntu issue.  Try asking in the [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328") forum and you're more liketly to get the help you need.

You can click on the report button and ask a mod to move a thread to another forum - in this case to the Apple subforum. I won't because the OP can use the report button on his/her own post if he/she wants. The report button isn't just for problematic posts. Move requests are a valid use.

---

### Post by linuxnovice on 2009-11-27
> **renegadespork said:**
> I have an extensive library of movies/music in my home folder in OSX, but I can't seem to access them in Ubuntu. I can mount my "Macintosh HD" fine, but when I navigate to my home folder, most of the sub folders are locked ("Music" "Pictures" "Movies" "Desktop" "Library" etc).

I went into OSX (10.5 Leopard) and changed the permissions on these folders (and all of their contents) for "everyone" to "read and write". However, when I try to access them back in Ubuntu, they are still locked. Any suggestions?

Hi,

I have this issue as well. And I tried as root, no luck. Any other suggestions?

Thanks.

---

### Post by renegadespork on 2011-05-09
> **coffeecat said:**
> When you mean access, do you mean simply copy them off, or do you mean modify/write to them in some way? Because you'll only be able to read them in Ubuntu. Your Leopard HD will almost certainly be formatted with the journalled version of hfs+, for which there are only read-only drivers in Linux. You can write to non-journalled hfs+ in Ubuntu, but it's exceedingly unlikely that your Leopard HD is non-journalled.

But if you can't access the files even for a read, that's curious. One problem would be that your Mac UID and Ubuntu UID will be different. For the first created user the UID in Ubuntu is 1000. Iirc, it's 501 in MacOS. Whatever, it's different. But by changing the permissions to read and write for everyone - which was basically a chmod - you should have made the Unix-permission system allow you read access in Ubuntu.

If you can't access the files even read-only, have you tried accessing them with a root Nautilus? That's a bit of a blunt hammer, but it might work. From a terminal...

```
gksudo nautilus
```If you manage to copy them that way, you'll have to chown them to your ownership once they're on your Ubuntu partition, since they'll now be owned by root.

**Edit:** just had another thought. I use an external HD formatted hfs+ unjournalled to transfer large files from MacOS to Ubuntu. It's just a data partition with folders of my own choosing and I've occasionally run into permissions problems - sometimes not. The permissions that MacOS sets seem to vary according to what mood it's in. :? Anyway, if I'm remembering this correctly, I found that I had to modify the permissions for the whole hierarchy of folders that my files were in before I could navigate up the folder tree without hindrance in Ubuntu. Which means that you might have to do the same for your home in MacOS - which would be a very bad idea. Something else to think about.


I mean I can't even look inside the folders let alone read/write/copy. When I navigate my way into "Machintosh HD/Users/[myusername]/", many of the folders display icons of folders with an 'x' on them. When I try to open these folders, I get the following error message: "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "[folder I'm trying to open]".

I apologize for the severely delayed follow-up, but Ubuntu has broken several times upon updating (due to a different issue) and I gave up on it for a while. I finally got the OS working again, but I'm still encountering the same permissions problem.

---

### Post by coffeecat on 2011-05-09
> **renegadespork said:**
> I mean I can't even look inside the folders let alone read/write/copy. When I navigate my way into "Machintosh HD/Users/[myusername]/", many of the folders display icons of folders with an 'x' on them. When I try to open these folders, I get the following error message: "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "[folder I'm trying to open]".

I wasn't entirely clear 18 months ago! :wink:

The folders you can't open will not have access permission for those other than your account in MacOS. You'll have to change the permissions in your Mac desktop. You do that in right-click > Get Info in MacOS. At the bottom of the get info window you'll see the permissions. Those folders set up already in a default installation of MacOS will probably have permissions set so that anyone apart from the account holder can't access the folder. For example, in my Mac the Documents and Pictures folders show this:

```
Name             Privilege
Me               Read and Write
everyone         No access
```But folders I have created myself show this:

```
Name             Privilege
Me               Read and Write
everyone         Read only
```Were I to access those from Ubuntu, the former would show the x that you see and I would not be able to open the folder. The latter I would be able to access. You have to change the permissions for everyone in anything like the former using the Get Info window in MacOS.

Whatever you do you will never be able to write to them from Ubuntu for the reasons I explained earlier - Linux cannot write to the journallled version of hfs+. But if you can access the folders, you will be able to copy the contents so long as the permissions of individual files are suitable.

---

### Post by ian2000gsxr on 2011-08-05
Is there anyway to access the folders without having access to the Mac? 
For whatever reason the Mac hard drive of a user at work here will not boot in the Mac.
I booted a 2nd computer with a liveCD but am having the same troubles as the user above...I can see the drive and mount it but can't access the X'd out folders and those happen to be where the data I need is.
Any help you could provide would be great.
Thanks,
Ian

---

### Post by decoherence on 2011-08-05
Macs are funny animals and I've had various problems connecting to them over the years. I've found the best method (as in, the one that usually works) is to use ssh as a go-between. Enable ssh on your Mac then connect to it with Nautilus. Nautilus can treat the ssh session as if it were a regular filesystem and, since you are logging in as the user on your Mac, you won't have any permissions issues.

---

