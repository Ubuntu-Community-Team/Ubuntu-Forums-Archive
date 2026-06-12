---
title: "sharing music"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by tjefferson on 2009-03-14
My laptop runs 8.10 while my family's computer is XP. I have a lot of music, saved as .flac, on the family computer. What's the best way to stream music from the windows box to my laptop? I want to keep the lossless quality, which Orb, for example, does not support. Thanks for any help.

---

### Post by joey-elijah on 2009-03-14
> **tjefferson said:**
> My laptop runs 8.10 while my family's computer is XP. I have a lot of music, saved as .flac, on the family computer. What's the best way to stream music from the windows box to my laptop? I want to keep the lossless quality, which Orb, for example, does not support. Thanks for any help.

If you have itunes on XP you can access/stream/listen to the music in Rhythmbox. Just enable DAAP in itunes and in Rhythmbox.

---

### Post by tjefferson on 2009-03-14
iTunes does not support .flac, unfortunately. Are there other daap capable programs for windows? Would this retain the quality of .flac?

---

### Post by rabiabidabi on 2009-03-14
> **joey-elijah said:**
> If you have itunes on XP you can access/stream/listen to the music in Rhythmbox. Just enable DAAP in itunes and in Rhythmbox.

Hi. I have been transferring my itunes library manually from my G5 imac to my Ubuntu Eee. I download about 180 songs at a time to my ipod, then switch the ipod to my eee and drag the songs into rhythmbox. Time consuming, but it works.

Can I use the method you describe to move the files?

---

### Post by tjefferson on 2009-03-14
If you have two computers on a network, especially if it's wired, transferring files through the LAN is as fast as you can go. My problem is that the hard drive space on my laptop is limited. If I can stream the music, then I wouldn't need to take up as much space.

---

### Post by BDNiner on 2009-03-14
Or you can share the folder that contains your music on your windows PC and mount that folder on your ubuntu PC and Rhythmbox will be able to browse that folder and play the files. You can even rip a CD and send it to the windows PC by setting the rip folder to the share that contains your music (kinda slow though!!)

---

### Post by tjefferson on 2009-03-14
That's certainly an option, but it's cumbersome and rather slow. I was hoping for something like an offline orb; streaming across my home's network and connecting to a standalone media player on my desktop while maintaining the fidelity of .flac.

---

### Post by vanadium on 2009-03-15
I do not see why sharing the Windows Xp folder would be cumbersome and slow. Once set-up properly, you just access your music as if it resides on your local hard drive. If hte network is slow, then not only file sharing but also streaming would be slow, I guess.

---

### Post by BDNiner on 2009-03-15
I completely agree with Vanadium. If setting up a network share and playing music from the share is slow then setting up a streaming service would also be slow. The only advantage I can see with going with a streaming solution than a network share is being able to setup access to your music from outside your network.

---

### Post by BDNiner on 2009-03-15
This got me interested and I have done some research. You can setup a streaming media server in Ubuntu using GNUMP3d, here is a link with basic setup instrutions:

[http://swik.net/Ubuntu/Only+Ubuntu/Streaming+Media+Server+in+Ubuntu+GNU%2FLinux/2cn9](http://swik.net/Ubuntu/Only+Ubuntu/Streaming+Media+Server+in+Ubuntu+GNU%2FLinux/2cn9)

---

### Post by Yashiro on 2009-03-15
Just share the folders on the WinXP machine. No need to do anything fancy at all. Sharing files is sharing files.

---

### Post by KayakJim on 2009-03-15
> **Yashiro said:**
> Just share the folders on the WinXP machine. No need to do anything fancy at all. Sharing files is sharing files.

+1

Share the folder and then play them on your Ubuntu system with whatever application you want.

---

### Post by egalvan on 2009-03-15
> **Yashiro said:**
>  Sharing files is sharing files.

Yep, too true...


but remember, the OP wants to play flac files on Ubuntu...

So, a quick Synaptic search, and many returns...

the first was 'audacious'

I don't use itunes or flac (at the moment), and I don't "stream" anything...
 so no further ideas from me :)

---

### Post by vanadium on 2009-03-15
[quote=egalvan]Yep, too true...


but remember, the OP wants to play flac files on Ubuntu...
[/quote]
I do not get your point. Files that are shared can be accessed. flac files that can be accessed, can be played with any player that supports them (that is virtually any player under linux).

---

### Post by egalvan on 2009-03-15
> **vanadium said:**
> I do not get your point. Files that are shared can be accessed. flac files that can be accessed, can be played with any player that supports them (that is virtually any player under linux).

Well, the OP stated that "Orb does not support flac".
That indicated that he was looking for something to access flac files.
So I pointed him in the direction of searching in Synaptic for "flac",
to find specific software...

Also, he was looking for ways to "stream" music, which means he wants more than just "file access", he wants "streaming software"...

As I stated, I have no experience with flac or streaming...

Others will have to chime in on those...

---

### Post by mkvnmtr on 2009-03-15
I haven't done it with my music but wouldn't it be the same as playing moves on a samba shared folder. Just enable the folder they are in and on the music player play them. Nothing hard about playing flac files or about sharing them from another computer.

---

