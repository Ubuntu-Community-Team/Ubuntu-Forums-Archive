---
title: "what is the equivalent of path in linux"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by harry003 on 2010-06-09
I am having a lot of trouble understanding - in "my mind's eye" - the directory structure of my file system.

I have 10GB partition for the Ubuntu OS, and a 20GB data partition.

However, it appears that something in the system gave my data partition an insane name "3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" how can I change that to "DATA" I cannot seem to find any way? (Of course a drive letter such as E:\ would be much better to my DOS-trained brain.)

It appears that this partition also appears a 2nd time in a separate and different guise as the "home" subdirectory in the "Filesystem" which seems to be the equivalent of the root directory of the 10GB partition. Why?

If I could SEE the "path" of any (or better yet, of all) file, directory, or subdirectory, step-by-step, completely, directly, back to the (one) source, it would be a GIGANTIC help to me in visualizing the files structure of my (one) hard drive. 

As you can tell, I am a visual person, and without being able "see" this conceptually, I feel like I am always LOST even though it is a single hard drive without really a whole lot on it.

Is there ANYTHING in Linux that corresponds to "path"?

I have 2 bound books, 1 on Linux and 1 on Ubuntu, and I have downloaded 2 lengthy and recommended PDF "guides" from this forum, and none address this issue in a satisfying way.

Thank you very much.

---

### Post by patchwork on 2010-06-09
/ = root directory
/home = home directory in root filesystem
etc...

so
/home/user_name/Documents for example, means
the user's Documents directory, in their home directory, in the root filesystem.

Judging by your post, your partition seems to be mounted as home (which is quite common and advisable to allow the preservation of personal data if you want to do a clean install of a new distro later on).

---

### Post by cbecker78 on 2010-06-09
Click on your home folder.  just below the menus and arrows (and on the left) you should see your user name.  To the left of your user name is probably a little button that looks like a tablet with a pencil (this could be different depending on you icon set).  But go ahead and click on that icon.  Your user name will transfer to the full path of your home directory.  You can do the same thing with any folder you open.

---

### Post by alphacrucis2 on 2010-06-09
> **harry003 said:**
> I am having a lot of trouble understanding - in "my mind's eye" - the directory structure of my file system.

I have 10GB partition for the Ubuntu OS, and a 20GB data partition.

However, it appears that something in the system gave my data partition an insane name "3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" how can I change that to "DATA" I cannot seem to find any way?

That looks like a partition [UUID.]("http://en.wikipedia.org/wiki/Universally_Unique_Identifier"). Not a good idea to change it. 


> 
 (Of course a drive letter such as E:\ would be much better to my DOS-trained brain.)

You have device names like sda, sdb (scsci drive a and b for example). Partitions on these would get named sda1, sda2, sdb1 etc.



> It appears that this partition also appears a 2nd time in a separate and different guise as the "home" subdirectory in the "Filesystem" which seems to be the equivalent of the root directory of the 10GB partition. Why?

If I could SEE the "path" of any (or better yet, of all) file, directory, or subdirectory, step-by-step, completely, directly, back to the (one) source, it would be a GIGANTIC help to me in visualizing the files structure of my (one) hard drive. 



