---
title: "Basic Linux/Ubuntu questions"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-06-07
I've been using Windows for about ten years now, and I consider myself fairly adept at getting it to do what I want. I was looking into Ubuntu and everything I saw/heard about it seemed so much better than Windows, that I had to switch. I've been reading up on it as much as possible, but still have a few basic questions, which I assume are fairly simple to answer, but I've not been able to find anything solid on them.

1. It seems from what I've seen that the vast majority of anything you could download is already stored away somewhere in one place. I keep seeing people talk about how you use "apt-get" to search for and download basically any program you could need. I was just wondering if all Linux programs are automatically shuffled off somewhere to be found by that, or what exactly it does.

2. I installed Ubuntu onto my external hard drive, and left Windows on my internal drive on my laptop. Is there a simple way for me to find the music/pictures/other random stuff that I have stored on Windows and bring it over to Ubuntu? I've read that they use different formats for storing information, and it seems that would make transferring programs and files difficult or impossible.

3. A lot of people seem to really love the KDE desktop, I tried Ubuntu on a virtual machine on Windows before I fully installed it, and downloaded KDE onto it. Honestly, I think it looks terrible. Is there any particular thing that KDE has absolutely better than the standard desktop, that I'm missing out on just because I don't like the aesthetics?

Thanks in advance for any help you guys have to offer.

---

### Post by seawolf167 on 2011-06-07
A good place to start reading is [here]("http://ubuntuforums.org/showthread.php?t=801404").

1. Not all software is in the repos, but most of what you'll want for a good while you'll find in the repos. There are tons of packages/programs that you have to manually configure/install, but you probably won't have to worry about that for a long time

2. If you click the "Places" menu item, you should see your Windows disk, probably labeled something like "XYZ GB Filesystem", simply click that to open it and copy anything out you want to. If you want to access a separate Windows computer with shared files you'd use a program called [I]samba

[/I]3. KDE/Gnome/Fluxbox/xfce/etc. are just different desktops, you can use anything that you like. There are nomajor functionality differences between them, it is mainly just aesthetics

Misc. Backups are a must (for ANY OS). I recommend [Clonezilla ]("http://www.clonezilla.org")to clone your drive, but you have a lot of [options]("https://help.ubuntu.com/community/BackupYourSystem").

---

### Post by nothingspecial on 2011-06-07
1. These places are called repositories. The apps in the default ubuntu ones have been tested and are known to be safe. You can however install stuff from external sources but in 99.99% of cases you shouldn't have to.

2. You should be able to access all your windows drives from Ubuntu, try opening the file browser and looking in the sidebar.

3. It's personal preference, use whatever you like ...... this is linux :P

There are others aswell xfce, lxde, enlightenment etc etc........ you are free to use whatever you want.

---

### Post by Neoncamouflage on 2011-06-07
I didn't bother about backing up as every picture and music file I have on my computer is also on my friend's, it's a fairly new laptop. So I really don't have anything to lose on it.

> If you want to access a separate Windows computer with shared files you'd use a program called samba 
I always heard that Windows doesn't play well with any other operating system (it barely plays well with other Windows) and that trying to network with Linux/Mac/whatever wouldn't generally work. Is Ubuntu different or just that program?

Thanks for the link seawolf. I'd found that looking around the forums before, the one thing I hate about being so new to all this, there's just soooooo much to learn about everything.

---

### Post by seawolf167 on 2011-06-07
> **Neoncamouflage said:**
> Is Ubuntu different or just that program?

That is a pretty standard package used to access Windows networked computers.

The *very basics* are:

Install samba (through a terminal, found in Applications -> Accessories -> Terminal, or the default keyboard shortcut [CRTL][ALT][T])

```
sudo apt-get install samba
```then when you open a folder, you can browse to the computer (just one way shown here) by it's IP address. Say the remote LAN computer has an IP of 192.168.1.217, then you'd access it's Windows shared files by typing

```
smb://192.168.217
```into the address bar

---

### Post by Neoncamouflage on 2011-06-07
Thanks a lot for that. Now, I have one final question. I downloaded samba, as well as clamav for antivirus, Linux or not I just don't feel safe without it. My problem is, I can't find them. They're not in the Applications, Places, or System list, nor on the Desktop. Just wondering exactly where these things go, or if there's a way to find them from the terminal.

