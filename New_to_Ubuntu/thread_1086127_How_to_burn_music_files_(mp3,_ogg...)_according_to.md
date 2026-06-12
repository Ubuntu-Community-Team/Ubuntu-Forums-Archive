---
title: "How to burn music files (mp3, ogg...) according to a playlist (m3u, pls...)"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Jan D on 2009-03-03
Hi!

I need help to create an "mp3 CD" which will play my music in my playlist order. Most CD/DVD players will play an "Data CD" (e.g. CD with .mp3 files) in alphabetical order... What I need is some kind of software that will copy and then rename all files listed in the playlist by adding 001, 002, 003.....and so on..... Maybe a script will do the job?

Please help me to never leave the path of Linux!

---

### Post by MrWES on 2009-03-03
> **Jan D said:**
> Hi!

I need help to create an "mp3 CD" which will play my music in my playlist order. Most CD/DVD players will play an "Data CD" (e.g. CD with .mp3 files) in alphabetical order... What I need is some kind of software that will copy and then rename all files listed in the playlist by adding 001, 002, 003.....and so on..... Maybe a script will do the job?

Please help me to never leave the path of Linux!


I'd be very interested in this solution; as I've been looking for the ability to burn a mp3 cd via the m3u file. I have not found such an app. 

Bill

---

### Post by Filippo on 2009-04-12
Hi,
save your playlist as .m3u and then :

```

sed '/^#/d' MyPlayListFile.m3u | tr '\n' '\0' | xargs -0 k3b --datacd
```

or if you prefer Brasero

```
sed '/^#/d' cd\ aprile\ 2009.m3u | tr '\n' '\0' | xargs -0 brasero -d
```

bye  Fil

---

### Post by snapback77 on 2009-04-12
Could you be a little more specific about the steps to take in terminal.  this problem has bothered me for years.  If I forget to number each file first they show up alphbatized!  Thanks for your help. 
Kenny

---

### Post by Filippo on 2009-04-14
my suggestion is for burn a mp3 Cd from a .3mu playlist file.

Probably what you need is batch renaming , ex :

