---
title: "Normalize / equalize the volume of MP3"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by misswham on 2009-07-22
Is there are program that I can use in ubuntu hardy that will equalize the volume of all my mp3's?

---

### Post by NightwishFan on 2009-07-22
You can try normalize or mp3gain, they should be in the repositories.

---

### Post by misswham on 2009-07-22
i went to synaptic and downloaded mp3gain from there and now I cant find it.  Each time I go back to synaptic it is there unchecked and when i hit apply it goes through the motions and it says has been installed but cant find it.  When I go back to synaptic, it is there again unchecked.

---

### Post by misswham on 2009-07-22
Just tried the same thing with normalize and it downloaded but cant find it in applications.  mp3gain nor normalize

---

### Post by NightwishFan on 2009-07-22
It should not be unchecked. I believe it is a command line application though. I do not know of any graphical ones.

Try this in a terminal:

```
sudo apt-get update && sudo apt-get install mp3gain
```

To learn how to use mp3gain run this in a terminal:

```
mp3gain --help
```

---

### Post by misswham on 2009-07-22
I ran the first command and it said already installed newest version but cant find it.  i ran the 2nd command and this is what i got

aretha@aretha-desktop:~$ mp3gain --help
--help
Can't open --help for reading
aretha@aretha-desktop:~$

---

### Post by NightwishFan on 2009-07-22
I think it is fine. For actual information try:
```
man mp3gain
```

To get it working try this:

In a terminal type 'mp3gain' (without quotes).
Add a space after mp3gain, and then drag and drop and mp3 file into the terminal, and push enter.

---

### Post by misswham on 2009-07-22
tried to drag and drop and the first file just started playing thats it.  Is there a way to actually pull up the mp3gain or normalize program?

---

### Post by bear24rw on 2009-07-22
> **misswham said:**
> tried to drag and drop and the first file just started playing thats it.  Is there a way to actually pull up the mp3gain or normalize program?

someone said above that is is a command line program, no gui

---

### Post by SunnyRabbiera on 2009-07-22
Well you casn just use a audio application, I prefer audacious myself as it has a equalizer compatible with winamp .eqf files.

---

### Post by misswham on 2009-07-22
I am sorry i am somewhat a novice at this but what is the command to use?  I typed in mp3gain and the space and dragged 2 files into the terminal and pressed enter and all that happened is the the first file started playing.  I assume that is what commandline means.  I assume that gui means an actual program that is in the applications menu.  I have never heard of the 2 things until now.  I have 18gigs of music I wanted to volume level and I thought there might be a program that would do this in ubuntu.

---

### Post by MrWES on 2009-07-22
> **misswham said:**
> I am sorry i am somewhat a novice at this but what is the command to use?  I typed in mp3gain and the space and dragged 2 files into the terminal and pressed enter and all that happened is the the first file started playing.  I assume that is what commandline means.  I assume that gui means an actual program that is in the applications menu.  I have never heard of the 2 things until now.  I have 18gigs of music I wanted to volume level and I thought there might be a program that would do this in ubuntu.


