---
title: "Going crazy trying to get Quicktime support"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by capleton on 2009-05-14
I can't play .mov in firefox, nor can I play on my desktop.  And this has become a serious issue now since I am taking a summer course where the teacher provides lectures in .mov movies.

I followed the [sticky]("http://ubuntuforums.org/showthread.php?t=766683"), including the troubleshooting at the end, but still no help.  For .mov on the desktop it says "no playable stream found" in totem, and doesn't work in mplayer or VLC either.  And online, it just says "click here for the latest version of quicktime."

I'm using Hardy Heron

Someone Help Please!!!!!!!!!!!!!!

](*,)

---

### Post by stephanvaningen on 2009-05-14
If I do this, I can play .mov-files:
```
sudo su
*(enter password)*

wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

apt-get update
apt-get install medibuntu-keyring
apt-get update

apt-get install libdvdcss2 w32codecs gstreamer0.10-plugins-ugly-multiverse ffmpeg
*(replace 32 by 64 if applicable)*
exit

```

---

### Post by capleton on 2009-05-14
Thanks for the reply, stephanvaningen

But it's still not working.  :-(  

I tried going to [this trailer]("http://www.apple.com/trailers/wb/terminatorsalvation/medium2.html")

What can I do?

---

### Post by cneil on 2009-05-14
It works fine for me.  Make sure that you are using totem-plugin-viewer 2.22.1 and the Browser Plugin using Gstreamer 0.10.18

You can right click on the video and select about to see what you're trying to use.

Cullen Hartley
[www.cullenhartley.com](www.cullenhartley.com)

---

### Post by marco123 on 2009-05-14
> **capleton said:**
> Thanks for the reply, stephanvaningen

But it's still not working.  :-(  

I tried going to [this trailer]("http://www.apple.com/trailers/wb/terminatorsalvation/medium2.html")

What can I do?

Works fine for me too.

All I do after a clean install is:

> sudo apt-get install ubuntu-restricted-extras

I'm pretty sure that this works in Hardy too.

Cheers, Marco.

---

### Post by capleton on 2009-05-14
> 
All I do after a clean install is:

Quote:
sudo apt-get install ubuntu-restricted-extras

I'm pretty sure that this works in Hardy too.

Cheers, Marco. 

Apt-get is telling me that I definitely have the restricted extras installed.  Could the problem be that there is a conflict somewhere?  If so how could I find and resolve it?   I would really hate to have to do a fresh install (although it would give me a chance to try out "ultimate ubuntu" :) )

> Re: Going crazy trying to get Quicktime support
It works fine for me. Make sure that you are using totem-plugin-viewer 2.22.1 and the Browser Plugin using Gstreamer 0.10.18

You can right click on the video and select about to see what you're trying to use.

I attached a photo of what happens when I try to watch [this trailer]("http://www.apple.com/trailers/disney/up/teaser_medium.html").

I also wonder if it's a problem that can be resolved in Firefox>Edit>Preferences>Applications or in firefox preferences in general.  I also attached a pic of my current settings.  my options are the two listed there, "save file", "always ask", and "other."  I tried using "always ask" and it never asked; I tried "other" but I don't know where to find the other plugins that could play .mov, and save file doesn't work either.

Any suggestions?


[ATTACH]113750[/ATTACH]

[ATTACH]113751[/ATTACH]

---

### Post by capleton on 2009-05-14
bump  :frown:

---

### Post by ainsworth_t on 2009-05-14
Try installing vlc along with mozilla-plugin-vlc from Synaptic or the command line: ```
sudo apt-get install vlc mozilla-plugin-vlc
```

---

### Post by capleton on 2009-05-14
Thanks ainsworth,

I re-installed VLC and installed the plugin, but now I can't figure out how to make Firefox use the VLC plugin instead of the other ones.  VLC doesn't appear in Firefox>Edit>Preferences>Applications


](*,)

---

### Post by Joeb454 on 2009-05-14
Install [libxine1-all-plugins](apt://libxine1-all-plugins) and see if that works :)

That's all I install (along with Ubuntu restricted extras) and that trailer plays fine for me :)

```
sudo apt-get install libxine1-all-plugins
```

---

### Post by kanikilu on 2009-05-14
That trailer works for me, although interestingly, apparently I don't have the ubuntu-restricted-extras packages installed. I do have the "pitfdll", "bad" and "ugly" gstreamer packages installed, though. Not sure if that makes a difference...

---

### Post by sloggerkhan on 2009-05-14
I prefer to use the mplayer browser plugin. To get any plugin to work, look in 
tools > add-ons > plugins
in firefox.

If you have a mix there, some will overide others. Disable all of them except the ones you actually want to use. In my case I disable all of the gstreamer ones and leave the mplayer plugin enabled.

---

### Post by capleton on 2009-05-14
Well, I've tried it all, and i'm still getting the same problem.

A bit fed up at this point.

On the brighter side I guess that dusty Windows partition i kept on my hard disk will actually be useful.  It's too bad though.  I was hoping to get rid of it on my next install.

I think in the next month or so I'll make the move up to Jaunty and start fresh.  In the meantime... back to windoze:cry:

---

### Post by freeman2000 on 2009-05-15
I have all that stuff installed and the site didn't work for me at first.  I had to disable the "NoScript" plugin to Firefox, and then it worked.  Don't know if that will help you.  Good luck.

---

