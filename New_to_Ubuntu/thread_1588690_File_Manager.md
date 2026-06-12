---
title: "File Manager"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Hans Upp on 2010-10-05
Installed Ubuntu last week and had a week of absolute HELL :mad: trying to get my head around it.
I am about 3/4 way up the wall with frustration, and don't have far to go till I go over the top.  It just seems to take complete control and allows you to do very little or nothing.

But right now I need a File Manager to show my hard disk file structure and partitions.

People refer to Nautilus, but I can't see any way to load that - applications (no) places (no) system (no) search for files (sure it lists nautilus files, but nothing loads)

I downloaded PC Man (seemed to be generally recommended) and all it shows is a list of meaningless crap :confused:

Any suggestions please as to how to get a file manager working to show what it ought to show, and do what it ought to do (i.e.manage files)?

Please, I'm at the end of my tether! ("Get a longer tether" would not be a helpful suggestion here)

---

### Post by Praveen30 on 2010-10-05
> **Hans Upp said:**
> Installed Ubuntu last week and had a week of absolute HELL :mad: trying to get my head around it.
I am about 3/4 way up the wall with frustration, and don't have far to go till I go over the top.  It just seems to take complete control and allows you to do very little or nothing.

But right now I need a File Manager to show my hard disk file structure and partitions.

People refer to Nautilus, but I can't see any way to load that - applications (no) places (no) system (no) search for files (sure it lists nautilus files, but nothing loads)

I downloaded PC Man (seemed to be generally recommended) and all it shows is a list of meaningless crap :confused:

Any suggestions please as to how to get a file manager working to show what it ought to show, and do what it ought to do (i.e.manage files)?

Please, I'm at the end of my tether! ("Get a longer tether" would not be a helpful suggestion here)

if i am right may be you want to see about the files and their spaces.you can use disk analyzer.it is built in.it will show you all files in a particular disk with the memory spaces which a particular file is taking.

---

### Post by philinux on 2010-10-05
> **Hans Upp said:**
> Installed Ubuntu last week and had a week of absolute HELL :mad: trying to get my head around it.
I am about 3/4 way up the wall with frustration, and don't have far to go till I go over the top.  It just seems to take complete control and allows you to do very little or nothing.

But right now I need a File Manager to show my hard disk file structure and partitions.

People refer to Nautilus, but I can't see any way to load that - applications (no) places (no) system (no) search for files (sure it lists nautilus files, but nothing loads)

I downloaded PC Man (seemed to be generally recommended) and all it shows is a list of meaningless crap :confused:

Any suggestions please as to how to get a file manager working to show what it ought to show, and do what it ought to do (i.e.manage files)?

Please, I'm at the end of my tether! ("Get a longer tether" would not be a helpful suggestion here)

Ok.

Nautilus i.e Places > Computer shows the file system. It manages files not partitions. It does it's job.

System>Admin>System Monitor. File System Tab will show you partitions. There's Edit>prefs to play with too.

System>admin>Disk Utility will also show partitions.

---

