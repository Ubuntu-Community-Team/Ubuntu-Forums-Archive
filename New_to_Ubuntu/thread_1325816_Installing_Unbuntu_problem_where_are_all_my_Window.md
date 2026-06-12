---
title: "Installing Unbuntu problem: where are all my Windows XP files???"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by rippedelastic on 2009-11-13
Hi, I'd really appreciate is someone could help me figure out what I did wrong in my ubuntu installation!
And since I would be at the bottom end of absolute beginners, I'll try my best to explain the problem as simplistically as possible!

My Problem: After installation, all was lovely and fine and dandy and I was very excited about my new ubuntu. Until I realised that all that crossed over from my old Windows XP to my brand spanking new ubuntu was realplayer. My entire folder for my drive D was there, with the folders for Program Files, etc etc, all of which COMPLETELY empty, apart from Program Files, which had real player. No my documents, none of my games, abolutely nothing.

How do I get everything, all my old files, to cross over so I can get going with ubuntu??

I'll outline all the particulars of what I did exactly during installation so you can pin point where I went wrong;

The Download: My connection is rubbish, so instead of downloading Ubuntu directly from the website, I got a torrent instead. I ended up with Wubi.

The Installation: Installed ubuntu with wubi, no bother, didn't do any of the iso burning to disc or anything like that. Selected drive D to partition (is it a problem if the size of the drive I selected to partition is BIGGER by a few gigs than the follwing "size of installation" option?) 

Then I just restarted the computer and installed, with nothing else for me to select to determine my installation.

Annnd..now I have all of drive D on unbuntu, with all it's old folders, but allll empty, except for realplayer who is the only one that has managed to cross over for some bizarre reason.

Thanks for advice! Tell me if I need to give any more details!

---

### Post by PadawanGeek on 2009-11-13
Does the grub give you the option to boot back into Windows? When you boot into Windows are all of your files still there?

---

### Post by rippedelastic on 2009-11-14
Yep yep! Nothing has been wiped on Windows, it's all still there totally unchanged, and I still have the option of booting back into it. Ubuntu is just like this extra empty shell...

---

### Post by oldfred on 2009-11-14
Ubuntu is not Windows which is a good thing. It will not run any Windows programs and therefore will not catch any of those nasty windows virus'.
There are equivalent programs for most windows applications. Some are rewritten to be 100% Linux, some offer equivalent fuctionality but are not the same, others run in wine and some do not work. Users that are into gaming often dual boot just to run their games in windows but find Ubuntu better for everything else once they have learned a little about Ubuntu.
Wubi is ok if you just want to dabble and learn a little about Ubuntu, but it is running as a program in windows so if windows ever gets corrupted you will not be able to get into wubi. 
A true dual boot requires a separate partition (in windows name a D: partition) and it is installed totally separate from windows. You still can boot into either windows or Ubuntu.

---

