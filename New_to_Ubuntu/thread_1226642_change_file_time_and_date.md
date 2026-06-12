---
title: "change file time and date"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-07-29
When I am in Windows, I am able to change a variety of file attributes using a nice little program called Properties Plus. Is there a similar program for Ubuntu? In my case, I run 8.04.3 on my main maschine but have other machines running intrepid and jaunty.

What I'd like to be able to do (easily) is to select several files or just one and change its/their creation time, modified time and/or accessed time/date. 

Thanks for your time.

---

### Post by lisati on 2009-07-29
Ubuntu has the "touch" command (I've seen Windows versions as well)

For more information, type the following on the command line: ```
man touch
```

---

### Post by Michael Dooley on 2009-07-30
Thanks lisati. I should have known that there would be a command line fix for this problem.

---

### Post by Michael Dooley on 2012-04-09
Replying to my own thread...

Does anyone know if there is work being done on a GUI for Ubuntu that would let folks change file attributes and time/date stamps as easily as Properties Plus functions in WinXP? I would bet that something like this has been submitted as an idea. I'm getting tired of typing the time/date stamps using touch and would like to think that a simple GUI is on somebody's mind.

---

### Post by Zill on 2012-04-09
> **Michael Dooley said:**
> ...I'm getting tired of typing the time/date stamps using touch and would like to think that a simple GUI is on somebody's mind.
Just out of interest, *why* do you want to change the time/date stamps of multiple files?  These stamps generally automatically show the correct info and so why would you change this?

If you do have a need to change multiple files then a script might be the way to go.

---

### Post by Michael Dooley on 2012-04-09
> **Zill said:**
> Just out of interest, *why* do you want to change the time/date stamps of multiple files?
I am going through old digital photos and changing time/date stamps on those images that have no exif data. These photos were scanned and saved as .jpegs and to set their date is tedious when I have to re-set hundreds of them one by one. If I could do some of this with batch script, I would. Do you have a suggestion as to where I might find a suitable script that I could modify?

Thanks for your time.

---

### Post by edm1 on 2012-04-09
I believe Phatch is able to batch process images and metadata. Its in the repository.

---

### Post by Vaphell on 2012-04-09
general idea would be
```
for f in *.jpeg; do touch -m -t 200012312359.59 "$f"; done
```

Depends on situation though. Are they contained to a single dir, do they need to be found first among many other pics, do they need one common timestamp or should it be extracted/parametrized somehow.

---

### Post by Zill on 2012-04-09
> **Michael Dooley said:**
> I am going through old digital photos and changing time/date stamps on those images that have no exif data. These photos were scanned and saved as .jpegs and to set their date is tedious when I have to re-set hundreds of them one by one. If I could do some of this with batch script, I would. Do you have a suggestion as to where I might find a suitable script that I could modify?
I had a related problem when using mogrify to resize photos while still wishing to retain the original time/date stamp data.

[Paddy Landau]("http://ubuntuforums.org/member.php?u=572807") very kindly came up with a script to do exactly this - see post [#6]("http://ubuntuforums.org/showpost.php?p=9442070&postcount=6") in thread [Preserve original datestamp with mogrify?]("http://ubuntuforums.org/showthread.php?p=9449553")

While this is not *exactly* what you wanted, maybe you could use this script as a basis for your task.

Unfortunately, I have to admit that I am unlikely to be able to help further with this as bash scripting is not my strong point. :-(

Hopefully someone more knowledgeable will shortly be able to assist.  Good luck!

---

### Post by Michael Dooley on 2012-04-09
> **edm1 said:**
> I believe Phatch is able to batch process images and metadata. Its in the repository.
Yes, in the repository. Not particularly useful for my needs. Thanks though.

---

### Post by Michael Dooley on 2012-04-09
> **Zill said:**
> I had a related problem when using mogrify to resize photos while still wishing to retain the original time/date stamp data.
I *think* jhead might be of assistance in this kind of task. If you have the time, check out jhead.

I *think* that I need a date/time stamp editor that will let me scroll through and select the desired alterations. I would like this to work on any kind of file or even a folder.

Thanks for the suggestions though.

---

### Post by Zill on 2012-04-11
> **Michael Dooley said:**
> [QUOTE=edm1;11831117]I believe Phatch is able to batch process images and metadata. Its in the repository.
Yes, in the repository. Not particularly useful for my needs. Thanks though.[/QUOTE]
Why not?
> Data stamping: You can write any combination of exif or iptc tags (date, time, aperture, shutter speed, … or other info) automatically on a collection of images.
Source: [http://photobatch.wikidot.com/faq]("http://photobatch.wikidot.com/faq")

Re jhead I guess you will be back to scripting to do what you want.  Not my area unfortunately!

---

### Post by Michael Dooley on 2012-04-12
> [QUOTE]Yes, in the repository. Not particularly useful for my needs. Thanks though.
Why not?[/QUOTE]
Phatch will edit the metadata, not the file date/time stamp. Jhead, another photo "editor", will change a jpg file date/time stamp. However, one must use jhead a terminal command and then type in the time/date. I would like an easier to use GUI.

Thanks Zill.

See:  [http://brainstorm.ubuntu.com/ideatorrent/idea/23505](http://brainstorm.ubuntu.com/ideatorrent/idea/23505)  where others also think a Nautilus control over time and date is a good idea.

---

### Post by dosware on 2012-08-05
If you are dead-set on finding a gui solution and aren't averse to installing KDE apps, KRename has a plugin which can change access and/or modification date and time on a selection of files. I use an older (4.03) version, so I assume recent versions maintain this plugin. The Krusader file manager also integrates/ uses KRename for its mult-rename function.

---

