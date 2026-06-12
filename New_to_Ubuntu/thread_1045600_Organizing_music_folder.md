---
title: "Organizing music folder"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Meph1st0 on 2009-01-20
I'm just another one of those anal music collection organizer guys.  I was wondering if anyone knows of an application that will go through my music folder and find the folders that don't contain .mp3 files.  I have a lot of folders in my music folder that are empty (with the exception of album artwork, so they're not completely empty), they're empty because I had deleted the file through Itunes.  But Itunes didn't delete the folder that the file was in.  So I'm looking for something to crawl through the directory structure and check each folder to see if there are any mp3 files in it and if there aren't then delete the folder.

I know that I can use maybe songbird and banshee to listen and view the library from within each application, but I want to actually clean out my file structure.  Can they do that too?

---

### Post by blueridgedog on 2009-01-20
That is one of the pitfalls of letting iTunes manage your music.  I generally manage mine the old way.  I or another member could write a shell script that could go through and delete directories without MP3 files in them, but I doubt it would be faster than a manual process and I doubt I would ever really trust it.

An another front, have you though of putting all your music into one folder?  Some of the younger people I know do it that way and I am starting to see the logic of it (even though my soul screams NO!).

---

### Post by snova on 2009-01-20
Well, I don't know of a specialized application for it (seems unlikely), but this quick command will search for directories and try to remove them (empty or not, it'll fail if there's anything inside):

```
cd Music # Or wherever you put it
find -type d -exec rmdir {} \;
```

There's probably a better way to do it (command-line wise), but it's all I know of. ;)

---

### Post by Meph1st0 on 2009-01-20
Really?  Put all of my music into one folder?  That just seems so wrong.  I can understand wanting to do that too now come to think of it.  But, like you, my soul screams no too. :)

snova, that command just looks scary. But come to think of it, any app that does what I'm wanting would probably naturally give anyone goosebumps.  Which reminds me, I need to go backup my hard drive.

Thanks anyway guys.

---

### Post by floatingpoint on 2009-01-20
I'm new, but can't you do it with wildcards?

I don't know if there's a 'cut' command, but there's certainly a copy.

So surely there could be a command line that would 'cp' all files from the parent directory ("iTunes Music" is it?) with .mp3 in them (with the wildcard *.mp3 in the line)?

You'd copy them to somewhere else, then delete the whole music directory, then copy the .mp3's back and organise them the way you like.

Yeah? No?

---

### Post by snova on 2009-01-20
> **snova said:**
> ```
find -type d -exec rmdir {} \;
```

> **Meph1st0 said:**
> snova, that command just looks scary. But come to think of it, any app that does what I'm wanting would probably naturally give anyone goosebumps.  Which reminds me, I need to go backup my hard drive.

Understandably. The **find** command is extremely flexible.

**-type d** -- Makes it only match directories
**-exec rmdir** -- Makes it run the **rmdir** command on all matches. rmdir removes directories, but it only does so if the directory is empty (you get an error message otherwise).
**{}** -- The file (or directory in our case) that it matches is put here, and passed to the program to run.
**\;** -- Ends the -exec with a semicolon (it needs a backslash because otherwise it has a different meaning, to the shell).

So, all put together, it runs **rmdir** on all subdirectories from where you are currently, which the **cd Music** command made sure was where your music is.

---

### Post by snova on 2009-01-20
> **floatingpoint said:**
> I don't know if there's a 'cut' command, but there's certainly a copy.

Yes, there is a **cut** command, but it doesn't operate on files- it's used to extract certain parts of each line in a file.

---

### Post by floatingpoint on 2009-01-20
Ah right.

But..... for the legacy-style 'cut' function, you would use 'mv' (move), am I right?

---

### Post by snova on 2009-01-20
> **floatingpoint said:**
> Ah right.

But..... for the legacy-style 'cut' function, you would use 'mv' (move), am I right?

Yes, assuming you're talking about moving files around...

---

### Post by floatingpoint on 2009-01-20
Well, generally you would 'cut and paste', moving something from one place to another.

