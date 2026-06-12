---
title: "copy files to windows"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by frumbert on 2009-11-29
Hi
A friend of mine set up my Mythbuntu box and for a while MythTV worked quite nicely. I have not got a CLUE about linux, and I don't really want to. That's why a friend did it and not me. I do know that that /var/lib was mounted as "the large partition", which was something like 900GB (Yay for taking notes!). Anyway, my friend has moved away from town and basically I can't do this over the phone.

Its recently run an "auto update" or something and ruined everything. My friend did do an initial "backup" but I have no idea what that means and that was months ago now, so I have no idea how to restore anything. I don't have sound or network anymore (and I recall these being hair-pulling-out experiences to get going), and mythtv settings are all over the place. I want to get my stuff back out first, and then format it all and start again.

It's not really a bad thing. I basically don't watch TV anymore because there's very little I enjoy on anymore (Australian TV sucks if you don't like cop shows). I also hated the music interface to the point where I've gone back to have CD's in my living room because it was just easier. No biggie there.

I have a QNAP NAS box to do my downloads and have been manually moving them from the torrent folder over the network to the mythbuntu box using my Windows 7 box. This seems horribly slow, and now I don't have the space to move them all back (plus now the network on the linux box is stuffed so I can't! Bummer). I also don't know if there would have been a better way to organise that download stuff so it was all automatic. I'm just going with what I know.

In trying to get my files back, I tried to use a thing for windows that let me mount Linux file systems, but it said the partition was "RAW" (not EXT2/EXT3) and needed to be formatted! Aargh! But it boots fine in linux and the data is all there if I open it in Thunar manager thingy. I tried two different programs (one a control panel, the other a driver or something). Neither gave me any success.

I'd like to be able to put in a NTFS formatted 1TB drive while linux is running and copy all the data from /var/lib/mythtv including the recorded tv, music and videos, so I can pop it back in my Windows box. I need to copy about 700GB of files.  I don't know if it's possible, what I would need (and I mean exact instructions with every single command so I can print it out, because I do NOT know a thing about how to access stuff or what all those folders mean). Internal would be ideal since it's faster, but I could hook it up to an external USB as well if I knew how to make the windows drive come up as an icon.

Can someone please let me know if it's possible or suggest what I can do (clearly, please).

---

### Post by u.b.u.n.t.u on 2009-11-29
> **frumbert said:**
> Hi
A friend of mine set up my Mythbuntu box and for a while MythTV worked quite nicely. I have not got a CLUE about linux, and I don't really want to. That's why a friend did it and not me. I do know that that /var/lib was mounted as "the large partition", which was something like 900GB (Yay for taking notes!). Anyway, my friend has moved away from town and basically I can't do this over the phone.

Its recently run an "auto update" or something and ruined everything. My friend did do an initial "backup" but I have no idea what that means and that was months ago now, so I have no idea how to restore anything. I don't have sound or network anymore (and I recall these being hair-pulling-out experiences to get going), and mythtv settings are all over the place. I want to get my stuff back out first, and then format it all and start again.

It's not really a bad thing. I basically don't watch TV anymore because there's very little I enjoy on anymore (Australian TV sucks if you don't like cop shows). I also hated the music interface to the point where I've gone back to have CD's in my living room because it was just easier. No biggie there.

I have a QNAP NAS box to do my downloads and have been manually moving them from the torrent folder over the network to the mythbuntu box using my Windows 7 box. This seems horribly slow, and now I don't have the space to move them all back (plus now the network on the linux box is stuffed so I can't! Bummer). I also don't know if there would have been a better way to organise that download stuff so it was all automatic. I'm just going with what I know.

In trying to get my files back, I tried to use a thing for windows that let me mount Linux file systems, but it said the partition was "RAW" (not EXT2/EXT3) and needed to be formatted! Aargh! But it boots fine in linux and the data is all there if I open it in Thunar manager thingy. I tried two different programs (one a control panel, the other a driver or something). Neither gave me any success.

