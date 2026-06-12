---
title: "Some basic Linux: size of drives, partitions"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by OllieGab on 2009-03-22
I'm running Ubuntu 8.10 on a 75 GB partition. The machine started to slow down and do all sort of strange things and the system monitor told me there was no space left. 
Right clicking on the home folder told me the size was 25 GB and the File System folder the same. That's 50 GB; so where are the last 25 GB residing?
Secondly I have had Linux installed for only about 4 months and I have of course intalled some programmes on top of the initial install. But not that many applications! Should the File System really be that large for a normal installation?
I have now increased the partition to 100 GB so will that sort the problem for a foreseeable future? Or is it going to clogg up again very shortly?

Cheers Ollie

---

### Post by CatKiller on 2009-03-22
```
gksudo baobab
``` will show you where all the space has gone. I seem to remember reading that a number of people were experiencing a problem where their log files (in /var/log) were growing extraordinarily large.  Perhaps you've been bitten by the same thing. I'm not sure if there was a fix, or if it just stopped when the log files were deleted. A search might turn up some of those threads. Some of the games are multiple gigs in size, but most applications are quite small. If you've got the huge logfile problem, then you'll probably run out of space again. If it's just that you've installed some really large applications, then you probably won't.

---

### Post by blueridgedog on 2009-03-22
To get an idea of where all the space has gone, can you post the output of the following?

```
cd /
sudo du --max-depth=1 | sort -g
```

You should not have used that amount of space in the amount of time you imply.  I suspect you have some fat tmp file or some other issue at play.

As an aside, for a graphical view of your files, you can run baobab from a terminal.

---

### Post by OllieGab on 2009-03-22
The machine in question is currently going through a partition re-size "exercise" - which will take another 3 hours!
I'll will definately try your suggestions as soon as I've got it "back"!

Cheers!

---

### Post by OllieGab on 2009-03-22
Further to blueridgedog's answer; this is what I got:


xx@xx-desktop:~$ gksudo baobab
xx@xx-desktop:~$ sudo du --max-depth=1 | sort -g
du: cannot access `./.gvfs': Permission denied
4	./.audacity1.3-ola
4	./.gnome2_private
4	./.hplip
4	./.icons
4	./Public
4	./Templates
4	./.themes
4	./Updater5
4	./.w3m
8	./.gnupg
8	./.idlerc
8	./.pulse
8	./.qt
8	./.update-manager-core
8	./.update-notifier
8	./Website
12	./.dbus
12	./.gphpedit
12	./.netx
12	./PythonFiles
16	./.adobe
16	./.gegl-0.0
16	./.mcop
20	./.audacity-data
24	./.avg7
28	./.xine
32	./.gftp
32	./.sane
36	./.gtkpod
36	./.wapi
48	./.bogofilter
52	./.ICAClient
64	./.purple
84	./.fontconfig
108	./.gconfd
128	./.bluefish
132	./.tomboy
408	./.compiz
412	./.gstreamer-0.10
480	./.gimp-2.6
676	./.local
740	./.macromedia
1072	./.nautilus
1736	./.kompozer
2160	./.openoffice.org2
2592	./.gconf
3228	./Work
4064	./.opera
4660	./gpodder-downloads
5116	./ICAClient
6612	./Citrix
7636	./.wine-doors
9008	./.mozilla-thunderbird
9260	./.config
25932	./Photos
38820	./Videos
39152	./.gnome2
43840	./.clamtk
46652	./.evolution
47236	./.mozilla
47568	./.azureus
48668	./.picasa
51656	./.cache
69008	./.songbird2
126420	./.thumbnails
130200	./.beagle
329736	./Ola
651972	./.kde
1699952	./.wine
2445280	./Documents
2613048	./Desktop
3163052	./Azureus Downloads
3949712	./Pictures
4502340	./DownloadedAppl
5881344	./Music
26016068	.
xx@xx-desktop:~$ 

Does it look "normal"?

---

### Post by blueridgedog on 2009-03-22
Looking at the big hitters:

> 1699952 ./.wine
2445280 ./Documents
2613048 ./Desktop
3163052 ./Azureus Downloads
3949712 ./Pictures
4502340 ./DownloadedAppl
5881344 ./Music

You have 2.4 gig in documents, 2.6 gig on your desktop 3.1 in a file called Azzureus Downloads, 3.9 gig in Pictures, 4.5 gig in DownloadedAppl and 5.8 gig in music.  So 22.3 gig can be accounted for in your home directory.  

Note that where you ran the command is only showing us your home directory (which looks to be the source of the space issue), to see the entire system, would require:

```
cd /
sudo du --max-depth=1 | sort -g
```

I suspect the biggest user there would be /home, but it can't hurt to test it.

---

### Post by OllieGab on 2009-03-22
This is the result this time. The ./media file is not the media file **within** the home folder, is it? Checking properties on **that** file shows only a few KB. 
So where is ./media ?

du: cannot access `./proc/6786/task/6786/fd/3': No such file or directory
du: cannot access `./proc/6786/task/6786/fdinfo/3': No such file or directory
du: cannot access `./proc/6786/fd/3': No such file or directory
du: cannot access `./proc/6786/fdinfo/3': No such file or directory
du: cannot access `./home/ola/.gvfs': Permission denied
0	./proc
0	./sys
4	./mnt
4	./srv
16	./lost+found
316	./tmp
1756	./root
3208	./dev
6228	./bin
8528	./sbin
14684	./etc
35864	./boot
189288	./opt
301944	./lib
412420	./var
2700112	./usr
26016856	./home
32909948	./media
62601180	.

