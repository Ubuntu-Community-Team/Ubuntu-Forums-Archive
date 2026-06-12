---
title: "General Observation on Video"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Brother_Marquis on 2009-04-11
Hi Folks,
Ubuntu n00b here again.   I'm loving Ubuntu so far and I'm getting comfortable using forums to get thinks working properly (like DVD playback, for instance).

My general observation is that the video playback in Ubuntu, whether on the web or in VLC Media Player, is grainy.  

When this laptop has WinXP, video wasn't a problem, so that rules out hardware.  Perhaps it's a driver issue, or perhaps I just don't know what I'm doing.

Anyway, is this just an Ubuntu thing or should I continue my research to optimize video?

Thanks,
George

---

### Post by 3rdalbum on 2009-04-11
In your video player, for instance VLC, take a look at the Video Output module (it's in the Preferences). It's probably on something like "Xv" or "XVideo" - try changing it to "X11" and see what happens.

---

### Post by Brother_Marquis on 2009-04-11
VLC was set to "default".  I changed to "X11" and it's a little better, thanks.  Will this change the video presentation for on-line clips as well?

---

### Post by Gen2ly on 2009-04-11
No, Brother_Marquis, probably not.  I don't think VLC has a browser plugin and i think Ubuntu uses gecko-mediaplayer?  You could try a different browser-plugin.  You'll want toremove the one already installed (better find out what it is first) and you can try mplayers for instance.  But better probably to use the one Ubuntu uses.  Could you give us a look at what you're seeing and a Link?

Also if you're playing DVD's with VLC you might want to look at the link below for playing DVD's with mplayer which i like quite a bit.

---

### Post by Paqman on 2009-04-11
> **Dirk.R.Gently said:**
> I don't think VLC has a browser plugin

[Behold!]("http://packages.ubuntu.com/intrepid/mozilla-plugin-vlc")

---

### Post by Gen2ly on 2009-04-11
Hey, what'ya know! :)

---

### Post by Brother_Marquis on 2009-04-12
OK, I used synaptic to download and install the VLC plugin.  I can play video from places like CNN.COM but can't play any trailers at QUICKTIME.COM.  'When I try to watch a trailer, a black box shows where the trailer should play.  When I click there, a message reads "video is loading...".  FireFox shows that both VLC and Gecko are installed & enabled. 

Any ideas?

---

### Post by Gen2ly on 2009-04-12
Quicktime trailers I know can be played with the gecko-mediaplayer, i use this on my laptop:

[http://packages.ubuntu.com/intrepid/gecko-mediaplayer](http://packages.ubuntu.com/intrepid/gecko-mediaplayer)

Videos do pretty well with it.  i recommend it.

---

### Post by Brother_Marquis on 2009-04-13
Hi Dirk,
Thanks for the help.  Not sure what to say...I have Gecko installed and enabled in FF.  Why wouldn't this work?

---

### Post by Gen2ly on 2009-04-13
Np.  if Gecko is installed, have you removed VLC?

---

### Post by Brother_Marquis on 2009-04-14
Um...I have VLC because Gecko wasn't working properly.  So, no, I haven't uninstalled VLC.  They're both installed.

---

### Post by Gen2ly on 2009-04-16
How about the vlc-plugin used by firefox?

---

### Post by billgoldberg on 2009-04-16
It's a driver issue.

Changing the output in vlc can help, but vlc can't play quicktime as you found out.

Just turn of compiz fusion if you need to watch a big video or update your graphics card driver to the latest one out.

---

