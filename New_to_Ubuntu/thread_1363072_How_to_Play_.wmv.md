---
title: "How to Play .wmv"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by halovivek on 2009-12-23
Hi
I have tried various players to run .wmv files in ubuntu 9.10.
I could not able to play the file and it is giving the codec error.
can somebody help me to install the perfect player? I need to run the .wmv for educational purpose.
thanks in advance

---

### Post by Marvin666 on 2009-12-23
Have you tried vlc? It's never given me troubles, even running on the second machine in my signtaure, and playing a game at the same time.

---

### Post by slumbergod on 2009-12-24
First thing I do on a clean install is add the medibuntu repository (google medibuntu) then use synaptic to add w32 codecs. 

That has all the ones you might need. Combined with vlc you cover virtually everything.

---

### Post by halovivek on 2009-12-24
i have tried with VLC player but it is not working.

---

### Post by lisati on 2009-12-24
Might be an encrypted wmv file or some such DRM issue - I recently purchased a DVD which had a couple of WMV versions of the movie on the disk, along with an insert with an unlock code printed on it for iTunes.

---

### Post by halovivek on 2009-12-24
I have to run from the ISO image. I have mounted and i can run the same file .wmv in windows it is working fine.

---

### Post by 3rdalbum on 2009-12-24
> **halovivek said:**
> I have to run from the ISO image. I have mounted and i can run the same file .wmv in windows it is working fine.

Have you tried adding the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and installing the "non-free-codecs" package? You need to do it every time you boot up, if you're just doing it from the live CD.

Ubuntu doesn't come with those sorts of proprietary, restricted codecs. Because they are proprietary and are restricted! If you need a live CD that can play these formats, check out Linux Mint.

Alternatively, install Ubuntu to your hard disk and then add the codecs.

---

