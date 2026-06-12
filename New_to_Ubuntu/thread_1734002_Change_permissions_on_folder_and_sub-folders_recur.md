---
title: "Change permissions on folder and sub-folders recursively using GUI"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Alan5127 on 2011-04-19
Hi All,
 
I have a brand new install of Ubuntu 10.10.
 
I am now setting up a data store that will, eventually, be used by multiple users.
 
I have two physical 500 GB drives in the machine, one of which has the OS partition, a swap partition (virtual memory?), and a data partition (Data1), and the other is purely for data (Data2).
 
I had copied some files and dorectories into Data1, but when I set it up, I used NTFS since I will be needing some Windows clients to access that partition and I figured they would not be able to read Ext4.
 
I then discovered that Ubuntu can't apply permissions to NTFS partitions, and my other users wouldn't be able to access it, so I used GParted to change it to Ext4, as upon reflection, I figured the data store would be 'shared' and not read directly from client machines, so the format of the partition shouldn't matter to the clients.
 
Now I am able to access the permissions options (right click - properties - permissions), but when I changed the ownership of Data1 from Root to Alan, it only changed the partition itself (Data1), and all the files and directories underneath are still owned by Root (ie it didn't apply recursively despite me clicking on the 'Apply permissions to enclosed files' button).
 
I searched here and it looks like this can be done using the command line using CHMOD -R, but if possible I would like to learn how to do this by using the GUI (I will need to train other users, and the command line is not likely to go down well with users!)
 
So, question:
[INDENT]How do I recursively change the ownership of all the files and directories in Data1 from Root to Alan using the GUI?
[/INDENT]Thanks,
 
Alan.
[INDENT] 
[/INDENT]

---

### Post by mikewhatever on 2011-04-19
Training other users to change permissions is asking for trouble, especially those of the root user.
Why did you assume that other uses wouldn't be able to access files on NTFS?

---

### Post by Alan5127 on 2011-04-19
Hi Mike,
 
Thanks for replying.
 
 
> **mikewhatever said:**
> Training other users to change permissions is asking for trouble, especially those of the root user.

 
I want the users to learn how to use the system fully - locking them out of things will restrict their learning opportunities and as long as I have overall admin access, the worst they can do is come to me to ask to fix a problem.
 
It has worked well on Windows for some time (e.g. my nine year old daughter knows about 'security' settings on her personal 'drive' in Windows (actually her 'My Docs' folder mapped onto an old Windows Server 2003), so now wanting to migrate to Ubuntu too and keep the learning going.
 
 
> **mikewhatever said:**
> 
Why did you assume that other uses wouldn't be able to access files on NTFS?

 
Any number of posts here state that Ubuntu is unable to set permissions on NTFS volumes, and I had no reason to figure they would be wrong, but to be honest the NTFS thing is a moot point as the partition is now Ext4 and unless absolutely necessary, I'd rather stick with that as being Ubuntu's native format.
 
 
 
Any idea on how to recursively apply permission changes to all files and directories using the GUI?
 
 
Thanks,
 
Alan.

---

### Post by mikewhatever on 2011-04-19
I don't know of any other GUI way other then the 'Apply permissions to enclosed files' button. It's either broken, or you've done something wrong. Did you launch Nautilus as root when modifying permissions?

---

### Post by earthpigg on 2011-04-19
you may find this to be an indirect solution, but an alternative file manager to the default 'nautilus' is called 'pcmanfm'. installing it will have no effect on nautilus.

when you change a folder's permissions in pcmanfm, it asks you;

> Do you want to recursively apply these changes to all files and sub-folders?
and, it works.

nautilus is a bit easier to use, but i prefer pcmanfm for certain 'heavy lifting' stuff. my 'music' folder, for example has over 3,000 files and is over 15gb, but opens instantly in pcmanfm. that same task takes several minutes with nautilus.

---

### Post by Alan5127 on 2011-04-19
Hi Mike,

> **mikewhatever said:**
> I don't know of any other GUI way other then the 'Apply permissions to enclosed files' button. It's either broken, or you've done something wrong. Did you launch Nautilus as root when modifying permissions?

Just tried that (command prompt - sudo nautilus), but it still doesn't recurse.

Is there another way to run a command as root?

Thanks,

Alan.

---

### Post by Alan5127 on 2011-04-19
Hi EarthPigg,

> **earthpigg said:**
> you may find this to be an indirect solution, but an alternative file manager to the default 'nautilus' is called 'pcmanfm'. installing it will have no effect on nautilus.

when you change a folder's permissions in pcmanfm, it asks you;


and, it works.

nautilus is a bit easier to use, but i prefer pcmanfm for certain 'heavy lifting' stuff. my 'music' folder, for example has over 3,000 files and is over 15gb, but opens instantly in pcmanfm. that same task takes several minutes with nautilus.


Just tried installing PCManFM, but it says the install failed with the following error stream:

[QUOTE=Ubuntu 10.10 Intaller]

installArchives() failed: Selecting previously deselected package pcmanfm. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 159206 files and directories currently installed.) 
Unpacking pcmanfm (from .../pcmanfm_0.9.7-1ubuntu1_i386.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_NZ.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up language-selector-common (0.6.7) ... 
dpkg: error processing language-selector-common (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of language-selector: 
 language-selector depends on language-selector-common (= 0.6.7); however: 
  Package language-selector-common is not configured yet. 
dpkg: error processing language-selector (--configure): 
 dependency problems - leaving unconfigured 
Setting up pcmanfm (0.9.7-1ubuntu1) ... 
No apport report written because MaxReports is reached already
Processing triggers for python-central ... 
Errors were encountered while processing: 
 language-selector-common 
 language-selector 
Setting up language-selector-common (0.6.7) ... 
dpkg: error processing language-selector-common (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of language-selector: 
 language-selector depends on language-selector-common (= 0.6.7); however: 
  Package language-selector-common is not configured yet. 
dpkg: error processing language-selector (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 language-selector-common 
 language-selector 

[/QUOTE]


Gets better and better [-(

Alan.

---

### Post by earthpigg on 2011-04-21
yes, that is a problem. has your new zealand language selection ever been a problem, before (from "esktop.en_NZ.UTF8.cache...")?

anything you may have done that could have influenced this, by chance?

my first reaction would be to try typing this:

```
sudo dpkg --configure language-selector-common
```

based mostly on reading this:

```
dpkg: dependency problems prevent configuration of language-selector:
language-selector depends on language-selector-common (= 0.6.7); however:
Package language-selector-common is not configured yet. 
```

or you could give this a shot:

```
sudo dpkg-reconfigure language-selector-common
```


if that doesn't do it, i'd probably open a thread specifically with that error message, and link back to this thread.

(to ensure people really good at fixing dpkg problems see it and can help you. i am very mediocre at that.)

---

### Post by Alan5127 on 2011-04-21
Hi EarthPigg,

> **earthpigg said:**
> yes, that is a problem. has your new zealand language selection ever been a problem, before (from "esktop.en_NZ.UTF8.cache...")?

anything you may have done that could have influenced this, by chance?



Not in the two days since I first decided to try Linux :(

I can't think of anything that I could have done to cause the error.  Perhaps the regionalisation is not very well developed either within the OS or more likely within that specific application, and the author(s) didn't think about it?

It is the second ever application I have installed into Linux (VirtualBox being the first).


> **earthpigg said:**
> 

my first reaction would be to try typing this:

```
sudo dpkg --configure language-selector-common
```based mostly on reading this:

```
dpkg: dependency problems prevent configuration of language-selector:
language-selector depends on language-selector-common (= 0.6.7); however:
Package language-selector-common is not configured yet. 
```

Before I do that, please could you explain what it does?

> **earthpigg said:**
> 

or you could give this a shot:

```
sudo dpkg-reconfigure language-selector-common
```

and that too .... :)

> **earthpigg said:**
> 


if that doesn't do it, i'd probably open a thread specifically with that error message, and link back to this thread.

(to ensure people really good at fixing dpkg problems see it and can help you. i am very mediocre at that.)

Okay - let's stick with it here first, but noted.

Thanks,

Alan.

---

### Post by nothingspecial on 2011-04-21
> **Alan5127 said:**
> 
 
I want the users to learn how to use the system fully - locking them out of things will restrict their learning opportunities and as long as I have overall admin access, the worst they can do is come to me to ask to fix a problem.
 


The worst they can do is completely hose the system. And loose all your data. If you are going to give your 9 year old daughter an admin account, make sure you have backups of everything.

---

### Post by Alan5127 on 2011-04-21
Hi nothingspecial,
 
> **nothingspecial said:**
> The worst they can do is completely hose the system. And loose all your data. If you are going to give your 9 year old daughter an admin account, make sure you have backups of everything.
 
I'm at a bit of a loss to see how she could achieve that with such limited access as controlling the security on her own files.
 
I have little idea (yet) how Ubuntu works, but she doesn't need full admin access to do that in Windows, so I would guess it isn't necessary under Ubuntu either. From what little I have read so far, Linux has a reasonably well developed security structure, so your concerns are likely overstated, but perhaps best to post a specific query in a new thread for someone better informed to help you as I cannot confirm.
 
HTH,
 
Alan.

---

### Post by nothingspecial on 2011-04-21
First you said you wanted to change the ownership of a newley formatted file system from root to your user.

Then you said you wanted a gui method because you wanted to show other users how to do it.

Then you mentioned your 9 year old daughter.

Because root (or yourself with sudo) has to format the partition root will own it. Therefore only root or an admin account can change that ownership.

For your daughter to be able to do that she will need root privaleges (sudo enabled on her account).

This is where things can go wrong

To change ownership of your data partition you would do this

```
sudo chown -R $USER:$USER /media/Data1
```

($USER is an environment variable for the current user)

**[COLOR="Red"][SIZE="3"]DON'T TYPE THIS NEXT BIT[/SIZE][/COLOR]** 

This is just to show you how easy it is to make a monumental cockup with root. If she typed

**[COLOR="Red"][SIZE="3"]REALLY, DON'T TYPE THIS[/SIZE][/COLOR]**
```
sudo chown -R $USER:$USER / media/Data1

```

Your system would be toast. The only difference is the space after the initial /
The result would be that she would change every file and folder in the entire system to be owned by her user and that is pretty much unrecoverable from.

---

### Post by nothingspecial on 2011-04-21
Rereading your original post I think I see where the confusion lies.

No user can change the ownership of files without sudo.

I think you are refering to read write and execute permissions which is different to ownership.

She should be able to do this with her own files recursively with nautilus. With a non admin account.

But she can't change who owns them.

---

### Post by Morbius1 on 2011-04-21
I am very confused by this post.
> I then discovered that Ubuntu can't apply permissions to NTFS  partitionsLinux cannot change ownership or permissions on an NTFS partition after it's mounted. Linux can change ownership and permissions on an NTFS at the moment of mount with either a specific mount command or preferably by adding a line to /etc/fstab so that it automounts with the desired permissions.
> I used  GParted to change it to Ext4, as upon reflection, I figured the data  store would be 'shared' and not read directly from client machines, so  the format of the partition shouldn't matter to the clients.Can't quite figure out if this "shared" partition is shared among local login users or across the network. Since it's now ext4 this can be somewhat complicated if it's to be shared among local users depending on what your definition of shared means ( there are at least 6 different variations of the meaning of shared in this context ).

In any event the 'Apply permissions to enclosed files' option has a long an infamous history of fluctuating between a working and a non-working state over the years. Probably why most folks ended up doing it by the terminal.

---

### Post by Sidewinder1 on 2011-04-21
nothingspecial, may I respectfully prevail upon your time and request that you go into a little more detail as to the ramifications of the above; "The only difference is the space after the initial /", as I have used chown (successfully with my 5 external drives :D) and am surprised that I never made that space screw-up. I then learned to copy-paste commands to minimize my clumsy  typing fingers. How does chown interpret that errant "space"?

And just so I will not be totally hijacking this thread...
To the OP, it is customary and highly recommended to use:

```
gksudo
``` 

(not sudo), when accessing a 'GUI' program such as nautilus. Please see the link below for a full explanation.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Side

---

### Post by nothingspecial on 2011-04-21
> **Sidewinder1 said:**
> nothingspecial, may I respectfully prevail upon your time and request that you go into a little more detail as to the ramifications of the above; "The only difference is the space after the initial /", as I have used chown (successfully with my 5 external drives :D) and am surprised that I never made that space screw-up. I then learned to copy-paste commands to minimize my clumsy  typing fingers. How does chown interpret that errant "space"?

And just so I will not be totally hijacking this thread...
To the OP, it is customary and highly recommended to use:

```
gksudo
``` 

(not sudo), when accessing a 'GUI' program such as nautilus. Please see the link below for a full explanation.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Side

Bash does what it's told to do left to right (in the main). It doesn't read the whole line first.

So with the space, the first thing bash sees is change the ownership of / and everything in it to $USER. That's the whole system. After it has done that it will tell you that media/Data1 doesn't exist.

---

### Post by Alan5127 on 2011-04-21
Hi nothingspecial,
 
> **nothingspecial said:**
> Rereading your original post I think I see where the confusion lies.
 
No user can change the ownership of files without sudo.
 
I think you are refering to read write and execute permissions which is different to ownership.
 
She should be able to do this with her own files recursively with nautilus. With a non admin account.
 
But she can't change who owns them.
 
 
Yep - apologies for my use of the wrong terminology.
 
I definitely want to be able to recursively change the permissions to read+write (for example).
 
I still cannot get this to work with Nautilus though - clicking the 'Apply permissions to enclosed files' button doesn't seem to do anything.
 
As I mentioned above, when I tried to install the suggested File Manager application, it gave that error message - an inauspicious start for me with Linux :( - at least it can only get better (he says!)
 
 
I'll wait to see if EarthPigg responds here before taking that issue to a new thread.
 
Thanks,
 
Alan.

---

### Post by Alan5127 on 2011-04-21
Hi Side,
 
> **Sidewinder1 said:**
> 
 
nothingspecial, may I respectfully prevail upon your time and request that you go into a little more detail as to the ramifications of the above; "The only difference is the space after the initial /", as I have used chown (successfully with my 5 external drives :D) and am surprised that I never made that space screw-up. I then learned to copy-paste commands to minimize my clumsy typing fingers. How does chown interpret that errant "space"?
 
And just so I will not be totally hijacking this thread...
To the OP, it is customary and highly recommended to use:
 
```
gksudo
``` 
 
(not sudo), when accessing a 'GUI' program such as nautilus. Please see the link below for a full explanation.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
 
Side
 

 
Thanks for that.
 
Once advantage of being new to Linux is that I don't have too many bad habits yet!
 
I'll just use```
gksudo
```if launching a GUI app.
 
Thanks,
 
Alan.

---

### Post by Sidewinder1 on 2011-04-21
Glad to've helped!
It's like the old adage: "Experience is the best teacher; only problem is that she's damned expensive." :D

Side

---

### Post by Alan5127 on 2011-04-21
Hi Morbius1,
 
> **Morbius1 said:**
> 
 
I am very confused by this post.
Linux cannot change ownership or permissions on an NTFS partition after it's mounted. Linux can change ownership and permissions on an NTFS at the moment of mount with either a specific mount command or preferably by adding a line to /etc/fstab so that it automounts with the desired permissions.
 

 
Gone way over my head there :-)
 
I searched the issue and found quite a few posts from people saying that Ubuntu cannot use permissions on NTFS - I had no reason to think they would be wrong, so I decided to get rid of NTFS and go to Ext4 since that (apparently) is the 'native' format for Ubuntu. I could be wrong at any point in that of course.
 
 
> **Morbius1 said:**
> 
Can't quite figure out if this "shared" partition is shared among local login users or across the network. Since it's now ext4 this can be somewhat complicated if it's to be shared among local users depending on what your definition of shared means ( there are at least 6 different variations of the meaning of shared in this context ).
 

 
I was meaning shared both among local users on the Ubuntu machine, and also with other machines on my network (mainly that would be a WinXP Pro SP3 machine that is in the family room).
 
> **Morbius1 said:**
> 
 
In any event the 'Apply permissions to enclosed files' option has a long an infamous history of fluctuating between a working and a non-working state over the years. Probably why most folks ended up doing it by the terminal.
 
The default file manager for the OS has a button that doesn't always work :confused:
 
 
Alan.

---

### Post by nothingspecial on 2011-04-21
You need to do gksudo nautilus first to change the drive to be owned by you.

Then still in root nautilus you need to create her directory then change it to be owned by your daughter.

Remember you need to be root to change the ownership.

Once that is done close nautilus and she should be able to change permissions within her folder.

---

### Post by Sidewinder1 on 2011-04-21
Thanks ns! I should've realized that / would mean root; duh to me. Sometimes I fail to see the forest for the trees. :)

Side

---

### Post by collisionystm on 2011-04-21
> **Alan5127 said:**
> Hi All,
 
I have a brand new install of Ubuntu 10.10.
 
I am now setting up a data store that will, eventually, be used by multiple users.
 
I have two physical 500 GB drives in the machine, one of which has the OS partition, a swap partition (virtual memory?), and a data partition (Data1), and the other is purely for data (Data2).
 
I had copied some files and dorectories into Data1, but when I set it up, I used NTFS since I will be needing some Windows clients to access that partition and I figured they would not be able to read Ext4.
 
I then discovered that Ubuntu can't apply permissions to NTFS partitions, and my other users wouldn't be able to access it, so I used GParted to change it to Ext4, as upon reflection, I figured the data store would be 'shared' and not read directly from client machines, so the format of the partition shouldn't matter to the clients.
 
Now I am able to access the permissions options (right click - properties - permissions), but when I changed the ownership of Data1 from Root to Alan, it only changed the partition itself (Data1), and all the files and directories underneath are still owned by Root (ie it didn't apply recursively despite me clicking on the 'Apply permissions to enclosed files' button).
 
I searched here and it looks like this can be done using the command line using CHMOD -R, but if possible I would like to learn how to do this by using the GUI (I will need to train other users, and the command line is not likely to go down well with users!)
 
So, question:
[INDENT]How do I recursively change the ownership of all the files and directories in Data1 from Root to Alan using the GUI?
[/INDENT]Thanks,
 
Alan.
[INDENT]
[/INDENT]
 
I am not sure what progress you have made so far, but may I make a suggestion that will save you a nightmare of headaches in your particular situation??
 
Use Zentyal
 
It is based on Ubuntu 10.04 and is  managed via the web with a very nice GUI. Users can add and delete shares, change permissions and groups all with the click of a button.
 
I think you may find it suits your needs very well..
 
I use it =)
 
[http://www.zentyal.com/](http://www.zentyal.com/)
 
It is available in the ubuntu respositores to install, but it only works on 10.04. Not 10.10 compatible...
 
Cheers

---

### Post by Morbius1 on 2011-04-21
> **Alan5127 said:**
> I searched the issue and found quite a few posts from people saying that Ubuntu cannot use permissions on NTFS - I had no reason to think they would be wrong, so I decided to get rid of NTFS and go to Ext4 since that (apparently) is the 'native' format for Ubuntu. I could be wrong at any point in that of course.
You didn't read enough posts by the right people. Here's an example of how you can mount an ntfs partition with specific ownership and permissions in fstab:
```
/dev/sda1 /media/WinXP ntfs defaults,uid=1000,gid=46,umask=007 0 0
```I've just mounted an ntfs partition with me (uid=1000) as owner and with permissions for me and all local login users ( gid=46 ) to read / write and with no permissions for anyone else (umask=007).
> I was meaning shared both among local users on the Ubuntu machine, and  also with other machines on my network (mainly that would be a WinXP Pro  SP3 machine that is in the family room).Please define shared:

(1) All users can add to or delete from the folder but only the owner can write ( edit ) a file?
(2) All users can add to but only the owner of the file can delete it and write ( edit ) is limited to only the owner?
(3) All users can add or delete and can also write to each others files?
(4) All users can add to but can only delete files they own and can read and write to every file?
(5) Same as (3) but only for a subset of the local users?
(6) Same as (4) but only for a subset of the local users?
> The default file manager for the OS has a button that doesn't always workYes
[COLOR=Blue]**EDIT:**[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/165113)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512)
[https://bugzilla.gnome.org/show_bug.cgi?id=352895](https://bugzilla.gnome.org/show_bug.cgi?id=352895)

---

### Post by Alan5127 on 2011-04-21
Hi nothingspecial,
 
> **nothingspecial said:**
> You need to do gksudo nautilus first to change the drive to be owned by you.
 
Then still in root nautilus you need to create her directory then change it to be owned by your daughter.
 
Remember you need to be root to change the ownership.
 
Once that is done close nautilus and she should be able to change permissions within her folder.
 
That's great, but it is what I tried (see my OP) with the exception of using sudo rather than gksudo which I hadn't heard of until this thread.
 
Creating a single directory and making it owned by whoever is no problem, but my question was how to change permissions recursively for the entire structure using the GUI given that nautilus doesn't seem to work.
 
 
Thanks,
 
Alan.

---

### Post by Alan5127 on 2011-04-21
Hi collisionystm,
 
> **collisionystm said:**
> I am not sure what progress you have made so far, but may I make a suggestion that will save you a nightmare of headaches in your particular situation??
 
Use Zentyal
 
It is based on Ubuntu 10.04 and is managed via the web with a very nice GUI. Users can add and delete shares, change permissions and groups all with the click of a button.
 
I think you may find it suits your needs very well..
 
I use it =)
 
[http://www.zentyal.com/](http://www.zentyal.com/)
 
It is available in the ubuntu respositores to install, but it only works on 10.04. Not 10.10 compatible...
 
Cheers
 
 
I'm persevering, but it does feel like wading through treacle right now :-)
 
I was anticipating going to 11.04 next week on the grounds that as a complete newbie, I might as well start on the latest and greatest, and if I don't move on for a while, I won't be too far behind.
 
Perhaps Zentyal will get upgraded to work with 11.04 shortly anyway....
 
Alan.

---

### Post by Alan5127 on 2011-04-21
Hi Morbius1,
 
> **Morbius1 said:**
> 
 
You didn't read enough posts by the right people. 
 

 
Probably right, but when you're starting out, you have no real way to discriminate, and multiple posts all seemed to say the same thing.
 
 
> **Morbius1 said:**
> 
 
Here's an example of how you can mount an ntfs partition with specific ownership and permissions in fstab:
```
/dev/sda1 /media/WinXP ntfs defaults,uid=1000,gid=46,umask=007 0 0
```I've just mounted an ntfs partition with me (uid=1000) as owner and with permissions for me and all local login users ( gid=46 ) to read / write and with no permissions for anyone else (umask=007).
 

 
Thanks for that, but as I mentioned above, it is moot now, since I moved it to a native Ubuntu Ext4 partition.
 
 
> **Morbius1 said:**
> 
 
Please define shared:
 
(1) All users can add to or delete from the folder but only the owner can write ( edit ) a file?
(2) All users can add to but only the owner of the file can delete it and write ( edit ) is limited to only the owner?
(3) All users can add or delete and can also write to each others files?
(4) All users can add to but can only delete files they own and can read and write to every file?
(5) Same as (3) but only for a subset of the local users?
(6) Same as (4) but only for a subset of the local users?
 

 
I would like to go for '3 - All users can add or delete and can also write to each others files' for now at least, but also being able to 'share' the directory and sub-tree with those users when they are logged into other clients (with the same username and password).
 
 
HTH,
 
Alan.

---

### Post by nothingspecial on 2011-04-22
> **Alan5127 said:**
> Hi nothingspecial,
 

 
That's great, but it is what I tried (see my OP) with the exception of using sudo rather than gksudo which I hadn't heard of until this thread.
 
Creating a single directory and making it owned by whoever is no problem, but my question was how to change permissions recursively for the entire structure using the GUI given that nautilus doesn't seem to work.
 
 
Thanks,
 
Alan.
 
I would use chown -R (bear in mind linux is case sensitive) on Data1 then try nautilus after that. No harm in you yourself learning a few admin commands.

---

### Post by Morbius1 on 2011-04-22
> I would like to go for '3 - All users can add or delete and can also write to each others files' for now at least,[1] Change group ownership of Data1 to plugdev:
```
sudo chown :plugdev /media/Data1
```[2] set the group id bit for Data1
```
sudo chmod 2775 /media/Data1
```[3] Change the default umask value for all local login users:
Edit /etc/profile as root:
```
gksu gedit /etc/profile
```At the bottom of that file change the umask value to 002:
```
umask 002
```[COLOR=Blue]*Logout and login again since the profile is read only once at login.*[/COLOR]

Notes:
The "2" in "chmod 2775" in combination with the setting of the group will force every new folder / file to "inherit" the group plugdev. All local users in Ubuntu are members of the plugdev group by default.

The umask change will force every new folder / file to save with permissions of 775 / 664 instead of the default of 755 / 644.

The result should be that for every new file added every local user will be able to read and write to that file.

As for the chown -R vs GUI question it has already been answered. Change the ownership of the existing files to yourself first using
```
 sudo chown -R username:plugdev /media/Data1
```then follow the steps above. If you would like you might want to add your voice to the bug reports I mentioned in my last post.

---

### Post by Alan5127 on 2011-04-22
Hi Morbius1,
 
> **Morbius1 said:**
> [1] Change group ownership of Data1 to plugdev:
```
sudo chown :plugdev /media/Data1
```[2] set the group id bit for Data1
```
sudo chmod 2775 /media/Data1
```[3] Change the default umask value for all local login users:
Edit /etc/profile as root:
```
gksu gedit /etc/profile
```At the bottom of that file change the umask value to 002:
```
umask 002
```[COLOR=blue]*Logout and login again since the profile is read only once at login.*[/COLOR]
 
Notes:
The "2" in "chmod 2775" in combination with the setting of the group will force every new folder / file to "inherit" the group plugdev. All local users in Ubuntu are members of the plugdev group by default.
 
The umask change will force every new folder / file to save with permissions of 775 / 664 instead of the default of 755 / 644.
 
The result should be that for every new file added every local user will be able to read and write to that file.
 
As for the chown -R vs GUI question it has already been answered. Change the ownership of the existing files to yourself first using
```
 sudo chown -R username:plugdev /media/Data1
```then follow the steps above. If you would like you might want to add your voice to the bug reports I mentioned in my last post.
 
 
Out of interest, why 'plugdev'?
 
I had a look through the default groups, and there is one called 'users' - if you hadn't suggested otherwise, that would have seemed the obvious choice?
 
Thanks,
 
Alan.

---

### Post by Morbius1 on 2011-04-22
Already answered that question:
> All local users in Ubuntu are members of the plugdev group by default.
Open a terminal and type:
```
id
```
It will show you every group you are a member of and on my system I am a member of plugdev. I am not a member of users.

You can make it users if you want but then you will need to add every local user to the "users" group for this to work.

---

### Post by Alan5127 on 2011-04-22
Hi Morbius1,
 
> **Morbius1 said:**
> Already answered that question:
 
Open a terminal and type:
```
id
```
It will show you every group you are a member of and on my system I am a member of plugdev. I am not a member of users.
 
You can make it users if you want but then you will need to add every local user to the "users" group for this to work.
 
Sorry - I did read that bit, but I (wrongly!) figured that 'users' would be all users.
 
So what is 'users' for?
 
Also, does any new user I ever create, automatically get added to 'plugdev', but not to 'users'?
 
Thanks,
 
Alan.

---

### Post by nothingspecial on 2011-04-23
> **Alan5127 said:**
> 
 
does any new user I ever create, automatically get added to 'plugdev', but not to 'users'?
 

No

---

### Post by Morbius1 on 2011-04-23
> **nothingspecial said:**
> > Originally Posted by **Alan5127**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10708520#post10708520")                 
                 [I] 
does any new user I ever create, automatically get added to 'plugdev', but not to 'users'?[/I]
No
The correct answer is: it depends ;)

If you add the new user the Unix way: "sudo adduser bob", then nothingspecial is correct:
> id bob
uid=1002(bob) gid=1002(bob) groups=1002(bob)If you add the new user the GUI way: Administration > Users and Groups > Add > bob, then the answer is yes:
> id bob
uid=1002(bob) gid=1002(bob) groups=1002(bob),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),30(dip),44(video),[COLOR=Blue]**46(plugdev)**[/COLOR],104(fuse)[COLOR=Blue]EDIT: I made a guess that most folks are adding new users via the GUI.[/COLOR] If you add them via the command line then you need to add a given user to the group:
```
 sudo gpasswd -a user2 plugdev
```You can also use this technique to create a share that is accessible to a subset of local users with no access to anyone else. For example:
Create a group for the parents:
```
sudo groupadd parents
```Add the parents to the group:
```
sudo gpasswd -a dad parents
```Then:
 ```
sudo chown :parents /media/Data1
sudo chmod 2770 /media/Data1
```Now only mum and dad can access the folder .

---

### Post by nothingspecial on 2011-04-23
> **morbius1 said:**
> i made a guess that most folks are adding new users via the gui.

:p

---

