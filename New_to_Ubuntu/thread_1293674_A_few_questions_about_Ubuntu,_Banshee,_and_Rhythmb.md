---
title: "A few questions about Ubuntu, Banshee, and Rhythmbox"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by pgtl10 on 2009-10-17
1. Whenever I try to download something from Firefox I need an application to open the file but I don't know which application to use. Does have an install wizard or something of that nature?

2. A few days ago I installed the Amazon MP3 Downloader for Ubuntu but I can't find the downloader. It's not at Applications>Sound & Video and I can't find the file via search. I tried to reinstall the application just to see where is the location of the file but it doesn't say. Where is it?

3. I downloaded Banshee. I made a mistake and imported songs that weren't mine. When I tried to remove a song from my playlist(One of my songs actually), Banshee deleted the file. How do I remove songs from Banshee without deleting.

4. I downloaded the song from Amazon without the MP3 Downloader. I Banshee won't seem to play the song. There is a red X next to it. How can get Banshee to play the song?

5. I tried install RhythmBox 2.5 but Synaptic package manager won't recognize there is an update Rhythmbox. I already added the Rythmbox PPA. Can anyone help me find get the update. I have Rythmbox 2.0 which doesn't allow transfer of music to mp3 players.

---

### Post by Ms_Angel_D on 2009-10-17
I'm not to sure of the other problems, but to select and application to use with firefox you might try looking in /usr/bin

---

### Post by Paqman on 2009-10-17
> **pgtl10 said:**
> 1. Whenever I try to download something from Firefox I need an application to open the file but I don't know which application to use. Does have an install wizard or something of that nature?


What sort of file are you trying to open?

> 2. A few days ago I installed the Amazon MP3 Downloader for Ubuntu but I can't find the downloader. It's not at Applications>Sound & Video and I can't find the file via search. I tried to reinstall the application just to see where is the location of the file but it doesn't say. Where is it?

IIRC it's under Applications > Accessories. But it'll also just open up when you need it on the Amazon site.

> 3. I downloaded Banshee. I made a mistake and imported songs that weren't mine. When I tried to remove a song from my playlist(One of my songs actually), Banshee deleted the file. How do I remove songs from Banshee without deleting.

I'm not at my machine with Banshee right now, but if no-one has the answer i'll take a look later. You could dump your whole catalogue then rescan them, but it's a bit brute force.

> 4. I downloaded the song from Amazon without the MP3 Downloader. I Banshee won't seem to play the song. There is a red X next to it. How can get Banshee to play the song?

Where is the red x? In Banshee? Where did you put the file? Can open it any other way (eg: by clicking on it)?

> 
5. I tried install RhythmBox 2.5 but Synaptic package manager won't recognize there is an update Rhythmbox. I already added the Rythmbox PPA. Can anyone help me find get the update. I have Rythmbox 2.0 which doesn't allow transfer of music to mp3 players.

What PPA have you installed? The latest stable version of Rhythmbox is 0.12, so i'm :confused:

---

### Post by pgtl10 on 2009-10-17
> **Paqman said:**
> What sort of file are you trying to open?

***[I]Any***[/I]



IIRC it's under Applications > Accessories. But it'll also just open up when you need it on the Amazon site.

***It's not there***

I'm not at my machine with Banshee right now, but if no-one has the answer i'll take a look later. You could dump your whole catalogue then rescan them, but it's a bit brute force.

***Is there a better way?***

Where is the red x? In Banshee? Where did you put the file? Can open it any other way (eg: by clicking on it)?

***Tried clicking it but it didn't work. Tried getting Banshee to recognize the file but no luck.***

What PPA have you installed? The latest stable version of Rhythmbox is 0.12, so i'm :confused:

**My bad I was referring to [0.12.5]("http://projects.gnome.org/rhythmbox/")The website mentions an updated Rhythmbox.**

Please help

---

### Post by Devon64327 on 2009-10-17
Err... Do you have the restricted package to play MP3s? 
For your downloading generally they give you a generic version like their Unzipper so just hit okay when it asks you

sgfsuddgfg1111.....!!!   WTF?!? Im running Rhythm box .12
Edit
OK my bad there is only .12

---

### Post by |Mitch| on 2009-10-17
The program needed to open downloaded files depends on what type of files you're downloading.

It might help if you added in what you're trying to download & open.

When you asked about Banshee not playing .mp3s, you might need the ubuntu-restricted-extras package. This is assuming that no other .mp3s can play and that the songs you downloaded are actually in .mp3 format

---

### Post by Paqman on 2009-10-18
> **pgtl10 said:**
> [/B]
 Originally Posted by Paqman  View Post
What sort of file are you trying to open?

**Any**


Ok, so what *exactly* are you trying to do, and what isn't working.

Can you give an example of a link to something that doesn't open when you donwload it through Firefox?

> IIRC it's under Applications > Accessories. But it'll also just open up when you need it on the Amazon site.

**It's not there**

Does it open when you try and download an album from Amazon?

> I'm not at my machine with Banshee right now, but if no-one has the answer i'll take a look later. You could dump your whole catalogue then rescan them, but it's a bit brute force.

**Is there a better way?**

Hopefully, yes. Anybody at a machine with Banshee to look into this?

> Where is the red x? In Banshee? Where did you put the file? Can open it any other way (eg: by clicking on it)?

**Tried clicking it but it didn't work. Tried getting Banshee to recognize the file but no luck.**

Just to be clear: when you just browse to the file through the file browser and click on it, it does nothing?

> 
What PPA have you installed? The latest stable version of Rhythmbox is 0.12, so i'm

My bad I was referring to 0.12.5The website mentions an updated Rhythmbox.


What PPA is it? Are you sure it has a newer version of Rhythmbox than the repos? Can you post a link to the PPA?

---