---

### Post by dFlyer on 2011-06-07
To answer your question about kde. The desktop environment (DE) is a personal choice, as is our OS. I've use gnome as my primary DE for well over 13 or 14 years. I use kde back at version 2 for about 1 year but could never get use to it. I'm currently using Unity which I do like. Knowing it's a newer DE it's got some problems, but I find it fairly stable. Waiting for gnome3, on ubuntu.

---

### Post by seawolf167 on 2011-06-07
> **Neoncamouflage said:**
> Thanks a lot for that. Now, I have one final question. I downloaded samba, as well as clamav for antivirus, Linux or not I just don't feel safe without it. My problem is, I can't find them. They're not in the Applications, Places, or System list, nor on the Desktop. Just wondering exactly where these things go, or if there's a way to find them from the terminal.

You can find programs through the terminal with

```
which *programname*
```

you can open a program directly by typing the program name into the terminal (provided the binary resides in your $PATH variable)

example:

```
gedit
```

You can also open a program directly by using the Run box, which is accessed by hitting [ALT][F2], then typing the program name.


Note that samba doesn't have a GUI front end, you'll need to manually edit the config files.

I think clamtk is the gui front end for clamav (not 100% sure on that though - its been a while)

---

### Post by Neoncamouflage on 2011-06-07
Hmm, well typing "which clamav" "which clamtk" and "which samba" yielded no results, simply drop me to another line, as thought it just ignored it. No command errors, nothing.

Tried the run command, said there's no such file name in directory. So I'll dig through the files and see where these things are ending up, just find them that way.

---

### Post by JKyleOKC on 2011-06-07
When you installed samba, it automatically inserted itself into the system so that you don't have to run anything. Think of it as a sort of driver for communicating with Windows and it will make sense.

I notice that nobody has addressed the back half of your original second question, about file format differences. They do exist, but many if not most of the Linux equivalents to Windows programs are aware of the differences and are at least able to read the Windows formats even if they cannot write them back out.

For instance, both OpenOffice and Abiword, two of the most popular replacements for MSOffice/Word, are able to read Word documents and to then write them out in their own, different, format. They may not preserve all the fancy formatting exactly like it was in Word, but as you mention, Word itself doesn't always do that either when moving from one revision to another.

You may need to install some "restricted" extras to play all of your music and to view movies. The reason they are restricted is that some of them are illegal to use in some countries although perfectly all right elsewhere. Since Ubuntu is distributed world-wide, it has to segregate such material in order not to be considered illegal itself in such areas. In addition, some distributions, including Debian on which Ubuntu is based, refuse to include programs that are proprietary or which use patented material -- and such programs are necessary for playing some of the formats, including MP3...

---

### Post by Paqman on 2011-06-07
> **Neoncamouflage said:**
> 
I always heard that Windows doesn't play well with any other operating system (it barely plays well with other Windows) and that trying to network with Linux/Mac/whatever wouldn't generally work. Is Ubuntu different or just that program?


Since there are so many Windows PCs, Linux has to be good at talking to them. Ubuntu comes pre-installed with the parts of Samba that you need to access shared folders on a Windows machine already. You only need to install the whole Samba suite if you need to share from Linux to Windows.

---

### Post by seawolf167 on 2011-06-07
```
which samba|clam|etc
```

wouldn't find anything, but try

```
locate samba|clam|etc
```

for the which command, you would need a binary like [I]gedit

[/I]```
which gedit|nano|etc
```

