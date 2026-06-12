---
title: "Rhythmbox not fetching album art?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Tahakki on 2010-01-25
I've got the plugin enabled and I'm definitely connected to the internet. The space where album art should be used to show a loading circle (on Hardy), but doesn't do anything here.

On a related note, are there any music players for Ubuntu that are actually really good? Rhythmbox is sparsely featured, Banshee's a bit slow and Songbird (while looking awesome) doesn't fit with GTK at all.

Help?

---

### Post by mbzn on 2010-01-25
Check your rhythmbox settings...(I'm not sure)
Have you tried amarok(it's a KDE app but liked by many)

---

### Post by llawwehttam on 2010-01-25
Hmm for me it can take a few minutes before it gets the artwork.

---

### Post by Tahakki on 2010-01-25
If I put a CD in it seems to get the art immediately, but playing from the library and it doesn't at all.

As for Amarok, I really need something that fits well with GTK. Banshee's almost perfect - just slow.

---

### Post by cptrohn on 2010-01-25
I have a large collection and got tired of messing with Amarok and Rythmbox's retrieval so I just go here.  [http://www.albumart.org/us/](http://www.albumart.org/us/) and find the album art I want and put it in the CD's folder after I rip it... that way I always have it anyway, Amarok automatically sees it, don't know about Rythmbox, but I imagine that it would.

---

### Post by maghoxfr on 2010-03-14
I have all the almbums art but rythmbox has a great delay when showing it, I really don't like it, I'm trying quod libet, it looks the same as Rythmbox, scans the library in a heartbeat and the album covers appear instanly...so long rythmbox. Songbird is great too.

---

### Post by kcleong on 2010-06-08
Album art is not showing in my collection when playing music. I think this is a 'show stopper'. Especially when you use Rhythmbox with an ipod, where it's kinda handy.

But I fixed it by using this plug-in:
[http://code.google.com/p/albumartsearch/]("http://code.google.com/p/albumartsearch/")

It searches album covers on Google images. You're presented a list of images. If you like one the image is draggable to the album art part (bottom left hand).

---

### Post by jeddycakes on 2010-10-02
I found that its a bit annoying getting album art to show, dare I say it, but its not as simple as say *whispers *iTunes*...but I have found a personal system to go about it.

First of all I installed this **script** :-

[CoverChooser]("http://gnome-look.org/content/show.php/CoverChooser?content=117330")

It works quite well, but on occasion crashes. I can live with that, however, lol.

Then I simply tag with Easytag (look in the software centre)

And Bobs your Uncle  :guitar:

Tag away!

---

### Post by jeddycakes on 2010-10-02
However, I like kcleong's approach, particularly as I use rhythmbox as my default player. Theres a raft of sweet plugins for it these days. If your not a fan of how Covergloobus does things it even has a simple plugin that does the same thing.

[Quick link to some awesome plugins]("http://www.omgubuntu.co.uk/tag/rhythmbox/")

Theres loads of stuff here :) really good blog for all things Ubuntu.

---

### Post by garyjmellor on 2011-02-16
Hi, I have this problem on Maverick 64-bit. I have Rhythmbox 0.13.1 and the plugin for artwork ('Cover art' checkbox in the 'Configure Plugins' dialog) is enabled. I have an active Internet connection. I haven't checked to see what happens if I play from a library but certainly running music directly through the ODD doesn't pickup album artwork. I had RHCP Stadium Arcadium playing for over an hour and in all that time it never found the artwork. If it was an obscure album I would be more forgiving. The same behaviour was also exhibited for Nirvana's 'In Utero' - over an hour of playback and no artwork displayed. Does anybody have any ideas before I report this as if I can solve it here that saves me taking up developer time with what is essentially something that is not critical to me but is 'nice to have'. My machine spec, if this is a factor, is in my signature. Thanks in advance.

---

### Post by PhilGil on 2011-02-16
Not sure what version of Rhythmbox y'all are using, but in version 0.12.8 you have to be logged in to last.fm for rhythmbox to display album art from the web.

---

### Post by plucky on 2011-02-16
> **garyjmellor said:**
> Hi, I have this problem on Maverick 64-bit. I have Rhythmbox 0.13.1 and the plugin for artwork ('Cover art' checkbox in the 'Configure Plugins' dialog) is enabled. I have an active Internet connection. I haven't checked to see what happens if I play from a library but certainly running music directly through the ODD doesn't pickup album artwork. I had RHCP Stadium Arcadium playing for over an hour and in all that time it never found the artwork. If it was an obscure album I would be more forgiving. The same behaviour was also exhibited for Nirvana's 'In Utero' - over an hour of playback and no artwork displayed. Does anybody have any ideas before I report this as if I can solve it here that saves me taking up developer time with what is essentially something that is not critical to me but is 'nice to have'. My machine spec, if this is a factor, is in my signature. Thanks in advance.

Try this [solution](http://www.webupd8.org/2010/10/rhythmbox-album-art-search-plugin.html) which I am using on 10.04 X86_64.The site says it will also work with 10.10.

Good Luck

---

### Post by garyjmellor on 2011-02-17
Thanks for the replies. According to the Rhythmbox documentation with the plugin enabled that I described in my earlier post it *should* get album artwork. No mention of having to be logged into last.fm for the version I'm running. Also, I don't want to use a third party plugin to do what should essentially be a feature that should work out of the box (but thank you for the suggestion all the same). I think I will raise it as a problem.

*EDIT* - I have added my issue and a debug output to Bug #209019 in Launchpad.

---

### Post by rlj1965 on 2011-03-25
> **plucky said:**
> Try this [solution](http://www.webupd8.org/2010/10/rhythmbox-album-art-search-plugin.html) which I am using on 10.04 X86_64.The site says it will also work with 10.10.

Good Luck

This was a great solution for me! Thanks!

---

