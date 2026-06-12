---
title: "Duplicate MP3's, How do I get rid of them easily?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by LowSky on 2010-01-03
I found an old hard drive which had a bunch of Mp3's and decided to merge it with my current hard drive;s collection. Well because I had a good deal of the same tracks, and I'm lazy, I need to deletes out all the doubles, without searching every file. I have about 40GB of music, probably  12GB of redundancy.

It will take hours to sort them by hand, and because Whatever windows program I used to scan these into my system named them differently than the program I used in Ubuntu, I now have multiples of the same tracks with slightly different names or even file sizes.

for example:

```
01 Kryptonite.mp3
3 Doors Down - 01 - Kryptonite.mp3
```


Anyone have an idea of what I can do? I rather keep the higher bit rated versions if possible, if that helps.

---

### Post by tgalati4 on 2010-01-03
sudo apt-get install easytag

---

### Post by LowSky on 2010-01-04
How is easytag going to get rid of duplicates?

---

### Post by LuisGMarine on 2010-01-04
This might seem like a lot of work, but I would install songbird.  Just for the fact that you can import just that extra hard drive of music.  You will be able to:

-Organize the mp3's into folders like Artist/Almbum/Song.mp3
-Write the metadata straight to the mp3, along with cover art.
-Remove Duplicates ( Using the Add-On called The Exorcist)

After that you can then just copy the .mp3 files and put them with the rest of your library.

That's just how I would do it .. if you are looking for a more nerdy command line way, then I'm sorry deff don't know that one. :lolflag:

---

### Post by LowSky on 2010-01-04
I have songbird installed so I'll try the exorcist add-on...

the music is already in folders, and when I copied the music over, some of it was already in my library (I recently re-ripped all my CD's). So now I have duplicates many with semi different names but maybe this will help.

---

### Post by LowSky on 2010-01-04
OK so songbird exorsim app only take it out of the library, not my file system. And songbird nearly crashed in the process, not cool.

All easytag did was rewrite the metadata, which doesn't help either. I think I now have more issue because of it.

So now I guess I'll have to re-create my playlist (I'll use banshee this time around because I know it has a delete option and its a bit more stable), mark all the doubles by hand and delete them permanetly.

---

### Post by LuisGMarine on 2010-01-04
Songbird acts like iTunes.  If you don't have in the options to copy files to songbird when you import them, then  yes it will just remove them from the library and not the file system.  

Songbird wont touch any files on the file system that is not within its domain.  So if you go to options and look for an option to organize your music into folder and stuff, it will not only copy songs to songbird when you add them to library, but it will give songbird the green light to modify delete as you see fit with out any problems.

---

### Post by Pifilatakanemu on 2010-01-18
> **LuisGMarine said:**
>  So if you go to options and look for an option to organize your music into folder and stuff, it will not only copy songs to songbird when you add them to library, but it will give songbird the green light to modify delete as you see fit with out any problems.

I activated the organization of my collection and gave "the exorzist" a try in order to get rid of my duplicates. He found a lot of duplicates but when I selected "Exorcise the clones!" He asked my whether he is supposed to delete them from **the library.**
(I confirmed, but Songbird crashed anyway...)

Could you please explain (step by step) how to delete the duplicates from the disk with SB?

Or recommend any other app that does not only compare file size and names?
I'm quite desperate as I did not find any Ubuntu-Tool to get this job done. Considering to start MediaMonkey in a XP-Vbox to do this, but I would rather prefer a Linux solution....

Thanks!!

---

### Post by LuisGMarine on 2010-01-18
It could be a bug with SB.  Try again, if not you might have to check to see if their is a bug with that add-on in the new songbird 1.4.  Unfortunately I no longer use SB since it completely stopped working with my iPod.

You are doing all the right steps, it's just SB not holding up to their end of the deal.

---

### Post by PenguinInside on 2010-01-19
> **LowSky said:**
> 
for example:

```
01 Kryptonite.mp3
3 Doors Down - 01 - Kryptonite.mp3
```


Anyone have an idea of what I can do? I rather keep the higher bit rated versions if possible, if that helps.

How about a Python script that descends into each subdirectory and keeps track of uncommonly occuring words (such as Kryptonite) and saving the results to a Mysql database, and later using the SOUNDEX function to find words that sound the same to make a match?

Also you'd have to keep track of the bitrate, too.

You can also use full text search to see if a substring of one filename occurs anywhere else in the database.

Sounds like a project in itself.

---

### Post by mikechant on 2010-01-20
Not at my Ubuntu PC at present, but I've got an application called 'kid3' installed and I'm pretty sure I used it to rename files to match their metadata. But I think it's worth playing with before doing anything manual and long winded. I think at least you might be able to get the filenames to include artist - track name in that order, then duplicates would be fairly obvious even with misspellings.

---

### Post by LowSky on 2010-01-20
> **PenguinInside said:**
> How about a Python script that descends into each subdirectory and keeps track of uncommonly occuring words (such as Kryptonite) and saving the results to a Mysql database, and later using the SOUNDEX function to find words that sound the same to make a match?

Also you'd have to keep track of the bitrate, too.

You can also use full text search to see if a substring of one filename occurs anywhere else in the database.

Sounds like a project in itself.

Well I ended up just going through my files by painstaking hand. Songbird Exorcist only removes the file from the playlist, not from the hard drive, but if you use Exorcist it does highlight the doubles and you can delete from there using right click.

My issue was tough because it wasn't just doubles it was bitrate differences that changed the game.

---

### Post by mips on 2012-11-08
> **LowSky said:**
> 
It will take hours to sort them by hand, and because Whatever windows program I used to scan these into my system named them differently than the program I used in Ubuntu, I now have multiples of the same tracks with slightly different names or even file sizes.

Anyone have an idea of what I can do? I rather keep the higher bit rated versions if possible, if that helps.

You are approaching this from the wrong angle and as you said just searching by name or file size is not good enough and could take days. What you have to do is search for duplicates by comparing the file contents using md5 & sha1 'summing'. This way even if you have two files with exactly the same name and size but are not actually the same thing it will get picked up because it looks at the actual content of the files and not the names & sizes.

Fortunately for you there are utilities to do this, I use fslint, 
sudo apt-get install fslint (ubuntu/debian)
sudo packer/yaourt fslint (Arch based distros, lives in AUR and not the main repos)

There are also other utils like fdupes, duper etc, some command line while others are GUI. You can find a list here [http://en.wikipedia.org/wiki/Fdupes](http://en.wikipedia.org/wiki/Fdupes)

When using fslint or any other program just use caution when you delete files. Say you have an entire album and then another song from the same album that's located elsewhere don't delete the one from the album, rather delete the one in the different locations as you don't want songs missing from a album, keep the entire album intact.

Where you have two of the same songs but the file sizes differ keep the bigger one as it's usually the one with the higher quality.

Hope this helps.

---

### Post by Elfy on 2012-11-08
Closed - as LowSky's not been back here for almost 2 years ...

---