I'd like to be able to put in a NTFS formatted 1TB drive while linux is running and copy all the data from /var/lib/mythtv including the recorded tv, music and videos, so I can pop it back in my Windows box. I need to copy about 700GB of files.  I don't know if it's possible, what I would need (and I mean exact instructions with every single command so I can print it out, because I do NOT know a thing about how to access stuff or what all those folders mean). Internal would be ideal since it's faster, but I could hook it up to an external USB as well if I knew how to make the windows drive come up as an icon.

Can someone please let me know if it's possible or suggest what I can do (clearly, please).

Yeah Australian TV is full of trash. I like the ABC and get that for free online with my ISP account iiNet. Some others ISPs provide a similar service.

[http://www.abc.net.au/tv/iview/](http://www.abc.net.au/tv/iview/)

There are many possible approaches and the one I would take is the following. Using a Ubuntu CD boot live, then access both HDDs, and make a cuppa while you transfer your 700GB of data.

Does that solve the problem?

Cheers

---

### Post by kevdog on 2009-11-29
How about installing the sshd and using sftp to transfer the files.

---

### Post by frumbert on 2009-11-29
> **kevdog said:**
> How about installing the sshd and using sftp to transfer the files.

A] I don't know what sshd is.

B] I don't know what fstp is.

Did you miss the part where I said (to effect) "You would have to tell me in painstaking detail each step? Unfortunately your answer represents the problem I have with asking questions on linux forums - people blurt out answers expecting everyone else to have the same knowledge as them. I apologise for not having the same education as you.

> **u.b.u.n.t.u said:**
> 

There are many possible approaches and the one I would take is the following. Using a Ubuntu CD boot live, then access both HDDs, and make a cuppa while you transfer your 700GB of data.

Does that solve the problem?

Cheers

Thanks I hadn't thought of this. However - hours later after downloading and building the CD I find that it can't copy the files because it has a warning on screen, which says:

"The file XX cannot be handled because you do not have permission to read it."

What permission is this and how does one set it?

---

### Post by quinnten83 on 2009-11-29
> **frumbert said:**
> A] I don't know what sshd is.

B] I don't know what fstp is.

Did you miss the part where I said (to effect) "You would have to tell me in painstaking detail each step? Unfortunately your answer represents the problem I have with asking questions on linux forums - people blurt out answers expecting everyone else to have the same knowledge as them. I apologise for not having the same education as you.



And this is the problem with many newbie posters on Linux forums.
They give too much attitude and expect those that know a bit more to not get miffed and still help. Got news for you, you are the one with the problem, not us. He didn't answer in a manner that you could follow, how about politely pointing that out to him instead of giving a smart@$$ remark. I wouldn't be surprised if he thought now you should shove it and he goes about doing something productive with his time.

Anyhow.
I think it is strange that you say that your data is in /var/lib, since usually the /var directory is a directory for system files that the operating system, in this case mythtv, uses to run or keep logs.
But then again I have no experience with mythtv.

Perhaps if you tell us a bit more about what kind of computer you have where the mythtv is running. Is there a filebrowswer on it? Perhaps a directory called home?
can you open a terminal? which version of myth are you running? Is it mythbuntu? Is this mythbox even installed on a *buntu linux?
a little more information about your setup goes a long way in helping us help you. If possible have your friend jump in and explain.

And really can it with the snarky attitude...

---

### Post by quinnten83 on 2009-11-29
if you are using the life CD.
try the following.
press alt+F2
in the run dialog box type "gnome-terminal" without the "".
in the doslike windows that pops up type: gksudo nautilus
A file browser à la Windows explorer will open, this one should have the rights to let you copy whatever you want.

---

### Post by frumbert on 2009-11-29
> **quinnten83 said:**
> 
I think it is strange that you say that your data is in /var/lib, since usually the /var directory is a directory for system files that the operating system, in this case mythtv, uses to run or keep logs.
But then again I have no experience with mythtv.


