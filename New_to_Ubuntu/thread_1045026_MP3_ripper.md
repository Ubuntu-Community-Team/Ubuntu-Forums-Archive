---
title: "MP3 ripper"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by loseby on 2009-01-20
Ok, I want something that I like and can modify all the settings. Something similar to CDEX. Have tried Ruby ( cant remember the full name but I did get it working )but it didnt give me the option of ripping to 320 kbps.

Maybe installing cdex under WINE may be the go but have not had much luck using Wine on the other computer.

So I guess the two questions are -

1/ How do I install CDex using Wine ?

2/ Or is there a really good ripping program that gives me options ?

---

### Post by diablo75 on 2009-01-20
Try Applications>Add/Remove...

Search for the word "ripper"

Scroll down just a tad, and you'll find Audio CD Extractor.  Works for me!

---

### Post by wolfen69 on 2009-01-20
i have used ripperx. it was the only one i've found that gave me 320kb.

---

### Post by mahalos on 2009-01-20
I've always liked Grip. Although i always forget how to set it up when i do a re-install.Have a look here
[http://ubuntuforums.org/showthread.php?t=183125&highlight=grip+ripper]("http://ubuntuforums.org/showthread.php?t=183125&highlight=grip+ripper")

---

### Post by mcduck on 2009-01-20
+1 for Grip. Absolutely the best ripper around. Indeed takes a bit of configuring the first time you use it, but produces almost any audio file at any bitrate as long as you have suitable encoder for the task.

Plus it supports Paranoia (for scratch detection, might fix copyprotections as well ;)) and multiple processors/cores..

If you want options then Grip is definitely worth a try.

---

### Post by loseby on 2009-01-22
thanks for the replies


will try a couple and see how they go

update: trying ripper x but it wont work. There is no plugin encoder for mp3 ( lame mp3 encoder ) . The only encoder that is highlighted is the OggVobis one.  I have downloaded codecs befpre and can play mpe's but looks like I need another one for this so where do I get it from ?

ok, have been searching threads and am trying this

sudo apt-get install ubuntu-restricted-extras lame

fingers crossed

---

### Post by loseby on 2009-01-22
> **mcduck said:**
> +1 for Grip. Absolutely the best ripper around. Indeed takes a bit of configuring the first time you use it, but produces almost any audio file at any bitrate as long as you have suitable encoder for the task.

Plus it supports Paranoia (for scratch detection, might fix copyprotections as well ;)) and multiple processors/cores..

If you want options then Grip is definitely worth a try.


does it do normalizing as well ?

---

### Post by mcduck on 2009-01-22
> **losbey said:**
> does it do normalizing as well ?

Never tried, but yes, it is able to do that.

In ripping options there's a check box for "Calculate gain adjustment". This will hep a bit.

But I believe the actual way to normalize is to simply run any CLI audio tool that can normalize audio for you, there's a field in rip options called "Wav filter command" that allows you to use pretty much any CLI tool you want to process the audio after ripping but before encoding. Quick google search suggested using something like "/usr/bin/normalize-audio -a -20dB %w" as the command.. It's also possible to use the calculated gain adjustment value as a variable in the command.

---

### Post by Jormeliini on 2009-01-22
> **mcduck said:**
> But I believe the actual way to normalize is to simply run any CLI audio tool that can normalize audio for you, there's a field in rip options called "Wav filter command" that allows you to use pretty much any CLI tool you want to process the audio after ripping but before encoding. Quick google search suggested using something like "/usr/bin/normalize-audio -a -20dB %w" as the command.. It's also possible to use the calculated gain adjustment value as a variable in the command.

There's also a way to adjust the volume of mp3s in a non destructive way. A command line program called mp3gain can do it. You can get mp3gain from the Ubuntu repositories using apt.

---

### Post by loseby on 2009-01-25
ok, have installed mp3 gain but have no idea of how to  open it or even where its installed

edit : simplest way is to install mp3 gain on mp XP computer and use CDex as I am convertiung allmy music to MP3's and I know what I am doing there :-)

---

