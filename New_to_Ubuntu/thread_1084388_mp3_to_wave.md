---
title: "mp3 to wave"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-03-02
I want to convert mp3 files to wave files,using ubuntu 8.1 full install
so i can copy them using K3b so i can play them in my cad cd player 
which can not play mp3
any help  many thanks

---

### Post by bumanie on 2009-03-02
I would look at [winff]("http://winff.org/winffwiki/UbuntuInstallation"). Although known as a GUI front end to ffmpeg and generally a video converter, it also converts a number of audio codecs as well.

---

### Post by mc4man on 2009-03-02
I was working out something in a similar vein so I'll give you the basic command and point you to a post where you can see how to modify if you wish.

You'll need ffmpeg and to make things really simple, 'nautilus-open-terminal' which allows you to right click on a directory (folder) and open a terminal at the proper prompt.
so run in a terminal
```
sudo apt-get install ffmpeg nautilus-open-terminal
```

When it's done go Ctrl+backspace to restart (will enable the 'open in terminal' right click option.

Then navigate to a folder that contains mp3's and right click either on the folder or inside it and choose "Open in Terminal"
In the *terminal that pops up*, copy and paste in this command

```
 mkdir temp && for f in *.mp3; do ffmpeg -i "$f" ./temp/"${f%.mp3}.wav"; done
```

Your .wav's will end up inside that folder in a folder named temp with the same name as the mp3's
You can move, rename the 'temp' to anything, anywhere, ect.

If you wish you can adapt the command to save the .wav's somewhere else and or make the command into a script

see here for some basic idea's

[http://ubuntuforums.org/showthread.php?p=6809938#post6809938](http://ubuntuforums.org/showthread.php?p=6809938#post6809938)

Note: this is not a 'recursive' command, the folder you r. click on or in must contain the .mp3's (in other words don't try to run on a folder containing other folders with mp3's inside of them

---

### Post by diablo75 on 2009-03-02
Just click Applications>Add/Remove... and then do a search for "Sound Converter".  You'll probably want to also install Ubuntu Restricted Extras while you're here (if you haven't done so already).  Change the search filter to say "All Available Applications" before searching for these two packages.

---

### Post by asmoore82 on 2009-03-02
if you are just trying to burn a basic music CD -
your burning software of choice (K3B, brasero, etc.) should handle
the little details of *.mpg,*.ogg to *.wav for you

if you must DIY - I would suggest mplayer because it is easily scriptable...
```
for song in *.mp3
do
mplayer -vo null -ao pcm:fast:wavheader:file="${song%.*}.wav" "$song"
done
```

---

### Post by blazemore on 2009-03-02
K3B and Brasero[SIC?] can burn a normal CD with CD Audio, that will play in any CD player.

---

### Post by cowboy7305 on 2009-03-02
i did what Diablo 75 said worked great 
many thanks to all who replied

---

### Post by cowboy7305 on 2009-03-02
Ok one more question the wave file is now to big to burn to cd 
is there a tool out there that can split it into smaller sizes ,what iam trying to do is a audio book and it is about 8 hours long

---

### Post by logos34 on 2009-03-02
> **cowboy7305 said:**
> Ok one more question the wave file is now to big to burn to cd 
is there a tool out there that can split it into smaller sizes ,what iam trying to do is a audio book and it is about 8 hours long
[B]
Wavbreaker[/B] works great for me:
> 
Description: A tool to split wave files into multiple chunks
 This application's purpose in life is to take a wave file and
 break it up into multiple wave files.  It makes a clean break
 at the correct position to burn the files to an audio cd
 without any dead air between the tracks.

---

### Post by MrWES on 2009-03-02
> **cowboy7305 said:**
> Ok one more question the wave file is now to big to burn to cd 
is there a tool out there that can split it into smaller sizes ,what iam trying to do is a audio book and it is about 8 hours long

```
sudo apt-get install wavsplit
```

then from the command line type:

```
wavsplit bigwavefile.wav time1 time2 time3
```

You can then use easytag to rename the files.

---

### Post by Zimmer on 2009-03-02
If you used Audacity to split the .wav you would have more control over where the split occured. Audacity will export your selection to .wav

---

### Post by cowboy7305 on 2009-03-02
I don't know where to find close thread 
but many thanks to every one that helped i now have it working 
many thanks again

---

