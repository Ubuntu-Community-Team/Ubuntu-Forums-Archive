---
title: "DVD Movie Plays fine But dd doesn't like it."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-12-13
I bought a DVD Movie (Dark Knight) and I want the iso on my computer. I can play the movie in vlc but when I run 
```

# dd if=/dev/dvd of=/home/user/Desktop/Bat.iso
dd: reading `/dev/dvd': Input/output error
720352+0 records in
720352+0 records out
368820224 bytes (369 MB) copied, 77.214 s, 4.8 MB/s

```

Since dd is a low-level operation, it makes no sense to me that the DVD plays but dd cannot simply read the 1s and 0s from the dvd.

---

### Post by jbrown96 on 2008-12-13
That's a strange device for your dvd player. Mine is /dev/scd0. Use the same device as listed in fstab ```
cat /etc/fstab
```

I can't remember if dd needs the device mounted or umounted, but you should try both ways. You can always try using  Brasero; I'm pretty sure it can make iso's. I prefer using command line tools, but it may be easier to go with GUI app.

---

### Post by JohnGalt131 on 2008-12-13
> **jbrown96 said:**
> That's a strange device for your dvd player. Mine is /dev/scd0. Use the same device as listed in fstab ```
cat /etc/fstab
```

I can't remember if dd needs the device mounted or umounted, but you should try both ways. You can always try using  Brasero; I'm pretty sure it can make iso's. I prefer using command line tools, but it may be easier to go with GUI app.

That's the one I tried first. It stopped at the same place (369 MB)
Also, brasero was the first method I tried. I have tried mounted and unmounted

---

### Post by Rolcol on 2008-12-13
If I remember correctly, that error comes up when you try to duplicate encrypted DVDs.  They purposely "corrupt" the data so it cannot be easily copied to reduce piracy.

---

### Post by insane_alien on 2008-12-13
/dev/dvd and /dev/scd0 will be the exact same device, just under two different aliases.

/dev/scd0 will be the actual device
/dev/dvd is mapped to it because its detected that there is a dvd there.

---

### Post by jbrown96 on 2008-12-13
> **Rolcol said:**
> If I remember correctly, that error comes up when you try to duplicate encrypted DVDs.  They purposely "corrupt" the data so it cannot be easily copied to reduce piracy.

This isn't true. dd makes a bit for bit copy, and encryption doesn't matter. While you won't be able to play the dvd unless you have some libraries to decrypt it, there won't be any problems making a copy. 

I don't really know what the problem is. What kind of filesystem are you using (if it's really strange, it might not support large files)? Could you try with another dvd? I'm sure you've tried this a few times; does it always fail at the same point?

---

### Post by JohnGalt131 on 2008-12-13
> **jbrown96 said:**
> This isn't true. dd makes a bit for bit copy, and encryption doesn't matter. While you won't be able to play the dvd unless you have some libraries to decrypt it, there won't be any problems making a copy. 

I don't really know what the problem is. What kind of filesystem are you using (if it's really strange, it might not support large files)? Could you try with another dvd? I'm sure you've tried this a few times; does it always fail at the same point?

Batman is a 2-Disc set.
The special features (7.8 GB) copied fine, but the actual feature won't
yeah it always fails at 369 MB

---

### Post by insane_alien on 2008-12-13
perhaps there is a scratch or even a bit of dust that causes a read error(beyond the capacity of the error correcting code ot compensate for) which could cause dd to exit.

i think there is something(dd_rescue maybe) that does the same thing as dd but will completely ignore read errors and continue on regardless that might be of use to you.

the program is in the repositories.

---

### Post by turkdavid on 2008-12-13
I have attempted to copy the same movie. Both my xp system and ubuntu system will not copy this dvd. I not sure how to get around this but usaly I have very good luck with most dvds.

---

### Post by djbushido on 2008-12-13
make sure libdvdcss2 is installed from the repos, and then there is a script included you have to run. this is already incorporated in vlc which is why it works. what you can also do is try and use handbrake. while it is command-line, it works for me every time when others would fail. Also, haven't tried this, but supposedly you can stream from vlc to file. My recommendation would be handbrake, but this might be appealing to some people.

---

### Post by jbrown96 on 2008-12-13
I doubt you will be able to burn it back to a dvd with this procedure, but it's worth a try. Copy all the files to a folder on your computer (make sure to look for hidden ones as well). Then dd that folder ```
dd if=/COPIED/LOCATION of=/DESTINATION/bat.iso
``` I have no idea whether this will play.

---

### Post by jerome1232 on 2008-12-13
I never had luck with dd and dvd's.

I've found dvdbackup and genisoimage to work well for me though, dvdbackup will copy the dvd structure to a folder, then genisoimage generates a dvd image from that.

k9copy is a gui app that can also generate iso images.

```
dvdbackup -M
genisoimage -dvd-video -o dvdtitle /path/to/dvd/folder
```

---

### Post by caljohnsmith on 2008-12-13
> **jbrown96 said:**
> This isn't true. dd makes a bit for bit copy, and encryption doesn't matter. While you won't be able to play the dvd unless you have some libraries to decrypt it, there won't be any problems making a copy. 

I don't really know what the problem is. What kind of filesystem are you using (if it's really strange, it might not support large files)? Could you try with another dvd? I'm sure you've tried this a few times; does it always fail at the same point?
I did the research once and Rolcol is right, it is (unfortunately) true; that's why you can't simply use "dd" to copy any DVD movie you want to. If you want to copy an encrypted movie, you have to use something like K9Copy, which is available in the repositories.

---

### Post by sneeks on 2008-12-13
i take it you are try to copy with brasisro,have you tried k9 copy?

---

### Post by mc4man on 2008-12-13
The only reason you can't copy it is because of the structure protection.

I just picked up the movie and am dumping it to an encrypted, structure protection .iso.

In this case the structure protection is mainly in the dvd structure itself, almost no unreadable sectors.

Actually it's almost done, taking about 10 min., will test the .iso and post back

---

### Post by mc4man on 2008-12-13
Plays fine, if you want I'll post the method but note that this is only for playback from a hdd. You cannot process, shrink or burn to media as a dvd video. (due to leaving the css intact
(took about 10 min. to dump to .iso

For any of that I advise to check here

[http://forum.doom9.org/showthread.php?p=1222386#post1222386](http://forum.doom9.org/showthread.php?p=1222386#post1222386)

edit: you can also use vobcopy (modified for fast skipping of bad sectors, takes 30 sec. in this title.
The resulting video_ts will need some fixing though.

---

### Post by CatKiller on 2008-12-13
> **jbrown96 said:**
> This isn't true. dd makes a bit for bit copy, and encryption doesn't matter. While you won't be able to play the dvd unless you have some libraries to decrypt it, there won't be any problems making a copy.

Rolcol is correct, although it isn't really part of the encryption in the strictest sense. Some studios (for cds, too, actually) will deliberately put bad sectors on the disc specifically to defeat bit-for-bit copies. Others will intentionally use a broken filesystem structure.

It isn't new, and serves no purpose other than to annoy their customers.

The forum guidelines probably prevent me from specifically saying how I regard people that do this.

---

### Post by egalvan on 2008-12-13
> **mc4man said:**
> Plays fine, **if you want I'll post the method but note that this is only for playback from a hdd.** You cannot process, shrink or burn to media as a dvd video. (due to leaving the css intact
(took about 10 min. to dump to .iso


edit: you can also use vobcopy (modified for fast skipping of bad sectors, takes 30 sec. in this title.
The resulting video_ts will need some fixing though.

***Exactly*** what I need. Can you post the instructions?

---

### Post by mc4man on 2008-12-14
To get .iso suitable for playback from your hdd then first install dvdisaster. (again note this is only for hdd playback, css and structure protections are untouched. (and irrelevant in this use.

After installing you'll find it in Applications -> system tools.
(leave all settings at default, only change the destination if wanted.
See screen, middle box in top panel

Insert your movie and open in a player, then pause playback.( this is needed for drive authenication

Open dvdisaster, make sure it's set to the correct drive (1st. box) and click on read.
The first time you use it you'll get a pop up, choose "disable rs02 .... ." and then " Skip ....".

You can now close out the movie player and wait for 'rip' to complete.

[B]Note that some drives are better at resuming full speed after read errors,
if your drive stays low (1.4-2x then this may not be for you
[/B]
If there are large numbers of unreadable sectors then this method is unsuitable due to time. (figure 16 unreadable sectors per 1.5 sec.

screen is from title in question, the 2nd read drop was caused by me, notice how my drive resumes good speed.

edit in the screen you'll see I forgot when renaming the destination a "." in front of iso.
Not a big problem, only needed to add back to the ripped iso. Better to make sure it's name.iso

---

