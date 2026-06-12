---
title: "Rythym Box Music Player not seeing music"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Ant01 on 2008-12-21
I am trying to use the Ubumtu Music Player to play my music from my removable drive but it won't add the music to the directory. I am using Rythumbox Musc Player, not sure if this is the est one to use?

---

### Post by Mazza558 on 2008-12-21
Try Banshee.

- Open a terminal (Applications > Accessories > Terminal)
- Type this into the terminal:

> sudo aptitude install banshee

- Enter your password (don't worry, it doesn't show any sign that you've typed it in)
- Press Enter

Then open it in Applications > Sound and Video > Banshee

---

### Post by Elfy on 2008-12-21
If it's not working - what does it say is the problem?

There are many different one's out there and you'll soon find everyone has a different favourite ;)

---

### Post by Ant01 on 2008-12-21
The Banshee is working, but I can't add my music which is stored on my removable drive, I can only open the songs one by one...

---

### Post by ajgreeny on 2008-12-21
If you ever start rhythmbox without the external disk attached, rhythmbox may be updating the music in its listing.  You can set it to not watch for new tracks in the Edit > Preferences > Music tab.  If that does not make a difference, I can't think of anything else, I'm afraid.

---

### Post by balaknair on 2008-12-21
As forestpixie noted, everyone has a different favorite in music players.
My personal favorite is Amarok(1.4.x, not 2.0 which is a bit unstable at present), but Rhythmbox has probably the best integration into the Gnome desktop(which is what you see in Ubuntu).

But returning to your problem, is the removable drive mounted? ie, When you open the File browser, is there a little 'Eject' symbol next to the entry for the drive in the left hand pane(the little Orange icons marked 'b' in the screenshot, where the drives marked 'a' are removable drives(1 GB USB drive/MP3 player and WD 500 GB external hard drive))? And can you access the files via the file browser? 

If you can access the files via the file browser(which is called 'Nautilus), then Nautilus too should be able to detect the files. You just go to Music> Import Folder--> and now browse to the folder where your music is and click 'Open'.

Note that you probably won't get anywhere with the 'Scan Removable Media' option, since that refers to CDs and DVDs. For a removable drive such as a flash disk or an external hard disk, use the 'Import Folder' option.

Update: OK so the drive is mounted, so I'm guessing you're using the 'Scan Removable Media' option. Try using 'Import Folder' instead.

Hope this is helpful.

---

### Post by Ant01 on 2008-12-21
> **ajgreeny said:**
> If you ever start rhythmbox without the external disk attached, rhythmbox may be updating the music in its listing.  You can set it to not watch for new tracks in the Edit > Preferences > Music tab.  If that does not make a difference, I can't think of anything else, I'm afraid.

Thanks for the tips, the removable drive is mounted. I used the above tip and was able to add the music to my playlists, thanks again. Which is the most popular media player for begginers

---

### Post by Ant01 on 2008-12-21
I notice Rythym Box doesn't have does the option to browse music via Genre, is this so or am I missing something?

---

### Post by chrisod on 2008-12-21
You can set up play lists by genre.

---

### Post by balaknair on 2008-12-21
In Rhythmbox, to get Genre view, Edit>Preferences> General gives you the option of choosing to view by Genre as well.

List of alternate music players suitable for beginners:
Amarok, Banshee, Exaile, Songbird, XMMS

1) Amarok: I've tried all these apps, and in the end I have to say my personal favorite Music Player is Amarok. IMO it's the best Music player and manager on any OS. Especially for large music collections. And it also has the option of using MySQL for the music collection instead of SQLite, which makes it even faster(though this might not be something for beginners). It's also extendible with numerous scripts/plugins available. Ive found it the most intuitive of all music players I've used. Organizing and searching your music is easy and painless, and you can browse your collection by various tagsI suggest you give it a try and spend a few days using it. Chances are that like me you'll wonder how you ever managed without it. In fact in the early days of my journey with Linux, I would boot into Linux just to listen to music with Amarok. 
In addition it has all the usual 'must-have' features like automatic cover fetching and Lyrics fetching.
The only drawback to Amarok on Ubuntu is that it's based in KDE, not Gnome. So looks-wise it won't share the same system theme as other applications. Also, the default layout might not appeal to everyone, with tabs on the left hand pane. 

2) Banshee: It's similar to Rhythbox in layout and feel, in that it tries to mimic iTunes, but it's prettier than Rhythbox, and can also handle most Video formats. I found it a tad slow compared to RB and Amarok though. And all the eyecandy uses up system resources as well. To use the latest stable version, add the Banshee repositories as per instructions on the Banshee website, since the version in the Ubuntu repositories is a little older(and not as stable).

3) Exaile: A Gnome version of Amarok, it's a pretty good player in its own right. The versions I used had some stability issues though.

4) Songbird: A nice little cross-platform player, based on Mozilla, with excellent net integration, and good eyecandy features(like the cover-flow visualisation similar to that in iTunes) and numerous plugins/Add-ons available. It's what I use on Windows, but I have found it less intuitive and customisable than Amarok.

5) XMMS: A rather spartan player with no frills. Sort of like the old Winamp Classic look. No music manager or extra fittings. It's desgned to do just one thing- play the music you tell it to without hogging your system resources.

There're a whole lot of other players out there, I've just listed what I consider the best of breed.

In the end, it comes down to what works for you. Have fun.

---

### Post by Ant01 on 2008-12-21
:guitar:Thanks everyone for the support, Linux rocks when it comes to support, can't wait till I can make the change over and throw my windows discs away....

---

### Post by balaknair on 2008-12-21
> **Ant01 said:**
> :guitar:Thanks everyone for the support, Linux rocks when it comes to support, can't wait till I can make the change over and throw my windows discs away....

Glad to Help.
Have fun :popcorn:

---

