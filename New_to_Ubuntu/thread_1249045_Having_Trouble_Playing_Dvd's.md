---
title: "Having Trouble Playing Dvd's"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-08-24
Hello World!

I have been having some troubles playing Dvd's. I have not been able to since I installed Ubuntu. Every time I pop a disk in and it opens up MoviePlayer to play it, it gives me the following message: 

An Error Occurred
Could not read from resource.

I am trying to watch a Friends Dvd, and I am I big fan of Friends, so, naturally I am annoyed to have to reboot into windows whenever I want to watch Dvd's.

I am not afraid of the terminal or command line. Every time I use it, I learn somthing about it, which is nice.

Thanks

Scott

P.S. Anyone get the joke with "Hello World"? If you have done programming of any sort, you will :).

---

### Post by SteveNorman on 2009-08-24
I use vlc and the restricted extras package

```
sudo apt-get install vlc ubuntu-restricted-extras
```

I find it powers through most media types.

For commercial DVDs youll need these:if you havent done so yet do

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by benmoran on 2009-08-24
You need libdvdcss2 for reading encrypted DVDs. I recommend installing the medibuntu repository. Go to [www.medibuntu.org](www.medibuntu.org) for instructions how to set it up.

---

### Post by Windows Nerd on 2009-08-24
```

scott@scott-laptop:~$ sudo apt-get install vlc ubuntu-restricted-extras
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scott-laptop:~$ sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3
scott@scott-laptop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found
scott@scott-laptop:~$ 

```

I had Vlc and restricted extras installed already, but I ran the command just in case.

Any feedback?

I think I have installed the Medibuntu Repositories as well, lemme check.

Scott

---

### Post by Windows Nerd on 2009-08-24
Ok, after doing the following in Terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install libdvdcss2
```I get a different error in Movie Player:

> An error occured

Could not open location; you might not have permission to open the file.
Looks like it is permissions...anyone got advice on this one?

---

### Post by llamabr on 2009-08-24
what movie player?  totem?  I don't know much about totem, but ya, that's a perms error.

What error do you get running vlc in the terminal?  Also, for dvd's, I use either mplayer, or xine.

---

### Post by Windows Nerd on 2009-08-24
> **llamabr said:**
> what movie player?  totem?  I don't know much about totem, but ya, that's a perms error.

What error do you get running vlc in the terminal?  Also, for dvd's, I use either mplayer, or xine.

Read the whole thread next time; I mentioned on my first post that I was using Movie player:
[quote=Windows Nerd]Every time I pop a disk in and it opens up _***MoviePlayer***_ ...[/quote]

Scott

---

### Post by Windows Nerd on 2009-08-24
I ran Vlc in terminal

The Error the GUI gave me:

 > 
[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
From Terminal

```
scott@scott-laptop:~$ vlc
VLC media player 1.0.1 Goldeneye
[0x9519140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: FRIENDS_SERIES_3
libdvdnav: DVD Serial Number: 2E315740
libdvdnav: DVD Title (Alternative): FRIENDS_SERIES_3
libdvdnav: Unable to find map file '/home/scott/.dvdnav/FRIENDS_SERIES_3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f00000. Regions: 1 2 3 4
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[0x97bdc30] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid title IFO (VTS_01_0.IFO).
[0x97bdc30] dvdread demux error: fatal error in vts ifo
[0x97bdc30] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0x97d0db0] main access error: no access module matched "dvd"
[0xb7500d18] main input error: open of `dvd:///dev/sr0' failed: no access module matched "dvd"

```Scott