---

### Post by beswatcher on 2009-03-22
Having read this thread, I was wondering how I was doing for space. I don't have near the amount of room that OllieGab has so I should be careful. With baobab I show that root is using 100% of 968.0 kb. Is it normal to show root as full?

As an aside, how do I directly post a screenshot here?

---

### Post by blueridgedog on 2009-03-22
Well, the 26 gig in /home was as expected.  the /media size may be a mounted drive (do you have an external USB drive).

To verify, you can post the output of:

```
mount
```

You can take a look with:
```

cd /media
sudo du --max-depth=1 | sort -g
```

For that mater, just looking in /media may be useful:

```
ls /media
```

---

### Post by OllieGab on 2009-03-22
It tells me I have an external hard drive mounted (or does it say that?) and although I have this ext hard drive available it is not (nor was it earlier) actually connected to the computer.
Does it "remember" that I sometimes have it connected?

Output:
ola@ola-desktop:/media$ ls /media
cdrom  cdrom0  EXT-HD2-500

---

### Post by sdowney717 on 2009-03-22
I had over 5gb tied up in root trash folder.

---

### Post by CatKiller on 2009-03-22
> **beswatcher said:**
> With baobab I show that root is using 100% of 968.0 kb. Is it normal to show root as full?

Baobab shows proportional usage. Since everything that's mounted is by definition somewhere under /, / will necessarily show 100% usage.

If anything else shows that your / partition is full (Nautilus or whatever) then you should worry. If it's just Baobab, then that is normal behaviour.

---

### Post by OllieGab on 2009-03-23
I think I may have come across something that stole a lot of my space. Please inform me if I can delete....
When clicking on Places (on main menu) I get, as expected, two main folders. One called **home** and the other **File System**.
I have just discovered that **within** the File System folder is a subfolder called **home**; containing identical files as my "normal" home folder.
This can't be right, surely?
Have I perhaps copied my home folder into the File System folder?
Is it safe to delete my home folder thats located within the File System folder?

Cheers Ollie

---

### Post by egalvan on 2009-03-23
> **OllieGab said:**
> clicking on Places (on main menu) I get, as expected, two main folders. One called **home** and the other **File System**.
 **within** the File System folder is a subfolder called **home**; containing identical files as my "normal" home folder.
**This can't be right, surely**?
Have I  copied my home folder into the File System folder?
Is it safe to delete my home folder thats located within the File System folder?

Cheers Ollie

Surely it's right... :)

It is the **SAME** folder... viewed from a different "angle".. **NOT** a copy.
Do NOT delete.

---

### Post by OllieGab on 2009-03-23
Yes!!! I realised that after I'd played around a bit! Stupid of me!
However, that sort of brings the original "problem" to the surface again.
If the total used space, according to Properties of the System Files folder, is 23G but my System Monitor says I've used 56G...where is the rest??

---

### Post by egalvan on 2009-03-23
> **OllieGab said:**
> Yes!!! I realised that after I'd played around a bit! Stupid of me!
Nothing "stupid" about it... you were just un-aware of things...

Same thing happened to me when I started with Ubuntu... :)

---

