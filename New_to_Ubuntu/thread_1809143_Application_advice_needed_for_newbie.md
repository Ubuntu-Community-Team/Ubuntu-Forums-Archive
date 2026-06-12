---
title: "Application advice needed for newbie"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by cliver1956 on 2011-07-21
Hi all,
Just looking at migrating from win7 to Ubuntu. I have Ubuntu 11.04 on a test machine at the moment and am trying out software to see what suits my needs before taking the plunge. So, I'd like your expert advice on suitable apps please.
I have what, for me, is a pretty clean and seamless system running on my Win 7 machine at the moment but I am rather fed up with windows. Hence the plan to migrate if I can get a similar set up that suits my needs.
My main use apart from the usual email, web browsing etc.. are Music management and playing, flac, wma and mp3 files, and a bit of web design, development and maintenance.

My current windows packages and reasons for using them are:

Web Design - Dreamweaver CS4 - Really powerful wysisyg, php and ajax.

Web Testing - xampp - Local testing of web sites with php and MySql.

Music Streaming - Squeezebox Server - Feed my SB touch perfectly

Local Music - MusicBee - Clean and powerful and it syncs playlists to my HTC HD2 converting on the fly

CD Ripping to flac - Eazy CD-DA Extractor or EAC - Both do the basic ripping job well. I'm not worried about the tagging at this stage as I use...

Tag Editor - Mp3Tag - It's simply brilliant at tagging all my files, making sure all tags are ID3V2.3, cleaning out any others and embedding album art.

Album Art Finder - Album Art Downloader - One stop search of all repositories, never fails to find it. 

I know I can get Sqeezebox Server and xampp on Ubuntu but the others aren't available themselves so.. If anyone has used these in windows and found an alternative in Linux or has any suggestions for apps that will do the job as well as these I'd love to hear from you. Many thanks.

---

### Post by yeats on 2011-07-21
Just a general word of advice here:  Rather than thinking about replacing particular programs, feature for feature, I've found that it's better to ask yourself "What needs do I have that could be filled by an open source alternative?"  For example, if you're a Photoshop devotee who wants to switch to GIMP, and you see GIMP doesn't have features X, Y, or Z (without some plugin finagling and possible configuration heartaches), you might walk away thinking that GIMP is sorely lacking.  On the other hand, if you think about what needs you have (the need for a powerful photo editing program, for instance), you might come away with a more accurate picture of the value of each open source program. </end_of_unsolicited_advice>

> Web Design - Dreamweaver CS4 - Really powerful wysisyg, php and ajax.

If you're used to Dreamweaver, this will probably be the hardest to replace with an open source program.  The closest you'll come are programs like Bluefish, which *looks* like Dreamweaver, but does not have some of the power features.  Please know that it's been a while since I've used either program, though, so my knowledge is dated.

As far as the music/tagging programs go, I think you'll find that most of the out-of-the-box Ubuntu programs will do a lot of what you're looking for.  I would advise setting up a dual-boot situation and trying them out.

I'll also mention that you can probably run some of these programs (including Dreamweaver) in Wine.

---

### Post by androssofer on 2011-07-21
> **yeats said:**
> just a general word of advice here:  Rather than thinking about replacing particular programs, feature for feature, i've found that it's better to ask yourself "what needs do i have that could be filled by an open source alternative?"  

+1

---

### Post by johnnybgoode83 on 2011-07-21
I can't speak for your web design needs but for music management I recommend Guayadeque for management, tagging, and album art fetching.  It also has a long list of online radio stations like itunes does.  For device synching I use Rhythmbox which I have had no problems with for my ipod and HTC Desire Z.  For CD burning, K3B is hard to beat and for CD ripping, I like sound juicer although any of the music management programs will have CD ripping features.
 
Hope you enjoy Ubuntu like I have for several years

---

### Post by An Sanct on 2011-07-21
Well, about bluefish ... 2.0 is here ... it is up to date ...

I was wondering about "flac" you mentioned ... it was a format I used to know somewhere about 20 years ago for audio/video (movie) compression ... is it still actual, or did someone just hike the extension name, since it was available?

edit: for web development, you need apache + a text editor and yourself ;)

---

### Post by yeats on 2011-07-21
> Well, about bluefish ... 2.0 is here ... it is up to date ...

I just downloaded it to investigate.  Looks far more feature-rich than last time I tried it out! ;-)

---

### Post by jjex22 on 2011-07-21
I agree most of the stuff you need is just there out of the box, and whilst i havn't used CS4 (as i don't own it) in wine, i know previous versions worked, so thats not really something you need worry about.. I can't think of an opensource program that's as good in my eyes, but as you already own it, shouldn't be a problem!
 
I'd like to throw in album art cover downloader, can't remember now if it was actually on ubuntu when i installed it or i added it after, but does the job well! and I find Brasero the best for burning.
 
it's all personal preferance at the end of the day, I would like to add that I never recommend removing windows. There are two reasons for this - firstly that at somepoint you inveriably find that you need a windows only program that wine doesn't support, or a usb device that simply will not talk to linux, or you want to flash your bios (yes you can use freedos, windows just FEELS safer someway) and secondly, you have already paid for it one way or another, so why not make use of it?
 