Edit: Looking at this, I realize it would be useful to understand Hexadecimal...I have only really used hexadecimal for naming colours in HTML, for colours such as white (#000000) and #FFFFFF, and so on. I will stop rambling now :)

---

### Post by flabdablet on 2009-08-24
Looks like the DVD is being recognized and read from (VLC gets the name right) which rules out device name or permissions issues. I'm thinking there's some trouble happening when reading some other part of the DVD.

When I have this kind of problem, I will generally try making a block-for-block copy of the DVD using GNU ddrescue, then seeing if VLC likes that any better.  This often works, because even if ddrescue fails to copy some DVD blocks (perhaps because a copy protection mechanism has deliberately corrupted them) VLC will still be able to read the corresponding blocks from the image file without suffering errors. They won't have the correct data (they will read as all zeroes) but that often doesn't seem to matter as long as they're readable.

First thing is to install a couple of packages:
```
sudo apt-get install gddrescue lsdvd
```
Next, we list the DVD contents (which has the useful side effect of having libdvdcss open the drive for us to bypass some of the encryption):
```
lsdvd
```
Now we can copy the DVD to an image file:
```
ddrescue /dev/sr0 friends.iso friends.log
```
While that's running, open a second terminal and do a bit of background reading on ddrescue:
```
info ddrescue
```
When ddrescue has finished, try playing the image with VLC:
```
vlc dvd://friends.iso
```

---

### Post by Windows Nerd on 2009-08-25
Will I have to do this with EVERY Dvd I want to play? Because the average Dvd is between 5-7 Gb, and I honestly don't have the space to store an Iso of every disk I play...also it takes forever to make that Iso...after 30 minutes it has barely copied 10 Mb of the disk.

After I ran the first command you outlined, I tried it again in Vlc media player for the hell of it. It gave me an error message saying it could not decrypt the entire disk...but I could actually "play" the disk, though it was unwatchable due to the fact that the Audio played 1 second on, one second off, and the pixels where going like crazy, though I could see a bit of the main menu.

Scott

---

### Post by flabdablet on 2009-08-25
No, just for the troublesome ones. And if ddrescue really has taken 30 minutes to copy 10MB, we're almost certainly looking at a hardware problem. Could it be something as simple as a scratched or dirty disc? Can Windows play the same disc on the same drive without trouble?

---

### Post by zkriesse on 2009-08-25
Ok wait just a minute. Go here before making any rash decisions...[UbuntuHelpDVD]("https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html")

---

### Post by Windows Nerd on 2009-08-25
Ok, for some reason, all Dvd's work for me now, I don't have to use dd rescue or anything. The now I cannot connect to the internet with my computer. I was able to up until yesterday night. It says I am connected via wireless to my home network, but I cannot see the other computers on the network, or acess any internet related services. 

Ubuntu has been a bit frustrating for me since installation. For me it has been: Problem->Post to Ubuntu forums for solution->Find a good solution after a couple days->Fix problem->Repeat. First it was creating and enabling a swap partition. Then it was making hibernate and suspend features work. Then it was making it possible to play dvd's. Now this. I am exploding in frustration here; if it is commonplace for new Ubuntu users to feel like this, let me know. 

Scott

Edit: Since I have solved my original problem that this thread concerned, this thread is closed. I will raise the issue with my internet in a new thread.

---

### Post by SteveNorman on 2009-08-25
linux is hard, and the learning curve steep. Ubuntu is arguably the easiest there is. We are using a community ran system that has had to fight legal battles just to get drivers made. 

As flashy as Ubuntu is, you still have to learn all the configuration tricks before you have a good system. It takes the process you spoke of to start getting it right. Then youll be helping others on here facing the same problems and now you will have the solution.

I am not the best at wireless problems. I recommend starting a new thread and someone will jump on it and help you fix it. Also a lot of times a reboot will fix wireless problems, or killing nm-applet and restarting it

```
killall nm-applet
nm-applet &
```

that may work for you, if not try rebooting.

Just remember the alternatives are expensive, proprietary, controlling, and invasive.

Good luck!

---

### Post by Windows Nerd on 2009-08-25
Turning nm-applet on and off did not help at all, though thanks for helping. I have started a new thread, though no one has posted on it yet ><.
 
Scott

---

### Post by Shibblet on 2009-08-25
I had the best luck going to [www.medibuntu.org](www.medibuntu.org).

I think you need libdvdcss2.

Either that, or download VLC.

---

### Post by JSJSJS on 2010-04-27
I'm new to Ubuntu and I am not a programming type. I've been trying to figure out how to get my DVDs to play and all the stuff I've tried typing into the terminal hasn't seemed to allow the DVD movies to play.  Please help.

When I try Movie Player I get the following error: "An error occurred. Could not read from resource."

jsjsjs@Vintage:~$ sudo apt-get install medibuntu-keyring && sudo apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package medibuntu-keyring
jsjsjs@Vintage:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
jsjsjs@Vintage:~$ ^C
jsjsjs@Vintage:~$

---

### Post by JSJSJS on 2010-04-27
I did this:


sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
 

Then tried what I tried before and now I was sort-of able to see the movie, but it was basically only a still image that changed occasionally and didn't have sound. Not sure if its a software/programming issue or a hardware issue (this is an old computer)

---