That's what I had written on my peice of paper. I don't know what it means. I am used to working with an ICON for hard drives, so making a hard drive or partition or whatever into some folder is news to me. But as I said someone more knowledgable than I set this up not me.

> **quinnten83 said:**
> 
Perhaps if you tell us a bit more about what kind of computer you have where the mythtv is running. Is there a filebrowswer on it? Perhaps a directory called home?
can you open a terminal? which version of myth are you running? Is it mythbuntu? Is this mythbox even installed on a *buntu linux?


Why, yes. It's mythbuntu. It says that within the first few words of my original post. Mythbuntu seems to have a menu at the top of the desktop part with about 10 things in it and says Application at the top. There's a terminal program, and a thunar file manager. Yes there is a home folder. It's empty. There are no other icons or anything on the bar at the top, just that menu. I don't recall there being any option to choose what I get with mythbuntu. Does this help you know what version? I'm sorry but there isn't a big fat thing on screen that says "Hello I'm version X", so I don't know. This has JUST WORKED in the past so I don't care about things like that. Now it seems to be screwed and I don't know what to do. So I am explaining to this community that the mythbuntu web site has directed me to what my experience level is and what I want to happen just in case there is someone with the knowledge to help me out.

> **quinnten83 said:**
> 
a little more information about your setup goes a long way in helping us help you. If possible have your friend jump in and explain.


Yes, great except that as I carefully explained at the start "my friend has moved away from town and basically I can't do this over the phone" - he doesn't remember the setup so can't really tell me. He said he could log into it if I could set up some router or something but as I carefully explained in my initial post "the network on the linux box is stuffed so I can't!".

Hope this clears things up for you.

---

### Post by u.b.u.n.t.u on 2009-11-29
> **frumbert said:**
> 

Thanks I hadn't thought of this. However - hours later after downloading and building the CD I find that it can't copy the files because it has a warning on screen, which says:

"The file XX cannot be handled because you do not have permission to read it."

What permission is this and how does one set it?

Your ISP sounds pretty bad. Check out this forum for more info about what is available in Australia.

