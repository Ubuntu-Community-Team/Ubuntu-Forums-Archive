---
title: "RhythmBox Annoyance (Codecs not found, pop-ups irritating)"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-15
Everytime I open rhythmbox, I get a tone of these dialogues.
When I click search on any of them, it never finds any of the codecs.
I'm wondering how I can fix this, or at least turn off the notifications.
It's quite annoying:(

---

### Post by zerhacke on 2009-06-15
Try installing the ubuntu-restricted-extras package, or if you are using Kubuntu, install the kubuntu-restricted-extras

---

### Post by csl5010 on 2009-06-15
ubuntu doesn't support those restricted formats such as .mp3. But download a file called "restricted extras" in Applications -> Add/Remove will solve your problem.;)

---

### Post by entikryst on 2009-06-15
Codec Problems? You can install Medibuntu.  Let NixiePixel guide you through it.



[http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)

---

### Post by Gp. on 2009-06-15
I get the error:

```

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
```

---

### Post by entikryst on 2009-06-15
Have you tried Medibuntu yet?

---

### Post by NightwishFan on 2009-06-15
Run this command in the terminal. If it asks you to say 'yes' to anything, do not, and post the output here.

```

sudo apt-get update && sudo apt-get -f install

```

---

### Post by Gp. on 2009-06-15
```
Hit http://mirror.netspace.net.au jaunty Release.gpg
Hit http://mirror.netspace.net.au jaunty/main Translation-en_AU
Ign http://mirror.netspace.net.au jaunty/restricted Translation-en_AU
Ign http://mirror.netspace.net.au jaunty/universe Translation-en_AU
Ign http://mirror.netspace.net.au jaunty/multiverse Translation-en_AU
Hit http://mirror.netspace.net.au jaunty-updates Release.gpg                   
Ign http://mirror.netspace.net.au jaunty-updates/main Translation-en_AU        
Ign http://mirror.netspace.net.au jaunty-updates/restricted Translation-en_AU  
Ign http://mirror.netspace.net.au jaunty-updates/universe Translation-en_AU    
Ign http://mirror.netspace.net.au jaunty-updates/multiverse Translation-en_AU  
Hit http://mirror.netspace.net.au jaunty-security Release.gpg                  
Ign http://mirror.netspace.net.au jaunty-security/main Translation-en_AU       
Ign http://mirror.netspace.net.au jaunty-security/restricted Translation-en_AU 
Ign http://mirror.netspace.net.au jaunty-security/universe Translation-en_AU   
Ign http://mirror.netspace.net.au jaunty-security/multiverse Translation-en_AU 
Hit http://mirror.netspace.net.au jaunty Release                               
Hit http://mirror.netspace.net.au jaunty-updates Release                       
Hit http://mirror.netspace.net.au jaunty-security Release                      
Hit http://mirror.netspace.net.au jaunty/main Packages                         
Hit http://mirror.netspace.net.au jaunty/restricted Packages                   
Hit http://mirror.netspace.net.au jaunty/main Sources                      
Hit http://mirror.netspace.net.au jaunty/restricted Sources                
Hit http://mirror.netspace.net.au jaunty/universe Packages                 
Hit http://mirror.netspace.net.au jaunty/universe Sources                  
Hit http://mirror.netspace.net.au jaunty/multiverse Packages               
Hit http://mirror.netspace.net.au jaunty/multiverse Sources                
Hit http://mirror.netspace.net.au jaunty-updates/main Packages             
Hit http://mirror.netspace.net.au jaunty-updates/restricted Packages       
Hit http://mirror.netspace.net.au jaunty-updates/main Sources              
Hit http://mirror.netspace.net.au jaunty-updates/restricted Sources        
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_AU              
Hit http://mirror.netspace.net.au jaunty-updates/universe Packages             
Hit http://mirror.netspace.net.au jaunty-updates/universe Sources
Hit http://mirror.netspace.net.au jaunty-updates/multiverse Packages
Hit http://mirror.netspace.net.au jaunty-updates/multiverse Sources  
Hit http://mirror.netspace.net.au jaunty-security/main Packages      
Hit http://mirror.netspace.net.au jaunty-security/restricted Packages
Hit http://mirror.netspace.net.au jaunty-security/main Sources       
Hit http://mirror.netspace.net.au jaunty-security/restricted Sources 
Hit http://mirror.netspace.net.au jaunty-security/universe Packages  
Hit http://mirror.netspace.net.au jaunty-security/universe Sources   
Hit http://mirror.netspace.net.au jaunty-security/multiverse Packages
Hit http://mirror.netspace.net.au jaunty-security/multiverse Sources 
Hit http://wine.budgetdedicated.com jaunty Release                   
Ign http://www.pvv.ntnu.no ./ Release.gpg      
Ign http://www.pvv.ntnu.no ./ Translation-en_AU
Ign http://wine.budgetdedicated.com jaunty/main Packages
Get:1 http://www.pvv.ntnu.no ./ Release [712B]
Hit http://wine.budgetdedicated.com jaunty/main Packages
Hit http://www.pvv.ntnu.no ./ Packages
Hit http://www.pvv.ntnu.no ./ Sources
Fetched 1B in 2s (0B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libiso9660-5 libdvbpsi4 libmatroska0 liblua5.1-0 libtar libvcdinfo0 libebml0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by NightwishFan on 2009-06-15
I see two easy solutions.

Solution 1: Disable scanning the music library in Rhythmbox, and that will disable the messages, the only problem is whatever music needs the codecs will not play.

Solution 2: Seems you have no conflicts. Open the Synaptic Package Manager and try to install Ubuntu-Restricted-Extras. That should enable all the gstreamer plugins.

---

### Post by guyminuslife on 2009-06-15
Do you have any non-music files in the library folder? I've had Rhythmbox try to search for codecs for files that aren't even music.

---

### Post by pous on 2009-06-15
[this]("http://ubuntuforums.org/showthread.php?t=1180896") thread helped me with my multiedia problems...

---

### Post by callan79 on 2009-06-15
> **guyminuslife said:**
> Do you have any non-music files in the library folder? I've had Rhythmbox try to search for codecs for files that aren't even music.


I was about to post the same thing ... :)

I've noticed that I get this same popup on my system(s), but only in Jaunty, it didn't happen before.

I suspect that Rhythmbox is trying to open non-music files. For example a folder full of music may have a text file, or a graphic, in there. Ideally Rhythmbox _should_ ignore these files, however it seems it's spitting errors instead.

I'm yet to try deleting all non-music files to see if it solves the problem.

Callan

---

### Post by lhb1142 on 2009-06-15
I have been using Ubuntu for a year now. I started with 'Hardy,' moved up to 'Intrepid,' and am now using 'Jaunty.'

I have tried RhythmBox in all three versions and I just do not like it. I do not use it at all. When the new Ubuntu version 9.10 arrives in October I'll take another look but I'm not anticipating much (if any) improvement.

May I suggest trying VLC, Audacious, and SMPlayer? I use all three as there are some times in which one will work better than another; with any given audio file/folder it's strictly (for me) trial and error to see which sounds/works best.

Just make sure you have the Medibuntu repository installed and activated. Add whatever audio codecs you can find in the Synaptic Package Manager, especially those recommended by others answering you.

I find it helpful in Synaptic Package Manager to just Search for "Audio Codecs" and install those entries which look as though they will be helpful/useful.

Also this site [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) is VERY useful. Read it CAREFULLY, follow its instructions CAREFULLY, and you'll be in business!

I hope this helps you.

---

### Post by kpkeerthi on 2009-06-16
This happened to me when I had non-music files (except .jpg - cover art - files & possible other image format) the Music folder imported into Rhythmbox's library. Getting rid of the files solved it.

---

### Post by Gp. on 2009-06-16
I've tried to install the extras, and it didn't do anything btw.
I've tried a few other players and Rhythm I actually like alot.
There doesnt seem to be anything other than music files....

---

### Post by callan79 on 2009-06-16
> **Gp. said:**
> I've tried to install the extras, and it didn't do anything btw.
I've tried a few other players and Rhythm I actually like alot.
There doesnt seem to be anything other than music files....


Hi Gp,

From memory, Rhythmbox uses your home directory as it's default media library. So perhaps it's imported something weird. Or perhaps one of your media files is corrupt.

To test this, I just started rhythmbox from a terminal, thinking that perhaps I'd see some errors on the screen. And, I did! It doesn't tell me the filename, but at least I can see what's going on :

> 
callan@brutis:~$ rhythmbox
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|text/html decoder|decoder-text/html


So it's getting upset about an HTML file. All I have to do now is find it I suppose.

Do you get something similar?

Cheers
Callan

---

### Post by Gp. on 2009-06-16
Nope :S
I get ones about Windows Media Codecs.
Maybe for .wma files?

---

### Post by callan79 on 2009-06-16
> **Gp. said:**
> Nope :S
I get ones about Windows Media Codecs.
Maybe for .wma files?


Possibly .... I don't have any .wma (eww!) files so I can't test that.

But I can tell you that for codecs, I just install the 'ubuntu-restricted-extras' package. This package includes fonts, flash and codecs. This seems to play everything that I ever try.

What do you have installed?

Cheers
Callan

---

### Post by Gp. on 2009-06-16
> **callan79 said:**
> Possibly .... I don't have any .wma (eww!) files so I can't test that.

But I can tell you that for codecs, I just install the 'ubuntu-restricted-extras' package. This package includes fonts, flash and codecs. This seems to play everything that I ever try.

What do you have installed?

Cheers
Callan

As I said, that's what I installed.
It didn't make any difference whatsoever.

Though I think I've found some files that could cause a bit of the problem.
I deleted a tone of desktop.ini files, created when I used windows probably.
But this didn't change much, I still get bombed with these messages.

---

### Post by callan79 on 2009-06-16
> **Gp. said:**
> 
But this didn't change much, I still get bombed with these messages.


Hi Gp,

Check out the man page for rhythmbox. Perhaps try starting it in debug mode or something. This may well provide too much output, but give it a try anyway (I'm at work on a Windows box now, so I can't try).

Else, look in ~/.local/share/rhythmbox, back up your database file somewhere safe, delete the real database file (rhythmdb.xml I think) and then re-create your library from scratch.

Good luck!

CD

---

### Post by Gp. on 2009-06-18
My solution?
USE BANSHEE!

sudo apt-get install banshee


MUCH BETTER!

---

### Post by JDorfler on 2009-06-18
If you are using Jaunty, I suggest installing Exaile.  If not go to the link [here]("http://www.exaile.org") and follow the directions for the latest and greatest.

---

### Post by Gp. on 2009-06-19
Exaile is also nice...=)

---

### Post by emeraldgirl08 on 2009-06-19
> My solution?
USE BANSHEE!

Ha ha ha. That's just what I was going to tell you!

I use Banshee and deleted Rhythmbox from my Applications.

Glad you found a solution :)

---

### Post by Gp. on 2009-06-20
Hahaha.
Great minds think alike XD

---

### Post by Gp. on 2009-06-20
Any light on this though?
[http://ubuntuforums.org/showthread.php?p=7487628#post7487628](http://ubuntuforums.org/showthread.php?p=7487628#post7487628)

---

### Post by clemmy on 2009-07-26
You can find which files are 'asking' a plugin codec directly in the rhytmhbox window, there's no need to use terminal for this task. If a codec is needed is because an 'import error' occured, and you can see the import errors list in the sidebar, just below 'Music' and 'Podcast' links ;-)

If you think that this windows is very annoying, maybe because rhythmbox is trying to find plugin for a file for which there is no plugin, or because that file is not music at all, there is a workaround to quickly disable this feature.
[COLOR="Red"]BE CAREFULL!! This will disable codec install feature at all. Codec install feature can be usefull sometimes!![/COLOR]
From terminal type
```
sudo mv /usr/bin/gstreamer-codec-install /usr/bin/gstreamer-codec-install-bak
```
you can enable again codec install feature with
```
sudo mv /usr/bin/gstreamer-codec-install-bak /usr/bin/gstreamer-codec-install
```

PS=newer versions of rhytmbox should be clever, and supposely they will not try to get plugins for NON audio files. But the annoying popup persist if you want to keep in your media folder an audio file not supported by rhythmbox

---

