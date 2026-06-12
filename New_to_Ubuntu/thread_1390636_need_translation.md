---
title: "need translation"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by degarb on 2010-01-25
1. what is equivalent to ctrl alt del?
2. what is equivalent to winkey d?
3. In videolan, I cannot open the network movies (on downstairs computer) because I am unable to navigate and find the network.  Where would it be?  what is the path?

---

### Post by oldos2er on 2010-01-25
You can use Keyboard Shortcuts (if you're using Gnome) to create whatever key-combo you'd like for a particular function. System, Preferences, Keyboard Shortcuts.

---

### Post by llamabr on 2010-01-25
I've not really used windows extensively, but ctrl-alt del does alot of stuff.  You can see system activity with:

```
top
```

i don't know what win-d does in windows

---

### Post by warfacegod on 2010-01-25
> **degarb said:**
> 1. what is equivalent to ctrl alt del?
2. what is equivalent to winkey d?
3. In videolan, I cannot open the network movies (on downstairs computer) because I am unable to navigate and find the network.  Where would it be?  what is the path?

.01 Inside of Windows Ctrl+Alt+Delete brings up the Task Manager. The simplest Ubuntu equivalent would be to add System Monitor to a panel.

.02 Don't know what Winkey+D does.

.03 Places> Network I'd guess.

---

### Post by theozzlives on 2010-01-25
We in the Linux family call it the super-key. You might have to install SAMBA to access Windows networks.

---

### Post by degarb on 2010-01-25
> **theozzlives said:**
> We in the Linux family call it the super-key. You might have to install SAMBA to access Windows networks.


Thanks for the tries guys,.   I will need to play with key mapping, eventually, once I have apps I know about and like, but not useful yet.  and, System Monitor to a panel..this, might just work, but I wonder if running it will slow system and if priority on run realtime enough to have good effect on rouge application.

The vlc issue is my biggest thorn.  Yes I can find network and movie directly in file explorer equivalent. I can right click on file and tell it to open with vlc (still too new to know how to set file associations to fix this). But this is no good, since I cannot setup the disk caching in vlc.  Moreover, i cannot setup a good queue, which is essential for some movies may have 5 parts or the like.  When I click open file in vlc, it shows me everything on my computer, even filesystem, just no smb:/mynetwork/videofiles  like in the file explorer equivalent.   But if I can explore the file system, I am guessing the network is buried in some sub folder, as seems the case in the confusing linux file system (designed by some unix sadistic geek back in 1985 for techies not consumers/endrant.)

---

### Post by degarb on 2010-01-25
winkey d shows desktop, no matter how many program open, with one hot key.

I see mapper can do this now, thanks.

---

### Post by warfacegod on 2010-01-25
> **degarb said:**
> System Monitor to a panel..this, might just work, but I wonder if running it will slow system and if priority on run realtime enough to have good effect on rouge application.

I have SM showing me CPU, RAM, Network, and Hard drive activity with an update interval of 50 milliseconds and the resource load it uses is negligible.

---

### Post by LowSky on 2010-01-25
Here is my desktop, just remember that this is Ubuntu and you can do much more than keyboard commands

---

### Post by oldos2er on 2010-01-25
> **degarb said:**
> ...enough to have good effect on rouge application.

If you use too much rouge you wind up looking like a clown. Sorry--I think you meant *rogue*. :)

---

### Post by degarb on 2010-01-25
> **LowSky said:**
> Here is my desktop, just remember that this is Ubuntu and you can do much more than keyboard commands
So, no answer to my vlc question yet?  why isn't network showing up there when I click open file/folder?

That second picture is pretty cool and would be sweet for an alt tab window change.  I guess a webshots equivalent or an auto  wall paper changer would be nice built in to the os.


I am tempted to install Opera, but only have 3 gigs of space left.  i am unsure how to control the cache in firefox.   (installed standard ubuntu even though only 6 gig of disk, but no problems as of yet.)  Also, I stumbled on go-oo which is a fork of open office and is supposedly much lighter.  I dont see it in repositories.

Also question about how to change file associations stands as of yet.

---

### Post by LowSky on 2010-01-25
you need samba to be set up

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by degarb on 2010-01-25
Another question: the ubuntu cannot get on network if wpa personal encrypted.  Why?

i had to open it up, which isn't good.


Thanks for not flaming me for my twenty questions.  However when I put more than one question on one thread, usually some issues don't get resolved, and if I open a new thread, since old one broken with too many issues clouding some point, the admin may merge.  Oh well.   I am impressed that no flaming has happened,  always a good sign and reason I wiped and installed ubuntu, along with number of responses.  This no matter the constructive criticism on lack of good bat files and exes to help people install devices.

---

### Post by degarb on 2010-01-25
> **LowSky said:**
> you need samba to be set up

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)


are you sure?   how can I test to see if I already have it?  In snaptic I see installed already: samba common , samba client and nautist share.  Should I install samba there?  I won't risk messing with my network as i already have it?

---

### Post by degarb on 2010-01-25
I also will add, how do i make a desktop shortcut?  right clickin on it does nothing.

and where is the device manager?  not under system admin.  control panel?

---

### Post by warfacegod on 2010-01-26
> **degarb said:**
> I also will add, how do i make a desktop shortcut?  right clickin on it does nothing.

