---
title: "Newbie here"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-01-09
Hi Ya'll,
 I got passed this Ubuntu on to me by a friend. I have been general web surfing with it from the live CD, and I took the step and installed it. I understand that I have to download some stuff for a better user experience. What codecs(?) should I download to be able to watch my DVDs and watch flash content from the internet?Also, can anyone recommend some good programs to make this less painful in my switch from Windows? I understand there is a newer version of open ofice which I messed with a little, how do I get it? What media players should I do? Can I still use Thunderbird? What about Google Docs? Where should I head for basic stuff?
Thanks for ya'll's time ahead

---

### Post by BlakeM on 2009-01-09
Hey,

Started with Ubuntu not long ago as well. So I was where you are now not long ago.

Yes, you can still use Thunderbird with Ubuntu. I installed Ubuntu on my grandparents computer and they use Thunderbird. Bit of a hassle transferring their emails and contacts from Outlook Express but I got it in the end. Just download it from their website, I think.

When you first try to play a media file that requires "restricted codecs", Ubuntu will ask if you want to search for them. It did a great job and I was watching Scrubs in under a minute.

Same thing with YouTube videos and flash content. You'll get prompted to install it. Just follow the instructions and you're done.

Ubuntu forums is a great source of information for new users. Answers to questions can usually be found here. Google is, as always, your best weapon.

That's about all I can help you with, sorry.

---

### Post by nhasian on 2009-01-09
you can install programs from the add/remove button under Applications or directly from a terminal (applications->Accessories->Terminal) and copy/paste the code:

```
sudo apt-get install thunderbird
```

to install flash:

```
sudo apt-get install adobe-flashplugin
```

and you dont need to worry about codecs with the VLC media player:

```
sudo apt-get install vlc
```

---

### Post by nothingspecial on 2009-01-09
Just follow [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") post and you`ll be fine.
Make sure you do the right instructions for your version of ubuntu.
All you got to do is copy and paste

---

### Post by computermacgyver on 2009-01-09
Many programs can be installed via the software repositories (Applciations->Add/Remove...). This is often a good idea because these programs have been tested with Ubuntu and found to work well. In addition, you will recieve updates as they are released. You can download directly from products' websites for the latest versions if you need a later version than what is currently in the repositories.

You should be prompted for codecs (compression-decompression files to tell the computer how to read formats) as they are needed. Same with flash as BlakeM wrote.

If you have specific challenges as you get started please search the forums here or post any issues and someone will be glad to help.

You should have totem installed as a default video player and rhythmbox as a mp3/music library. These work pretty well for beginning. 

I was just using GoogleDocs today on Ubuntu with no problems.

Welcome to Ubuntu, we're glad you've made the switch.

---

### Post by hashimoto on 2009-01-09
I recommend that you read Psychocat's:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by ibizatunes on 2009-01-09
To play dvd install medibuntu
[www.medibuntu.org/](www.medibuntu.org/)

That will also allow you to run adobe reader, google earth, picasa, and skype

i would also install ubuntu restricted - to play java and flash etc

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by blazemore on 2009-01-09
The following command will allow for MP3, flash, java etc:
```
sudo apt-get install ubuntu-restricted-extras -y
```
To accept the terms and conditions, the TAB key will come in useful... You'll find out what I mean.

---

### Post by hyper_ch on 2009-01-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