[http://ubuntuforums.org/showthread.php?t=629060&highlight=batch+rename+prefix]("http://ubuntuforums.org/showthread.php?t=629060&highlight=batch+rename+prefix")


bye

---

### Post by logos34 on 2009-04-14
> **snapback77 said:**
> Could you be a little more specific about the steps to take in terminal.  this problem has bothered me for years.  If I forget to number each file first they show up alphbatized!  Thanks for your help. 
Kenny

just use k3b--I believe it will do what you want it to do

---

### Post by jdpipe on 2009-06-23
The attached script does a much better job... it will keep your files in the original order as specified by the M3U playlist file.

Files will be burned to data CD in their original MP3/M4A/OGG formats, there is not format conversion happening here.

Happy to hear any feedback about this... [http://jpye.dyndns.org/](http://jpye.dyndns.org/)

---

### Post by big_dog1968 on 2009-07-07
> **jdpipe said:**
> The attached script does a much better job... it will keep your files in the original order as specified by the M3U playlist file.

Files will be burned to data CD in their original MP3/M4A/OGG formats, there is not format conversion happening here.

Happy to hear any feedback about this... [http://pye.dyndns.org/](http://pye.dyndns.org/)

How do you use this (or any for that matter) script?
I have a playlist I want to burn to MP3, but it only give option for audio CD. 

Is there a Player or Burner that will do this automatically?

---

### Post by jdpipe on 2009-07-07
To use the script, save it to your home directory (~/m3utocd.py), then save your /path/to/your/playlist.m3u (whatever its name is) then open a terminal window and type

python ~/m3utocd.py /path/to/your/playlist.m3u

that should make some output, then it should pop up a Brasero window allowing you to burn your MP3 CD with the correct track ordering.

I couldn't find any current software that supported this feature. I reported the script to the Rhythmbox developers but no reply just yet.

---

### Post by webceo on 2009-12-18
Well the solution is simple and already exists..

1. Open Rhythmbox and go to your playlist, select all tracks
2. Open Brasero and create a data project
3. Drag the selected tracks from Rhythmbox inside the Brasero add files window
4. Voilà! you're done

Hope this helps


P.S : you can do the same thing to copy the playlist inside a folder in a file system (Removable media for instance)

---

### Post by jdpipe on 2009-12-18
@webceo: unless i'm mistaken, the approach you suggest destroys the ordering of the playlist. If you are burning songs from multiple albums, they will likely all be jumbled up together with the naive approach. This is because most MP3 players order the files by name and nothing else.

---

### Post by webceo on 2009-12-21
@jdpipe: that's right, that method doesn't respect the playlist order, I failed to read the part where the order of the tracks is important, my mistake, will keep my naive approaches to my self in the future ;)

---

### Post by psypher on 2010-05-14
> **webceo said:**
> Well the solution is simple and already exists..

1. Open Rhythmbox and go to your playlist, select all tracks
2. Open Brasero and create a data project
3. Drag the selected tracks from Rhythmbox inside the Brasero add files window
4. Voilà! you're done

Hope this helps


P.S : you can do the same thing to copy the playlist inside a folder in a file system (Removable media for instance)
Dude that an awesome solution, didn't know u could do that. Linux win! Doesn't do it in order, but in my case I didn't require it

---

### Post by Albvieira on 2010-11-22
> **webceo said:**
> Well the solution is simple and already exists..

1. Open Rhythmbox and go to your playlist, select all tracks
2. Open Brasero and create a data project
3. Drag the selected tracks from Rhythmbox inside the Brasero add files window
4. Voilà! you're done

Hope this helps


P.S : you can do the same thing to copy the playlist inside a folder in a file system (Removable media for instance)

Thanks, I'm really happy with my new cd :)

---

### Post by JanAcc on 2011-02-25
> **jdpipe said:**
> The attached script does a much better job... it will keep your files in the original order as specified by the M3U playlist file.

Files will be burned to data CD in their original MP3/M4A/OGG formats, there is not format conversion happening here.

Happy to hear any feedback about this... [http://jpye.dyndns.org/](http://jpye.dyndns.org/)

Thanks man, that seems to do the job :)
JanAcc

---

### Post by bods on 2011-03-19
> **jdpipe said:**
> The attached script does a much better job... it will keep your files in the original order as specified by the M3U playlist file.

Files will be burned to data CD in their original MP3/M4A/OGG formats, there is not format conversion happening here.

Happy to hear any feedback about this... [http://jpye.dyndns.org/](http://jpye.dyndns.org/)

Two years on and that script just helped me out a hole.  Great stuff

---

### Post by pasu11 on 2012-02-09
> **webceo said:**
> Well the solution is simple and already exists..

1. Open Rhythmbox and go to your playlist, select all tracks
2. Open Brasero and create a data project
3. Drag the selected tracks from Rhythmbox inside the Brasero add files window
4. Voilà! you're done

Hope this helps


P.S : you can do the same thing to copy the playlist inside a folder in a file system (Removable media for instance)

At first I tried to create a script to do that but was unsuccessful. After I read this solution, I can now do it the easy way. Thanks webceo :D

---

### Post by Jack Brown on 2013-01-14
awesome thread.

3 ways to do it, depending on your requirements.
Tested the rhythmbox / brasero way, confirmed that the digital music list copies to the New Data Disc Project for Brasero, with the option of automatically renaming files for compatibility in the other popular OS.

useful for making that special mp3 disc on a cd-RW for playing on a standalone mp3 cd player.

2009 and 2010 seems like good years for ubuntu!  (and we are still reaping that goodness today.)

Thanks filippo, jdpipe and webceo!

---

### Post by oldos2er on 2013-01-14
Old thread closed.

---

