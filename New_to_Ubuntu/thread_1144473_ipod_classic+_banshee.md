---
title: "ipod classic+ banshee"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by thesuperjman on 2009-04-30
ive imported my songs into the library and they all stay there when i unplug my ipod and all, but they wont play unless i actually have it plugged in. any suggestions on how to fix this?

---

### Post by blueridgedog on 2009-04-30
Are the songs anywhere on your PC or simply on the iPod?  It seems that you imported them off of the media, so it knows them on that location, but that location is not available when the device is removed.

---

### Post by thesuperjman on 2009-04-30
im trying to import media from the ipod to banshee. everything stays in the library but it won't play unless the ipod is plugged into the computer.

---

### Post by Garrovick on 2009-04-30
If you click on Library, are there any files in Library? I believe you have to drag the files from the iPod to the Library.

Try that.

Plus, there isn't any support for iPods in Linux like there is with iTunes.

---

### Post by kanikilu on 2009-05-01
I believe that's a known issue:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/f630183eaaf8dc9b?pli=1](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/f630183eaaf8dc9b?pli=1)

[http://www.nabble.com/Banshee-doesn%27t-copy-files-from-iPod-to-PC-td22934040.html](http://www.nabble.com/Banshee-doesn%27t-copy-files-from-iPod-to-PC-td22934040.html)

Unfortunately it seems that neither of those reports generated a response, so I'm not sure if a fix will be coming eventually or not...

The main problem is that the *expected* behavior is to copy the song to your physical hard drive, when in fact all it does is add the path to the song on your ipod to the library, hence it doesn't work when you disconnect.

The strange thing is that when you drag a song from your library to the ipod, it *does* work as expected, and it copies the actual file to the device... go figure :confused:

Anyways, I noticed this problem a couple weeks ago and have been on the hunt for an alternative music manager. So far nothing quite fits the bill that "does everything", but **gtkpod**, while somewhat of a "single-tasker" is able to transfer files to and from my ipod with no problems.

In fact, I'm more and more finding myself moving away from programs that try to do too many things because I just end up getting disappointed when an application does **everything** I want except one or two things.

So, for now, I use gtkpod to manage my iPod, and I use whatever else is available to actually listen to music on my computer (moc, listen, audacious, exaile, songbird, vlc, and so on...).

---

### Post by thesuperjman on 2009-05-01
yea you know exactly what i'm talking about kanikulu. thanks i'll try out gtkpod and see how it handles for me. ill put up my results on this thread for everyone.

---

### Post by Ericyzfr1 on 2009-05-01
It works fine on 2 Ipods I own righto out of the box.

---

### Post by nothingspecial on 2009-05-01
Somewhere in the preferences or the window that appears when you click on the ipod icon on the left is an option "copy songs to library when importing" ( or something like that ... haven`t used banshee for a while)
 Check that box, remove the ipods songs from your library then import them again. That will copy them to your computer.

---

### Post by blueridgedog on 2009-05-01
Or simply open the iPod with Floola and copy the songs over.

---

### Post by kanikilu on 2009-05-01
> **nothingspecial said:**
> Somewhere in the preferences or the window that appears when you click on the ipod icon on the left is an option "copy songs to library when importing" ( or something like that ... haven`t used banshee for a while)
 Check that box, remove the ipods songs from your library then import them again. That will copy them to your computer.

That option was already checked for me (Edit > Preferences > General > Copy files to media folders when importing), and it wasn't working.

Although, strangely, after I **un**checked it and then checked it again, it seems to have worked - at least for one of my devices...I'll try my iPod tonight.

> Or simply open the iPod with Floola and copy the songs over.

Floola is nice (portability is it's main asset), but in my experience, it's even slower than gtkpod.

---

### Post by blueridgedog on 2009-05-01
> **kanikilu said:**
> 

Floola is nice (portability is it's main asset), but in my experience, it's even slower than gtkpod.

Do you see it as slow?  I have never thought about the speed that it works.  I have 60 gigs on my iPod and it works with it reasonably fast.  Prior to getting my new CPU I did notice that it took a while to decode the iPod (an older AMD at about 1.8 clock).  With my new Quad core chip, it seems almost seamless.  My only real complaint about Floola is the limited error reporting (there are times it refuses to import files, but it is up to the user to debug why).

I will look at gtkpod ...

---

### Post by kanikilu on 2009-05-01
> **blueridgedog said:**
> Do you see it as slow? I actually haven't used it in well over a year, so I don't have a current opinion on it...it very well might be better now, and I just don't know it yet ;)

My only complaint with gtkpod is that there doesn't seem to be a way to search the contents of the ipod. You can use filters and sort it by artist, album, whatever, but you still have to scroll through to find what you are looking for.

---

### Post by kanikilu on 2009-05-01
> **kanikilu said:**
> I'll try my iPod tonight.

Well, that was failure - no matter what I do, I cannot copy from my iPod to my library/computer. Banshee creates the proper directory structure, adds the songs to the library database, but doesn't actually transfer any files.

The strange thing is, if I right-click on the iPod and choose "Import to Library", it actually starts to copy, and as I watched it, the files were in fact being created locally. I stopped it though, because I didn't need to backup my entire iPod (~100GB).

It just seems that trying to copy individual files, albums, or artists to the local drive simply does not work :( With an iPod, that is, it worked with my G1 phone, but that's a mass-storage device, so not really the same thing...

I confirmed again that gtkpod works with no problems, and if you add the filter bar to the view, it acts as a pretty decent search, similar to how iTunes does it (albeit a little slow).

I guess I'll wait it out and see if Banshee continues to improve. For now I'll stick with gtkpod for managing my devices and use something else for playback and local library management...it's not that big of a deal.

---

### Post by blueridgedog on 2009-05-01
> **kanikilu said:**
> Well, that was failure ...

It just seems that trying to copy individual files, albums, or artists to the local drive simply does not work :( With an iPod, that is, it worked with my G1 phone, but that's a mass-storage device, so not really the same thing...

I guess I'll wait it out and see if Banshee continues to improve. For now I'll stick with gtkpod for managing my devices and use something else for playback and local library management...it's not that big of a deal.

I have come to REALLY enjoy Floola for just what you suggest.  I have a collection of directories for my music and audio books.  These include to be sorted, to be sent to the iPod and to be archived.  I plug in the iPod and copy all the content from the to be sent to the iPod directory to it.  Live is good.  Also, all my iPod content rests on a media drive that is backed up once a week.  With a 1000 gig drive at about $100 now, I find that three 500 gig drives are pretty cheap.  I have one for "media" and two for backup.  

All of my "stuff" goes on the internal 500 gig drive that is my home directory and the other two are rotating backups.

---

### Post by thesuperjman on 2009-05-02
> **nothingspecial said:**
> Somewhere in the preferences or the window that appears when you click on the ipod icon on the left is an option "copy songs to library when importing" ( or something like that ... haven`t used banshee for a while)
 Check that box, remove the ipods songs from your library then import them again. That will copy them to your computer.

This box in mine was unchecked. So, I checked the box, then re-imported the songs and now it works.

My only discrepancy (and I'm aware I'm now going into a slightly different territory) is that I can't play the songs I've bought from itunes. Some of them show up in my library, but just say idle when I click them, others won't even import into my library. Is there a way to bypass this BS?

---

### Post by DennisD on 2009-05-02
OP, I have not tried banshee, but today, I plugged my ipod into my ubuntu (9.04) box and after a moment, my box found the ipod and I selected Rhythmbox for my music file manager, I selected the music tab, then import folder, selected my now music sync folder on my box, importing was easy, after, I went to that folder and clicked "select all" and dragged the content to the "Device" and away I went to success.

Copying files from the IPOD to another ubuntu box is even simpler. After plugging in the cable and your box finds the ipod, select all in the device folder from Rhythmbox to your destination folder on your box and DONE.

I hope this is of help to you, I realize I am not speaking in reference to banshee, but when I read about your issue, I thought maybe my success would be a benefit to you.

---

### Post by thesuperjman on 2009-05-03
Will rhythmbox support itunes downloaded songs? because none of the songs i downloaded from itunes will play or some wont even import at all.

---

### Post by thesuperjman on 2009-05-06
bump the above.

also, any word on support for ipod 2nd gen. touch support on linux yet?

---

### Post by thesuperjman on 2009-05-14
bump

---