The file system is very simple. It's just a nested tree of directories. Partitions can be mounted at any point in the tree. For example you could have a directory like /home/me/music and mount a partition againt /home/me/music and any files you put in there (or its' subdirectories will go into that mounted partition, whereas files just stored into /home/me would be  stored in the partition mounted against file system root / (unless another partition was mounted against /home


> As you can tell, I am a visual person, and without being able "see" this conceptually, I feel like I am always LOST even though it is a single hard drive without really a whole lot on it.

Is there ANYTHING in Linux that corresponds to "path"?

I have 2 bound books, 1 on Linux and 1 on Ubuntu, and I have downloaded 2 lengthy and recommended PDF "guides" from this forum, and none address this issue in a satisfying way.

Thank you very much.

In DOS or Windows I thought a PATH was just the collection of directories that the OS will look for files in when mentioned just by name. Linux has exactly the same concept:

[http://www.linuxheadquarters.com/howto/basic/path.shtml]("http://www.linuxheadquarters.com/howto/basic/path.shtml")

---

### Post by Miljet on 2010-06-09
When you create a partition, it goes by 3 identifiers, a partition number like sda2 or sda4, the UUID (Universally Unique Identifier), and whatever name you assigned to it. The number "3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" appears to be the UUID of the partition. You do not want to try changing that. It is used in several configuration files in your system.

If you created a separate /home partition during install, that partition is automatically mounted when you boot. Once a partition is mounted, it is accessed through the mount point and is considered to be part of your main file system. Linux doesn't care if the data is on another partition, or on a different disk, or even on another computer. It sees it just like it is part of the file system. In other words, you don't access files in another partition by specifying a path to that partition, you mount the partition and use it just like it is on the same partition you are working on.

---

### Post by steveneddy on 2010-06-09
> **harry003 said:**
> I am having a lot of trouble understanding - in "my mind's eye" - the directory structure of my file system.

I have 10GB partition for the Ubuntu OS, and a 20GB data partition.

However, it appears that something in the system gave my data partition an insane name "3a6f3d1a-e01b-406e-8ec9-06b37c1c5e12" how can I change that to "DATA" I cannot seem to find any way? (Of course a drive letter such as E:\ would be much better to my DOS-trained brain.)

It appears that this partition also appears a 2nd time in a separate and different guise as the "home" subdirectory in the "Filesystem" which seems to be the equivalent of the root directory of the 10GB partition. Why?

If I could SEE the "path" of any (or better yet, of all) file, directory, or subdirectory, step-by-step, completely, directly, back to the (one) source, it would be a GIGANTIC help to me in visualizing the files structure of my (one) hard drive. 

As you can tell, I am a visual person, and without being able "see" this conceptually, I feel like I am always LOST even though it is a single hard drive without really a whole lot on it.

Is there ANYTHING in Linux that corresponds to "path"?

I have 2 bound books, 1 on Linux and 1 on Ubuntu, and I have downloaded 2 lengthy and recommended PDF "guides" from this forum, and none address this issue in a satisfying way.

Thank you very much.

Where do you see this information and how are you trying to access the 20 GB data partition?

Does the data partition that you trying to access mount automatically? Or are you trying to get it to auto mount?

Are you able to access this data partition at all?

---

### Post by qyot27 on 2010-06-10
> **alphacrucis2 said:**
> In DOS or Windows I thought a PATH was just the collection of directories that the OS will look for files in when mentioned just by name. Linux has exactly the same concept:

[http://www.linuxheadquarters.com/howto/basic/path.shtml]("http://www.linuxheadquarters.com/howto/basic/path.shtml")
True, PATH (capitalized for simplicity) is the environment variable that tells Windows to look for executables in a set of directories.  But the term 'path', somewhat ambiguously, also can refer to 'file/folder path' (as in 'absolute path' vs. 'relative path').





If the real question is understanding the common directories in *nix vs. the ones in Windows, well, you kind of have to start over.  There are a few similarities, particularly since Microsoft adopted the whole 'User\My Documents' setup, but overwhelmingly the system is organized in a much different fashion.

Others have already generally supplied the relevant info, that internal and external devices are 'mounted' and in doing so are seen as just another part of the main filesystem.  Or that you can enable Nautilus to display the textual directions (note: in 10.04, this requires you to use GConf to switch the display back to editable text).

If you're asking about the individual directories that make up said filesystem, then you kind of have to start over from scratch, because Windows' directory structure and *nix's only share a couple of things in common.  Compare /home/User to C:\Documents and Settings\User\My Documents, or C:\Documents and Settings\User\Application Data - and Local Settings\Application Data - to /usr/share.  Program Files roughly corresponds to /bin, /usr/bin, and /usr/local/bin ('roughly', because Program Files contains more than strictly executables, and there is no User/System separation there).  Windows doesn't strictly adhere to its own filesystem arrangement in regard to what users are allowed to do or not do, but this is because of the difference in user accounts - Windows historically gave users Administrator accounts by default, which would allow you to save and manipulate files anywhere on the filesystem.

*nix systems don't do that, for many very good reasons, and restrict users to being lords of only their own domains, not the system domain.  Windows only started doing it this way by default with Vista, and this is the main reason that in Vista (and I presume, Win7 also) you're free to modify files and move stuff around in your own User folder, which is displayed in the top left of Windows Explorer, but it requires you to Cancel/Allow->Continue or have Administrator privileges to put anything in C:\Program Files or C:\Windows.  You could of course set it up this way on earlier versions of Windows, but it just wasn't default.

---

### Post by tgalati4 on 2010-06-10
pwd  

Print working directory.

---

### Post by formaldehyde_spoon on 2010-06-10
Seems to be two separate questions: the path, and the directory/partition structure. 

I know how much I like visual explanations when I want to understand something, and I needed some activity to procrastinate with, so here's a couple of little pictures, both of the same system, which has three partitions, red, green and blue. 

First Windows:
[IMG]http://img263.imageshack.us/img263/5585/38128719.png[/IMG]
The three partitions are presented to you separately in My Computer. Red is your Windows install, and Blue and Green are for data or whatever.


Now Linux:
[IMG]http://img139.imageshack.us/img139/8462/lfs.png[/IMG]
Again you've used Red for your main OS install, and Green and Blue are data partitions.

You must have a partition to mount ''/'' on, and then everything under ''/'' in the tree is on the same partition unless you decide to mount another partition at a directory somewhere underneath, in which case everything under that directory (the ''mount point'') is on the second partition unless you decide to mount a third partition at a directory somewhere underneath...and so on.

You can put partitions anywhere in the directory structure, in any fashion, basically without limits.  
Linux won't care, it will just navigate to any point in the tree regardless of what partition it's on.

 The partitions have the long, strange names (uuid) that you've mentioned, but as soon as a partition is mounted to a mount point (a directory in the tree) you can forget the uuid; you will refer to the partition by the name of the mount point.
Because you can name directories anything you like, you CAN refer to it as '/DATA', or '/E' if you want.
I've mounted Green as '/mnt/diskD', but it's just an example, you can mount anywhere you feel like.

How to choose where stuff is mounted is a question about /etc/fstab (or you can choose when you install) which is a topic for another thread.

In Gnome (the GUI you are using) the thing it calls 'Filesystem' is '/'.

It sounds like your 20GB partition has been mounted at '/home'.  
It's quite common for linux users to put '/home' on a separate partition, because they can reinstall an OS onto the partition they have at '/' without losing any settings they had, or any files they had in their home or desktop directories.

I'm not sure where you are actually seeing the UUID (''insane name'') unless you are looking at /etc/fstab....?
Your 20GB partition isn't mounted twice, it's only at '/home'.

Although the picture makes it look like Blue and Green are ''inside'' Red, that is only the case from the point of view of the directory tree structure.  
'diskD' and 'diskE' and all the files and directories on them are only on Green and Blue respectively, they are NOT on Red, in any fashion.
The OS knows that when it wants any file starting with '/mnt/diskD' it should look on the Green partition.

---

### Post by harry003 on 2010-06-10
Thanks, you guys really rose to the occasion, especially formaldehyde_spoon, you really knocked yourself out with those diagrams!

Having said that, qyot27 is the only one who started to understand what I was asking on a deeper level. You all said things like "Linux doesn't care where you mount" or "it can be anywhere" - that kind of talk just blows my mind. I want to know where it IS. I want a map. The true map of the physical space.

I come from an engineering background. When you draw the plans for a building, you draw the foundation plan, the floor framing plans, the wall framing plans, and the roof framing plan. Each component depends entirely on the components below it for its very existence.

What you are saying, to me, sounds like you are saying "oh, just put the roof frame wherever you want, something will make it stay up" and that does not work in my conception of the universe.

I think that qyot27 may be right, Vista and Windows 7 completely lost me when they created a (as I see it) false non-reality in the files structure. My computer is "harry" and so in my Windows 7 file system what I see at the top of the screen in Windows Explorer is "harry" that is presented to me as a top level directory (it is not something that I created or endorsed in any way, it just appeared, of course).

But "harry" is actually a sub-directory to "Documents and Settings" which is itself a sub-directory to the C:\ drive. Why create a deception like that?

This has the feeling of being the same sort of thing you are describing, and it makes me want to scream. I just want a clean, straight "picture" of everything, as it really is, physically, I need a map, as I said before. I don't want to be told that anything can be anywhere, I want to know where it IS.

In Ubuntu, there is also a "harry" directory that seems to be the sole occupant of "home" but where is something that actually SAYS THAT? I created a Data partition for efficiency and security but who created "harry" ? Not I !

Because there is not a "path" command or visual that clearly describes to a person WHERE they ARE at any given time, I cannot navigate.

Please folks, I am a pathologically visual person and I am blind and lost here.

Thank you again.

ps - these words that are all caps, they are carefully and deliberately used, they are speaking to the very heart of my frustration.

---

### Post by tom.swartz07 on 2010-06-10
> **harry003 said:**
> Thanks, you guys really rose to the occasion, especially formaldehyde_spoon, you really knocked yourself out with those diagrams!

Having said that, qyot27 is the only one who started to understand what I was asking on a deeper level. You all said things like "Linux doesn't care where you mount" or "it can be anywhere" - that kind of talk just blows my mind. I want to know where it IS. I want a map. The true map of the physical space.

I come from an engineering background. When you draw the plans for a building, you draw the foundation plan, the floor framing plans, the wall framing plans, and the roof framing plan. Each component depends entirely on the components below it for its very existence.

What you are saying, to me, sounds like you are saying "oh, just put the roof frame wherever you want, something will make it stay up" and that does not work in my conception of the universe.

I think that qyot27 may be right, Vista and Windows 7 completely lost me when they created a (as I see it) false non-reality in the files structure. My computer is "harry" and so in my Windows 7 file system what I see at the top of the screen in Windows Explorer is "harry" that is presented to me as a top level directory (it is not something that I created or endorsed in any way, it just appeared, of course).

But "harry" is actually a sub-directory to "Documents and Settings" which is itself a sub-directory to the C:\ drive. Why create a deception like that?

This has the feeling of being the same sort of thing you are describing, and it makes me want to scream. I just want a clean, straight "picture" of everything, as it really is, physically, I need a map, as I said before. I don't want to be told that anything can be anywhere, I want to know where it IS.

In Ubuntu, there is also a "harry" directory that seems to be the sole occupant of "home" but where is something that actually SAYS THAT? I created a Data partition for efficiency and security but who created "harry" - not I.

Because there is not "path" command or visual that clearly describes to a person WHERE they ARE at any given time, I cannot navigate.

Please folks, I am a pathologically visual person and I am blind and lost here.

Thank you again.

To continue with your engineering comparison, think of / as the foundation. From there, the /home folder, the mounted partitions in /mnt, and various other system files are all built off of this foundation.

In a Windows based world, you would have 2 or 3 separate foundations, each pointing to a different root directory. One for the main OS install, another for the 1st extra partition, and another for the next extra partition.

The Unix way is a bit more concise, as all of the data used by the OS is located or mounted where the OS is located, yet all of the programs run separate from the OS to prevent any catastrophic accident that is common to Windows installs.

Hope this sheds a bit more light on the subject

---

### Post by harry003 on 2010-06-10
Thank you for your reply. This is exactly the kind of "brain disconnect" that I am flummoxed by.

I have used DOS and Windows for decades, and I always avoided partitions like the plague. I tried to always use my hard drives as discreet devices, with 1 partition each. Perhaps this was to keep my own brain intact.

I perceive a partition as a sort of "fake" hard drive, it isn't one but it pretends to be, and acts like one. That I can deal with.

Your analogy seems backwards to me. In Windows, the OS is just residing in a sub-directory in the one root directory on the ONE hard drive.

You call "/" the root directory, but "home" is really another (fake) drive altogether. It is not a subdirectory, it is a peer, an equal, something parallel. Putting it "below" its parallel peer "feels" like a falsehood, a deception, in my mind. Just because you can bury (mount) it into some obscure corner does not alter WHERE it really is.

Somehow I am just having a gargantuan amount of trouble with this "mounting" concept.

---

### Post by dookiebowser on 2010-06-10
> **harry003 said:**
> 
Your analogy seems backwards to me. In Windows, the OS is just residing in a sub-directory in the one root directory on the ONE hard drive.


When you install linux with X amount of partitions, it is still on one hard drive. If you think of your hard drive as a filing cabinet, and partitions as drawers you will have a better understanding. You can even take a drawer from the cabinet out and put 2 smaller ones in it's place, but it doesn't mean you just made another filing cabinet altogether. 

With Windows and one partition this is like stuffing all of your files in one giant filing cabinet drawer.

If you want a diagram of how the physical space is broken up into partitions and how much data is used in those partitions, there are programs for that.

Otherwise I don't really know what you're asking.

---

### Post by b0b138 on 2010-06-10
Ok bear with me but here is something to help you out some. This used to be easier to change before lucid (bad devs, no caffine)

Ok so in nautilus (the file browser) just above the icons it shows some boxes that indicate the location. Well I never liked that so lets change it to show the full path.

Open up a terminal window ( applications, accessories, terminal) and type in gconf-editor then hit enter. Now go through the tree stucture to apps->nautilus->preferences    check the box always_use_location_entry

---

### Post by lisati on 2010-06-10
Hmmmmm...... /me gets thinking about how "/" represents the top level management of a corporation, and the lower levels represent different departments. Some of the different departments are in the same room (partition), others are in a different room, which *can* be on a different floor of the building (disk drive). Some of the different departments might be on a different building altogether.....

I'm not sure if we can go anywhere useful with this analogy, but I thought I'd put it out there anyway.

---

### Post by dookiebowser on 2010-06-10
> **lisati said:**
> hmmmmm...... /me gets thinking about how "/" represents the top level management of a corporation, and the lower levels represent different departments. Some of the different departments are in the same room (partition), others are in a different room, which *can* be on a different floor of the building (disk drive). Some of the different departments might be on a different building altogether.....

I'm not sure if we can go anywhere useful with this analogy, but i thought i'd put it out there anyway.

Sorry Dave. it was a joke and was self-censorship rather than circumvention.

---

### Post by anewguy on 2010-06-10
> **dookiebowser said:**
> f**king hard drives, how do they work?!?!?

Please see forum rules regarding language on the forum, including this type of "hiding".

Dave

---

### Post by oldfred on 2010-06-11
These help explain the file structure. From that you can add just like in windows additional storage. In windows you might add the D: drive which is really a partition that in linux might be mounted and labeled as /data.
On my system it is this:
/dev/sdc6: LABEL="Data" UUID="a55e6335-616f-4b10-9923-e963559f2b05" TYPE="ext3" 

Explaination of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

---

### Post by qyot27 on 2010-06-11
> **harry003 said:**
> Having said that, qyot27 is the only one who started to understand what I was asking on a deeper level. You all said things like "Linux doesn't care where you mount" or "it can be anywhere" - that kind of talk just blows my mind. I want to know where it IS. I want a map. The true map of the physical space.
Granted, this isn't going to be as nice as a picture diagram, but maybe I can see if I can explain the general concept.

You have a hard drive.  In its native form, it cannot hold any data - it's a blank slate.  No filesystem, no partitions, not even filesystem formatting (FAT, NTFS, ext2/3/4, HFS, etc.).

To make this hard drive usable, you have to create space which *is* formatted and allows the data to be written.  The formatted areas are what partitions are.  Partitions don't have to take up the entire drive, much like a stack of papers doesn't have to take up the entirety of your desk area.

In Windows, the system install always takes up the first partition it finds, which is determined by the physical geometry of the drive.  Subsequent partitions are listed sequentially (thus, the drive letter system, although NT-based versions of Windows don't require drive letters from what I've read; old habits just die hard).

The concept of 'mounting' a drive is simply making the partition accessible to the OS.  If you imagine the OS and its mounted partitions as a shelf with plugs, then Windows would be organized like this:

-OS
-Empty plug
-Empty plug
-and so on, pretty much infinitely

But for Unix-like OSes like Linux and Mac OS X, there is a directory in the regular OS filesystem where these extra plugs reside, and they only get created when the partition is mounted.

On /, the root of the filesystem (I only listed a few directories for simplicity):
/bin
/home
/media
---Empty plug
---Empty plug
/usr

However, there is nothing intrinsically special about the /media directory.  The command to mount the partition can create a plug anywhere on the filesystem, or just about anywhere (/media, or sometimes /mnt, is just the usual default location - but if you use 'mount' from the command line, you yourself could create the plug in other directories).  This is what we mean when we say that 'it doesn't really matter' - it does matter, because the OS needs to see partition in order to use it, but it's like the difference between putting the television remote on the coffee table or holding it in your hand.  Either place is acceptable, as long as it's pointed at your TV and has batteries in it.

Basically, C:\ (or F:\, G:\, A:\, etc.) and / describe the very same notion - the base directory, in which all other directories are stored.  / just happens to be more specific, being the root directory of *everything* that *nix sees.

> I think that qyot27 may be right, Vista and Windows 7 completely lost me when they created a (as I see it) false non-reality in the files structure. My computer is "harry" and so in my Windows 7 file system what I see at the top of the screen in Windows Explorer is "harry" that is presented to me as a top level directory (it is not something that I created or endorsed in any way, it just appeared, of course).

But "harry" is actually a sub-directory to "Documents and Settings" which is itself a sub-directory to the C:\ drive. Why create a deception like that?
This is where the difference between a single-user and a multi-user OS comes in.  "harry" was created when you installed Windows and gave it your User information.  It created that set of folders for you so you'd have a hub to do your work from.  It puts it there (C:\Documents and Settings) because that's the way multi-user OSes work - they assume there are other users, and their user profiles would be located there as well.  All NT-based versions of Windows are multi-user, starting back in the early 90s (Windows NT, 2000, XP, Vista, and Win7 all fall into this category; DOS and Win 9x were pretty much single-user systems).  Unix and its various clones and evolutions have always or near-always been multi-user systems.

The ideal Microsoft (and all other multi-user OS distributors) shoots for in this is to keep users away from mucking about with vital system files unless they know what they're doing - for the OS to know that you're trustworthy, you need Administrator privileges (which usually requires entering a password first to identify yourself, or encountering that Cancel or Allow dialog).  Unfortunately MS only started to actively enforce this from the beginning of the user experience with Vista.  The lack of such *default* protections in XP and prior is part of the reason why Windows has such an awful reputation for viruses.  Users had Administrator privileges by default, and thus any malware that gets in would have them too, potentially (and quite often) ruining your system in the process.

> In Ubuntu, there is also a "harry" directory that seems to be the sole occupant of "home" but where is something that actually SAYS THAT? I created a Data partition for efficiency and security but who created "harry" ? Not I !
As I described with Windows and multi-user setups, the same holds true for Ubuntu - it created the folder when you gave it your Account information during the install phase, so that your data and any other users' data is kept separate, and that user data is kept separate from locked-down system data that needs admin privileges to be edited.

Basically, unless you are installing software (which is generally a matter of giving a password when prompted) or have to do something very specific to a task (in which case you might need to know the filesystem a bit better, and still need admin privileges), a user doesn't need access to the rest of the system, only their own directory in /home.  The other directories in a *nix system are reserved for system use, not user use.

If you only work in the GUI apps, then this is pretty abstracted for you, and the only thing that matters is whether you have permission to deal with the partition(s)/directories in question or not.  If you're using the Terminal to do command line work, then it starts to matter more.

> Because there is not a "path" command or visual that clearly describes to a person WHERE they ARE at any given time, I cannot navigate.
First, the use_location_bar option already mentioned for Nautilus in gconf will render the address bar of the file manager in such a way - you'll see the entire directory path, e.g. /home/harry/Videos.

If you mean a command-line equivalent to 'dir', then the 'pwd' command was already suggested, which will print out the entire directory path.  The other function of 'dir', to list all the contents of your working folder, is available through the command 'ls'.

---

### Post by formaldehyde_spoon on 2010-06-11
> **harry003 said:**
> Thanks, you guys really rose to the occasion, especially formaldehyde_spoon, you really knocked yourself out with those diagrams!

Having said that, qyot27 is the only one who started to understand what I was asking on a deeper level. You all said things like &quot;Linux doesn't care where you mount&quot; or &quot;it can be anywhere&quot; - that kind of talk just blows my mind. I want to know where it IS. I want a map. The true map of the physical space.

I come from an engineering background. When you draw the plans for a building, you draw the foundation plan, the floor framing plans, the wall framing plans, and the roof framing plan. Each component depends entirely on the components below it for its very existence.

What you are saying, to me, sounds like you are saying &quot;oh, just put the roof frame wherever you want, something will make it stay up&quot; and that does not work in my conception of the universe.

I think that qyot27 may be right, Vista and Windows 7 completely lost me when they created a (as I see it) false non-reality in the files structure. My computer is &quot;harry&quot; and so in my Windows 7 file system what I see at the top of the screen in Windows Explorer is &quot;harry&quot; that is presented to me as a top level directory (it is not something that I created or endorsed in any way, it just appeared, of course).

But &quot;harry&quot; is actually a sub-directory to &quot;Documents and Settings&quot; which is itself a sub-directory to the C:\ drive. Why create a deception like that?

This has the feeling of being the same sort of thing you are describing, and it makes me want to scream. I just want a clean, straight &quot;picture&quot; of everything, as it really is, physically, I need a map, as I said before. I don't want to be told that anything can be anywhere, I want to know where it IS.

In Ubuntu, there is also a &quot;harry&quot; directory that seems to be the sole occupant of &quot;home&quot; but where is something that actually SAYS THAT? I created a Data partition for efficiency and security but who created &quot;harry&quot; ? Not I !

Because there is not a &quot;path&quot; command or visual that clearly describes to a person WHERE they ARE at any given time, I cannot navigate.

Please folks, I am a pathologically visual person and I am blind and lost here.

Thank you again.

ps - these words that are all caps, they are carefully and deliberately used, they are speaking to the very heart of my frustration.

The image I drew seems to be exactly what you're asking for: it is a map of your computer, so to speak.

Here's another try ;) (I'm not drawing these by hand, btw!!) :
[IMG]http://img411.imageshack.us/img411/5702/fs2z.png[/IMG] 
(This pic is Linux)
The image above is of your computer n it's current state: ''/'' is on your 10GB partition, and ''/home'' is on your 20GB partition.
 You can see the two partitions, represented by large grey boxes. The red directories are the only ones you are likely to ever navigate to, except for CDs or external drives. 

Your entire computer system is represented by ''/'' (''c + d + e +...'' in Windows), always, no exceptions. ''/'' is the root of a tree (an upside down one) that leads to every single file and folder on your system. 
''/'' = your computer.  
It's not ''harry'', harry is just your account folder where your personal settings are stored, and where you are encouraged, but not forced, to store your files (same idea in both Linux and Windows).

When you install, you choose a partition that ''/'' will be automatically placed on when you boot up the computer.
If you want, you can leave it at that, and the whole tree will be stored on that one partition.

But if you want, you can put parts of the tree on other partitions - you decide what goes where, and it will be done automatically when you boot up.

 ''/'' = ''Filesystem''
''/home/you(~)'' = the little house symbol link that you can click on.
''/home/you/desktop'' = the desktop - always visible on your screen. 

Both terminal and the GUI browser tell you where you are:
 [IMG]http://img808.imageshack.us/img808/7050/scr2.png[/IMG]
[IMG]http://img819.imageshack.us/img819/8449/scr1.png[/IMG]
and like someone already mentioned, you can type ''pwd'' into the terminal to be told where you are. 
I went to /usr/share/themes/Clearlooks/gtk-2.0/ fro those images, just for examples sake, not because it has any significance.

EDIT: I think, possibly, we misunderstood what you were trying to ask when you mentioned ''path''.
Linux also has paths, just like Windows, only with minor syntax differences. For example: 
Window's ''**c:\**Documents and Settings\harry\'' = Linux's ''**/**home/harry/''

---

### Post by srs5694 on 2010-06-11
> **harry003 said:**
> You call "/" the root directory, but "home" is really another (fake) drive altogether. It is not a subdirectory, it is a peer, an equal, something parallel. Putting it "below" its parallel peer "feels" like a falsehood, a deception, in my mind. Just because you can bury (mount) it into some obscure corner does not alter WHERE it really is.

Somehow I am just having a gargantuan amount of trouble with this "mounting" concept.

Others have presented perfectly good analogies (I've used the filing cabinet one myself on multiple occasions), but here's another that may help you over your conceptualization problems: Imagine a partition as being like a clothes hanger. In the Windows world, every partition/hanger must be accessed as an equal by putting it directly on the rod in your closet, as you probably do. In Linux, though, you can hang them in a cascading fashion off of one another, and in fact it's impossible to mount more than one directly on the rod in the closet. (That one being the root, or "/", partition.) Of course, this analogy breaks down because clothes hangers normally hold clothes, and arranged in this way real clothes hangers wouldn't be able to hold clothes, but if you ignore this failure of the analogy, it may help you understand the flexibility of the Linux structure. Certainly it's a better analogy if you're a 6-year-old who's playing with clothes hangers!

More broadly, this is an example of data abstraction. Data as stored in a computer need not closely resemble the data as perceived by humans. I don't know anything about the internal workings of this forum software, but it's possible that the posts in this forum thread are in fact scattered all over the server's hard disk; they might only be collected together for display when a user clicks the link to see the thread. In a similar way, partitions can be created and spread across hard disks in a way that's convenient for reasons of disk size, filesystem type, and so on, and then recombined in ways that make it convenient to access the data in a file browser or a text-mode shell. This isn't "falsehood" in any way, but it is something that's common in computers but uncommon in physical engineering.

---

### Post by formaldehyde_spoon on 2010-06-11
> **harry003 said:**
> ... Your analogy seems backwards to me. In Windows, the OS is just residing in a sub-directory in the one root directory on the ONE hard drive.

You call &quot;/&quot; the root directory, but &quot;home&quot; is really another (fake) drive altogether. It is not a subdirectory, it is a peer, an equal, something parallel. Putting it &quot;below&quot; its parallel peer &quot;feels&quot; like a falsehood, a deception, in my mind. Just because you can bury (mount) it into some obscure corner does not alter WHERE it really is.

Somehow I am just having a gargantuan amount of trouble with this &quot;mounting&quot; concept. After reading srs' excellent analogy I realized I hadn't replied to this post, so here's my take on it.

Windows is inside ''C:\windows'', but if you look in there you'll see that it is then split up into many sub-directories.
Linux is similar, but it is immediately split up into many different sub-directories at ''/'', without first going to a sub-directory.

  Home (your home, the home icon you can click on) is not a fake drive, it is not a peer (assume you mean of ''/''?) it's *true* location is in the tree at ''/home/harry/''.
If it appears otherwise it's because the OS can, for important directories (home, desktop, etc), put in links to quickly jump to these directories from anywhere in the tree.  You can create links like this too if you want.

Lastly, mounting/partitions/etc have no effect on the structure of the tree, the tree always looks the same, no matter what, same directories, same files, same hierarchy (you can create/move/delete them of course).  Mounting only decides which partition (physically, in hardware) a branch of the tree will be stored on.

Also, a partition isn't a fake disk.  The OS deals with partitions, not disks.  Every disk must have at least one partition, and most commonly it's a single partition that covers the whole disk, but you can divide a single disk into multiple smaller partitions (like you: presumably you don't have two physical disks, 10GB and 20GB, each with a single partition covering the whole of each disk - you probably have a 30GB disk with two partitions on it: 10GB and 20GB).

---

### Post by harry003 on 2010-06-11
These are all great answers and most of them at least sideswipe the pseudo-question that I asked. I kind of understand the virtual structuring concept, like a bunch of extension cords that can all plug into each other but only one outlet to power it all up. I more or less get that. 

F-spoon, your diagrams are great, and I feel guilty that you spent so much time and energy on them. I hope other people (newbies) are being helped by this discussion, too, so that your work provides maximum benefit. Bob, your instruction on getting the path displayed in Nautilus was helpful, although it does not go as far as I would like, leaving gaps at crucial junctions, it seems to me. And why doesn't the big blue bar at the top tell the real story? 

In Windows "classic" Explorer, in the left pane was a tree structure where each directory had a plus sign beside it that would open and show its contents. These could be nested or expanded to your heart's content, and all were connected together, reaching directly upwards. You always saw where everything was in relation to everything else. This picture is what I yearn for.

Knowing that something could be this way, or could be that way, is all well and good.

What I want is a clear and concise and complete map showing the exact structure of my computer files, right now, exactly as they are stacked up, physically or virtually, today. If Linux wants the root directory of my Windows C:\ drive to be called /media within Linux, I can live with that, now that you have told me, but nothing else would have told me that until I dug around to and see which directories I might recognize inside of it, and make assumptions.

I specifically set up the larger Linux partition called /home for safety and backup issues. I am pleased that it is working as I hoped.

I have not yet ventured to rename it "Data" as old Fred suggested but I am going to try that soon.

I am getting there. Thanks again, all

---

### Post by oldfred on 2010-06-12
Oh you do not want to rename /home to data. 

I still have a /home and at least for now it still is a separate partition. It is just that I install multiple distributions and then you should not share a /home as different versions of software may save settings that are not compatible. I have the /data partition so I can easily share all my data. I have a shared NTFS partition to share with my XP install and a ext3 /data partition for any data I do not think I will ever need in windows (now an hour or two a week) but want to share with other linux distributions.

---

### Post by oldfred on 2010-06-12
If you want your tree structure, you can have that also. In places on the left pane, where it says places, click on places and it gives you several choices including tree.

---

### Post by formaldehyde_spoon on 2010-06-12
> **harry003 said:**
> These are all great answers and most of them at least sideswipe the pseudo-question that I asked. I kind of understand the virtual structuring concept, like a bunch of extension cords that can all plug into each other but only one outlet to power it all up. I more or less get that. 

F-spoon, your diagrams are great, and I feel guilty that you spent so much time and energy on them. I hope other people (newbies) are being helped by this discussion, too, so that your work provides maximum benefit. Bob, your instruction on getting the path displayed in Nautilus was helpful, although it does not go as far as I would like, leaving gaps at crucial junctions, it seems to me. And why doesn't the big blue bar at the top tell the real story? 

In Windows &quot;classic&quot; Explorer, in the left pane was a tree structure where each directory had a plus sign beside it that would open and show its contents. These could be nested or expanded to your heart's content, and all were connected together, reaching directly upwards. You always saw where everything was in relation to everything else. This picture is what I yearn for.

Knowing that something could be this way, or could be that way, is all well and good.

What I want is a clear and concise and complete map showing the exact structure of my computer files, right now, exactly as they are stacked up, physically or virtually, today. If Linux wants the root directory of my Windows C:\ drive to be called /media within Linux, I can live with that, now that you have told me, but nothing else would have told me that until I dug around to and see which directories I might recognize inside of it, and make assumptions.

I specifically set up the larger Linux partition called /home for safety and backup issues. I am pleased that it is working as I hoped.

I have not yet ventured to rename it &quot;Data&quot; as old Fred suggested but I am going to try that soon.

I am getting there. Thanks again, all

I think maybe the problem with this thread is that we don't know exactly what you want to know (not your fault, you don't know exactly what to ask). 

Like Fred said, when you have a folder open in the GUI, make sure View > Sidebar is ticked, then click the button at the top of the sidebar and select Tree.  You'll get this:
[IMG]http://img532.imageshack.us/img532/368/screenshotbrlttyfilebro.png[/IMG]
Filesystem(''/'') is the root of the tree, your computer.  
Just to be confusing, the GUI knows that your home folder is probably the most important one, and the one you will most often navigate to, so it copies the icon for it to outside the tree (as well as it still being inside the tree, of course) and renames it from ''/home/harry'' to ''Home Folder''.
But this hasn't actually copied any files or directories, or moved anything, it's only copied th icon shown by the GUI, as an aid to fast navigation. 

Note the blue highlight on /lib/britty, this is the current location, and you can see it's also at the top of the window (no need to turn this on, it's on by default).
 Note though that if you are in your home directory, or a subdirectory of it, the path shown at the top there will be shortened from ''/home/harry/yourLocation'' to ''harry/yourLocation'' but this is only changing what is displayed (for ''convenience's'' sake ;) ), it has no effect on your location. Rest assured, you *are* at /home/harry/yourLocation. 

Just to drive home a point already made by Fred, do NOT rename your /home directory to something else.  You can name and locate directories you create however you like, but don't change ones created by the OS. 

Just thought I'd point out for interest's sake that you can see in the image that I have a directory called 'diskD'. This computer is my girlfriend's, who is used to Window's way of showing extra partitions so I created /diskD and mounted the partition, that used to be called D when she had Windows, there.

---

### Post by The Cog on 2010-06-12
@formaldehyde_spoon: 
Your pictures are wonderful - you have a talent there.

@harry003: 
Most of your queries should have been answered, especially once you know how to get the tree panel up in nautilus. I will add a couple of comments though:

In *nix systems, a partition can be mounted into any existing directory (folder) in the existing filesystem tree. When you do this, any existing contents of that folder become replaced with the contents of the partition you are mounting there, until the partition is un-mounted again. It's not often useful to have great swathes of your file tree disappear when you mount a new partition, so it is normal to create an empty folder to mount the partition you want to mount into. When you plug removable media in, Ubuntu will create a new folder in /media and mount the removable media contents into that new folder. The new folder is often given a name that matched the UUID of the partition - a number set when the partition is formatted. Attached is a screenshot of my media player which is currently recharging on USB. If the partition has been given a LABEL, that label will be used as the folder name. My backup disk always mounts as /media/BACKUP. I haven't bothered to label my media player, obviously. More permanantly mounted drives/partitions are traditionally mounted under /mnt instead of /media, but I suspect that /media is slowly becoming the default place. It it possible (but confusing) to mount one partition/drive to more than one place at once.

---

### Post by zer010 on 2010-06-12
Even though I understand the FS already, the diagrams and analogies are great. Great work everyone!

---

### Post by lavinog on 2010-06-12
> **harry003 said:**
> 
I think that qyot27 may be right, Vista and Windows 7 completely lost me when they created a (as I see it) false non-reality in the files structure. My computer is "harry" and so in my Windows 7 file system what I see at the top of the screen in Windows Explorer is "harry" that is presented to me as a top level directory (it is not something that I created or endorsed in any way, it just appeared, of course).

But "harry" is actually a sub-directory to "Documents and Settings" which is itself a sub-directory to the C:\ drive. Why create a deception like that?


Although it might not be what you are asking for, but Windows also links "C:\Documents and Settings\" to "C:\User\" (this is called a junction point in windows, and a hardlink in linux.)  This was done to maintain compatibility with older software.
From the parent folder (C:\) it looks like you have 2 subdirectories with identical contents, but the information is only stored once.
For the filing cabinet analogy: you would have two folders (foo and bar.) The bar folder would contain a bunch of documents, and the foo folder would contain a post-it saying "See bar folder"
Actually that analogy better describes symbolic links.  A more accurate analogy for hard links would be to reach into the foo folder and grab a document from the bar folder.

---

### Post by harry003 on 2010-06-13
Thank you all so much. I cannot believe the outpouring of interest and response on this topic. With 600 views in 3, days this one is obviously something that is on a lot of people's minds.

I have asked a few other questions during my 3 months in Ubuntu-world, and gotten to the solution in a few hours, or weeks, with the help of a few, or quite a few, responders, who made guesses that were anywhere from sincere but worthless to right on. But those were questions like "how do I get this wireless card to work in Lucid when I only have Windows 7 drivers?"

This was a conceptual or even philosophical "problem" that I never really articulated as a proper question. Ultimately, the simplest form of what I was asking was: where is LIST and TREE? but I really wanted more than that.

And of course we all know that with computer hardware and software, asking the proper question using the proper terminology is all-important to getting a usable answer. Those of you who are working to bring Ubuntu to the common man should endeavor to keep a precise list of questions wrongly asked by ignorant newbies, and what "common" words and terminology in plain English are referring to specific programming terms.

To address certain specific points, and by the way 

THANK YOU ALL EVER SO MUCH FOR THE DOZENS OF MAN-HOURS YOU HAVE SELFLESSLY DONATED TO THIS - YOU REALLY ARE SAINTS !

Lavindog, your comment about (junction points/hardlinks) really opened my eyes. I would never, in 99 years, have even conceived that something so transcendantly stupid and convoluted would even exist. Reach into the foo folder and pull something out of the bar folder?!? What is that supposed to be, black magic? Is that what libraries and playlists are all about? I have never understood any of that stuff.

F_spoon, your visual aids are magnificent. As much as I hate the concept of taking different roads to get to the same place, actually having a limb of the tree appear to be attached at 2 different points on the trunk, with 2 different names, is mind-boggling. Is it possible to turn off this "feature" of showing the "sub-sub" folder at the top and just start at / with nothing above it? 

Telling me to "Rest assured ... " and stripping away the front end of the path is a horrible thing to do, in my opinion, can that be fixed? That is a great concern for me. And I must beg to differ with what you said, the blue bar at the top says "britty - File Folder" (although it is cut off in your picture). Sure would be nice if that was an accurate and complete path - that is where I would MOST like to see it.

Lastly, old fred, you gave me the "short version" of my original question, after multiple days and dozens of posts - you told me how to find TREE.

---

### Post by formaldehyde_spoon on 2010-06-13
> **harry003 said:**
> ...
Lavindog, your comment about (junction points/hardlinks) really opened my eyes. I would never, in 99 years, have even conceived that something so transcendantly stupid and convoluted would even exist. Reach into the foo folder and pull something out of the bar folder?!? What is that supposed to be, black magic? Is that what libraries and playlists are all about? I have never understood any of that stuff. The file system stores a name for a directory, and then a location for it on the disk.  If two directory entries store the same location, then two directories in the tree will both go to the same location.  Don't worry about this, you aren't likely to come across it in your day-to-day activities, but hard links are a powerful and important tool. 

> F_spoon, your visual aids are magnificent. As much as I hate the concept of taking different roads to get to the same place, actually having a limb of the tree appear to be attached at 2 different points on the trunk, with 2 different names, is mind-boggling. Is it possible to turn off this ''feature'' of showing the ''sub-sub'' folder at the top and just start at / with nothing above it?Not as far as I know, but there are others here who know much more about this than I do.
Note that the extra icon made by the GUI is NOT in the tree, it's at the same level as ''/'', so outside the tree.
You can just ignore it if you like.

 > Telling me to ''Rest assured ... '' and stripping away the front end of the path is a horrible thing to do, in my opinion, can that be fixed? That is a great concern for me.   A little confusing if you don't know it's happening, but it does display a box like ''[ < ]'' to show that it's shortened, and you can click this box to see the full path.  
In Ubuntu 9.10 and earlier you could witch between the ''buttons'' view and a textual view which didn't get shortened, so I'm sure it's possible.  > **harry003 said:**
> And I must beg to differ with what you said, the blue bar at the top says ''britty - File Folder'' (although it is cut off in your picture). Sure would be nice if that was an accurate and complete path - that is where I would MOST like to see it.
...

This depends on the Window Border (Metacity) you select in System > Preferences > Appearance > Theme > Customize > Window Border.  
None of the defaults supplied display a full path, but you could look up how to customize Metacity themes and then edit the file like usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml (for Clearlooks, for example)
But I don't personally feel it's necessary, because the same information is replicated just below the toolbar.

Thanks everyone for the comments about my images. ;)  I can't take the credit though, I used [Xmind]("http://www.xmind.net/") to create trees, I just drew the wonky triangles around the outside.

---

### Post by technmom on 2010-06-13
I am also not understanding the file structure. I started using ubuntu because I needed to get a video off a separate server. So I went through SSH and logged into that server. Now I have another file system that makes no sense to me. 
I read things about not being the root, but don't really understand that. When I created my user I assume I am not at the root..
I commiserate!

---

### Post by harry003 on 2010-06-13
f_s your comment about "Don't worry about this, you aren't likely to come across it in your  day-to-day activities ... " is far from true in my case. For years, as a Windows user, the first thing I did when I booted up was call up Windows Explorer.

If I want to hear a song, I navigate to it and double-click on it. If want to work on a spreadsheet, I navigate to it and double-click on it. After the spreadsheet program is open, and I want another one, THEN I might go up to File/Open etc but I still have to navigate.

Perhaps I am different, but this is the way I do everything, and it seems to me the most logical and comfortable way. Maybe you could characterize it by saying that I am a GUI user who likes to delude myself and pretend that I am working a little closer to the system level, without really understanding what I am doing. But I am a map person - if I am driving, I need to see a map. Telling me to turn left at the 4th light then right at the brick church is just not the way my mind works.

Another problem that I created for myself is that my Windows computer is "harry" and my Ubuntu computer is "harry" and they both have sub-directories "Downloads" and "Documents" and so that is part of why the path is so important! 

I need to know whether I am in (C:\Documents and Settings\harry\Downloads - aka - C:\Users\harry\Downloads) or in (/File System/home/harry/Downloads - aka Home Folder - aka - /home which is actually an entire and discreet partition on my hard drive that is just "plugged in" somewhere down the line in a smaller directory's file tree). I understand that this is a trap I totally set myself up for, but it does not change the underlying conundrum.

For someone comfortable with this system, I can imagine uses for it, but for someone like myself, it is utterly confusing and an enormous stumbling block. And from some other comments to this thread, I must not be alone.

Thank you again for your time.

---

### Post by harry003 on 2010-06-13
2 more very quick side questions:

sometimes I see 3 forward slashes, I presume that means root, but why does it show like that?

after technmom there was a reply from eyedoctor that seems to be gone now. can you delete your own posts, and why?

---

### Post by QLee on 2010-06-13
[QUOTE=harry003]
... For someone comfortable with this system, I can imagine uses for it, but for someone like myself, it is utterly confusing and an enormous stumbling block. And from some other comments to this thread, I must not be alone.[/QUOTE]

At this point, you might choose to have a look at this:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

These also might help:
[http://tldp.org/LDP/tlk/fs/filesystem.html](http://tldp.org/LDP/tlk/fs/filesystem.html)
[http://tldp.org/HOWTO/Filesystems-HOWTO.html](http://tldp.org/HOWTO/Filesystems-HOWTO.html)

---

### Post by harry003 on 2010-06-13
QLee thank you, I will check out that paper. It seems that I must manually page through but that is not the worst thing.

f_s I think I had a eureka! moment a few minutes ago when I started to use my laptop to play some music while I did paperwork. Looking through my guides made it look like what I want is possible but did not say how to do it.

In the dreaded Ubuntu "Home Folder" is a directory called "Music"

If I am understanding the process correctly, what I COULD make use of is to mount my REAL Music folder (C:\Documents and Settings\harry\Music) so that it showed in Ubuntu in place of the OS-created (empty) Music folder. 

Is that what this is about? Can I do it, and how?

The more I dig through this the more I wish that all these things did not carry the same names in their respective partitions.

Thanks a lot.

---

### Post by teilnehmer on 2010-06-13
Hey people, 

I really enjoyed reading this discussion. It's a very friendly atmosphere!

harry003, I remember setting off into Linux with similar difficulties. I, too, thought of the Windows way as factually representing my computer. C:\ is a hard drive. I put it into the machine, and now I see it and see everything on it. D:\ is another hard drive where I have all my data. Fair enough. It's like having one garage for my car and another for some stuff I don't need in the house. 

It must seem utterly confusing that, in Linux, this second garage can be put anywhere in the first garage. Other metaphors that were insightfully given fit the realities of a unix system better, but maybe the garage one fits your confusion. 

As you come from a physical engineering background, I'm sure you're aware that everything we use to describe computers is a metaphor. There are no "directories", really, there are zeros and ones, stored on a magnetic hard drive. At the very core, something like "C:\Documents" is an abstraction of some of these zeros and ones.  

The decisions how exactly to represent these zeros and ones are arbitrary and do not necessarily aim for "most realistic representation of data structures", but for usability.
In Linux, the decision was not representing a seemingly objective architechture of DATA, but a presentation of THE SYSTEM, which lives somewhere (on a harddrive), and anything else is sorted underneath, "mounted" somewhere inside the system. 

Regarding hard drives, this seems to make less sense. Regarding a computer system, it makes more sense (or at least the same amount of sense). Linux sees the whole system as one hierarchical system, not as some spaces next to each other, of which some contain system items and some other items. 

Alas, the garage metaphor cannot hold up. A more fitting metaphor is that of a house (which would be / ). In this house, you decide how to organize all the data you got (living room, bedroom), and what used to be the bedroom can become a guest room. 
Please note: This house doesn't represent the hard drives. It represents the system. 
And that, I believe, is the fundamental difference in presentation that is flummoxing, but it is there.

---

### Post by srs5694 on 2010-06-13
> **harry003 said:**
> Lavindog, your comment about (junction points/hardlinks) really opened my eyes. I would never, in 99 years, have even conceived that something so transcendantly stupid and convoluted would even exist. Reach into the foo folder and pull something out of the bar folder?!? What is that supposed to be, black magic? Is that what libraries and playlists are all about? I have never understood any of that stuff.

Please refrain from calling a feature "transcendantly stupid" if you don't understand it. Links (both hard and soft) exist for real reasons. One common reason is to help with versioning. For instance, in the Linux library-naming system, libraries have names like libz.so.1.2.3.3, where 1.2.3.3 is the version number; but most programs that use libz only need be concerned with the first part or two of the version number (1 or 1.2). Thus, there's likely to be a link from libz.so.1 or libz.so.1.2 to libz.so.1.2.3.3. Programs can then use the library via this name (this process is often called "linking to" the library, but this is an entirely unrelated use of the word "link"). If the library is updated, say to version 1.2.3.5, the programs that use it don't need to be updated. If links didn't exist, then the programs that use the library would need to be recompiled, the library would have to exist twice on the disk (once under each name), or the library would have to exist using only the more generic name (which would likely lead to confusion and ambiguity).

Filesystem links are useful for things other than libraries (see below for another example relevant to you personally); they aren't library-specific. The implementation of play lists depends on the specific program in question. The ones I'm familiar with don't use links for this purpose, but I can imagine ways to do it with links.

Note I referred to hard and soft links. The versioning setup I just described is generally implemented via soft links, in which the link is a separate file that acts as an indirect pointer to another file. Hard links, by contrast, are implemented as two filenames that independently point directly to one file. The two types of links have subtly different properties that make them useful in different situations, although there's substantial overlap. Soft links seem to be more common in Linux.

> I need to know whether I am in (C:\Documents and  Settings\harry\Downloads - aka - C:\Users\harry\Downloads) or in (/File  System/home/harry/Downloads - aka Home Folder - aka - /home which is  actually an entire and discreet partition on my hard drive that is just  "plugged in" somewhere down the line in a smaller directory's file  tree).

First, you're mixing Linux and Windows nomenclatures on the locations. Those two locations could theoretically be one and the same thing, depending on how the various partitions are mounted in both OSes. (Windows reportedly supports mounting partitions in a Linux-like way, although I've never looked into this feature myself.)

Second, I'm afraid you're very confused about the Linux nomenclature. There is no standard Linux "/File System" directory (although you could create one). Chances are that what you referred to as "/File System/home/harry/Downloads" is actually /home/harry/Downloads. The root of the Linux directory tree is "/" (pronounced, and often referred to in print, as "root"). GUIs sometimes reference "file system" as a synonym for this, but it's not part of the path. Furthermore, an individual user's "home folder" is *not* the same as /home; /home is a specific directory that holds potentially huge numbers of individual users' home directories. Your own home directory (aka "home folder") is likely to be /home/harry or some other specific subdirectory of /home. Remember that Linux is a *multi-user* OS, so each user needs his or her own home directory. This fundamental architectural feature doesn't change even if the computer has just one user.

> sometimes I see 3 forward slashes, I presume that means root, but why  does it show like that?

I can't say without seeing the context. The most common use for three forward slashes I know of is in Web browsers, where you might see something like "file:///home/harry/foo.html" as a way to refer to the /home/harry/foo.html file. That's just part of the way URLs referring to files on the local computer are specified. At a shell prompt, a single forward slash ("/") refers to the root of the Linux directory tree. Adding more slashes has no practical effect, AFAIK. For instance, typing "ls /bin" has the same effect as "ls //bin" or "ls /////////bin". These might or might not be the same as typing "ls bin"; without the "/", the "bin" file or directory is interpreted as being relative to the current location. If you happen to be in "/" at the time, "ls bin" and "ls /bin" will produce the same results; but if you're anywhere else, "ls bin" will show you the bin file or directory in the current directory. For instance, if you're in /usr, "ls bin" will show you the contents of /usr/bin.

> If I am understanding the process correctly, what I COULD make use of is  to mount my REAL Music folder (C:\Documents and Settings\harry\Music)  so that it showed in Ubuntu in place of the OS-created (empty) Music  folder.

Sort of. You could create a symbolic link from /home/harry/Music (assuming you use "harry" as your username) to wherever the equivalent Windows directory is located under Linux. The latter location is not "C:\Documents and Settings\harry\Music" in Linux, since that's a Windows directory path that's meaningless in Linux. If you've mounted the Windows C: partition at /windows/c, then you'd do something like this at a Linux shell prompt:

```

cd ~
mv Music Music-old
ln -s /windows/c/Documents\ and\ Settings/harry/Music ./Music

```

Instead of the mv command, you could delete the Music folder, if it doesn't have any data you want to preserve. You'll need to change "/windows/c" in the ln command (which creates a link) to whatever the Windows C: partition's mount point is.

A caveat: I don't recommend giving direct access to one OS's key system partition(s) from another OS except on a temporary basis. This is because most OSes don't fully understand or honor other OSes' file access controls and security features, making accidental damage to the first OS from the second far too easy. If you want to store music, video, word processing, or other files that will be frequently accessed by two OSes, I recommend you create a separate partition explicitly for this task. This minimizes the risk of your accidentally damaging your Windows installation from Linux or your Linux installation from Windows.

---

### Post by oldfred on 2010-06-13
You can mount your music a couple of ways. I have all the "data" folders now in a /Data partition and link them so they look like they are in my /home but are else where. I also directly mount a shared partition into /home but it appears as /home/fred/shared and then my folders are inside that. I do not write into my windows XP system partition if I can help it so I created a shared NTFS partition for any data I want to use in both.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I had to delete the current Music folder adn from my home I did this.
ln -s /usr/local/fred/data/Music

If you are not in the folder you want to put the link then you have to tell it where to go.
see this for more info on linking
man ln

Depending on how you mount windows

ln -s yourwindowsmount/harry/Music

Are you mounting windows in fstab 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

These are my mounts in fstab, the shared works better with just defaults:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768                      /media/cdrive      ntfs-3g      defaults,locale=en_US.UTF-8,fmask=0111,dmask=0000         0  0

---

### Post by Don1500 on 2010-06-13
Try this, go to PLACES=>COMPUTER in the upper left of the screen.

Does this look familiar? Now you have the drives you are looking for and everything flows down from there.

The File system Icon is your "SYSTEM" or the place where all the operating system is, everything else is auxiliary. 

In the file system is "HOME", and all the stuff that would be in windows/system32 of a windows installation (and the PROGRAMS directory).

In "HOME" you will find "Harry", this is your "Documents and Settings/user-name" folder. You should have access to anything in this directory. (don't worry about the other folders in "HOME" you'll learn about them as you go along.

BACK to "PLACES=>COMPUTER":
All the other hard drives, CD-Drives, Pen-drives, Floppy Drives, etc. connected to your machine are here. They may not be mounted, and you may not want them mounted, your choice, unlike windows where everything hooked up is "alive". You can have a drive mounted on startup or only when you want it to mount. A drive not mounted is not accessible to any attempt to use it without authorisation (a security level not available in windows). Separate partitions are treated as separate drives here so you have to learn the names. None of my drives show up with the UUID number here but rather the Volume Name I gave them.

Hope this helps.

---

### Post by The Cog on 2010-06-13
Of the top-level icons in the nautilus tree view, the File System icon will show you the entire filesystem, starting at the root directory / and under that are /bin, /etc, /home and friends. These are all system directories that normal users aren't interested in, and don't have write access to. 

In *nix, each user has their own home folder under /home and that home folder is their domain, and normal working area, e.g. /home/andy, /home/bill, /home/charlie and so on. The nearest windows equivalent would be documents and settings/username. Since users can only write to their home folder, normal users are not normally interested in looking up/outside their little domain, it does actually make sense to give the file manager the ability to concentrate on that area and just ignore all the other stuff. The Home Folder does this - it just shows you the sub-are of the filesystem that users spend all of their time in. I think half your difficulty might be just not having realised that the Home Folder view is just a "local area" map, a subset of the bigger tree. Anyway, you know how to see the full tree now.

Also in *nix, there is a strong separation between the role of user and of administrator. You will slowly get used to that distinction - every time you want to do administrator type things, you will have to give your password. As you mentally switch roles, you also, to an extent, switch between worrying about only what goes on inside your home folder to worrying about what goes on in the rest of the computer filesystem. Once you get used to that mental switch, having a File System icon and a Home Folder icon in nautilus really does make sense. Little Pond, Big Pond, Little Pond, Big Pond. Hope that doesn't sound too stupid.

> If I am understanding the process correctly, what I COULD make use of is to mount my REAL Music folder (C:\Documents and Settings\harry\Music) so that it showed in Ubuntu in place of the OS-created (empty) Music folder. 
No. You cannot mount a folder, only a drive/partition. So you can mount drive C: into your filesystem somewhere, maybe /media/C or /mnt/C, wherever you want, really. You need an entry in the configuration file /etc/fstab if you want the drive to get auto-mounted as the PC boots. Then you can make a link inside /home/harry/Music to /media/C/Documents and Settings/harry/Music to use as a short-cut. To make that link, do the following:
1: Open a nautilus file explorer and navigate to your /home/harry/Music directory
2: Open a second nautilus and navigate to /media/C/Documents and Settings/harry/
3: Using the **middle** button on the mouse (scroll-wheel?), drag the Music folder from Documents and Settings in the second nautilus, and drop it in the  first nautilus window. A pop-up menu will ask if you want to copy, move or link the folder. Choose to link it. Now in your home Music folder you have a link called Music that takes you to the windows music folder. I would be inclined to rename the link to Windows-Music or something like that.

If you want help making your windows disk always mount into the Ubuntu filesystem, you are probably better off starting a new thread. But basically it consists of making a folder for it to mount into (maybe /mnt/C as a suggestion), and editing the file /etc/fstab, adding a line in there that says to what partition to mount where, and what mount options.

---

### Post by harry003 on 2010-06-13
Each time I figure this thing is over I get new responses and learn and understand more.

First, SRS5694 I stand chastised and you are right, I should not call a system stupid. In my defense I will say that I have always been a single user on my "personal" computer and have been perpetually annoyed at all the things I perceive as stumbling blocks that are embedded in every OS to accommodate multiple users. This is my problem.

Thanks for the advice on how to create links to my music files, and it is good to know, but that is not what I want. Making my file system look like a plate of spaghetti-like links is the opposite of what I want. I want everything to be as clean, simple, and direct as it can possibly be.

Knowing what I now know, I would prefer to strip out every single link that I can feasibly eliminate, and go directly to the source file I want, wherever it actually resides. A few extra keystrokes or mouse clicks is well worth the satisfaction of feeling that I am going to the source. It is also enormously helpful at backup time.

Maybe that brings me full circle to my original post wanting to know the original, un-linked location of my files.

At some point during all this, an icon appeared on my desktop called simply "Computer" that puts me in Places in a differently-appearing setup than usual. (I wish I could figure out how to embed a screenshot in this message but it never seems to work.) It is a great starting place, and seems to refer to my entire 250GB hard drive, and the Windows partition ("Acer" 190GB) directly, but after I click on anything in it and move away, I can never get back there.

I hope some of you gurus are hanging onto this thread. Last I looked it is getting well over 200 views per day, so it must be a hot topic that might be addressed, somehow.

thanks again

---

### Post by formaldehyde_spoon on 2010-06-13
> **harry003 said:**
> f_s your comment about ''Don't worry about this, you aren't likely to come across it in your  day-to-day activities ... '' is far from true in my case. For years, as a Windows user, the first thing I did when I booted up was call up Windows Explorer.

If I want to hear a song, I navigate to it and double-click on it. If want to work on a spreadsheet, I navigate to it and double-click on it. After the spreadsheet program is open, and I want another one, THEN I might go up to File/Open etc but I still have to navigate.

Perhaps I am different, but this is the way I do everything, and it seems to me the most logical and comfortable way. Maybe you could characterize it by saying that I am a GUI user who likes to delude myself and pretend that I am working a little closer to the system level, without really understanding what I am doing. But I am a map person - if I am driving, I need to see a map. Telling me to turn left at the 4th light then right at the brick church is just not the way my mind works. This thread is still going strong! 
Good! I'm enjoying it. ;)

Those activities are not using hard links, and to answer your earlier question, playlists etc. are not examples of hard links.
Off the top of my head I can't think of any hard links that exist in the system by default after an install, but there are others who will know better than I do if that's true.
You will find some soft links inside the /lib folder, but that's all I can think of.
Like I said, you really aren't likely to come across hard links very often, if at all.  

> Another problem that I created for myself is that my Windows computer is &quot;harry&quot; and my Ubuntu computer is &quot;harry&quot; and they both have sub-directories &quot;Downloads&quot; and &quot;Documents&quot; and so that is part of why the path is so important! Do you actually mean that your **username** on Windows and Linux is Harry? You do also name your ''computer'' for networking purposes, but I suspect you are actually talking about users, not computers.  Could you confirm this?  

> I need to know whether I am in (C:\Documents and Settings\harry\Downloads - aka - C:\Users\harry\Downloads) or in (/File System/home/harry/Downloads - aka Home Folder - aka - /home which is actually an entire and discreet partition on my hard drive that is just &quot;plugged in&quot; somewhere down the line in a smaller directory's file tree). I understand that this is a trap I totally set myself up for, but it does not change the underlying conundrum.
... I'm not sure how to answer that, could you post the contents of /etc/fstab (''cat /etc/fstab'' will do it) and the result of entering ''sudo fdisk -l'' and ''sudo blkid''.
This will let us understand your system better. 
> **harry003 said:**
> ...
sometimes I see 3 forward slashes, I presume that means root, but why does it show like that?
... A little more confusion for you... 

Do you mean 'computer:///'?  This is not a real location, but the GUI file browser puts this fake location 'above' the root of the tree.  
It shows (as I remember) 'FileSystem' which is '/', and also any partition currently mounted in a subdirectory of /media, including CDs and external disk drives.  There is also an icon for the CD drive when it is empty, which basically does nothing. So if you don't want the GUI to display icons for partitions here, don't mount them in /media, mount them somewhere else.

Bear in mind that these icons will transport you inside the tree to the mount point for these partitions.
If the CD drive is empty then the icon doesn't correspond to a location.

Again, it's not a real location. It's very similar to Windows' 'My Computer' which is also not a real location.  It just shows all partitions mounted in /media, plus Filesystem for '/' and Home Folder for '/home/harry'. 
  > **harry003 said:**
> ... 
f_s I think I had a eureka! moment a few minutes ago when I started to use my laptop to play some music while I did paperwork. Looking through my guides made it look like what I want is possible but did not say how to do it.

In the dreaded Ubuntu ''Home Folder'' is a directory called ''Music''

If I am understanding the process correctly, what I COULD make use of is to mount my REAL Music folder (C:\Documents and Settings\harry\Music) so that it showed in Ubuntu in place of the OS-created (empty) Music folder. 

Is that what this is about? Can I do it, and how?
... I think a couple of people have now already told you that won't work.  You could mount the partition your music is on there.
If you music is on your Windows partition you could mount it at /home/harry/Music, and then your music would be available in Linux at /home/harry/Music/Documents and Settings/harry/Music/ 
But this seems a convoluted way to do it! ;) 
Post the stuff I asked for above, someone will be able to give you a good suggestion on a nice way to make your music available in Linux.  
> **harry003 said:**
> ...
Maybe that brings me full circle to my original post wanting to know the original, un-linked location of my files.
 For that you can just look at 'Filesystem' in the tree, and nothing else. 
> At some point during all this, an icon appeared on my desktop called simply &quot;Computer&quot; that puts me in Places in a differently-appearing setup than usual. (I wish I could figure out how to embed a screenshot in this message but it never seems to work.) It is a great starting place, and seems to refer to my entire 250GB hard drive, and the Windows partition (&quot;Acer&quot; 190GB) directly, but after I click on anything in it and move away, I can never get back there.
...Again, the stuff I asked for at the top will make it much easier to explain this to you.
What version of Ubuntu are you using?  You have the textual location display in your GUI that I mentioned earlier in the thread, instead of the 'buttons' version.

---

### Post by JKyleOKC on 2010-06-13
> **harry003 said:**
> f_s your comment about "Don't worry about this, you aren't likely to come across it in your  day-to-day activities ... " is far from true in my case.The reason you're not likely to come across it in your day-to-day activities is because hard links apparently don't exist in an out-of-the-box installation, not because you won't be looking for them. You can create hard links, but you have to do it yourself if you want them -- and for many reasons, you ought not try them until you understand all that you're looking for about the file system!

Soft (or symbolic) links, on the other hand, are quite frequent throughout the systems, and are quite useful for many reasons. One of the most common uses of a soft link is to simplify reference to your CD drive. When it's mounted by the system, it may get a name such as /dev/cdrom0 or even /dev/opticaldrive1. The system automatically creates a soft link so that you can refer to it as simply /dev/cdrom no matter what its actual name happens to be.

In the days when standard modems and dial-up were the only tools we had for getting connected, the modem might be /dev/stty0 or /dev/stty3 depending on which COM port it was set up for; a soft link to call it /dev/modem made it easy to standardize all the programs that used it.

One point that nobody seems to have yet mentioned is that in Unix-based systems, including all flavors of Linux, EVERYTHING involved in input and output is a "file" and is addressed in essentially the same way as every other file. Even the keyboard, monitor, and printer are treated as files. This is different from Windows, where files and devices are separate concepts. However, it makes the system a bit simpler to understand; input always comes from reading some sort of file, and output always writes to a file. The hardware devices are all collected in the main directory /dev. and if you browse through it you'll find the various consoles shown (the normal gui is /dev/tty7).

Searching through all of the main directories and their subdirectories is a great way to get a better grasp of the system's organization. Here are a few of the "conventional" names and their uses: /bin is for program files that anyone can run. /sbin is for system maintenance files that require special permission to use. /etc is where system-wide configuration information gets stored, similar to Windows' registry. /lib is where library files and documentation get stored. /var is where logs are written and system variables live. /usr is where Ubuntu puts most of its programs, rather than /bin or /sbin; within /usr you'll find bin, sbin, and lib directories again, with the same usage as their higher-level equivalents.

In your home folder, you'll see quite a few directories and files whose names begin with "." (if you press ctrl-h while in Nautilus; they are normally hidden to reduce the clutter). These are your individual configuration data, taking the place of much of the Windows registry.

---

### Post by srs5694 on 2010-06-13
> **formaldehyde_spoon said:**
> Off the top of my head I can't think of any hard links that exist in the system by default after an install, but there are others who will know better than I do if that's true.

You can find most of the hard links (to normal files) on your system by typing the following command:

```

find / -links 2 -type f

```

You can run it multiple times, increasing the links value from 2 to 3 to 4 and so on to find files with more than two hard links. I was surprised at how many turned up when I tested this on an Ubuntu 9.10 system. Most of them were time zone files, but some were command files, such as /bin/gunzip.

> **formaldehyde_spoon said:**
> You will find some soft links inside the /lib folder, but that's all I can think of.

There are many more than that. JKyleOKC has already mentioned one common use, in device filenames. They're also frequently used to provide duplicate names for commands (on my Ubuntu 9.10 system, bzcmp, bzegrep, nc, pidof, and quite a few other commands are all symbolic links), to link certain critical directories under duplicate names (/usr/lib64 is a symbolic link to /usr/lib on 64-bit Ubuntu; /usr/bin/X11 is a symbolic link to /usr/bin; and so on). You can find all the symbolic links on your system with the following command:

```

find / -type l

```

> **harry003]Thanks for the advice on how to create links to my music files, and it  is good to know, but that is not what I want. Making my file system look  like a plate of spaghetti-like links is the opposite of what I want. I  want everything to be as clean, simple, and direct as it can possibly  be.[/quote]

Since you seem to want to create identical Windows and Linux access paths to the same user data, I suggest you split your cross-platform data off into one or more separate partitions and mount it at the same location, relative to your home directory, in each system. For instance, you could mount it at /home/harry/Data in Linux, and research Windows' Unix-style mounting facilities to put it in an equivalent location in Windows. You can then store your data there, with no "spaghetti," since that seems to offend you.

Incidentally, I think "spaghetti" is the wrong analogy. You've said you like maps in previous posts. A link (hard or symbolic) is just an alternate route to a file, much like an alternate set of directions to reach a physical location. If I'm at Point A in a city and I want to get to Point B, I can map out any number of ways to get there. A link is just a way to specify an alternate route from Point A to Point B.

Remember also, as others have said, it all comes down to 0s and 1s on the hard disk or in the computer's memory. The physical reality bears very little resemblance to a directory path such as /home/harry/foo.html said:**
> I have always been a single user on my "personal" computer and have been  perpetually annoyed at all the things I perceive as stumbling blocks  that are embedded in every OS to accommodate multiple users.

I can understand this; however, you may want to consider a few points:


[list]
[*]Modern OSes (Linux, Windows, OS X, etc.) all run many processes in the background, and these processes have varying security needs. Therefore, these processes run using different accounts. Even if you're the system's only user, your system has multiple system accounts to keep bugs (or worse, malicious intruders) from stomping all over your vacation photos, destroying the documents you were creating for work, or whatever. Type "ps aux" to see all the processes running on your system, and check the first column ("USER") to see who's running them all. Chances are most of these processes will be owned by root or by your login username, but a few will be owned by other system accounts.
[*]As a single user on a multi-user OS such as Linux, you'll be unable to do too much accidental damage to the system as a whole without explicitly invoking superuser (aka root or administrative) privileges. On a simpler system, such as DOS or Windows 9x/Me, it's very easy to completely trash the entire installation with a single errant command. Maybe you've heard jokes (or horror stories) about people typing "FORMAT C:" by accident...?
[*]Having the machinery to support multiple accounts creates possibilities you may find useful at some point. For instance, you can create an account for a house guest without giving that person access to your own files. You can also create multiple accounts for yourself as a way to experiment with personal account or program settings without risking your regular settings.
[/list]

---

### Post by formaldehyde_spoon on 2010-06-14
Here's an image that may aid understanding of the ''Computer'' (computer:///) 'location'.  Possibly. 
It's a bit too big to embed inline, you'll have to click the thumbnail to see it. 
[[IMG]http://img72.imageshack.us/img72/1506/aa1s.th.png[/IMG]]("http://img72.imageshack.us/img72/1506/aa1s.png")  Uploaded with [ImageShack.us]("http://imageshack.us") 

I have Ubuntu installed on a single disk (although it has multiple partitions), a CD in the CD drive, and and external disk plugged into a USB.
The CD and external disk have automatically been mounted in '/media'.

I can click on the CD icon in 'Computer' to move to the CD and see it's contents, or I can get there by going to it's mount point in the tree: '/media/Ubuntu 10.04 LTS amd64'
Either way, I end up in the same place.

The icon in 'Computer' (and the extra icon outside the tree in the tree pane) are just placed there by the GUI as quick, convenient ways to get to '/media/Ubuntu 10.04 LTS amd64'.

Exactly the same applies for the external disk.

---

### Post by formaldehyde_spoon on 2010-06-14
Another way of conceptualizing the extra stuff 'created' by the GUI: 
[IMG]http://img20.imageshack.us/img20/1475/compr.png[/IMG] 
This is what your system would look like if you inserted the same CD and external disk that I just did.
The things in the cloud are not locations, they are just convenient icons for navigation.  > **srs5694 said:**
> ... 
 A link (hard or symbolic) is just an alternate route to a file, much like an alternate set of directions to reach a physical location. If I'm at Point A in a city and I want to get to Point B, I can map out any number of ways to get there. A link is just a way to specify an alternate route from Point A to Point B. 
...
More like a route from C to B, I'd say. 

Remember guys, this is the **Absolute Beginner** forum, and it is possible to be **too** helpful, and offer too much information. :p 
Links, especially hard links, aren't really something Harry is likely to come across any time soon, and I think they are making the fog a bit thicker...
But I'd hate to derail this thread by discussing what we should discuss, so I won't bring it up again.

---

### Post by formaldehyde_spoon on 2010-06-14
sorry, double post. mods, please delete...

---

### Post by harry003 on 2010-06-14
This is just too cool. I feel like the guy on one of those youtube  videos that knocks over the first domino and then it snakes through 3  rooms doing all kinds of amazing tricks.

What is particularly nice is that this is a true conversation amongst at  least a dozen people that has been viewed 1300 times in what, 5 days? Awesome! Whoever wants to write should shape this into something good.

My wife is a magazine editor so the printed word reigns supreme around our house (she works on a Mac in order to be seamless with the art dept).

I have purchased and checked out of the library probably something on the order of a dozen books on Linux and Ubuntu. I have also downloaded a couple of guides from this site, and none of them addressed what is being discussed here in a substantial and/or coherent way. Somebody here needs to take that on, as a project.

I have pretty well exhausted my questions, but I need to dream up something else for formaldehyde_spoon to produce great diagrams for. 

Now that I am starting to understand links, I want to get rid of as many of them as I can. I prefer to know where something is in case I need to back it up.

And yes, since I did not know how this really works, my computer is named harry, and my user name is harry in both OSs, everything has the same name, although I think that I might have named my Ubuntu partition hubuntu, and I know that the overall hard drive is named Acer under Windows. Next time I will know better and give myself a way to differentiate each of these items.

Are there any other questions I need to be asking? I will spend some time digesting what you have given me. Thanks again!

---

### Post by srs5694 on 2010-06-14
> **harry003 said:**
> Now that I am starting to understand links, I want to get rid of as many of them as I can. I prefer to know where something is in case I need to back it up.

My advice: Don't. Linux relies on both hard and symbolic links to work. Deleting the links in the system (that is, outside of your home directory) is almost certain to break something. It'd be like opening your car's hood, seeing the spark plug wires, thinking "those things are unaesthetic," and removing them for this reason. The mechanic will be happy to charge you for the service call and a new set of spark plug wires, but you won't be happy with the bill or the inconvenience.

I don't recall offhand what, if any, links Ubuntu creates in users' home directories by default. Deleting them is likely to be safer, in the sense that your computer will still boot if you delete them in error, but your desktop environment might no longer work, or it might do weird glitchy things. It's also possible that your software will automatically re-create those links you find so offensive.

So in sum, you should accept links for what they are: A useful tool. There's no law that says you have to create them yourself, but trying to rid them from a Linux system will cause you nothing but grief.

> I know that the overall hard drive is named Acer under Windows.

That's probably the name of the main Windows partition, not the entire hard disk. There's no place for a name in the Master Boot Record (MBR) partitioning data structures, so the disk as a whole can't have a name. (It can have a 4-byte ID number, but that's it.) Windows probably just shows you one partition on the disk, so you think it's the name of the whole disk, but in fact it's just the name of one partition.

---

### Post by JKyleOKC on 2010-06-14
> **harry003 said:**
> Now that I am starting to understand links, I want to get rid of as many of them as I can. I prefer to know where something is in case I need to back it up.

I don't think you've yet fully grasped what links do; either of the directory entries involved in a hard link contains the absolute same information about "where something is" as the other one -- and if you delete a hard link, that automagically deletes the actual file just as if you deleted the original entry! Here's what the "info" utility says about hard links: A "hard link" is another name for an existing file; the link and the original are indistinguishable.  Technically speaking, they share the same inode, and the inode contains all the information about a file--indeed, it is not incorrect to say that the inode _is_ the file.

Soft links, which seem to be the only kind that exist in the *buntu systems, are more like Windows' shortcuts on the desktop, and they serve much the same purpose. According to "info," they are a special file type in which the link file actually refers to a different file, by name.  When most operations (opening, reading, writing, and so on) are executed on the symbolic link file, the kernel automatically operates on the target of the link.  But some operations (e.g., removing) work on the link file itself, rather than on its target.

Thus it's safe to delete a soft link, but if the system expects to reach the file by its linked name rather than the more detailed original (which is true for many if not most of the files involved in booting up) you may make it impossible to boot the system.

To use your map analogy, removing all the soft links would be like erasing all the streets that you never use from your map.

> **harry003 said:**
> Are there any other questions I need to be asking? I will spend some time digesting what you have given me. Thanks again!There are many that you **could** be asking, but those of us who have been using the system for a while aren't the right people to list them because we cannot tell just which parts of the system you'll need more explanation about! I'm sure that you will find other points of puzzlement (to quote the King of Siam) as you progress through the adventure, and as you can see posting your own question here can trigger a flood of response from a wide variety of us and give you an assortment of viewpoints!

Your wife has my heartfelt sympathy about what's happening to her profession; I first sold material to a national magazine some 61 years ago, and earned my keep primarily as a professional writer and editor until switching to software development in 1990. Even then I kept writing for publication until the magazines I worked with shut down in December of 1997. Since then I've observed that almost all print publications are succumbing to economic pressures. Our local newspaper, which filled 50 pages daily and more than 100 on Sundays back in the 50s, now has less than a dozen pages most days! Magazines, too, seem to be a vanishing breed of publication -- which is too bad!

---

### Post by srs5694 on 2010-06-14
> **JKyleOKC said:**
> I don't think you've yet fully grasped what links do; either of the directory entries involved in a hard link contains the absolute same information about "where something is" as the other one -- and if you delete a hard link, that automagically deletes the actual file just as if you deleted the original entry!

If a file has hard links, you've got to delete all of them before the file is actually deleted. That said, deleting any one link could be damaging if the system expects to read a file using a particular name.

> Soft links, which seem to be the only kind that exist in the *buntu systems

As I wrote in an earlier message, hard links *do* exist on default Ubuntu installs -- or at least, there are quite a few of them on my Ubuntu 9.10 installation. Most of them are used to reference time zone data files.

> To use your map analogy, removing all the soft links would be like  erasing all the streets that you never use from your map.

The danger being that the delivery truck bringing your new TV, the plumber you've called to fix your sink, or the fire engine coming to put out the car on fire in front of your house might need to use the streets you've deleted!

---

### Post by harry003 on 2010-06-14
Yeah, I get it. I won't get rid of any links without knowing what they do, but I certainly won't create any new ones.

I would rather keep things as simple and straightforward as possible.

Especially at backup time, I want to know where everything important is.

This thread has been great fun, I am sorry it is winding down.

Thank you all so much, I have learned a lot!

---

### Post by formaldehyde_spoon on 2010-06-14
> **harry003 said:**
> This is just too cool. I feel like the guy on one of those youtube  videos that knocks over the first domino and then it snakes through 3  rooms doing all kinds of amazing tricks.

What is particularly nice is that this is a true conversation amongst at  least a dozen people that has been viewed 1300 times in what, 5 days? Awesome! Whoever wants to write should shape this into something good.

My wife is a magazine editor so the printed word reigns supreme around our house (she works on a Mac in order to be seamless with the art dept).

I have purchased and checked out of the library probably something on the order of a dozen books on Linux and Ubuntu. I have also downloaded a couple of guides from this site, and none of them addressed what is being discussed here in a substantial and/or coherent way. Somebody here needs to take that on, as a project.

I have pretty well exhausted my questions, but I need to dream up something else for formaldehyde_spoon to produce great diagrams for.  :p 

> Now that I am starting to understand links, I want to get rid of as many of them as I can. I prefer to know where something is in case I need to back it up.Don't do that. If you don't like links then restrict yourself to not creating any of your own.
A super brief summary of links:
Soft links: same as Windows 'shortcuts'. For files or directories.
Hard links: you can think of them as a copy of a file that has it's contents synchronized with the original. ie if you edit either one of the two, the changes will apply in both. For files only. 
> And yes, since I did not know how this really works, my computer is named harry, and my user name is harry in both OSs, everything has the same name, although I think that I might have named my Ubuntu partition hubuntu, and I know that the overall hard drive is named Acer under Windows. Next time I will know better and give myself a way to differentiate each of these items. Doesn't matter, this is only important for your own understanding of your system. 

Your disk isn't called 'Acer', it's 'called' ''250 GB Hard Disk''. Acer is a partition.
The format of the names you see in 'computer:///' are  '<Disk Name>:<Partition Name>'
If a partition doesn't have a name/label, the UUID (''insane name'') will be shown instead. 
If you want a visual explanation of disks/partitions, install gparted (sudo apt-get install gparted) and run it from System > Administration.  It will present the disk and partitions to you visually. Don't go changing stuff in there though unless you know what your changes mean. > Are there any other questions I need to be asking? I will spend some time digesting what you have given me. Thanks again!If you have more questions about your own system be sure to post the stuff I asked for on page 5.

---

### Post by qyot27 on 2010-06-15
> **harry003 said:**
> Yeah, I get it. I won't get rid of any links without knowing what they do, but I certainly won't create any new ones.

I would rather keep things as simple and straightforward as possible.

**Especially at backup time, I want to know where everything important is.**
To answer this particular part, if you mean just *your* files, then it would be everything in /home/harry.  In which case, there shouldn't be any links, or at least not any of note.  And copying the entirety of the contents of one's $HOME shouldn't be hard to manage.

If you mean the entire system, then the links would need to be backed up with the things they link to.  Considering they're probably less than a kilobyte in size, I don't think there'd be any kind of space concerns.  

If there are specific files you need to make sure to backup, then you'll just need to know where those exact files are.  But that only becomes relevant when you know there are other files that you had to edit in the first place.  Things like xorg.conf come to mind, at least for me, but that's because of my video card/monitor resolution issues, not *just because*.

If what you're concerned about are the program installations, then I'd recommend making a list of which apps were installed (along with listing any added repositories from whence they might have came), and have this list located in with the rest of your personal files in /home/harry.

---

### Post by Zeike on 2010-06-15
> **harry003 said:**
> I would rather keep things as simple and straightforward as possible.

Especially at backup time, I want to know where everything important is.

It is funny you bring this up.

Hard links are an incredibly valuable tool if you want to make incremental backups of large amounts of data.  By using hard links you can store the same version of a file in seemingly two different places without using twice the disk space.  This works extremely well with a program called rsync, to make wonderful automated incremental backups, not dissimilar to what Mac OS's 'Time Machine' does.

Also, it isn't as though links hide files from you in any way.  They point you right to the files.

---

### Post by -kg- on 2010-06-15
>  Originally Posted by harry003  View Post
Yeah, I get it. I won't get rid of any links without knowing what they do, but I certainly won't create any new ones.

I would rather keep things as simple and straightforward as possible.

Especially at backup time, I want to know where everything important is.

At this point, I'll add my little bit.

It would seriously behoove you to obtain external media, such as an external hard drive.  Such a drive is ***invaluable*** as a backup media, and can be used for other purposes, as well, such as separate storage for your music files that you want to access, without the necessity to mount your Windows partition from Linux (which, as has been said before, can be dangerous).

I have one (1 TB), and I not only store my music files there, but anything else that I don't particularly want cluttering up my main partitions, including my mail files.  I have Thunderbird set to store them all on that external hard drive instead of using my /home partition.  In that way, they're portable between my computers, rather than being tied to one.

As far as backup, yes, all your critical files are mainly stored under /home, and you can copy your /home directory to another location and be fairly well confident that you have your critical information ***that is stored under Linux*** backed up.  /home is "normally" not unusually large, unless you have many files stored there (like my 34 GB of mp3 files, alone!  Not to worry, though...I store those on my external drive! :p ).

I rather like to back up the entire partitions, or the whole hard drive (and all the partitions residing on it) instead.  That way, in case of catastrophic hard drive failure, you can replace the hard drive, create the partitions (or possibly the backup software creates them for you...I don't know, because I always create them manually), and reload the entire system...OS, files, and all...back the way it was before the failure.  That sure beats reinstalling the OS, loading your drivers, codecs, software, and reconfiguring everything, after which you reload your files.

It also helps if you screw something up and can't get back into Ubuntu.  Just take your backup file and reload the image, and you're back where you were before the screwup.  I used to make regular Ghost files in Windows, for just that occasion. :oops:

As far as partitioning goes...I have been partitioning ever since hard drives went over 2 GB.  Partitioning is handy dandy for a few reasons.

When hard drives first went over around 2 GB, there was a minimum "Cluster size" (a cluster is a sector, or group of sectors on a hard drive. A cluster holds one file, no matter what the file size) which depended on the size of the partition.

I would create separate partitions, one for the Windows installation and one for my data and text files in order to decrease the cluster size (especially in the data and text partition) to increase storage efficiency (or at least, that was the theory).

Nowadays, with extremely large hard drives and advances in the technology, minimum cluster size is essentially no longer an issue, and partitioning editors create partitions with cluster size set with "efficiency" in mind.  If I'm not mistaken, the cluster size can also be manually set, but with the size of the drives these days, it's essentially unnecessary.

Another advantage to more than one partition, at least in Windows, is defragmentation.  With separate partitions for the OS, software, and data, it is much easier to defragment the partitions, and varying data in one will not fragment the other.

A third is your favorite...ease of backup.  Instead of having to go all through your directories (folders, in Windows) and having to know where all the files are that you need to back up are, they're all contained in another partition (drive, in Windows).  Just back that partition (drive) up, and you have all your files without even knowing where they are or having to search for them.

If you would like a simple guide on partitions and partitioning operations, click on the link in my signature block.  Understanding partitions and partitioning can come in handy.  There are also links to back-up software and Live CDs which will aid you in backing up entire partitions and hard drives, such as my favorite, [Clonezilla]("http://clonezilla.org/").

---

### Post by harry003 on 2010-06-15
Hard disks are not in shortage. I am working in a hotel room 700 miles from home on a 2 month work assignment with this laptop I bought for the occasion. The first day I, partitioned the tail end of the 250GB hard drive for Ubuntu (20GB data, 10GB system, and 10GB swap, in that order, probably should have been reversed) and installed Lucid. I went through some serious pain getting everything (esp wireless) working, and re-installed Lucid a couple of times.

This has been my hobby at night (better than TV, huh?) and I have learned a lot, mostly on this forum. The books I have bought are a pale shadow of what happens here. Even though I have always been a book person, this is fun and real.

I installed Ubuntu on my big computer at home, my monster tower with multiple everything. I think I currently have 4 hard drives in it. I had not done much with it when I left, but I had given an entire 40GB drive over to Ubuntu. Generally I run XP on it and plan to keep it that way for a while.

I have 2 or 3 loose hard drives and a nifty USB plug that does not even have a case, so I can plug in whatever, whenever, wherever. I just need to do it more often, but I have multiple copies of everything. The absurd complication of this hardware is part of the reason I am so frantically trying to get my head around a whole new way of thinking about file management. The old way is not going away either. And not or.

---

### Post by lavinog on 2010-06-15
10GB of swap is a little excessive.
The thumb rule for swap is 1.5 * Ram...which should put you at 6GB.  That thumb rule is for back when memory was limited though.  With 4G of memory, you should be fine with 1G (I believe thought that 4G of swap is needed for hibernate, but someone else could correct me)

---

### Post by harry003 on 2010-06-15
This has been extraordinary and enlightening.

Is there an easy way to save this tread to a file, or print it, either on paper or to pdf?

I will spend quite some time trying to absorb all this and for some tasks, paper really is easier.

---

### Post by JKyleOKC on 2010-06-15
Most browsers can print to paper, but only one web page at a time. You can also "print" to PDF if you have an appropriate print driver installed. However, you can save the individual pages of the thread to your hard drive for reference just in case they should vanish from the forum.

I often just print the pages I'm most interested in to paper for future reference. Then I can use highlighters of various colors to mark points of special interest.

I don't know of any way to print or save the entire thread with a single command, though...

---

### Post by oldfred on 2010-06-15
I have a Firefox addin called autopager. It lets me keep scrolling down. It loads 2 or 3 pages and then as you scroll down it keeps adding.

When I went to the first page it printed 10 pages. After scrolling thru the entire thread it printed the entire thing to PDF on 58 pages - 5.7MB.

---

### Post by BobJam on 2010-08-26
formaldehyde_spoon pointed me here, and I'm glad he/she did.

My own thread on a similar issue, from which formaldehyde_spoon did the pointing, is at [http://ubuntuforums.org/showthread.php?t=1560160](http://ubuntuforums.org/showthread.php?t=1560160)

I'm surprised nobody has pointed this out yet.  I think the main reason Harry and I (and other noobs, I presume) are having so much trouble with this mounting concept is that **WE'RE STILL THINKING OF THINGS FROM A WINDOWS PERSPECTIVE.**

I, like Harry and many other noobs I presume, am a refugee from Windows.  Consequently, a lot of us still have that Windows mind-set.  As long as we think we'll understand 'nix things if they're put in a Windows reference, like /usr/ . . . is like \Documents and Settings, we're setting ourselves up for more confusion.

The big problem is that once you've got this Windows mind-set in your head, it's almost impossible to get it out of there.

**I BET SOMEONE WHO STARTED USING LINUX WITHOUT EVER HAVING USED WINDOWS BEFORE**, consequently not having a frame of reference set in their head for Windows architecture, **DOES NOT HAVE SO MUCH OF A PROBLEM UNDERSTANDING THIS "MOUNT" CONCEPT**.  It's like having a clean slate, and all you ever knew was Linux.

For the transition from Windows to Linux, that Windows-to-Linux comparison may be helpful at first . . . but that just makes it all the more harder to get rid of it and fully understand Linux.

Indeed, I wish I had never used Windows (since the days of 3.1) and started out with Linux.

Obviously I'm still struggling, like Harry perhaps, with Linux concepts, primarily because I'm trying sometimes to draw analogies with Windows.  In many cases, it's like trying to fit a round peg into a square hole . . . it just can't be done and confuses you even more when you try.

I've found that I get the best Linux "Aha" moments when I push Windows completely out of my mind . . . unfortunately, it keeps pushing itself back in . . . and just when I think I've got it, I say to myself "Geezz, I wonder how that would compare to Windows?.  And with that question, confusion reigns again.

So, like Harry maybe, I'm going to have to read and digest this thread several times, and hope I "get it".  Promising!

Thanks again, formaldehyde_spoon, for directing me here.  There have been a few times that I say to myself "I think I almost have it" . . . then of course that "How would this compare to Windows?" question pops back into my head and I'm all the way back at square one again.  Thanks, Mr. Gates!

---

### Post by QLee on 2010-08-26
Yes, it would be nice if everyone starting to use Ubuntu would start with the community documentation, something like:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

However, in general that doesn't happen, generally people don't even read through the "stickies" at the top of the absolute beginners talk, which have been placed there because of their usefulness to beginners.

Learning something new always takes some effort and usually some experience, meaning a time period during which mistakes are made. The people who have the most trouble are the ones who think that they "should" know this stuff without learning it first.

---

### Post by BobJam on 2010-08-26
@ QLee,

Yes, us Windows refugees think that simply because we used computers for years, the Windows experience should translate to Ubuntu.  We think that because we're computer savvy, this Ubuntu stuff, as you say, "should" come easy.  Talk about setting yourself up for frustration . . .

Nevertheless, I have in fact read all the stickies and the documentation, but I still wasn't able to get the hindrance of Windows architecture out of my mind.

If I were to give advice to a Windows refugee transitioning to Ubuntu, I'd likely tell them to **FORGET** Windows stuff, and approach it as if it were the first time ever that you sat in front of a computer.  Then the stickies and documentation would have much more meaning.

---

### Post by Vaphell on 2010-08-26
That windows experience will somewhat translate but only when you realize you need to operate on a more abstract level of ideas standing behind the actual implementations. It's like people who don't use Open Office because some option is called different in MS Word or functions in Excel are slightly different. Either you understand the concept of a document editor or a spreadsheet and can find your way around them or not - same thing with operating systems. When you try to translate your experience 1:1 you will fail.

Does more than 1% of windows users know why exactly drives are called A: B: C: D: and why C: is the most important of them?  It doesn't make any sense if you think about it a little. The only reason is that this is a decades old legacy cruft from the ancient dos era, first there were floppies and they took A and B, hard drives got C. Once you see beneath it, everything becomes easier to grasp.

---

### Post by Diametric on 2010-08-26
^^What he said.  Nicely put.

---

### Post by cariboo on 2010-08-26
> In Ubuntu, there is also a "harry" directory that seems to be the sole occupant of "home" but where is something that actually SAYS THAT? I created a Data partition for efficiency and security but who created "harry" ? Not I !

The installation created the **harry** directory, it is basically the same as c:\Documents and Settings\harry. All the configuration files for the programs you use as well as theming are contained there. The /home/<user> directory also contains:

[list]
[*] Desktop
[*] Documents
[*] Downloads
[*] Music
[*] Pictures
[*] Public
[*] Videos
[/list]

The directories are created during installation, to make Windows users feel a little more comfortable with the directories they can access without being root.

I found [this]("http://www.slideshare.net/Ahuka/linux-directory-structure-2979890") slide presentation that may help

---

### Post by Vaphell on 2010-08-26
i think you can compare linux to an USian school :-) Students get their own lockers with their name slapped on simply because they attend to that school and they can hold anything there (let's say ;-)) but they are not allowed to do whatever they want anywhere else, they have to obey the rules.
/home is like a wall of lockers and user's home dir is one of them, with premade shelves for different categories of stuff but you don't have to follow them. File/dir permissions are like what you can/can't do in parts of school.

---

