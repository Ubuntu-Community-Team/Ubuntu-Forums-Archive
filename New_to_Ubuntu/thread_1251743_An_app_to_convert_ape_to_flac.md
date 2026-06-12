---
title: "An app to convert ape to flac"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-08-28
I'm looking for an actual gui app(I don't want to do this through terminal) that will split an ape into separate flac files. Does one exist for Ubuntu? Either native or through Wine?

Thank you.

---

### Post by Flimm on 2009-08-29
**EDIT:** actually, Sound Converter can convert from .ape directly! So you don't need to install wine or Monkey's Audio. I've crossed out the irrelevant bits.

Here's how I did it:
[LIST][s][*]Install wine. ```
sudo aptitude install wine
```
[*]Download [Monkey's Audio](http://www.monkeysaudio.com/download.html), save it in an easily accessible location.
[*]Right click the file (MAC_406.exe). If **Open with "Wine Windows Program Loader"** isn't the first option, look for it under **Open with**
[*]Install the program. (next, next, next)
[*]Launch the program, it should be under Applications, Wine, Programs, Monkey's Audio
[*]Click File, Add file, and open the .ape file you want to convert.
[*]Click Mode, Decompress
[*]Click File, Process files. A .wav file should be created with the same name and in the same folder as the original .ape file.[/s]
[*]Now we need to convert it to .flac. Install Sound Converter ```
sudo aptitude install soundconverter
```
[*]Open it. You'll find it under Applications, Sound & Video.
[*]Add the [s].wav[/s] .ape file.
[*]Click Edit, Preferences, and make sure the output format is .flac
[*]Click Convert on the toolbar. You're done![/LIST]
I've attached screenshots of Monkey's Audio and Sound Converter.

---

### Post by jamesisin on 2009-11-19
I hope you don't get upset with me, but it's actually really easy to do via the command line.  I wrote a post on splitting and tagging album length FLAC files:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)

I will write one for APE files right away.

Someone here also wrote a script to make this easier, but since we are only talking about two lines of code to begin with...

The trouble with the APE files (as compared to FLAC files) is that it looks like you need to add the MAC (Monkey Audio Codec) to interpret the APE files.  I have found a repository but am seeking a key to secure the repository (once I find that I will publish my new post).

---