[http://forums.whirlpool.net.au/forum-threads.cfm?f=72](http://forums.whirlpool.net.au/forum-threads.cfm?f=72)

The top three in my view are iiNet, Internode, TPG. The worst three are Telstra, Optus, Primus.

As to the permission error, I would suggest enabling root also known as administrator. That should enable all permissions.

Open the terminal and type in the following:

```
sudo su
```

To leave this mode type in:

```
exit
```

Please note that as a general rule, root should only be enabled on a temporary basis, specific to a task at hand. Seeing you have a critical problem, an exception to this wise computing rule is needed.

Once all is working again, use sudo if and when needed.

I agree with quinnten83 that it is rather strange to have your personal files what equates to in Microsoft terms as "Program Files". Still getting things sorted should come before learning a bit more about Linux.

---

### Post by SuperSonic4 on 2009-11-29
> **frumbert said:**
> [COLOR="Red"]SS4: tl;dr[/COLOR]

I'd like to be able to put in a NTFS formatted 1TB drive while linux is running and copy all the data from /var/lib/mythtv including the recorded tv, music and videos, so I can pop it back in my Windows box. I need to copy about 700GB of files.  I don't know if it's possible, what I would need (and I mean exact instructions with every single command so I can print it out, because I do NOT know a thing about how to access stuff or what all those folders mean). Internal would be ideal since it's faster, but I could hook it up to an external USB as well if I knew how to make the windows drive come up as an icon.

Can someone please let me know if it's possible or suggest what I can do (clearly, please).

If you hook up the external drive it should come up on the desktop and double click to mount it

```
cp -Rv /var/lib/mythtv /media/disk
```

If you want to reinstall or remove mythbuntu it would be quicker to replace **cp** with **mv**

---

### Post by sdowney717 on 2009-11-29
> "The file XX cannot be handled because you do not have permission to read it."

What permission is this and how does one set it?

simply do this,

when running the live cd, click applications-accesories-terminal

when the terminal program opens, type in

gksu nautilus
or
sudo nautilus

this will open the file manager with super user rights and then you can copy files anywhere.

---

### Post by frumbert on 2009-11-30
> **sdowney717 said:**
> simply do this,

when running the live cd, click applications-accesories-terminal

when the terminal program opens, type in

gksu nautilus
or
sudo nautilus

this will open the file manager with super user rights and then you can copy files anywhere.

This mostly worked. I am able to copy some files using sudo nautilis as you suggested. However the same warning comes up on other folders still (e.g. I have two folders beside each other. the first one copies, the second one does not and gives the same permission warning as before.)

---

### Post by frumbert on 2009-11-30
> **u.b.u.n.t.u said:**
> Your ISP sounds pretty bad. Check out this forum for more info about what is available in Australia.

[http://forums.whirlpool.net.au/forum-threads.cfm?f=72](http://forums.whirlpool.net.au/forum-threads.cfm?f=72)

The top three in my view are iiNet, Internode, TPG. The worst three are Telstra, Optus, Primus.


Yes, I am locked into a plan with Telstra right now. I think when it runs out I'll probably disconnect the phone and the internet for a couple of months to see if/how much I miss it.

---

### Post by jrrader on 2009-11-30
always use gksudo when opening GUIs (such as nautilus)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sdowney717 on 2009-11-30
I am curious can you right click goto properties, goto  permissions and post a screen shot of the folder?
perhaps side by side, the one that copies and the one that cant copy
applications-accesories-take screenshot

---

### Post by frumbert on 2009-12-01
> **jrrader said:**
> always use gksudo when opening GUIs (such as nautilus)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the tip! There's so many commands to remember :(

> **sdowney717 said:**
> I am curious can you right click goto properties, goto  permissions and post a screen shot of the folder?
perhaps side by side, the one that copies and the one that cant copy
applications-accesories-take screenshot

Sorry it's taken so long. I took a screenshot of permissions of the folder called "mythtv" which is /media/uuid/mythtv/ and also of a file that wasn't copying (on the right).

[IMG]http://i45.tinypic.com/oasyf9.png[/IMG]

In the background you can see that I have managed to copy some files, so I chose one that said "permission denied" for the left-hand property window. Can I just change these things at the mythtv folder level and say "root owns and has right" to all folders and files below (which should be ok right? Since I want to nuke the drive after this finishes).

---

### Post by u.b.u.n.t.u on 2009-12-01
> **frumbert said:**
> Can I just change these things at the mythtv folder level and say "root owns and has right" to all folders and files below (which should be ok right? Since I want to nuke the drive after this finishes).

That sounds logical. Post how that goes.

---

### Post by frumbert on 2009-12-01
> **u.b.u.n.t.u said:**
> That sounds logical. Post how that goes.

gah, I forgot. when booted from the livecd and performing a long operation like a file copy of multi-gig files like these the keyboard stops responding after I leave the computer alone for more than 10 minutes. The CD drive light is going nuts. Is there any safe way to make the system respond to input at this point - because the file copy will take at least another 24 hours to finish by the speed of this :(

---

### Post by u.b.u.n.t.u on 2009-12-01
Q1. How large is the file roughtly, eg 5, 10, 20 GB?

Q2. What are the two transfer mediums and how does the transfer take place? Eg: HDD 1 to HDD 2 a 7 GB file through copy and paste.

Q3. Also is it a single file or are the files queued for transfer?

Q4. One more question, if you are using two HDD, what operating system are you using to perform the file transfer?

---

### Post by frumbert on 2009-12-01
> **u.b.u.n.t.u said:**
> Q1. How large is the file roughtly, eg 5, 10, 20 GB?

Q2. What are the two transfer mediums and how does the transfer take place? Eg: HDD 1 to HDD 2 a 7 GB file through copy and paste.

Q3. Also is it a single file or are the files queued for transfer?

Q4. One more question, if you are using two HDD, what operating system are you using to perform the file transfer?

1. Most of the files are between 2 and 6 GB.
2. 2 Samsung Sata2 1GB drives with 32mb cache on seperate controllers
3. Queued.
4. The ubuntu live cd I downloaded from the site yesterday.

---

### Post by u.b.u.n.t.u on 2009-12-01
> **frumbert said:**
> 1. Most of the files are between 2 and 6 GB.
2. 2 Samsung Sata2 1GB drives with 32mb cache on seperate controllers
3. Queued.
4. The ubuntu live cd I downloaded from the site yesterday.

Thank you for that clarification. Queuing large files may on occasion create instability in the transfer process. Depending on the method.

It may be worthwhile to set sleep, turn off monitor after X minutes and the like to an off setting.

I think the only assured method is the rather laborious one of monitoring single file transfers. Perhaps testing such as in move 2GB and then next say a total of 5GB etc and seeing what the upper limit is while maintaining stability.

---

### Post by sdowney717 on 2009-12-01
first off it says the file is owned by root.
try changing the file access and or group part from access only to read and write, create and delete etc... to see if it can copy

Also you can try something like this
 from terminal you can issue a command to change properties of all the files in a folder at once.

[http://www.debianhelp.org/node/4076](http://www.debianhelp.org/node/4076)

example
$ sudo chmod -R +rw /home/fabre/data

That will make everything in data, including data itself, readable and writable.

sudo chmod -R +rw /your home directory/your subfolder/your data folder

more info
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

the other command is chown
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

you might have to change folder permissions and then change ownership of the folder
example

sudo chown -R us base

    * Change the ownership of base to the user us and make it recursive (-R)

sudo chown -R yourusername /home/yourusername/yoursubfolder

---

### Post by TheProphetJonah on 2009-12-01
One issue that's a Windoze issue is that NTFS has as default that the only way to write to NTFS is from Windows. That's the only security XP etc actually has. From the LiveCD you can


[LIST=1]
[*]Disconnected from internet (security, people, Security!)
[*]Run an app like gparted or
[*]If you're feeling particularly confident use a terminal and fdisk
[*]Since you're starting with fundamentally a blanked disk.
[*]with gparted you can resize the partition, if it has data therein
[*]or if it doesn't
[*]change the partition type to FAT32, or make one partition to be whatever the largest size FAT32 supports
[*]THAT partition would be accessible, easily (hah!) from both Winbloze and The Better OS
[/LIST]

---

### Post by sdowney717 on 2009-12-01
i can write to NTFS partitions with no trouble

---

### Post by TheProphetJonah on 2009-12-01
If you intend to transfer files between filesystem types, Linux -> FAT32 is ridiculously easy.

So easy, in fact, it SHOULD scare the B'Jeezus out of you when it comes to actually going online using Microsux products.

There's a couple of utilities for transfer to NTFS,
 BUT, 
if you're copying to a partition which has your Windows system files on it, you'll give Windoze screaming fits, once you reboot into M$. 

If you were, say, a rather dishonest type of fellow and wanted to take over somebody's data from his WinXp or Vista or Win7 installation that wouldn't matter at all, but since it's your own and you'd rather keep that filesystem useable, a large separate FAT would be the easiest way to store files that aren't Applications. Like your mp3s and your videos.

One sticky little tiny insignificant wee eensy teensy small itty-bitty small little wee problem is that FAT32 won't hold a file larger than 4 Gb. Which some .iso files are that big.

I'm using Karmic Koala Ubuntu 9.1 and it has Selinux enabled by default. 

It didn't have a "root" login immediately available, and if I recall correctly didn't have my favorite file manager Midnight Commander installed by default either.  That's a nice security feature. I had to use the administration tool System>Administration>Users & Groups and add a password and permissions for the root user. (the super-user)

mc is a nice semi-graphical utility, you can even do web transfers with it. To copy files to restricted areas of the filesystem, like DOS and NTFS partitions, you type "su" then at the prompt your root password.
then once you're shown as "root@whatever-your-computer-name #" bang, you've got full read and write access to anything on your system.
 
For the love of God, man, don't do this while you're connected to the internet.
 
It bears repeating.

But in the terminal, type next "mc"

This opens the Commander. What you can do next with it SHOULD give you pause because it will show you just how easy it would be for some Socially Retarded Animated Sphincter with the proper tools to muck up your computer.

I invite you at that point to look up in your WinNT directory "system32" or perhaps "catroot". DO NOT CHANGE ANYTHING.

Then boot Windows and look at what files you can actually see in those directories, from the Windows environment. Huge difference. 

That's the reason for all the permissions and other Security measures you have to work around in order to write to a Windows filesystem.

It's why you should avoid using Windows on the web.

there's a couple of manual pages you could look at while you're mucking about with the terminal, you don't have to be the root user to see them.
type "man ntfs3g" and
"man ntfs3g.probe"  for even more instructions on dealing with Windows partitions and how to (hopefully) not muck them up with a simple file transfer.

Once you've scared yourself silly by seeing how easy it is to take or destroy your M$ system, you're ready for the next step, which I shall place as a "reply" to this thread.

---

### Post by TheProphetJonah on 2009-12-01
The next step is, since Linux media players actually ARE better than the pay-to-play crappola you get to add on to Windoze, if you want to save your files to view and listen to in Linux, the filesystem you'd probably like best is "xfs".

Because it CAN hold files larger than 4 Gb.  This is handy if you're grabbing a DVD distribution of Linux for later install. Some of which go above that Magick 4G Number.

AND with those windoze based applications that can read and write to a Linux partition you can access those files from Windoze.

I know it causes headaches to do it, but practice using the perspective of the Average Thief when you're looking at Security issues. Like, for instance, using Windoze, it's a huge security risk and  they can't actually make it secure.

Think to yourself "Self, how can I take the files away from this poor, unsuspecting victim without getting arrested and thrown into prison or other unpleasant Karmic consequences befalling me?"

Which is the underlying problem of everything in this entire thread.

xfs is a good alternative.

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

I keep a windoze installation mostly because I'm trying to port as many of the windows applications  as possible to Linux

Because M$ fanatics are addicted to Windoze-Only applications and say that they would use Linux instead, if only they can have the (IMHO mostly useless) Windoz apps.

 Just my way of giving something back to the Linux users who built the Linux system on a cashless basis.

If I'd had to pay for the education I got from Linux the way I had to pay for my Windoze knowledge I'd have been stuck.

Just in case anybody needs to know.

---

### Post by TheProphetJonah on 2009-12-01
> **sdowney717 said:**
> i can write to NTFS partitions with no trouble

Yeah, it's easy once you get used to it.

There's more to it than just how to actually do it though.

Risks and consequences, the real price of using M$.

I think, could be wrong, but just an opinion, windoze is TOO easy to manipulate.

It makes you appreciate the permissions and other security measures.

---

### Post by sdowney717 on 2009-12-01
> Yeah, it's easy once you get used to it.

as easy as copy and paste
simply use nautilus.
click on the windows partition, 
type in your password
start copying files.

ntfs3g is standardized for some time now, included in ubuntu for some time now and works fine.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
> 
NTFS-3G Stable Read/Write Driver


The NTFS-3G driver is a freely and commercially available and supported read/write NTFS driver for Linux, Mac OS X, FreeBSD, NetBSD, OpenSolaris, QNX, Haiku, and other operating systems. It provides safe and fast handling of the Windows XP, Windows Server 2003, Windows 2000, Windows Vista, Windows Server 2008 and Windows 7 file systems.

NTFS-3G develops, quality tests and supports a trustable, feature rich and high performance solution for hardware platforms and operating systems whose users need to reliably interoperate with NTFS.

The driver is used by millions of computers, consumer electronics devices for reliable data exchange, and referenced in 45 computer books. Please see our test methods and testimonials on the driver quality page. 

---