This site should help out:
[http://www.linux.com/archive/articles/59957]("http://www.linux.com/archive/articles/59957")

There is a link to a Java based GUI for mp3gain.


~Bill

---

### Post by fooman on 2009-07-22
if the "normalize-audio" package is installed (it is in synaptic),  you can use that to normalize an entire directory (and every directory within it) using this command:

```
find . -type d -exec sh -c "normalize-audio -b \"{}\"/*.mp3" \;
```so,  if your mp3 collection is in your /Music directory....then use this command:

```
~/Music$ find . -type d -exec sh -c "normalize-audio -b \"{}\"/*.mp3" \;
```that should scan and adjust all the mp3's in your /home/<user name>/Music directory to the same volume level.

taken from here (see # 7 under q&a):

[http://normalize.nongnu.org/README.html](http://normalize.nongnu.org/README.html)

*note: at that link they refer to the package as "normalize"...it is now "normalize-audio" (i changed it in the commands i posted above).

hope that helps.

---

### Post by eriqjaffe on 2009-07-22
There's actually a GTK-based GUI:

```
sudo apt-get instsall easymp3gain-gtk2
```

It will show up under Applications -> Sound & Video.

---

### Post by brookie on 2009-07-23
I used to use iTunes, but now use Banshee 1.43. iTunes had a setting for playback gain control (or volume control or something like that) and Banahee has one under Edit/Preverences General Tab/ Enable ReplayGain Correction. I think it only works when the mp3 file has some kind of embedded gain control tag in it but I'm not sure. I use it and it works with most of my music files but not all. 
Cheers, brook

---

### Post by Sweaty Elvis on 2009-07-23
Hi guys, noob here, just trying to transition into Ubuntu and I'm interested in the same thing.

It sounds like mp3gain and normalize will permanently modify my mp3's.  That's not good!  

When listening to an album, some tracks are SUPPOSED to be louder than others so it's good to be able to turn this feature off.  But, when listening to a mix playlist, this feature is priceless.

I just tried checking the gain control box in Banshee, and it's not very effective.  Could be that my mp3's do not have the required property.

There seems to be a concensus on this forum that Banshee is the best music player, but I'm not completely sold.

---

### Post by laffinet on 2009-07-23
As mentioned before, mp3gain is a command line tool, so to use it, open a terminal (Main Menu - Accessories - Terminal) and navigate to the directory that holds the mp3s. 

There are various option that you can use 

```
man mp3gain
```

will give you an idea what's possible.

> When listening to an album, some tracks are SUPPOSED to be louder 

mp3gain has a feature called "album adjust". Use this and the louder tracks within an album will stay louder than the more quiet tracks. 

For example, all my music is organised in folders, eg /Artist/Album/track.mp3

If I open a terminal in the folder /Artist/Album/track.mp3 and run 
```
mp3gain -a *mp3
```
the tracks will be adjusted so that the loudest part of the album does not exceed a certain value (forgot what the default setting is), but the volume of the tracks relative to each other within one album will not change.

---

### Post by misswham on 2009-07-23
I didnt know that you had to open the folder first then open the terminal.  Does that mean to just double click on music folder and then open the terminal from the applications menu?  So whatever command you put in the terminal will only be for that particular folder?

---

### Post by CatKiller on 2009-07-23
> **Sweaty Elvis said:**
>  It sounds like mp3gain and normalize will permanently modify my mp3's.  That's not good! 

It depends on how you use it. There is the option to make a version of the file that has the gain of the audio already adjusted for use in players that don't understand the ReplayGain tags (obviously you can only choose one of Track mode or Album mode for this method) but the most sensible option is to just write tags to the file. You can write both Album mode tags and Track mode tags to the file, and any players that know how to interpret those tags will adjust the gain accordingly. Any players that don't understand the tags will just ignore them. This is for mp3gain. I've never used normalise.

Many modern media players understand ReplayGain tags.

Just use EasyMP3Gain, select the files that you want to sort out, and then select Analyse to write the appropriate tags to the files. If you select Album mode it will assume that all files in the same directory come from the same album. It has backends for writing tags for MP3, Ogg and FLAC. It's all pretty straightforward.

---

### Post by laffinet on 2009-07-23
> **misswham said:**
> I didnt know that you had to open the folder first then open the terminal.  Does that mean to just double click on music folder and then open the terminal from the applications menu?  So whatever command you put in the terminal will only be for that particular folder?

You don't have to open the folder before opening the terminal. I'll try to explain:
When opening a terminal you are by default in your home folder. Any command you execute that doesn't explicitly specify a path will therefore apply to your home folder. 
For example if you open a terminal and run 
```
mp3gain -a *mp3
```
mp3gain will look for all mp3 files in your home folder and adjust the volume accordingly.
But your mp3s are probably not in your home folder (at least not directly, probably in subfolders). Therefore you have to navigate to wherever the mp3s are, using

```
cd /folder1/folder2/
```

and run the above command or alternatively you can specify the path in the command itself

```
mpagain -a /folder1/folder2/*mp3
```

mp3gain will now look for all mp3 files in /folder1/folder2/ and adjust the volumes.

---

### Post by Sweaty Elvis on 2009-07-24
> **laffinet said:**
> 

mp3gain has a feature called "album adjust". Use this and the louder tracks within an album will stay louder than the more quiet tracks. 


> **CatKiller said:**
> It depends on how you use it. There is the option to make a version of the file that has the gain of the audio already adjusted for use in players that don't understand the ReplayGain tags (obviously you can only choose one of Track mode or Album mode for this method) but the most sensible option is to just write tags to the file. 

Thank you all for the help.  I'm still undecided about Banshee, but I now realize that modifying files can be a good way to fix gain problems.

---

