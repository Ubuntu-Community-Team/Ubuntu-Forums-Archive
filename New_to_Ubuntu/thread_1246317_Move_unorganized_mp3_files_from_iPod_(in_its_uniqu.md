---
title: "Move unorganized mp3 files from iPod (in its unique system) to hard drive"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by hanzj on 2009-08-21
Hello,
I have an iPod. Using both Windows and Ubuntu, I have used various programs to put audio/MP3s into the iPod. These include iTunes, gtkpod, rhythmbox,  songbird, banshee and others.

But now I want to "export" my audio from the iPod to my hard drive. A mere copy-and-paste (or drag-and-drop) will not do because on my iPod, the music is scattered in special folders and have special names, thanks to iPod's special way of syncing. How can I export my stuff from iPod into nice human-workable folders and filenames, just as things were when I synced audio from my hard drive to the iPod?

(This is 1 reason why I wish I had a regular mp3 player. 8-)   )

---

### Post by LowSky on 2009-08-21
I dont know of a way as the ipod crappy rule for changing names and odd detination folder is part of its attempt to make it hard for people to pull the music off the player.

---

### Post by tgalati4 on 2009-08-21
Put floola on your ipod.  With it, you can drag and drop files off of the ipod with meaningful names.

You should also be able to use any of several music players.  Take rhythmbox.  Plug in your ipod, click on it in the devices section.  Import the music with the "copy music into Library" preferences setting.  That will simultaneously index the music, create directories, and put the tracks onto the harddisk.  Then you can move them around.

---

### Post by hanzj on 2009-08-21
tgalati4,
I have rythymbox open, but where's the "copy music into library" preference setting?

---

### Post by hanzj on 2009-08-21
tgalati4, i downloadde floola-linux, and it has 2 files:
1) Floola
2) Readme.txt

According to nautilus, Floola file appears to be an executable. Are not executables Windows OS terminology?

---

### Post by tgalati4 on 2009-08-21
I believe it's a JAVA application.  You drag it to the root directory of your ipod.  When it's there, double-click it and it will open up and start to index the files on the ipod.  This will take some time, so be patient.

When the files show up in floola, then you can copy music to any directory you want.

Floola is simply a music database that resides on the iPod, sort of a human-readable backup to iPod's crazy system.

---------------------

For rhythmbox, you have to delete your current library--basically start out fresh.

You're right, that switch is on another player, perhaps banshee.  Rhythmbox copies files to your /Music directory making Artist and Album subdirectories as needed.  So when you plug in your ipod, songs should show up.  Highlight a bunch of songs and drag them to the "Library".  Be patient, it takes time to copy the files.  When done, the songs show up in your Library. 

Open Nautilus and go to your Music directory and the files should be there.

---

### Post by hanzj on 2009-08-21
tgalati4,
Thanks! I did the rhythymbox option. It took time. But it worked well! I removed the songs from my library (not the one that really deletes the source files, but just the one that removes songs from Rhythmbox view). I then did select all in the iPod music folder and did "copy". Then I went up to "library". Then clicked paste. It works well.

Thanks again.

---

### Post by tgalati4 on 2009-08-22
Definitely install floola.  A new version is out that runs faster than previously.  Read the readme.txt file.  Floola is handy because it works wherever you plug your iPod into.  It runs on Linux, Mac and Windows.  Truly a novel solution to a pesky problem that has plagued iPods for years.

As for Rhythmbox, I don't know of any way to do it without clearing out your Library. Otherwise it will simply mix the music in with your existing library with no way to sort the music out without special ID3 tags and smart playlists.

Having several music players in Linux is helpful because you can use each one for a specific purpose.  For instance if you didn't want to trash your existing library, you could download the "Listen" music player with no library, set up the music database directory to someplace useful and import your iPod into it.

Most of the music players use the same iPod-reading libraries so if one works, they all work.

---

### Post by hanzj on 2009-08-22
can you give me step-by-step instructions for floola? I read the readme.txt but I don't know what to do.

---

### Post by tgalati4 on 2009-08-22
The readme.txt used to include installation instructions.

Run floola by double-clicking it.  Go to help-about to make sure you have version 5.3 (the latest and greatest).

Close floola.

Hook up iPod with USB cable to computer with floola on it.  Open up a file manager window on the iPod.  You should be at the root directory of the iPod.  Open up a file manager with floola showing.  Drag and drop floola into the root directory of the iPod.

That's it.

To run floola, connect your iPod to any computer, simply double click on the floola icon.  It uses 22 MB of space plus a few megs for the database.  Floola will index your iPod.  This will take some time.  Once that is done, songs will show up.  You can now move songs back and forth between the computer and the iPod.

If you are really happy with the performance of floola, donate to the project.

---

### Post by hanzj on 2009-08-22
i extracted floola-linux.tar.gz into a folder. I then double-clicked on Floola. 

But nothing happened.

Just to let you know, Right-click/Properties/Basic Tab/Type: says:
> executable (application/x-executable)isn't this a Windows thing? 
I downloaded Floola-**linux**.tar.gz so I don't think I downloaded the wrong thing.

---

### Post by hanzj on 2009-08-22
I realized I needed to do:
> sudo apt-get install libstdc++5

---

### Post by hanzj on 2009-08-22
A question re: floola.
If I install Floola on my iPod, does this mean I can now drag-and-drop my MP3s from my hard drive to my iPod, via a file-manager program like Nautilus, and without a special program like gtkpod or iTunes?

---

### Post by pedja_portugalac on 2009-08-22
Don't mess with floola, it's stand alone program and personally for me gtkpod is the best!

GtkPod will copy back songs on your computer and wherever you want to. Just select songs you want to extract then right click on them and chose Copy selected track(s) to > Music Library > Music Library and then chose your Music directory or create a new one. 

PS. Do not chose to copy to many files at the same time because to many files can crash gtkpod, instead copy them by 20 par example.

For the folders, you can inside gtkpod window select one album then create folder for it in your music library and send whole album to that directory. The songs preserve id tags anyway.

---

### Post by tgalati4 on 2009-08-22
Since floola is cross-platform, you can run it on several machines.  Since it resides on your iPod, it's always available.

---

### Post by pedja_portugalac on 2009-08-28
> **tgalati4 said:**
> Since floola is cross-platform, you can run it on several machines.  Since it resides on your iPod, it's always available.

It's cross platform but for every platform you need one executable on your ipod. One for Linux, another for Windows and one for Mac. You can't run same program on all of them.

---

### Post by hanzj on 2009-08-29
I put the linux program and the windows program on my iPod since those are the two operating systems I will be using. Floola is good stuff, at least so far! Thanks for suggesting this, tglati4.

---

