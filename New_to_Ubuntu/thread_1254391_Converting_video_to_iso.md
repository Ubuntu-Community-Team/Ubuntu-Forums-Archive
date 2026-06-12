---
title: "Converting video to iso?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Benbow on 2009-08-31
I have added a "memup" 1tb box to my audio setup so that I can add my photos, music, films and home dv to it and have them all in one place and show them on my pc or dvd projector. The box comes formatted with fat32 and I don't think that I can change this without upsetting the system.
I have to use NTFS and the box refuses all formats (including AVI) except ISO which is ok.
My question is, how do I change AVI and other formats to ISO. I use Ubunto all the time even though I am not very technical so the command line, unless very simple, is not an option.

---

### Post by Tu1J4kXk8NUhMz on 2009-08-31
An ISO is otherwise known as an Image File. If you're familiar with the ZIP file, it's a similar concept. You are storing all of your files within the ISO. More technically, the ISO file is meant to be a copy of a disc.

I'm not familiar with the system you are referring to. Is it a digital media player?

Does the ISO file have to resemble a DVD Video? Or can it be a data DVD?

---

### Post by halitech on 2009-08-31
Look into Devede, it will convert everything into the proper format for a video dvd and create the iso file for you as well.

---

### Post by SuperSonic4 on 2009-08-31
+1 for devede, the resulting ISO can also be played directly in VLC

---

### Post by gchand7 on 2009-08-31
Yes DEVEDE is the best and most user friendly. AVI files are great but the ISO files will be an average of 4,?gb where the AVI files usually are less than 900mb. Converting time varies depending on your equipment I can usually convert AVI to ISO in about 50 minutes.

---

### Post by halitech on 2009-08-31
that depends, I've taken 700meg avi files and just used the default settings and I get a 2 - 3gig iso file. (average around 2.3gig)

---

### Post by Benbow on 2009-08-31
Yes, it's a digital media player (I did say that I wasn't very technical:confused:). On the minimal info, it says it supports -
Video - Video decode: MPEG 1,2,4, DivX, Xvid.
      - Format: AVI, VOB, DAT, MPEG, MPG.

It doesn't mention ISO although it works for me? Could it be something to do with the fact that it is formatted with FAT32 and I am using Ubuntu? It does say that it can be reformatted but I am not sure how to tackle this. I would really like to get it working as it should and any help with reformatting the player would be welcome.
Thanks for your replies.

---

### Post by zerhacke on 2009-08-31
Since it supports XVID and DIVX, you don't need to convert it to an ISO at all.  Just burn it as a standard data file to a CD or DVD and your player will pick it up automatically.

---

### Post by Benbow on 2009-08-31
Ah yes, but it is a 1tb hard drive and I need to copy it direct to the multimedia player (hd)  from the pc. The idea of these things is that you can put all your photos, music and films on to one hd and everything is available from one source or alternatively it is simple to transport to another room or wherever.
I think that possibly the fact that the hard drive of the multimedia player is formatted to FAT32 may be the problem and formatting this for linux is the answer but I don't know how to do it.

---

### Post by halitech on 2009-08-31
mke sure its unmounted and then use partition editor to format it ext3

---

### Post by zerhacke on 2009-08-31
No no no, you do not need to make it ext3.  Linux can read FAT and FAT32 just fine.

Try copying the file as just a file.  There is no need to convert it to ISO.  If you stick just the plain jane file into your media player it should work since your media player supports DIVX and XVID.

---

### Post by Benbow on 2009-08-31
Thanks to all, particularly Halitech for sticking with me. I am about to try your last suggestion, wish me luck!

---

### Post by Benbow on 2009-08-31
I have tried avi and mpeg but only iso will work. Before I format I will try it with just a basic Video ts and audio ts in a folder.
Thanks zerhacke

---