Or did you mean as opposed to moving text? I expect you did.

Never mind.

---

### Post by blueridgedog on 2009-01-20
> **Meph1st0 said:**
> Really?  Put all of my music into one folder?  That just seems so wrong.  I can understand wanting to do that too now come to think of it.  But, like you, my soul screams no too. :)



Some of my younger associates have a new approach to music and files in general.  They rely on searching and on indexing.  To them, the computer should find what you are looking for, not the user.  I have seen it work, but I still organize my stuff my way.

---

### Post by boof1988 on 2009-01-21
> **Meph1st0 said:**
> I'm just another one of those anal music collection organizer guys.  I was wondering if anyone knows of an application that will go through my music folder and find the folders that don't contain .mp3 files.  I have a lot of folders in my music folder that are empty (with the exception of album artwork, so they're not completely empty), they're empty because I had deleted the file through Itunes.  But Itunes didn't delete the folder that the file was in.  So I'm looking for something to crawl through the directory structure and check each folder to see if there are any mp3 files in it and if there aren't then delete the folder.

I know that I can use maybe songbird and banshee to listen and view the library from within each application, but I want to actually clean out my file structure.  Can they do that too?

This may not be what you want... but... One of the music converters (Soundconverter or the like) may have a feature to organize your music into <path>/artist/album/ using the tags on the file.  I don't know what the application would do if there were no "converting" (file compression change) and only moving the file to a different directory.

I used Soundconverter to convert my collection to ogg since I'm trying to leave proprietary stuff behind.  And it had features to create the <path>/artist/album/ as well as a couple other organizing schemes.

HTH...

---

### Post by starscalling on 2009-01-21
> **boof1988 said:**
> 
[quote=Meph1st0]
I'm just another one of those anal music collection organizer guys. I was wondering if anyone knows of an application that will go through my music folder and find the folders that don't contain .mp3 files. I have a lot of folders in my music folder that are empty (with the exception of album artwork, so they're not completely empty), they're empty because I had deleted the file through Itunes. But Itunes didn't delete the folder that the file was in. So I'm looking for something to crawl through the directory structure and check each folder to see if there are any mp3 files in it and if there aren't then delete the folder.

I know that I can use maybe songbird and banshee to listen and view the library from within each application, but I want to actually clean out my file structure. Can they do that too?


This may not be what you want... but... One of the music converters (Soundconverter or the like) may have a feature to organize your music into <path>/artist/album/ using the tags on the file.  I don't know what the application would do if there were no "converting" (file compression change) and only moving the file to a different directory.

I used Soundconverter to convert my collection to ogg since I'm trying to leave proprietary stuff behind.  And it had features to create the <path>/artist/album/ as well as a couple other organizing schemes.

HTH...[/QUOTE]

eh i think we [by we i mean me :P] need a scripty - would like it to read tags, and then organize by album, creating dir if none exists



also:

> **snova said:**
> Understandably. The **find** command is extremely flexible.

**-type d** -- Makes it only match directories
**-exec rmdir** -- Makes it run the **rmdir** command on all matches. rmdir removes directories, but it only does so if the directory is empty (you get an error message otherwise).
**{}** -- The file (or directory in our case) that it matches is put here, and passed to the program to run.
**\;** -- Ends the -exec with a semicolon (it needs a backslash because otherwise it has a different meaning, to the shell).

So, all put together, it runs **rmdir** on all subdirectories from where you are currently, which the **cd Music** command made sure was where your music is.

looks like this [worx great btw]
```

nekostar@nekostar-desktop:~$ cd music\ for\ richie/
nekostar@nekostar-desktop:~/music for richie$ find -type d -exec rmdir {} \;
rmdir: failed to remove `.': Invalid argument
rmdir: failed to remove `./DjBoo-PavorNocturnusfinalTake_vbr_mp3': Directory not empty
rmdir: failed to remove `./corpidextra013_vbr_mp3': Directory not empty
rmdir: failed to remove `./Jon Kennedy - Useless Wooden Toys (2005) - Trip Hop - www.torrentazos.com By FEFE2003': Directory not empty
rmdir: failed to remove `./01-Zero-Blade_-_Abyssal_Celebrant-2007_vbr': Directory not empty
rmdir: failed to remove `./gfat2007-01-18.flac16_vbr_mp3': Directory not empty
rmdir: failed to remove `./Pulp Fiction (1994) soundtrack': Directory not empty
rmdir: failed to remove `./VA_-_Ritual_of_Harakiri-2008_vbr': Directory not empty
rmdir: failed to remove `./Trip-Hop': Directory not empty
rmdir: failed to remove `./Trip-Hop/Samsung.Chillout.(2003)': Directory not empty
rmdir: failed to remove `./Trip-Hop/Ibiza.Chillout.CD1': Directory not empty
rmdir: failed to remove `./Trip-Hop/Ibiza.Chillout.CD2': Directory not empty
rmdir: failed to remove `./Trip-Hop/Drum\'n\'Bass': Directory not empty
rmdir: failed to remove `./DjBoo-PavorNocturnus_vbr_mp3': Directory not empty
rmdir: failed to remove `./ouimnet': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet013': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet044': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet046': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet047': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet038': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet008': Directory not empty
find: `./ouimnet/ouimnet030': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet049': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet001': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet005': Directory not empty
find: `./ouimnet/ouimnet025': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet002': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet043': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet035': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet040': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet037': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet021': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet051': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet012': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet023': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet052': Directory not empty
find: `./ouimnet/ouimnet033': No such file or directory
find: `./ouimnet/ouimnet027': No such file or directory
find: `./ouimnet/ouimnet018': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet039': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet006': Directory not empty
find: `./ouimnet/ouimnet028': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet019': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet017': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet022': Directory not empty
find: `./ouimnet/ouimnet016': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet042': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet007': Directory not empty
find: `./ouimnet/ouimnet034': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet015': Directory not empty
find: `./ouimnet/ouimnet026': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet014': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet020': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet041': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet010': Directory not empty
find: `./ouimnet/ouimnet032': No such file or directory
find: `./ouimnet/ouimnet011': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet009': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet050': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet045': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet004': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet029': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet003': Directory not empty
find: `./ouimnet/ouimnet024': No such file or directory
find: `./ouimnet/ouimnet036': No such file or directory
rmdir: failed to remove `./ouimnet/ouimnet048': Directory not empty
rmdir: failed to remove `./ouimnet/ouimnet031': Directory not empty

```

awesomeness...


however... i would like to point out that windows media player has had this `organize collection/library auto-magically` and it IS useful if you have the foresight to tag everything. its really a matter of just organizing an incoming path - and don't put everything in the main collection/library folder(s) till it's been tagged properly - DON'T BE LAZY!!!


====================
lucky post 13

---

### Post by musungu on 2009-02-10
i've been happy using fslint to clean out my filesystems...

---

### Post by Scubdup on 2009-03-04
I'm a beginner so this is a theoretical answer but couldn't you use a script like I requested [here]("http://ubuntuforums.org/showthread.php?t=1085448") to find all MP3s, rename them with their path and then move them into one Music folder (so Metallica>Black Album>Enter_Sandman.MP3 goes to Music>Metallica_XIXIXIX_Black Album_XIXIXIX_Enter Sandman.mp3)

Then you could either leave it like that, or use the (hopefully unique) string XIXIXIX to help another script put them back into the same directory structure.

---

### Post by abdusamed on 2010-08-29
> **Scubdup said:**
> I'm a beginner so this is a theoretical answer but couldn't you use a script like I requested [here]("http://ubuntuforums.org/showthread.php?t=1085448") to find all MP3s, rename them with their path and then move them into one Music folder (so Metallica>Black Album>Enter_Sandman.MP3 goes to Music>Metallica_XIXIXIX_Black Album_XIXIXIX_Enter Sandman.mp3)

Then you could either leave it like that, or use the (hopefully unique) string XIXIXIX to help another script put them back into the same directory structure.


What we all are looking for is **Picard from MusicBrainz**. It's in the repo. Don't forget to get cover art plugin.

---

