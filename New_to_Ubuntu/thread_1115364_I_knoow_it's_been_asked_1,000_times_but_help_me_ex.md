---
title: "I knoow it's been asked 1,000 times but help me extract.rar files!"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Jokaman70 on 2009-04-03
OK, so I've read and I've read and I've read these forums about how to download rapidshare (.rar) files and extract them and view/listen to them but I'm just not getting it! 

I JUST switched from Vista and I DL a lot of music, movies, television shoes, etc. I'm used to finding a bunch of rapidshare links, downloading them via Flashget, and extracting them via winrar - simple, beautiful, reliable.

Now I'm using Ubuntu and the entire thing's stressing me out!

So I'm locating these rapidshare links while using Konqueror, I copy the links and begin downloading them using KGET, once they're all DL'd I open up the folder I have the .rar files in and I highlight them all and 'extract here' and it creates an empty folder. If I double click them 'archive manager' opens up, I see the appropriate file type (.avi for example), double click it and it won't play in totem, vlc, etc. 

I open up 'terminal' (I've already installed unrar), I enter:
unrar x *filename*

Sometimes it'll say 'all ok' (mostly when I'm doing music), but when I'm doing movies it'll say 'crc error.'

Anyways, I clearly don't know what I'm doing, please help!

---

### Post by Jokaman70 on 2009-04-03
joe@joe-laptop:~$ cat /name/of/file > /dev/dsp
bash: /dev/dsp: Device or resource busy
joe@joe-laptop:~$ unrar x '/home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part1.rar' 

UNRAR 3.80 beta 2 freeware      Copyright (c) 1993-2008 Alexander Roshal


Extracting from /home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part1.rar

Extracting  House.S05E19.HDTV.XviD-LOL.avi                            24%

Extracting from /home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part2.rar

...         House.S05E19.HDTV.XviD-LOL.avi                            49%

Extracting from /home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part3.rar

...         House.S05E19.HDTV.XviD-LOL.avi                            60%
House.S05E19.HDTV.XviD-LOL.avi - CRC failed

Extracting from /home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part4.rar

Extracting  House.S05E19.HDTV.XviD-LOL.avi                            99%
Calculating control sums of all volumes.
Cannot find volume /home/joe/Desktop/RS Downloads/House.S05E19.HDTV.XviD-LOL.part5.rar
House.S05E19.HDTV.XviD-LOL.avi - CRC failed
Total errors: 2
joe@joe-laptop:~$

---

### Post by Jokaman70 on 2009-04-03
When I simply highlight both completed (of 2 total parts) .rar files and 'extract here' it'll say 'extracting files from archive and then say 'an error occurred while extracting files' and 'Cannot find volume /home/joe/Desktop/RS Downloads/House__M.D._5x19_-_Locked_In.part3.rar
House, M.D. 5x19 - Locked In.avi - CRC failed.'

I have no clue what's going on.

---

### Post by Jokaman70 on 2009-04-03
joe@joe-laptop:~$ unrar e '/home/joe/Desktop/RS Downloads/House__M.D._5x19_-_Locked_In.part1.rar' 

UNRAR 3.80 beta 2 freeware      Copyright (c) 1993-2008 Alexander Roshal


Extracting from /home/joe/Desktop/RS Downloads/House__M.D._5x19_-_Locked_In.part1.rar

Extracting  House, M.D. 5x19 - Locked In.avi                          49%

Extracting from /home/joe/Desktop/RS Downloads/House__M.D._5x19_-_Locked_In.part2.rar

...         House, M.D. 5x19 - Locked In.avi                          99%
Calculating control sums of all volumes.
Cannot find volume /home/joe/Desktop/RS Downloads/House__M.D._5x19_-_Locked_In.part3.rar
House, M.D. 5x19 - Locked In.avi - CRC failed
Total errors: 1

CRC failed again, and there is no part 3 - what is it talking about?! 

I've tried this with like 4 different sets of links so it's not just that the files are bad.

---

### Post by karlr42 on 2009-04-03
Maybe the files are being corrupted in the download? CRC is a way of verifying a file is the same inbetween the server and the client(you) after download.

---

### Post by Jokaman70 on 2009-04-03
> **Jokaman70 said:**
> I've tried this with like 4 different sets of links so it's not just that the files are bad.

I dunno, man.

---

### Post by Jokaman70 on 2009-04-03
I have a theory I'm going to try out...

When I downloaded a music album, a single link, it worked fine. Maybe it's downloading multiple links that's screwing me up, which might indicate that KGET isn't working properly (maybe that my rapidshare premium account info. isn't entered properly or something.)

I'm going to DL a single link television show now just as an experiment, we'll see if it works, and if it does maybe I'll be able to zero in on what's going wrong.

---

### Post by rhcm123 on 2009-04-03
if you have the rar and unrar packages installed, just use the archive roller to unrar. Also, house is a great show.

---

### Post by billgoldberg on 2009-04-03
Remove unrar and install p7zip-full.

Is there any reason you are using all those KDE apps?

It says you are using Ubuntu.

---

### Post by Jokaman70 on 2009-04-03
> **rhcm123 said:**
> if you have the rar and unrar packages installed, just use the archive roller to unrar. Also, house is a great show.