and where is the device manager?  not under system admin.  control panel?

If you want a device manager to view hardware info, open a Applications> Accessories> Terminal>

```
sudo lshw
```

If you're looking to "manage" your hardware, I don't think there is one all encompassing app for that.

---

### Post by 3rdalbum on 2010-01-26
You don't need to install anything extra to see shares. Ubuntu already comes with the Samba client.

Basically you use Places > Network to browse your network and see what shares are available. When you open a share, it is mounted on your desktop and also inside a hidden folder in your home directory, called ".gvfs". You can create a bookmark to this folder within your program's Open/Save dialog box.

And yes, you can control the buffering in VLC. It's in the Advanced settings. You should be able to drag files to the VLC playlist to queue them up too.

---

### Post by 3rdalbum on 2010-01-26
> **degarb said:**
> I also will add, how do i make a desktop shortcut?  right clickin on it does nothing.

and where is the device manager?  not under system admin.  control panel?

1. Right-click on the desktop and choose "Create Launcher...". If the program you desire is in the Applications menu already, you can drag it from the menu onto your desktop. Don't worry - on Ubuntu it just copies the launcher.

2. There is no "device manager" on Ubuntu, and I'm not sure what benefit it has on Windows. From what I can tell, the closest thing is either the "lshw" command, or the Hardinfo program that's in the repositories.

---

### Post by Darce on 2010-01-26
To access your network, you might need to browse your way to where ever you have the shares mounted. For example, mine would be under File System/media/MediaServer/

What version of vlc are you running ?

---

### Post by Paqman on 2010-01-26
> **3rdalbum said:**
> You don't need to install anything extra to see shares. Ubuntu already comes with the Samba client.


If you want to mount them permanently you will need to install smbfs.

---

### Post by degarb on 2010-01-26
> **3rdalbum said:**
> You don't need to install anything extra to see shares. Ubuntu already comes with the Samba client.

Basically you use Places > Network to browse your network and see what shares are available. When you open a share, it is mounted on your desktop and also inside a hidden folder in your home directory, called ".gvfs". You can create a bookmark to this folder within your program's Open/Save dialog box.

And yes, you can control the buffering in VLC. It's in the Advanced settings. You should be able to drag files to the VLC playlist to queue them up too.
wow, i don't think I would have ever guessed .gvfs  but only when nautist opens the network. Ridiculously counter intuitive and bad design.

i dont see how to do video caching in vlc prefs advanced. only plugin cache enabling, which says has to do with how fast it launched.

---

### Post by degarb on 2010-01-26
what does sudo mean and stand for?

installing sbfs and applying upgrades to client and something else.  If I cannot reach network, do I reinstall ubuntu from scratch?

Is ubuntu like vector linux, where you have to reinstall all applications after upgrade or reinstall (this is hell)?

Also getting multiverse and universe to work was very difficult, and I am not sure what I did to make it work.  I think I had to manually start choosing servers.  This should be fixed to at least make it either easier or fix what ever bug made it hard.

---

### Post by degarb on 2010-01-26
I am confused about priority.  In vlc you can bump priority, but they don't tell you if +5 bump lowers or raises priority.  Reason i think adding to the number lowers a priority is because the sysmonitor requires you to lower the priority number to raise the priority.

---

### Post by Paqman on 2010-01-27
> **degarb said:**
> what does sudo mean and stand for?


Super User DO.

It allows a regular user to temporarily gain admin rights so that you can administrate the system.

> installing sbfs and applying upgrades to client and something else.  If I cannot reach network, do I reinstall ubuntu from scratch?

No, we should be able to help you get connected. Is this a wifi connection? If so, plug in with a cable for now so that you can get the wifi drivers you need.

> Is ubuntu like vector linux, where you have to reinstall all applications after upgrade or reinstall (this is hell)?

No, upgrading keeps all your apps in place. Even if you reinstall the whole system you can reinstall all your apps with a single command.

> 
Also getting multiverse and universe to work was very difficult, and I am not sure what I did to make it work.  I think I had to manually start choosing servers.  This should be fixed to at least make it either easier or fix what ever bug made it hard.

All you need to do to get access to those repos is go to System > Admin > software sources and tick the boxes. You can also change what server you connect to there if you want.

---

### Post by degarb on 2010-01-28
> **Paqman said:**
> Super User DO.

It allows a regular user to temporarily gain admin rights so that you can administrate the system.



No, we should be able to help you get connected. Is this a wifi connection? If so, plug in with a cable for now so that you can get the wifi drivers you need.



No, upgrading keeps all your apps in place. Even if you reinstall the whole system you can reinstall all your apps with a single command.



All you need to do to get access to those repos is go to System > Admin > software sources and tick the boxes. You can also change what server you connect to there if you want.

This lap top has no eth port.

What is the procedure for reinstalling all aps? what if no longer found in repo.?

---

### Post by Paqman on 2010-01-28
> **degarb said:**
> This lap top has no eth port.


Seriously? Is it a really old machine? Any laptop made in the last 10 years should have one.

> 
What is the procedure for reinstalling all aps?


There's a few different ways, [this one]("http://ubuntuforums.org/showthread.php?t=261366") is nice and straightforward.

> 
 what if no longer found in repo.?

In that case you'd need to reinstall it from where you got it originally. Things don't often get removed from the repos though, and never without good reason.

---