For the run command - again you need an actual program like *gedit*, for samba, you will edit the configuration files (see [how-to here]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/"))

Also - MAN pages! they are your best friend. To find out how to use something, like say, rsync, type

```
man rsync
```

---

### Post by Anuovis on 2011-06-07
As a fellow newbie to Linux, I would recommend the default Gnome for a start.

Looks of KDE are a matter of taste (although I'd argue that Gnome will probably suit more people in that regard as well) but it is also more overwhelming and confusing to a newcomer. Gnome is simpler to navigate and has less buttons, it's mostly stripped down to the basic necessities.

A lot of books and online resources are also written for the default Gnome. The differences in that reagard are really minor but they can be confusing nonetheless, especially if you take your first steps. 

Once you warm your feet and get to know how Ubuntu works, you can try other desktop environments. Maybe you'd even like KDE better in the long run.

As for file sharing, other people can probably give better advice but FAT systems can be read by both Windows and Linux. It would be fairly easy to move everything via a hard disk that is formatted in that way, much like you can use a FAT USB key to carry files around.

---

### Post by Neoncamouflage on 2011-06-07
Locate found the files, thanks a ton.

Also, I love the Man command now. I already knew about Info, and used that a great deal, but Man just seems to be so much more descriptive. I'll be using that a lot for sure.

Thanks a ton for all the help, everyone. I love how helpful this community is, I think it'll make switching over to Linux about a thousand times easier than otherwise.

---

### Post by seawolf167 on 2011-06-07
> **Anuovis said:**
> As for file sharing, other people can probably give better advice but FAT systems can be read by both Windows and Linux. It would be fairly easy to move everything via a hard disk that is formatted in that way, much like you can use a FAT USB key to carry files around.

I definitely would recommend against using FAT for anything but flash drives. Ubuntu doesn't have a problem reading or writing to NTFS, the issue is Windows playing nice with other formats like ext. Just ensure you don't use NTFS for things like backups since it doesn't store file/folder attributes/permissions.

If, for example, you want to format a drive in NTFS, you can do so in GParted after you get

```
sudo apt-get install ntfsprogs
```

If you want to write to your Windows drive, simply mount it in Ubuntu and transfer whatever you'd like from Ubuntu -> Windows

---

### Post by Neoncamouflage on 2011-06-07
Yeah, I really think I'll stick with the default desktop for the moment. It's what I used the whole time I was playing with it before I installed it, and it seems to take care of everything I need. I do fully plan to see what else is out there though.

---

### Post by Neoncamouflage on 2011-06-07
I kept Windows on my main hard drive with everything as is, so even if my external drive were to take a bullet or something and Linux was just gone, Windows is still there. So if I need anything on that I can always go install it normally, no need for Linux to write onto the Windows drive at the moment.

---

### Post by Paqman on 2011-06-07
> **Neoncamouflage said:**
> Locate found the files, thanks a ton.

Your problem was that command lines apps or utilites like Samba don't show up in the menus. Only graphical apps will do that. However, a lot of things which operate on the command line do have graphical tools available to use them, such as Grsync for rsync, and Gufw for ufw. You'll probably find it easier and more intuitive to use them. 

> Also, I love the Man command now. I already knew about Info, and used that a great deal, but Man just seems to be so much more descriptive. I'll be using that a lot for sure.

Man pages vary wildly in quality, you'll find that you'll need to supplement some of them with other sources of info. This forum, askubuntu.com, the Ubuntu wiki and psychocats.net are all good places to look for info. Google can turn up some gold, but you'll also find a lot of irrelevant or outdated info, and it can be hard to tell the good stuff from the bilge when you're new.

> 
Thanks a ton for all the help, everyone. I love how helpful this community is, I think it'll make switching over to Linux about a thousand times easier than otherwise.

Hope so!

---

### Post by vkbidve on 2011-06-07
> **Neoncamouflage said:**
> I kept Windows on my main hard drive with everything as is, so even if my external drive were to take a bullet or something and Linux was just gone, Windows is still there. So if I need anything on that I can always go install it normally, no need for Linux to write onto the Windows drive at the moment.

Also, take a look at '[Remastersys]("http://www.geekconnection.org/remastersys/")'. You can backup whole bunch of your linux installation in an ISO and make a live CD/DVD of that and install it later in case your external drive takes a bullet.... :)  You need not go through sequence of installing and upgrading everything one by one..... you will have your own Live CD with you.

---

### Post by AlphaLexman on 2011-06-07
Also, if you don't know exactly what command you are looking for use '**apropos**'. For example if you are looking for commands or programs related to images:
```
apropos image
```
Will search all man page descriptions for 'image'

---

### Post by walt.smith1960 on 2011-06-07
Here is a free pocket guide by Keir Thomas.  it's dated,  being written around the time 8.04 or 8.10 was current but the basics, especially command line stuff haven't changed that much.  I found it useful when I was getting started

[http://ubuntupocketguide.com/index_main.html](http://ubuntupocketguide.com/index_main.html)

---

