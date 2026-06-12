---
title: "Need Installation Help"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by c5vetter on 2009-08-15
Okay, old fart newb here - made the switch from MicroShit and was able to use WUBI to load - figured out how to get everything configured that did not auto configure

do, have one problem though - downloaded a program but now don't know where it was saved! and, then once someone tells me where to look - exactly how do I do an install of the downloaded program?

guess, am looking for a GUI type of install or something? not very command-line literate ---- like I said BRAND NEW to Ubuntu!

TIA for any and all assistance

BTW - to prove how old a fart I am, am a veteran of Woodstock

---

### Post by pedro3005 on 2009-08-15
The files with .deb extensions will provide you with a GUI installer. The easiest way you get to install programs is going to Applications > Add/Remove... But, not all programs are there. If you download a .deb package, double click it, install. Ubuntu cannot open packages like .rpm , they are made for other distros. You may try to convert them using a tool named alien.

As for where it is, how did you download it? If you need, go to Places > Search for Files  ;)

---

### Post by jonabyte on 2009-08-15
depends on what type of file you downloaded, was it a deb file?
if so, you can right-click the file and select Open with GDebi package installer.
if not, you probably downloaded a tar.gz file which you will need to use the command line to install it, read this:

[http://www.cyberciti.biz/faq/install-tarballs/]("http://www.cyberciti.biz/faq/install-tarballs/")

alternatively, you can try installing your program from the repositories.
just open terminal and type:

```
sudo apt-get install "packagename"
```

replace packagename with the name of the software

---

### Post by nhasian on 2009-08-16
Here's a guide you should read:  [Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by SunnyRabbiera on 2009-08-16
Yeh installing sotware in Ubuntu is different then windows, but its not that hard to learn.
Although compiling can be a chore

---

### Post by colau on 2009-08-16
> **c5vetter said:**
> Okay, old fart newb here - made the switch from MicroShit and was able to use WUBI to load - figured out how to get everything configured that did not auto configure

do, have one problem though - downloaded a program but now don't know where it was saved! and, then once someone tells me where to look - exactly how do I do an install of the downloaded program?

guess, am looking for a GUI type of install or something? not very command-line literate ---- like I said BRAND NEW to Ubuntu!

TIA for any and all assistance

BTW - to prove how old a fart I am, am a veteran of Woodstock
Welcome to the forum.
> have one problem though - downloaded a program but now don't know where it was saved! and, then once someone tells me where to look - exactly how do I do an install of the downloaded program?
How did you download, using the firefox downloader?
If you download using the firefox downloader,check from the Firefox Browser>Edit>Preference>Main>*Downloads*
Check the file in Places>Home Folder and /home/"other folders" or in the "/" directory.
To install any software:
System>Administration>Synaptic package manager

---

### Post by c5vetter on 2009-08-16
okay, understand what each of you said - but......where the heck is the file I downloaded? don't have a clue where it is located!?

how do I find the downloaded file?

once I find it, believe I now know how to install

---

### Post by mrbiggbrain on 2009-08-16
Probably in /home/username/

my reasoning, by default users have the right to write reatty much exsclusivly in there home directory (~/)

the output of 

```
ls ~/
```

should list the file. if not there might be a downloads folder or something.

---

### Post by colau on 2009-08-17
> **c5vetter said:**
> okay, understand what each of you said - but......where the heck is the file I downloaded? don't have a clue where it is located!?

how do I find the downloaded file?

once I find it, believe I now know how to install
Run the find command.

---

### Post by colau on 2009-08-17
[find]("http://www.computerhope.com/unix/ufind.htm")

---

### Post by pedro3005 on 2009-08-17
If you don't want to use commands, like I said, go to Places then Search for Files. If you really can't find it, and it's not very big, maybe you just download it again, now setting firefox to ask you where to put the files (Edit - Preferences - Select 'Always ask me where to save files').

---

### Post by trilobite on 2009-08-17
> **pedro3005 said:**
> If you don't want to use commands, like I said, go to Places then Search for Files. If you really can't find it, and it's not very big, maybe you just download it again, now setting firefox to ask you where to put the files (Edit - Preferences - Select 'Always ask me where to save files').

Agreed, this is very good advice. 

One thing that I think you'll actually begin to like (eventually!) is that in Ubuntu (and in most other distros), if you use the built-in tools like apt (or the graphical front-end to it called "Synaptic"), then you actually *don't need to know* where an app is installed. This is because the built-in tools (apt in this instance) take care of that for you, automatically. All you have to do is to sit back with a cup of coffee and enjoy the ride.... ;)  

Of course, if you (say) download a tar.gz file and compile it manually, *then* yes, you do need to know where you've downloaded it to, and where it'll be installed. But, as long as you stick with apt or Synaptic, that isn't the case. They just slap the app on your system and you're "good to go".... 

Hope this helps... ;) 
- trilobite

---

### Post by Bartender on 2009-08-17
I'm also an "old fart" using Ubuntu.  Well, middle-aged anyway.  I know one of the things that freaked me out about Ubuntu was I didn't know where things were going.
One thing that I think will help you is changing where Firefox saves downloads.  Although Firefox behaves very much like it does in Windows, Options isn't under Tools.  Go to Edit>Preferences.  On the "Save downloads to:" line, change it to Desktop.  That's the simplest thing to do.  You'll know where to find stuff that you downloaded in Firefox.  I also created a folder in the Home folder called "D'loads" or something similar.  When I want to get a download off the desktop I'll move it to that folder in Home.

trilobite's comments remind me of something I read on these forums a few years ago, made by a guy who was not a newb.  He said he didn't care where 98% of the stuff went, or what such-and-such folder did.  All he cared about was his Home folder.  That sounds pretty strange coming from the Windows world but I've found it to be applicable.  Unless of course you want to start digging into the guts of how Linux works.

---

### Post by c5vetter on 2009-08-17
okey dokey - thanks for all the "spot on" replies - will TRY to find the file when I get home - if not, will download again and make sure to download as suggested

---

### Post by egalvan on 2009-08-17
The best place for "old fart newbs" to find software to install is Synaptic.

This is found in

 System -> Administration

It's similiar to Add/Remove that is found in Applications,
but lists FAR more software...
Jaunty listed 26,753 packages avaiable.

Synaptic does all the hard work for you, allowing you to learn the system.


And one last point...

Some of us here on the forums don't like Microsoft one little bit...

but calling it MicroS**t is un-called for...

Respect is one thing almost all of us strive for.

ErnestG

On the north side of 50.

---

