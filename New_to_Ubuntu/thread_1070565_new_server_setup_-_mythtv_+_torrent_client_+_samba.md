---
title: "new server setup - mythtv + torrent client + samba + printer"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jonody on 2009-02-15
i am fairly new to linux, I have in the past installed and used mythdora but that's about the limit of my experience.

i currently run two servers at home, one is running mythdora but i find it unreliable (requires a reboot every couple of days else programs stop recording, i'm not able to get my hauppauge dual tv tuner to work, haven't been able to connect with any other frontends or play recordings through windows or xbox, the list goes on) and the other is running windows XP for sharing files, downloading torrents and for network printing.

it would make sense to me to combine these two machines into one and this is what i intend to do, since i found instructions for the hauppauge dual tv card for ubuntu this became my distro of choice (also i like the look of mythbuntu control centre).

my new server will require to meet the following criteria:
1. share media files via samba to be watched on other computers or my xbox.
2. download torrents and preferably have a web interface for controlling this.
3. share a printer to be used by other computers on the network.
4. host a mythtv backend that will record tv shows and be configurable via mythweb web interface, able to be connected to from the xbox.

and there are some other options which would be desirable, but not essential:
5. the ability to run firefox as a browser to use when all other computers are shut down.
6. i'm running my own business so in the future a mail server may be useful.
7. likewise in the future a fixed-ip web server may be useful.
8. likewise in the future a project management system may be useful (i've dabbled with apache-based project.net on windows)
9. since i'm installing a mythtv backend, a frontend would also be quite useful for testing hardware and occasionally watching recorded or live tv (or other media) whilst at my desk.

So I have a few options:
1. install ubuntu server then install a desktop and install mythtv, a torrent client (my preferred is azureus for it's variety of features), samba and maybe CUPS(?) for printing.
2. install ubuntu desktop and install all the above.
3. install mythbuntu and add whatever extras i require.

i've already tried option 1 and run into a couple of brick walls, and now i'm scared to try again. currently a lot of files on a windows-only NAS drive are copying onto an ntfs drive in the machine in question (did i mention i'd like to dual boot the old XP setup with the new ubuntu?)

the final specs of the machine will be 2100 athlon XP with 1gb of ram, 1x 40gb hard disk for operating systems, 2x 700gb hard disks for media and storage (if possible as a logical drive spanned across both but atm one drive is an ntfs full of media data), 200gb hard disk for downloading torrents onto, and a 160gb hard disk for recording tv shows (the layout of the drives reflects what they are currently being used for shared between the XP and mythdora servers and the windows-only NAS, and is up for debate).

so i have a lot of questions coming up...

i'll start with what distro do people recommend as the base for my setup, ubuntu server plus extras, ubuntu desktop plus extras, or myhtbuntu plus extras?

many thanks in advance for any advice offered, should i also add this is my first linux forum posting ever?

:) Jon

---

### Post by johnjohn2 on 2009-02-15
Ubuntu Desktop would be king as all the server gubbins are easy to install and i personallylike to use a gui.

Also disable the items that you do not want to start and run,that way you will have a fast,reliable and easy to configure machine.

It will also be able to do anything you want.

Regards John

---

### Post by johnjohn2 on 2009-02-15
Deluge is a lot less ram and processor hungry than Vuze.

---

### Post by jonody on 2009-02-23
> **johnjohn2 said:**
> Ubuntu Desktop would be king as all the server gubbins are easy to install and i personallylike to use a gui.

Also disable the items that you do not want to start and run,that way you will have a fast,reliable and easy to configure machine.

It will also be able to do anything you want.

Regards John

I have now installed ubuntu desktop with gnome, which was nice and easy.

I have configured samba which is working really well. my pc is called blackbox and if you remotely point to //blackbox/video for example then whether the server is booted into windows or ubuntu then you'll be able to see the files, which i like. the only problem with this is that in ubuntu the drive has to be mounted before the share is accesible. you can do this just by clicking on the drive in 'places' but i'd still prefer it to be automatic. the drive is 700gb of media files formatted ntfs.

I've also configured the printer sharing and i'm able to print from windows pc's via the network - nice :)

i've downloaded and installed deluge, but not yet configured it (there are exsisting torrent downloads on another 200gb ntfs drive which i'd like to continue to download without losing any data, the client i'm using in windows is uTorrent and all the exsisting downloads are appended .!ut)

i've downloaded and installed mythtv frontend and backend, and again haven't configured it yet. i'm waiting until after i've combined the hardware from the two machine and installed the nova-t 500 tv card.

i've also installed mythbuntu onto my recently salvaged laptop (had to hardwire the power supply to the motherboard ooer) and after a bit of reading and typing in commands which i didn't quite understand, the wireless network is working and it's plugged into the bedroom tv waiting for the new backend to appear on the network :)

and a new requirement for the server has also surfaced... ftp to xbox. after poking around the t'interweb i get the impression filezilla is the way to go, and i'm pretty sure the xbox ftp server is running a modified xbfilezilla (running xbmc as dash).

so my questions this week...

1. how do i automatically mount my ntfs drives as soon as ubuntu starts so i don't have to be logged in and click on the drive to mount it?

2. i have an existing mythdora backend running (single 160gb hard drive with default partitioning) which has recordings set up and lots of recordings stored. what is the best way to transfer these files and settings onto the new mythbuntu super-combo-server?

3. i have 100gb+ of current downloads using uTorrent (preallocated disk space and appended .!ut) will these downloads be able to be continued in deluge, and if i need to remove the .!ut from each file how could i do this?

4. can anybody tell me whether or not the xebian preinstalled E-images, or the native support for mythtv is working with mythbuntu 8.10 (my whole entertainment system depends on it!)

many thanks,

Jon

---

### Post by jonody on 2009-02-24
question 1. i've answered myself by using ntfs-config.

had a bit of a panic last night after uninstalling a load of programs i thought i didn't need, and then my top and bottom panels vanished and had to be reinstalled! i had to use the xfce session to launch synaptic as i couldn't find any way to fix the installation using gnome.

filezilla is downloaded and installed, and is able to connect to the xbox but haven't tried transferring any data yet (which is where the normal ubuntu ftp was failing).

I know this might be a bit late but i've been trying to figure out my partitioning layout on paper and it'd be good to get a second opinion on what i'm planning to do... (i hope this works)

before:
1:1.+----+-----+.1:2.+-----------+
....|.40gb.hd..|.....|.700gb.hd..|
....|.XP.+.Ub..|.....|.media.....|
....+----+-----+.....+-----------+
2:1.+----------+.2:2.+-----------+
....|.cdrw/dvd.|.....|.200gb.hd..|
....|..........|.....|.downloads.|
....+----------+.....+-----------+

after:
1:1.+----+----+------------+.1:2.+----------+
....|.200gb.hd.partitioned.|.....|.700gb.hd.|
....|.XP.+.Ub.+.downloads..|.....|.tv.shows.|
....+----+----+------------+.....+----------+
2:1.+------------+.2:2.+----------------+
....|.160gb......|.....|.700gb..........|
....|.recordings.|.....|.movies.+.music.|
....+------------+.....+----------------+

downloads and recordings will be doing a lot of reading and writing, tv shows and movies/music will be mostly storing data with occasional read or writes. is the layout i've sketched the best way to attach the drives?

my main sticking point now is copying the boot partitions from the 40gb drive onto the 200gb drive. is it possible to do this using an ubuntu live cd maybe?

one other question i have is why am i not able to post to answer other peoples questions? i found a posting on here last night about someone trying to install ubuntu onto an xbox and keep normal xbox functionality - the answer is to install xbmc as a dashboard and launch ubuntu, or games, or stream media from there.

and are my postings too long? i'm thinking maybe i should break up my questions and make one seperate posting for each! what would be the forum etiquet? ;)

---

### Post by jonody on 2009-02-24
> **jonody said:**
> i have now installed ubuntu desktop with gnome, which was nice and easy.

:p

---

### Post by jonody on 2009-03-26
in conclusion i've given up on the idea.

my fileserver is going to stay seperate from the mythtv, and carry on using windows over ubuntu.

my mythtv server has been upgraded from mythdora to mythbuntu, but a lot of the original issues still remain.

---

### Post by JohnFH on 2009-03-26
What idea have you given up on exactly?  I have a MythTV server which acts as a Mythtv backend, frontend, webserver, torrent server and it all works perfectly.

I used Ubuntu + MythTV rather than Mythbuntu, but Mythbuntu would be a better choice I think.

I also use Apache for the webserver, torrentflux for the torrent server (useful web interface), and Webmin for easy administration.  All highly recommended.

To answer some of your questions:

to automatically mount partitions at boot time, put the entries in /etc/fstab (see man fstab).

to transfer Myth info from one box to another, either do a Myth Backup from within MythTV (perferable, potentially easy although haven't done it myself) or backup the MySQL database and copy the media files separately (will require more configuration).

One other thing, 160Gb is not a lot for recordings.  I tend to compress my movies, but recordings are stored in Mpeg2 format which takes up more space.

---

### Post by jonody on 2009-03-26
i gave up on the idea of combining the hardware of the two pc's, pretty much about the same time as i opened them both up and discovered the gb of ram that the myth box isn't compatible with the motherboard i wanted to use from the other server, and also the 2100mhz athlon processor i wanted to use wouldn't post when swapped out with the 850mhz amd duron in the server.

i'm very happy with the performance of my windows server after a lot of tuning, and with 850mhz processing and 512mb ram it still outperforms most other xp machines of higher spec that i've had in to repair. it has two jobs: download torrent files and share files over the network, and it does them both well.

the problem with the myth box taking over the torrent and filesharing duties is purely space and expandability. the motherboard i'm using has only one pci slot for tuner cards and not much room for extra hard disks, and having discovered that the nova-t-500 pci card that i've been trying to configure works perfectly first time in mythbuntu with another motherboard has convinced me that i need to invest in hardware before trying to combine servers again.

i did purchase a dvb-s card which i'm now trying to get working with the originalpcbutreinstalledos machine and getting "error parsing parameters" messages when i try to scan for channels. if anyone can help with that i've started a new thread here:
[http://ubuntuforums.org/showthread.php?t=1105086](http://ubuntuforums.org/showthread.php?t=1105086)

lesson learned, if it's not broke don't try and fix it.

not a defeat, a tactical retreat.

---

