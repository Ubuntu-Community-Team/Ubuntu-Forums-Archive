---
title: "Converting wav to mp3 with lame. I don't get the basics..."
date: 2009-09-17
forum: New to Ubuntu
---

### Post by kingdonerkebab on 2009-09-17
Er, yeah. I've tried looking for the answer to this but I can't find it maybe because it's so basic that nobody's thought to post it anywhere, but there you go.

I've got some big fat .wav files on my computer taking up room and I want to convert them to 320kbps mp3s. The thing I don't know how to do is make lame find the files I want to convert. 

This is what I've been trying:

lame --preset insane home/kingkebab/music/track1.wav track1.mp3

or even

lame --preset insane track1.wav track1.mp3

But obviously isn't working.

Say the files are in home/kingkebab/music/artist/album, how can I make it locate this album and convert them? And is there a way of converting a full album at once instead of individual files?

Thanks!

---

### Post by iansane on 2009-09-17
Hope this isn't a silly question.

Are you putting a / in front of home for that absolute path?

/home/kingkebab/music/track1.wav track1.mp3

---

### Post by wildman4god on 2009-09-17
a much easier way is to use an app called sound converter.

install throught add/remove, synaptic or cli with:

sudo apt-get install soundconverter

that should be much easier.

---

### Post by por100pre1 on 2009-09-17
Use Sound Converter.

Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install soundconverter
```

EDIT:Too Late!!!

---

### Post by tgalati4 on 2009-09-17
lame will probably take ~/Music/track1.wav 
~/ is a shortcut for your home directory.  Of course you must respect case as well.  You have "music" directory, but by default, Ubuntu comes with "Music" directory.

---

### Post by kingdonerkebab on 2009-09-18
Thanks guys. I was being stupid and missing the "/".

The other thing I wanted to know was about how to batch convert a full album, or do I have to enter in the name of the song and it's location every time?

I'm sure I've seen some funky piece of code somewhere that could get this to happen on some forum somewhere, but now I can't find it.

I might try soundconverter. Will it convert to 320kbps? Although I kind of wanted to get it to work in lame as a matter of principle :)

---

### Post by CaptainMark on 2009-09-18
Sound converter has a batch option and its about as easy to use as they come, i think you can select the bitrate in the preferences but its been a while since i used it

---

### Post by camaron1 on 2009-09-18
> **kingdonerkebab said:**
> Thanks guys. I was being stupid and missing the "/".

The other thing I wanted to know was about how to batch convert a full album, or do I have to enter in the name of the song and it's location every time?

I'm sure I've seen some funky piece of code somewhere that could get this to happen on some forum somewhere, but now I can't find it.

I might try soundconverter. Will it convert to 320kbps? Although I kind of wanted to get it to work in lame as a matter of principle :)


You may want to have a look here: [http://izanbardprince.wordpress.com/2009/07/28/soundconverter-on-linux-mutilates-the-mp3-files-it-creates/](http://izanbardprince.wordpress.com/2009/07/28/soundconverter-on-linux-mutilates-the-mp3-files-it-creates/)

---

### Post by kingdonerkebab on 2009-09-18
Had a look at sound converter. Even with all the settings at maximum quality it only gives me a target quality of 256kbps.

---

### Post by tgalati4 on 2009-09-18
man lame

lame -b 320

This will do 320 kbps constant bitrate.  If you have useful filenames, then you can probably use wildcards (*) in the filenames.

lame -b 320 ~/Music/Album 1/*.wav 

See how that works.

---

### Post by rsambuca on 2009-09-18
> **kingdonerkebab said:**
> Had a look at sound converter. Even with all the settings at maximum quality it only gives me a target quality of 256kbps.

Sound Converter just uses lame to convert to mp3.  Just edit the mp3 instructions to whatever you want in the "preferences" menu.

---

### Post by garyed on 2009-09-18
I've never tried this with a whole album but I've done this with 3 or 4 .wav files at a time so it should work.
Go to a terminal & to the directory with the .wav files you want to convert.
Type this command & that should do it:
```
for i in *.wav; do lame -b 128 $i; done
```
You can change 128 to 320 but it depends on the codec of the wav file whether or not it will work. 128 usually works on anything.
All your wav files will remain intact & the new mp3 files will have the original names with .mp3 appended to the end.

Sometimes you don't have permissions so you need to be root if that happens. In that case put > sudo  in front of the command.
Good luck

---