I do recommend moving your C:\ users to a different drive or partition formated in FAT32 (may as well move your program files, program data and winsxs while you're at it for ease of reinstalling) and putting Ubuntu's /home directory (and which ever othe directories you want to move) on it so all your important dat is in the same place and accessable from both OS.
 
Hope that helps!

---

### Post by nothingspecial on 2011-07-21
There are many many applications that will do all those things.

But if you are running squeezeboxserver why have a different music player.

Install squeezeslave and run it on your computer. Even sync it with your other squeezeboxes, it's like having another one ;-)

[ATTACH]197971[/ATTACH]

---

### Post by An Sanct on 2011-07-21
If album art an lyrics are what you are searching for, try Clementine, I have it ... it works magic, but I considered a professional approach of using a computer in my reply, sorry ...

---

### Post by Brad55 on 2011-07-21
> **cliver1956 said:**
> 
Web Design - Dreamweaver CS4 - Really powerful wysisyg, php and ajax.

Web Testing - xampp - Local testing of web sites with php and MySql.

Music Streaming - Squeezebox Server - Feed my SB touch perfectly

Local Music - MusicBee - Clean and powerful and it syncs playlists to my HTC HD2 converting on the fly

CD Ripping to flac - Eazy CD-DA Extractor or EAC - Both do the basic ripping job well. I'm not worried about the tagging at this stage as I use...

Tag Editor - Mp3Tag - It's simply brilliant at tagging all my files, making sure all tags are ID3V2.3, cleaning out any others and embedding album art.

Album Art Finder - Album Art Downloader - One stop search of all repositories, never fails to find it. 

As far as Dreamweaver goes there is nothing better for web pages, and I think Macromedia should have never sold it, but I have Dreamweaver MX running on Ubuntu 10.04 under wine and it works well, but I have not tried everything.

Oh and for web design you can have the CMS Drupal, Joomla, and Wordpress installed under Ubuntu.

MusicBee I have no idea what it does but I have a Droix X and I just drop music in the folder and the play pulls it in. Ubuntu sees it as a storage device like an SD card.

CD Ripping to many programs to name that will do that for you in Linux. ([[COLOR="Blue"]Asunder[/COLOR]]("http://littlesvr.ca/asunder/"), [[COLOR="Blue"]RipOff CD ripper[/COLOR]]("http://ripoffc.sourceforge.net/"))

Tag Editor again a lot out there [[COLOR="Blue"]EasyTAG[/COLOR]]("http://easytag.sourceforge.net/") for one ans another [[COLOR="Blue"]puddletag[/COLOR]]("http://puddletag.sourceforge.net/")

For Album Art there are a few [[COLOR="Blue"]Album Cover Art Downloader[/COLOR]]("http://www.unrealvoodoo.org/hiteck/projects/albumart/"),  [[COLOR="Blue"]Banshee[/COLOR]]("http://banshee.fm/"), [[COLOR="Blue"]Rhythmbox[/COLOR]]("http://projects.gnome.org/rhythmbox/") with plugins.

Side note: You can run a VirtualBox with Windows installed on that if you need a windows program I do some graphics and I have Windows XP with Photoshop CS2 installed in a VirtualBox only when I need it.

---

### Post by cliver1956 on 2011-07-21
Thanks guys, some good advice there. 

@yeats: I was trying to think about what I need in posting my reasons for using the particular app. I'm not saying I want all the functionality of each windows app but those that I have stated in my OP are key. Yes I agree Dreamweaver is going to be hard to replace but then I don't use all its bells and whistles.

@An Sanct: flac is the Free Lossless Audio Codec. It is still a perfectly valid codec and is, as the name suggests, "lossless" which is why I use it where I have an original copy of the album.

@jjex22: I'm trying to avoid wine if I can (hick! ;-). May well fail miserably though ;-) 
I have just tried installing album art cover downloader using the command line from the web site "#sudo apt-get install python-qt3 python-imaging".
It seemed to install OK but I can't find it to run it. What am I missing? (newbie daft question no doubt ;-)
Thanks to everyone else for responding so quickly. I'll read through and try some out.

Many thanks guys.

---

### Post by andrew.46 on 2011-07-22
> **An Sanct said:**
> Well, about bluefish ... 2.0 is here ... it is up to date ...

Or 2.0.3 even if you fancy a little compiling:

Howto: Build the newest version of Bluefish under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

Gratuitous screenshot attached :).

---

### Post by nothingspecial on 2011-07-22
To install squeezeslave

```
sudo apt-get install subversion liblircclient-dev libncurses5-dev libasound2-dev
svn checkout http://squeezeslave.googlecode.com/svn/squeezeslave/branches/squeezeslave-1.1-253
cd squeezeslave-1.1-253/
make -f makefile.linux26-alsa-display
sudo mv bin/squeezeslave /usr/local/bin
```

To run it
```

squeezeslave -D [COLOR="Red"]192.168.1.10[/COLOR]
```

change the red ipaddress for the host of your server.

Navigate the menus (which are exactly the same as a squeezebox) with your arrow keys.

 
                                ```
  Insert or I      Add
                                  Cursor Keys      Arrows
                                  >,<              Fwd,Rew
                                  Home or H        Home
                                  End or N         Now Playing
                                  Space or P       Pause
                                  Enter            Play
                                  Q                Quit
                                  R                Repeat
                                  S                Shuffle
                                  ?                Search
                                  b                Browse
                                  F                Favourites
                                  %                Size
                                  Z                Sleep
                                  +,-              Vol up,down
```

---