Archive roller? I don't think I have a 'rar' package installed, just 'unrar' - unless that comes preinstalled with Ubuntu?

House is a GREAT show!

> **billgoldberg said:**
> Remove unrar and install p7zip-full.

Is there any reason you are using all those KDE apps?

It says you are using Ubuntu.

p7zip-full, I've heard of that, will I use that in the terminal or will I just right click, extract here like I normally would in Windows? 

KDE apps?

---

### Post by SuperSonic4 on 2009-04-03
> **Jokaman70 said:**
> Archive roller? I don't think I have a 'rar' package installed, just 'unrar' - unless that comes preinstalled with Ubuntu?

House is a GREAT show!



p7zip-full, I've heard of that, will I use that in the terminal or will I just right click, extract here like I normally would in Windows? 

KDE apps?

Konqueror is a KDE app, it would just be unusual to use konqueror instead of firefox in gnome (ubuntu's standard).

You should be able to right click and extract although I don't know for sure

---

### Post by rhcm123 on 2009-04-03
> **Jokaman70 said:**
> Archive roller? I don't think I have a 'rar' package installed, just 'unrar' - unless that comes preinstalled with Ubuntu?

rar makes rar archives. unrar unmakes rar archives. fairly simple. Archive roller is the nickname for the archive manager built into ubuntu. go to Applications -> Acessories -> Archive Manager to open it. Or right click the rar and hit "open with archive manager".

EDIT: You do not need the rar package to open rar archives, only the unrar package. The rar package is used to make rar archives. :)

> **Jokaman70 said:**
> 
House is a GREAT show!

Indeed. I have all the episodes on DVD - i only torrent things i cant really buy.

> **Jokaman70 said:**
> 
p7zip-full, I've heard of that, will I use that in the terminal or will I just right click, extract here like I normally would in Windows? 

p7zip-full is the backend for the archives. You can use it both in terminal or with archive roller. Archive roller is the front-end, so as long as the nessecary back-end packages are installed, it work with the archives fine.

> **Jokaman70 said:**
> 
KDE apps?
Yeah, you had a bunch of KDE listed

---

### Post by mustache ride on 2009-08-04
:) Let me try this out for you guys who still have issues. I am a total ubuntu noob. I am learning fast that there are several ways to do the same thing in Ubuntu that others insist can only be done through a command line. This thing is working like Windows for me but with an occasional malfunction that I can find help with 99% of the times on this forum. 

To have a setup like mine you need the new Ubuntu (jackaloupe), install anything you can find that relates to updates from the Synaptic Package Manager found in your System/Administration, I installed Konquerer and a bunch of other stuff (no idea what most of it is!)...yep, noob! :popcorn:

Now I had this "CRC FAILED" everytime I tried to unzip things from various places. Some .zip files opened right up and extracted quickly with no issue. I assume many of you with this problem are using "extract here" as I did for a week. It then deletes what appears in the extraction folder.

So I did this: Open the .rar file with the selection you see at the top of the menu you get after right clicking. Now drag and drop the file in the folder you see to your desktop. PRESTO! Your done. You may get another CRC FAILED error but I assure the file is indeed fine (unless it really is damaged). 

I then delete and clean up all parts of the original .rar files I had and CUT & PASTE the new (un rar'ed) file into the folder it belongs in.

A Tip: Many of you have .001 .002 .003 files. These are split files and I myself download WINE (found in the Synaptic Package Manager) and then I downloaded (from the internet) HJ SPLIT. HJ SPLIT seemed to work just by double clcking on the desktop icon after WINE was installed. Once the files are joined your done. If they are .rar files that needed to be joned to unrar them, just follow the steps above! :P

---

### Post by supertoddler on 2009-10-15
Guessing that you have split compressed files (hence the crc checks failing).

Put all the related rar files in one directory.
Open a terminal and go to that directory.
Run this command:
unrar x -kb <add the name of the first rar file here>
[B]
AN example for these 3 files:[/B]
SomeProgrameS02E01.part1.rar, SomeProgrameS02E01.part2.rar, SomeProgrameS02E01.part3.rar

Put them all in /downloads/tmp1/
Then in the open terminal window
**cd downloads/tmp1**
then 
**unrar x -kb SomeProgrameS02****E01.part1.rar**

This will extract the content from the 3 rar files, join the 0s & 1s into a single resulting .avi (or whatever) file. CRC will now be OK and you will have a good file.
[B]
-kb (keep broken)[/B]

---

### Post by marcelo danico on 2009-10-20
> **mustache ride said:**
> :) 

A Tip: Many of you have .001 .002 .003 files. These are split files and I myself download WINE (found in the Synaptic Package Manager) and then I downloaded (from the internet) HJ SPLIT. HJ SPLIT seemed to work just by double clcking on the desktop icon after WINE was installed. Once the files are joined your done. If they are .rar files that needed to be joned to unrar them, just follow the steps above! :P

Thanks so much for the above tip. Worked perfectly on the split rar files!:P

---

### Post by spiepie on 2010-04-15
Thanks i have been trying for ages to sort this our your method worked

great help
cheers!!!

---

