---
title: "Networking...and media"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by bertcakes on 2006-09-12
Dont really know where to stick this:


Ok, let me explain:

I am just so so when it comes to linux. I can get myself by and when I dont know something, I will spend hours to fix it (just like this). What started out as a possible codec issue turned out to be nothing of the sort.

I have a windows XP box that has about 500 gigs worth of various media, the drives are NTFS. All I did in my Bunutu box was goto Places -> Network Servers -> and from there I browsed to my own network and was able to see and share my files. I have the ability to delete files and rename on those NTFS drives from my linux box. What does NOT work...is mplayer or xmms or any other media player other than totem...now I wouldnt mind totem if it didnt have such a hard time buffering my AVI files. If i try to fast forward any of my AVI files it takes like 15 minutes to buffer them. If I try to (for example) open an MP3 with xmms...it doest play, it doesnt register that anything was requested to play through it. Even though I set it to the default MP3 player...but if I open it in totem it does...now lets take an AVI...if I try to open it with Mplayer (which is the default video player) it does the exact same thing, it doesnt register that it has a file to play. However, in both cases, if I copy that file to my ubuntu box and play it locally....it works flawlessly...PLEASE are there any ideas? I really cant find any info on this.

One more note, it doesnt matter if I do this as root, or as me.

I have now verified this problem on two different linux boxes trying to access two different windows machines.
Edit/Delete Message

---

### Post by Jussi Kukkonen on 2006-09-12
No answer for you, just a clarification for others who might have a problem understanding this (I had to read it twice before understanding -- although it was probably just me): 
The problem seems to be playing media files over samba (XP server, Ubuntu client).

I guess you've tried the same thing with a windows client?

---

### Post by bertcakes on 2006-09-12
Thanks for clarifying it up. That is exactly my problem.

Now what do you mean have I played with with a windows client?

Have I tried a windows client box to access the windows box in question? If that is the question, then yes. Thats how I normally do it. 

Basically, at home, I have a dual boot (only dual boot because ubuntu doesnt play WoW very well). My main PC has pretty much zero media on it. I have another box that has about 500 gigs worth of media...its just my work horse machine. I have no problems if I boot into windows and do it. My windows box can also access my linux box without any problems. 

Its like I said, its a really weird case. It works...but only with totem.

Sorry if this sounds kind of jumbled but I spent a large portion of last night working on this. Its really just a personal preference and an annoyance.

---

### Post by Jussi Kukkonen on 2006-09-12
> Have I tried a windows client box to access the windows box in question? If that is the question, then yes. Thats how I normally do it.

That's what I meant, yes. Then the problem is probably in (linux) samba -- Totem probably just accesses the mounted disk 'normally' just like it accesses any disk (although somehow differently than other media players).  

Maybe you could check if there are any samba-specific mount options (related to buffering or something) you could put in /etc/fstab?

---

### Post by bertcakes on 2006-09-12
Ok I fixed my problem. 

Other than totem, the media player will not play the way I was trying to, you need to fool them to think you are playing the file locally. Had to edit fstab. Problem solved.

---

### Post by profeXorGeek on 2006-09-12
Hey folks, I had a similar problem and didn't get a clear answer from this thread.

**System 1:** Ubuntu Breezy Badger used as a LAMP, dedicated gaming, work, media and proxy server. An archive folder with media,etc is shared using Samba.
**System 2:** Ubuntu Dapper Drake desktop version(6.06) that I just installed because my old windows drive died (bye bye win).
**System 3:** WinXP laptop.

All systems access Sys1 for media, work files etc. I just installed the latest Ubuntu desktop distro on Sys2. My laptop with windows (Sys3) can easily connect to Sys1 and play media. I installed XMM on Sys2 but it cannot play files (just like bertcake's problem) unless I copy them to local folders. I can connect to Sys1 (using the network browser) and browse the files, open text files etc but I cannot play media from this network folder.

My goal is to mount the archive folder from Sys1 as /network_archive on Sys2 so my files can access it like a normal folder. On my laptop I have the /archive folder mapped as a drive in windows and that's what I'm trying to accomplish on Sys2. I have been using Linux for about 6 months and am no pro!

I tried:
sudo mount -t nfs hostname:/archive /net_archive
I also tried ext3 instead of nfs but neither work...I don't know how to mod the fstab stuff as applied to networks.

---

### Post by profeXorGeek on 2006-09-12
Alright, I fixed my own problem but I'm posting the answer for any other newbies that want to do the same thing.

Mounting a directory from one Linux box on another Linux box requires that you have an nfs (network file system) server installed on the server machine. It also requires that your basic networking, etc is configured.

An nfs server can have some security holes so first alter your /etc/hosts.deny server so that everyone is denied access to the nfs files by adding these entries (these are the daemons that the nfs server uses):
[B]portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL[/B]

Then you manually allow the computers that you want to have access to the nfs server by creating the following entry in your /etc/hosts.allow file:
[B]portmap: ipaddress1, ipaddress2, etc
lockd: ipaddress1, ipaddress2, etc
rquotad: ipaddress1, ipaddress2, etc
mountd: ipaddress1, ipaddress2, etc
statd: ipaddress1, ipaddress2, etc[/B]

Now you are configured, install the server:
**sudo apt-get install nfs-user-server**

Your **server** machine should now be configured to allow directories to be mounted. Now configure the **client** machine by mounting the network directory to a local directory. Make sure that there are entries in your hosts file for the other computers in your network (create "localdirname" first):

**sudo mount -t nfs serverhostname:/dirname /localdirname**

I did this with my music folder so that XMM and gFTP could open the folder and access the files. Hopefully that was a clear explanation. Anyone who has a better understanding of this process can feel free to point out any errors I may have made. This works great on my system(s).

---

### Post by tbonius on 2006-09-12
That is exactly the problem.  the SMB slave IO for libsmbclient that runs in Gnome doesnt really "mount" the files system for the Media Players to play the file.  I have also found this annoying as hell over the years.  You can mount the remote filesystem via sMBFS or NFS.  In your fstab you can put mounts for NFS..  I am not sure about SMBFS.. I think you need the actual Samba.. smbclient packages installed to be able to pass smbfs as a valid filesystem type to mount in your fstab.  Once mounted.. you can play the files with any media player just fine.  

T

---

### Post by tlimon on 2007-02-16
I had a similar problem of not being able to play media files from the samba-mounted windows shares.  I filed a bug report (launchpad.net:84729).  It seems to be isolated to the xine version of totem.  I installed the gstreamer version (sudo apt-get install totem-gstreamer) and now all is well for me.   Just thought I'd pass it on.

---