### Post by Hippytaff on 2010-10-05
[http://linuxcrunch.com/content/10-secrets-about-nautilus-file-manager](http://linuxcrunch.com/content/10-secrets-about-nautilus-file-manager)

---

### Post by Morbius1 on 2010-10-05
Nautilus is the file manager and it's your Home folder:

Places > Home Folder

*[COLOR=Blue]EDIT: Wow, 4 simultaneous replies. Is that a record?[/COLOR]*

---

### Post by Diametric on 2010-10-05
Sorry to hear you're frustrated.  First, before you move forward, I'm going to assume you're used to using MS Windows.  If that's so, and this is your first forray into Linux - it requires a bit of "unlearning" as Yoda would say.
 
There is a disk usage analyzer that comes with Ubunutu and it's located under "System" -> "Aministration"
 
Are you just trying to browse your files and directories?  If so, "Places" is a good place to start.
 
Slow your roll and ask lots of questions - I've found that most folks on here are great at answering questions.  SOmetimes the more advances users can give an answer that assumes a few things, but if that happens just reframe the question.
 
Good luck and welcome to Ubuntu Linux!
 
Cheers.

---

### Post by Hans Upp on 2010-10-05
No, its not the analyser I need.

I simply want to be able to do the things you'd normally do in a file manager.

[LIST]
[*]Create or delete folders and files
[*]Move or copy files from folder to folder
[*]Move or copy folders or files from one partition to another
[*]View the file/folder structure so you can see what is where
[/LIST]

and all those little, basic, everyday kind of things to make things work as they should

---

### Post by Calash on 2010-10-05
> **Hans Upp said:**
> No, its not the analyser I need.

I simply want to be able to do the things you'd normally do in a file manager.

[LIST]
[*]Create or delete folders and files
[*]Move or copy files from folder to folder
[*]Move or copy folders or files from one partition to another
[*]View the file/folder structure so you can see what is where
[/LIST]

and all those little, basic, everyday kind of things to make things work as they should

That is the "Places" menu.  

Where you may be running into issues is in how Linux creates and manages partitions and/or the permission scheme used.

There are no drive letters in Linux.  No matter how many partitions you have there are no letters assigned to them.  Instead they are displayed under the root, signified by the "/", also called File System under Nautilus.  Partitions are created under this point as directories.

The second part has to do with permissions.  As a standard user you only have rights to change/create/modify files under your home directory.  This is noted as Home Folder under places.  This is your world where all your configuration and documents live.

Writing outside of the home directory requires root privileged.  However unless you have a need to do so stick with using your home directory.

---

### Post by Morbius1 on 2010-10-05
> **philinux said:**
> Nautilus i.e Places > Computer shows the file  system. It manages files not partitions. It does it's job.
> **Morbius1 said:**
> Nautilus is the file manager and it's your Home folder:
Places > Home Folder
> **Diametric said:**
> Are you just trying to browse your files and  directories?  If so, "Places" is a good place to start.
I'm fairly certain you have your answer

---

### Post by philinux on 2010-10-05
> **Hans Upp said:**
> No, its not the analyser I need.

I simply want to be able to do the things you'd normally do in a file manager.

[LIST]
[*]Create or delete folders and files
[*]Move or copy files from folder to folder
[*]Move or copy folders or files from one partition to another
[*]View the file/folder structure so you can see what is where
[/LIST]

and all those little, basic, everyday kind of things to make things work as they should

Nautilus does all the above. However you will run into permissions problems with files outside of your Home directory. 

My favourite way round this is to install the package nautilus-gksu from synaptic or sofware centre. This gives a new right click menu item "open as administrator". It does need your login password.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by fatality_uk on 2010-10-05
Everyone posted before is correct, however what I "*think*" you want can be done. Go into the **Places** menu and select your home folder. Makes sure the side pane is activated. If there isn't a side pane on the left, hit **F9** that should bring it up.

Just above the items in the left pane, select the drop down menu and choose the **tree** option. This will give you a **"File Manager"**

---

### Post by searchfgold6789 on 2010-10-05
For the record, you probably will not see or open a program called nautilus, unless you run into problems, and even then rarely.
It is the equivalent of the Windows Explorer. You click on a file and it shows up.

---

### Post by oldos2er on 2010-10-05
> **Hans Upp said:**
>  It just seems to take complete control and allows you to do very little or nothing.


If you're coming from a Windows mindset, you might want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

File permissions are explained here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) and [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Hans Upp on 2010-10-05
oh, this is madness (and maddening)
I simply want to drag a couple of files into another directory and it says permission denied and then further "not allowed to change permissions because I am not the owner".
If I am not the owner, who-the-hell-is? It is my computer and my installation of ubuntu.

Why does everything have to be made so-o-o-o damn difficult?

I have now installed nautilus-gksu but it doesn't give me an "open as administrator" option.
However, I am already set as Administrator in users Settings.

**and also . . **
I have downloaded a file, and as to be expected, ubuntu has tucked it away in some secret place. No amount of searching by name or text will show it up. How do I find it now? :mad:

---

### Post by foxmulder881 on 2010-10-05
> **Hans Upp said:**
> I have downloaded a file, and as to be expected, ubuntu has tucked it away in some secret place. No amount of searching by name or text will show it up. How do I find it now? :mad:

Assuming you haven't changed the default directory, it should be in Home > Downloads

---

### Post by oldos2er on 2010-10-05
> **Hans Upp said:**
> I have now installed nautilus-gksu but it doesn't give me an "open as administrator" option.


You need to log out and log back in (or reboot) to activate nautilus-gksu.

I suggest you read the link I posted earlier about file permissions; they'll help you out.

---

### Post by ramjet_1953 on 2010-10-06
A few of pieces of information that may help you to get your head around how 'NIX file systems work.

1. Firstly remember that even in a 'Desktop Version' of Linux you are still a user, not an administrator.
This is one of the strong points of a 'NIX system, as it makes it fairly bullet-proof against all the nasties that plague Windows desktops.

2. If you are trying to copy files and you are getting permission issues, I would ask you why are you trying to copy files into the root directory?

3. Generally speaking, you should not need to do this and if you tamper with things in the root directory, you can bork your system.

4. I can understand your frustration, but let me ask you this: How long did it take you to master Windows? Remember, any 'NIX system is NOT Windows (Thank God!).

5. If you do a little 'Googling' on how the file structure of any 'NIX system is organised, and read it, you will begin to understand the logic of this file system.

6. Continue to ask questions on this forum and you will be surprised how many people will be there to help you.

Regards,
Roger :)

