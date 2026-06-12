---
title: "I'm giving up on Ubuntu if I can't burn a data CD"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by nick987654321 on 2009-08-19
I've tried Brasero, K3b, GnomeBaker, and Nero Linux; and none of the data CDs I burn will play on my stereos.  I am trying to burn a data CD and not an audio CD because a data CD can hold more songs.  I have been using windows for years and have never had a problem with data CDs.  Please help or its back to Windows for me!!!

---

### Post by michy99 on 2009-08-19
Are you sure that your stereo can play data cd? I thought most could only play audio cd's.

---

### Post by zerhacke on 2009-08-19
I'm assuming you're burning a data CD of MP3 files.  You have to make sure your stereo supports MP3 or whatever format you are using.

---

### Post by BigBananaMan on 2009-08-19
I think that's hardly a reason to go back to Windoze and all it's helplessness and frustrations.  In either case, all you're trying to do is burn the data to the disk so have you tried just using nautilus?  If you put a blank CD into your drive, you should see it show up on your desktop (alternately you can access it through "places".  From there you can just drop your files onto the icon or double click and dump them in there.  Then click "write to disk" and choose your burn speed. Banana-tip#371: slower is usually better since the laser has more time to burn into the write surface.

---

### Post by wojox on 2009-08-19
You cannot select data cd, it won't play in a cd player. It has to be a audio.

---

### Post by sumeshgupta on 2009-08-19
Try burning using the terminal. First collect all your songs in a directory say 'songs' by copy and paste.
then make an iso of that directory by typing following command in the terminal:
 
[php]$  mkisofs -r -J -o songs.iso ~/path/to/songs[/php]
 
Then burn the iso to a CD using Terminal by using following command
 
[php]$  cdrecord dev=/dev/scd1 speed=0 driveropts=burnfree -v -data path/to/songs.iso[/php]
 
here 'scd1' may be different for you. Please check your drive number in /dev directory and use that.
Hope this helps.;)

---

### Post by admiralspark on 2009-08-19
Why not just use Brasero Disk Burner? It burns audio CD's and Data CD's for me with no problems. It's free, there's a media guide on here somewhere that details where to get a whole bunch of good programs and software for multimedia...in fact, here it is: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) . 

Oh, and is it possible that it needs to be FINALIZED as an audio cd, which won't take place if you use Data mode? I would think data mode would only allow you to view the files on a computer (like opening a folder) as opposed to playing them directly from the CD. Audio quality is better as an audio CD setup.

---

