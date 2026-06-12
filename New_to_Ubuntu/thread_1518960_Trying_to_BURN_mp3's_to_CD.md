---
title: "Trying to BURN mp3's to CD"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-27
64 bit Ubuntu 10.4

I have k3b, but have yet to succeed in:

FINDING the k3b handbook to INSTALL (wound up with KDE docs with an icon for the k3b handbook, but no content!)

INSTALLING libk3b2-mp3

Last effort from this site:

[B][http://packages.ubuntu.com/dapper-backports/amd64/libk3b2-mp3/download](http://packages.ubuntu.com/dapper-backports/amd64/libk3b2-mp3/download)

[/B]Got me this:[B]


Error: Dependency is not satisfiable: libdbus-1-2 (>= 0.60)

[/B]And, although someone suggested the following for GPG errors I'm seeing in my list of sources, I'm afraid I'm not using the right syntax to get it to work![B]

"sudo add-apt-repository <rep_name>"

[/B]Apparently, I don't know how to enter <rep name>"

---

### Post by cariboo on 2010-06-27
Why not use the current version of K3b that is in the repositories? You can use The Software Center, or Synaptic Package Manager to install it. Make sure you have the libk3b6-extracodecs installed.

---

### Post by cogier on 2010-06-27
I am not sure exactly what you are trying to do but I have just installed k3b from the repository and the help files are available if you load up the khelpcenter4

---

### Post by phubert28 on 2010-06-27
Well, I have Gnome, if that makes a difference.

I DID install via Synaptic.

When I drag mp3's to the project, they show up as MPEG1's and take as much space as the original track.

I WANT the compression of the mp3's. I am trying to get 7 CD's on one (as I did do using RealPlayer on Windows (when I HAD Windows! :-D - not that I want to go back!)

And of course I want the result to BE an audio CD with full track info. The one I burned on Windows has all this.

Everything I read says I need libk3b2-mp3 to do what I want and I haven't been able to find one that will install.

Nor did my k3b install with its documentation (handbook)

I also don't plan to move to KDE... tho I suppose I might if that's what's required...

I was trying to keep this move to Ubuntu as uncomplicated as possible... so far that hasn't been very uncomplicated!

I picked 64 bit because it makes little sense to me that we'd still be USING 32 bit OSes when all the CPUs are 64... it's simply irrational.

---

### Post by AlphaLexman on 2010-06-27
> **phubert28 said:**
> When I drag mp3's to the project, they show up as MPEG1's and take as much space as the original track.

I WANT the compression of the mp3's. I am trying to get 7 CD's on one 

And of course I want the result to BE an audio CD with full track info. 

I don't believe this is possible based on ISO standards for CD-ROM. Audio cd's are limited by minutes ~80. Data cd's are limited by megabytes ~700.

A standard audio cd player will NOT play an mp3 data disc. An mp3 compatible drive will play BOTH audio cd's and mp3 data cd's.

Even in M$ windoze this is not possible.

Regards.

---

### Post by phubert28 on 2010-06-27
Which part is not possible? I HAVE the CD I ripped w. mp3's and my CD player plays it... with all track info: title, artist, etc.

And I was able to write the content of the original 7 CD's (first downloaded to the hard drive as mp3's) to it.

---

### Post by AlphaLexman on 2010-06-27
Then your cd player is dual mode, meaning it will read data/mp3 discs.

Find a really old cd player and see if it works. [It won't]

In K3b just select New Data Project. Drag and Drop your mp3's and burn. Your cd drive will still play them with all id3 info.

---

### Post by phubert28 on 2010-06-27
That simple, huh? I ASKED one member at varlinux.org that specifically, but you know these written communications are often inadequate for full understanding.

Sorry for being so stupid, tho. I'll try that.

---

### Post by corncob on 2010-06-27
I burned (and played) 200 mp3's on a single CD one time.  This was about 15 years ago on Windows with Roxio CD Creator so this is probably not much help here.  I just wanted to say that I burned it as a data disk, not a music disk.

---

### Post by phubert28 on 2010-06-27
Well, to show you where my MIND is, I may have done the same not realizing that is what I had done.

Thanks for the additional confirmation, anyway!

---

### Post by Cresho on 2010-06-27
I use k3b or brasero to burn data disks with mp3's in them.  What is so hard about that?  it works fine on cars that play mp3's cd;s

nero stupifies things with "mp3 cd"  that kind of crap.  It is basically a data disk.  open up brasero and tell it you want to make a data disk.....throw all your mp3 into it and burn.  make sure if finalizes.

---

### Post by phubert28 on 2010-06-27
And that's the entire point... I simply didn't EXPECT that burning AS a data disk would work!

Part of the problem there is that I have no specs on what is WRITTEN with an mp3 file.

In the old mainframe days, I'm used to the manuals that document file headers & such, down to the byte level (and below (that is to bit switches and their significance)).

I'm afraid I hadn't even THOUGHT looking for the same for these formats.

In every case, of course, the applicable term is "protocol".

---

### Post by Rey117 on 2010-06-27
Brasero works for me!

---

### Post by Cresho on 2010-06-27
I take it this is solved.  Mark thread as solved.

---

### Post by Cresho on 2010-06-27
> **phubert28 said:**
> And that's the entire point... I simply didn't EXPECT that burning AS a data disk would work!

Part of the problem there is that I have no specs on what is WRITTEN with an mp3 file.

In the old mainframe days, I'm used to the manuals that document file headers & such, down to the byte level (and below (that is to bit switches and their significance)).

I'm afraid I hadn't even THOUGHT looking for the same for these formats.

In every case, of course, the applicable term is "protocol".

ya you got to remember windows makes people stupid.  Even the help files suck.  Everything sucks on it.  I can't ever remember using a manual even installing windows 98 on my first pc.

format dis, fat32 partition, and issue the command to execute from floppy the cd executable after cd drive drivers where loaded into memory and bam.  easy.

Now its load cd into tray and install ubuntu.  super easy.

---

### Post by phubert28 on 2010-06-27
:-)

Yes, you're likely right on target.

I was 'downsized' from mainframe support to Windows server support - UGH!!!

A consultant told the site to move to UNIX - of course management wouldn't listen to that.

Now I'm retired (after being fired for insubordination! Cool! I just got a gold star!!! :lol:)

Can you imagine a 61 year old getting fired for insubordination! They did me such a favor!!!

:-D

---

### Post by Cresho on 2010-06-27
ya, my brothers company went from windows to unix in a blink of an eye.  He is unix system admin with a resume so big it stacks with 20 plus sheets last i looked 10 years ago.

Have fun!

---

### Post by Dustin2128 on 2010-06-27
I'd use brasero; it's always worked well for burning MP3's for me. Available via synaptic if its not preinstalled.

---

### Post by phubert28 on 2010-06-27
Yeah, I installed it some time ago... but that was to burn an iso (GParted live)

Ahhh, Data! How appropriate! :)

---