---

### Post by fatality_uk on 2010-10-06
> **Hans Upp said:**
> oh, this is madness (and maddening)
I simply want to drag a couple of files into another directory and it says permission denied and then further "not allowed to change permissions because I am not the owner".
If I am not the owner, who-the-hell-is? It is my computer and my installation of ubuntu.

Why does everything have to be made so-o-o-o damn difficult?

I have now installed nautilus-gksu but it doesn't give me an "open as administrator" option.
However, I am already set as Administrator in users Settings.

**and also . . **
I have downloaded a file, and as to be expected, ubuntu has tucked it away in some secret place. No amount of searching by name or text will show it up. How do I find it now? :mad:

I can only *assume* that you have **READ** the posts people have given you previously! Most of your frustrations should have been dealt with with those but if not, please see this screenshot.

If you are looking for a "Windows type" file manager, as you can see, it is possible. Your downloads will more than likely be in the downloads folder. Pretty much everything in your home folder is editable. Outside of that you need raised privileges, in the same way Windows XP for instance would ask you if you want to view files and folder in **c:\windows\**.

---

### Post by mastablasta on 2010-10-06
You can't access root files without permission, but then again neither can the viruses. and you odnt' need to.
 
all you do, you will do in your home folder. and most data is there (it's like my documents in windows). downloads, shared public folder etc. it's all there for you to use. 
 
ofcourse you could create more folders elsewhere but it's not practical, unless you have a separate parittion or disk you want to move the files to.

---

### Post by Morbius1 on 2010-10-06
You seem to be having a particularly hard time making the conversion from Windows to Linux.

First, you are not the administrator of your machine - root is. You as the first user have elevated administrative privileges but it's not the same. You do have the ability to become root for periods of time in order to accomplish things that only root can do. This is how Linux is set up and this is what differentiates it from Windows.

You seem to want to copy a file from X to Y but you can't because you are not the owner of the destination. This is as designed. If you tell us the source and the destination then perhaps it will clarify for us what you are attempting to do. If you're trying to copy something to a newly created ext4 data partition for example then you can easily alter the ownership to allow that. If you're trying to copy something to a location that root owns then that is another matter. 

If you've installed something from synaptic and now you can't find it's location go back into Synaptic, search for the package again, and select the "Installed Files" tab at the bottom of the window.

If you don't see the "Installed Files" tab then in Synaptic:
Settings > Preferences > General > "Show package properties in main window"

---

### Post by Calash on 2010-10-06
> **Hans Upp said:**
> oh, this is madness (and maddening)
I simply want to drag a couple of files into another directory and it says permission denied and then further "not allowed to change permissions because I am not the owner".
If I am not the owner, who-the-hell-is? It is my computer and my installation of ubuntu.

Why does everything have to be made so-o-o-o damn difficult?

I have now installed nautilus-gksu but it doesn't give me an "open as administrator" option.
However, I am already set as Administrator in users Settings.

**and also . . **
I have downloaded a file, and as to be expected, ubuntu has tucked it away in some secret place. No amount of searching by name or text will show it up. How do I find it now? :mad:

What "exactly" are you trying to do?  What files are you trying to drag and where are you trying to move them to?

As noted, several times, if you are trying to move files outside of your home directory you will run into permission issues.  You can do this, but without knowing what you want to accomplish it can be dangerous in that you gain the ability to overwrite system files at that point.

---

### Post by nikefalcon on 2010-10-06
[QUOTE=[Hans Upp]("http://ubuntuforums.org/member.php?u=1153128")]
No, its not the analyser I need.

I simply want to be able to do the things you'd normally do in a file manager.

[LIST]
[*]Create or delete folders and files
[*]Move or copy files from folder to folder
[*]Move or copy folders or files from one partition to another
[*]View the file/folder structure so you can see what is where
[/LIST]

and all those little, basic, everyday kind of things to make things work as they should
[/QUOTE]

Nautilus is what you use when you are looking at your files(even on the desktop). It is launched when you click on any entry in the "places" menu. Creating,deleting,renaming, moving is the same as in Windows Explorer.(rt. click, click n drag etc)

---

### Post by Hans Upp on 2010-10-06
First I'd like to thank everyone very much for their contributions.

I've been working through the issues and managing to resolve things bit by bit.

By way of example, for those who asked what I want to move and to where, I have installed VLC Media Player, a very common application.

That is buried deep in the labyrinth, or so it seems, as I had no control over where it was installed. But then I downloaded skins for the player and they are in my downloads folder. (See, given a choice, I'd have created a folder called 'Audio and Video Tools' and put all installations of any such kit in their own folders in there - logical, easy to locate, easy to organise and manage)

So the skins need to be transferred to a preset VLC sub-folder named Skins2 to become operational. So I managed to track down the VLC installation BUT even though Skins2 subfolder is present, it will not allow me to drag the skins files into it even though VLC wants them there.

Next issue. I installed Xchat, again another common application. Using Xchat I downloaded a file. Now I could see the file path by looking in [COLOR=Blue]'Recent Documents[/COLOR]' and it shows it as [COLOR=Blue]/home/my "profile"/xchat2/downloads[/COLOR], so looks fine so far hmmm? But when you come to use the File Manager (File Browser/Nautilus whatever) then [COLOR=Blue]/home/my 'profile/ [/COLOR]does not show the existence of xchat and from that obviously not the downloaded file, yet [COLOR=Blue]Recent Documents[/COLOR] still shows the path as before - mucho frustration!

It turns out that the Xchat installation is hidden - why???
So now, to get to the download, I've had to activate 'show hidden files'. 

That all seems a bit bizarre to me.  Somewhat akin to nailing one foot to the floor and then wondering why you can only move round in a circle.

---

### Post by cgroza on 2010-10-06
> **Hans Upp said:**
> oh, this is madness (and maddening)
I simply want to drag a couple of files into another directory and it says permission denied and then further "not allowed to change permissions because I am not the owner".
If I am not the owner, who-the-hell-is? It is my computer and my installation of ubuntu.

Why does everything have to be made so-o-o-o damn difficult?

I have now installed nautilus-gksu but it doesn't give me an "open as administrator" option.
However, I am already set as Administrator in users Settings.

**and also . . **
I have downloaded a file, and as to be expected, ubuntu has tucked it away in some secret place. No amount of searching by name or text will show it up. How do I find it now? :mad:


Every thing is in the home folder. I think you are lost somewhere at the base of the filesystem.

---

### Post by cgroza on 2010-10-06
Read this : 
[http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/](http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/)

---

### Post by Hans Upp on 2010-10-06
Read it now thanks
Helps understanding a bit

> Every thing is in the home folder
As you'll see from my last post, everything is **not** in the home folder.
The destination folder for those VLC skins for a start.

---

### Post by jjakspaw6 on 2010-10-06
I feel your pain Hanns... Linux is extremely frustrating when you first start out.... but so is windows. Especially vista and 7 with UAC.

I had the same difficulties that you're having... but I cheated and created a launcher on the desktop (right click on desktop and choose create launcher) the command is 

gksu nautilus  

it will still ask for your password but this will give super user rights in that window only and allow you to move files where you want... 

Be careful where you copy and edit files.. it could lead to more frustration. Like previously said, it is usually best to keep files your and folders in the /home.
I keep my mp3s in different folders on a separate partition. I used bookmarks (in nautilus) to add the folder to my places list.

---

### Post by Hans Upp on 2010-10-06
well, I have made /home a separate partition from the start, but now I'm wondering if I ought to make another partition just for my mp3s, because that will be a very complex set of folders.

---

### Post by oldos2er on 2010-10-06
/home/my "profile"/ is not a proper directory name; is that just an example?

/home/user/.xchat/downloads is where xchat saves downloads; the "." dot in front of xchat means the directory is hidden. You can view hidden files and folders in Nautilus by hitting Ctrl-H, or View, Show Hidden Files.

Linux file systems don't really deal well with file or folder names with spaces in them, for what it's worth.

Also you can change xchat's download directory, via menus Settings, Preferences, Network, File Transfers.

---

### Post by foxmulder881 on 2010-10-07
OP, I think you need to do a Linux Fundamentals course. I reckon it would help you a lot in at least learning and understanding to some extent what you are actually doing.

---

### Post by Calash on 2010-10-07
> **Hans Upp said:**
> First I'd like to thank everyone very much for their contributions.

I've been working through the issues and managing to resolve things bit by bit.

By way of example, for those who asked what I want to move and to where, I have installed VLC Media Player, a very common application.

That is buried deep in the labyrinth, or so it seems, as I had no control over where it was installed. But then I downloaded skins for the player and they are in my downloads folder. (See, given a choice, I'd have created a folder called 'Audio and Video Tools' and put all installations of any such kit in their own folders in there - logical, easy to locate, easy to organise and manage)

So the skins need to be transferred to a preset VLC sub-folder named Skins2 to become operational. So I managed to track down the VLC installation BUT even though Skins2 subfolder is present, it will not allow me to drag the skins files into it even though VLC wants them there.

Next issue. I installed Xchat, again another common application. Using Xchat I downloaded a file. Now I could see the file path by looking in [COLOR=Blue]'Recent Documents[/COLOR]' and it shows it as [COLOR=Blue]/home/my "profile"/xchat2/downloads[/COLOR], so looks fine so far hmmm? But when you come to use the File Manager (File Browser/Nautilus whatever) then [COLOR=Blue]/home/my 'profile/ [/COLOR]does not show the existence of xchat and from that obviously not the downloaded file, yet [COLOR=Blue]Recent Documents[/COLOR] still shows the path as before - mucho frustration!

It turns out that the Xchat installation is hidden - why???
So now, to get to the download, I've had to activate 'show hidden files'. 

That all seems a bit bizarre to me.  Somewhat akin to nailing one foot to the floor and then wondering why you can only move round in a circle.

It can take some time to get use to the difference in the file structure.  On top of that you end up having to deal with differences in the applications themselves.  

To start, to have full drive access in the GUI open a terminal, or hold ALT and tap F2 for the run line, and type the following

```

gksu nautilus

```


This will open up a file manager window with root permissions, allowing you to get the file where you need.  Since it is a "Root" window the home folder for that window is for the Root account.  Your personal home folder is under /home/user/

Be careful in this window and close it when you are done.  Root is powerful and dangerous, even more so than Administrator in Windows.

The Download location of xchat, along with needing higher privileges for VLC, are not so much issues with Ubuntu as they are with the applications themselves.  You see the same type of behavior in Windows with poorly designed applications.

I also noticed your question about a separate partition for mp3s/  This would have no benefit since you already have /home in a separate partition.  In Linux the only real benefit for separate partitions is to allow partition wiping without causing data loss.  Organization is all by folders and the partitions will be mostly transparent in the file manager. You will see them in the "Computer" level of nautilus, but that will just take you to their mapped location in your home folder.

---

### Post by QLee on 2010-10-07
[QUOTE=Hans Upp]...
By way of example, for those who asked what I want to move and to where, I have installed VLC Media Player, a very common application.

That is buried deep in the labyrinth, or so it seems, as I had no control over where it was installed. But then I downloaded skins for the player and they are in my downloads folder. (See, given a choice, I'd have created a folder called 'Audio and Video Tools' and put all installations of any such kit in their own folders in there - logical, easy to locate, easy to organise and manage)[/QUOTE]

Mr. Upp,
Naturally, in an operating system that is intended for multi-user, there is a difference in location of applications that are available globally and "customisations" or additions to a single user's interface, some of the complications you find are related to security and security is always a trade off between secure and easy to use. It might be useful for you to review the Linux file system hierarchy, to help you understand file locations. You can read the manual page for that by entering the command, man hier, in a terminal window.

[QUOTE=Hans Upp]...
 Somewhat akin to nailing one foot to the floor and then wondering why you can only move round in a circle.[/QUOTE]
Amusing. It's good you can keep your sense of humour during the process of learning a lot of new concepts. We haave to keep our sense of humour too, because lots of people come here and tell us how illogical and hard our chosen operating system is. Most of them eventually change their minds. As I mentioned above, security can be a pain, so can the alternative. It would be easier to come home from the store with an arm load of groceries if the door was left open, however, in many locations, if you didn't lock the door when you left your valuables would be gone when you returned.

The good news is that, when you learn how to operate in Ubuntu, you'll not have these problems that are related to differences to what you already know.


Edit: I found this pdf document which might have more info than the man page. It also gives you another download to practice with.
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf)

---

### Post by nikefalcon on 2010-10-07
I hope I'm not adding to your confusion. But you need to keep a few things in mind when you use Ubuntu.(and any Linux OS.)
Linux is based on UNIX(sort of); from the very start it was designed to run in a networked system, with multiple users using a given computer.(there was no thing such as a "Personal" Computer back then. Computers usually occupied entire rooms and were quite common in Universities etc. Users used the computer from various "terminals", which were used to interact with the central computer. Since many users used the same computer it was important to make sure that no-one messed up with each others files,and more importantly, no-one should screw up the system. This is where file permissions come in. A "owner" is usually one who creates the file, or owns a given directory(folder). A owner decides who has access to his stuff; he decides whether a user or a group of users can read, write(modify) or execute(run) files, programs under his ownership. On modern Linux systems(like Ubuntu) a user owns a "home directory", everything outside it does not belong(i.e. he doesn't have "ownership") to him.
The "root" is the superuser of a Linux system, he has access to ALL files on the system. It is important to note that just because I refer to the root user as "he" doesn't mean "root" is a person. Anyone who has THE password can act as root; in this case its you.
(On earlier computers a root user was usually a system administrator-employed by the establishment that housed the computer)
summary: "root" is the dictator, everyone else is just a humble user.
To prevent installation of malicious programs only root is allowed to install programs, though others can run them-but they can't modify the way the program works.
Most applications have a preferences menu and can be modified according to the users taste. The application makes a note of these modifications and stores them in a file in the users home folder.(these files are usually hidden to prevent accidental modification/deletion - to view them press Ctrl+H) 

whew! hope you got the picture.
Regards and good luck.

---

### Post by The Cog on 2010-10-07
It doesn't come naturally to a long-time windows user, but try to develop a mental separation between working as a normal user, and working as the administrator (root). They are distinct roles and you only do one at a time. 

You have already discovered that as a normal user, you don't have write permissions outside your home folder. This is normal for *nix but feels very odd to a windows user, but only because windows users don't have any appreciation of the dual roles. Even though you are in the admin group, this just means you are allowed to assume the role of root when you want to: it doesn't mean you have those rights in you normal user activities. 

When you are acting as root, you have full rights to do anything. This is dangerous - you have more powers than a windows admin has, and Linux doesn't normally ask "Are you sure you want to do that?" So you never never ever do normal user type stuff as root. After doing your admin work, you return to your normal user persona to continue with your day-to-day stuff.

Like I say, it feels odd to windows users, but it's the *nix way and you'll get used to it. Keep all your user stuff inside your home folder - all of it, and accept that outside of your home folder is system stuff that only root can tinker with. This arrangement makes it more difficult for viruses to get a hold, and much less likely that a mistake will trash the system.

---

### Post by Hans Upp on 2010-10-08
> **oldos2er said:**
> /home/my "profile"/ is not a proper directory name; is that just an example?
Did I overplay the underdog?

Despite all appearances, I am not really as dumb as Homer Simpson and it was indeed just a representation, not the real directory name.

and > Keep all your user stuff inside your home folder - all of it, and accept  that outside of your home folder is system stuff that only root can  tinker with. I think I got that message now, thanks.

But I have a new problem to fix, and no-one seems interested in helping where I posted elsewhere.

It seems I need to install the latest ver 2.4 of Audacious, but Ubuntu only offers ver 2.3
I have downloaded the files for ver 2.4 but how do I now get them to install? (I see the good old double click is also out the window with linux)

---

### Post by Morbius1 on 2010-10-09
First it's generally ( not always but generally ) not a good idea to install applications from outside the repository. There's usually a good reason it's not included there - stability, computability, bugs, etc..

In any event, in what form is the download. If it's a *.tgz for example then the README file usually gives you a step by step procedure for installing the package.

---

### Post by Hans Upp on 2010-12-16
> **Morbius1 said:**
> First it's generally ( not always but generally ) not a good idea to install applications from outside the repository
OK so I took your advice and didn't install from outside the repository. I found out that Audacious 2.4 is included with 10.10 Meerkat so I 'updated' (ha ha) to that.

Jeez, what a pain that is. You can't update from Ver 10.4 to 10.10 so it has to be a complete install from scratch?
So the inevitable drive format loses all my data, music, video and installed programs to do a simple upgrade.

Luckily I haven't been using Ubuntu for long so there wasn't too much to re-install but if I had used it like I'd expect to in due course this would drive me nuts. Now I can see why they say Linux is for enthusiasts only. You'd have to be an enthusiast to want to do that every time.

Anyway, now I have a whole new problem to resolve.
Trying to burn a cd or a further multi-session in ubuntu is causing a severe headache. Is there a better burning programme than Brasero?
First, it took my previous multi-session CD and  although it did add the new session I wanted, but in doing so it blanked all the previous data written on the disk. I've never had that happen before.

Then, when I tried to write a new CD, it burned the files but with errors making every one of them unreadable. 

I haven't made a coaster in the last 12 years, but now I have a pile of them trying to solve this problem. Is burner incompatibility a common problem with ubuntu?

---

### Post by Yougo on 2010-12-16
I've been reading up on this thread, and i see you like steep learning curves, huh? ;-) you're doing great (greater than i did at first :redface: ) just make sure you don't dive in too head-first. take brakes, don't forget to get some sleep :-)

i'm a bit surprised you had to go for a fresh install. depending on your update settings ( [https://help.ubuntu.com/10.10/keeping-safe/C/updates.html](https://help.ubuntu.com/10.10/keeping-safe/C/updates.html) ), the update-manager would tell you a new version of ubuntu is out, and you could roll from there. 

(personally i prefer a fresh install with backed up configuration. upgrades made weird things happen in the past)

as for Brasero, you're not the first one to lose hair and CD's over it, sadly.
i can't help you on multi-session disks as i don't really ever do that, but i feel a lot more secure and in control using a burning program called K3B. it is in the software center, and so are some more burning programs.

be warned though. K3B is written for KDE based desktops, like the Kubuntu desktop, so it will draw in quite some files such as libraries from KDE in order to run. it will also look a bit out of place in the standard ubuntu theme.
if you're ok with this, it sure is worth trying (you can get writ of it just as easily too ;) )

Nero has a version for linux too, but it costs money and -ofcourse- is not in the repositories. i can't say how well it does or doesn't work.

hope this helps

---

### Post by Hans Upp on 2010-12-16
Thanks for that.
I do have a Nero Linux 4 trial version on a Nero 9 essentials CD, but if I tried to install that outside the repository I'd be back in the clutches of Post #36 above. Damn!
.

---

### Post by col48 on 2010-12-16
I use cdrecord in Terminal for burning CD/DVDs.  No GUI, and you build your iso image first (mkisofs) from a folder.  It doesn't have any fancy features (some will call them essential) and you have a copy on the hd of what you put onto cd/dvd, which might be overkill.

I find that most of the fairly common things I want to do could be done in Windows in either no way or 1 way, or very occasionally as a spin-off of something else in 2 or 3 ways, and the 1 way is usually fairly easy to discover.  In Ubuntu they can be done in no way (less often than in Windows) or many ways, but can be much harder to discover. I think this is because there is no central authority laying down the law about (and paying the bills for) what gets written, so anyone with the knowhow can write a new flavour of whatever it is at any time.  After a while you get favourite places to search for information on how to do things - this forum is a good one.  Internet search (Google or whatever) is another powerful weapon - more useful than with Windows in my inexpert opinion.

---

### Post by Morbius1 on 2010-12-16
> **Hans Upp said:**
> Thanks for that.
I do have a Nero Linux 4 trial version on a Nero 9 essentials CD, but if I tried to install that outside the repository I'd be back in the clutches of Post #36 above. Damn!
.
What I said was:
> First it's generally ( [COLOR=Blue]not always but generally[/COLOR] ) not a good idea to install applications from outside the repository.As it turns out I have Nero installed ( paid version ). This is one of those "not always" situations for me.

---

