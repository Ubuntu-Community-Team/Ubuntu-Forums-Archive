---
title: "Windows Media Player compatible plugin not found..."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by SwooshOU on 2008-12-18
I get an error message saying something like I need to install a Windows Media Player compatible plugin.  I understand that VLC can do that so I think I installed it.  But i'm still getting the message.

If VLC is the right plugin to use, in simple terms, how do I install it and then make sure Firefox uses the VLC plugin instead of the plugin that it is attempting to use and failing.

By the way, the site I am trying to connect to is the link called "Live Radar" on this site...

[http://www.koco.com/weather/grid.html](http://www.koco.com/weather/grid.html)

Can this be done?

Thanks

---

### Post by linuxguymarshall on 2008-12-18
Works fine for me. Do you have flash installed?

---

### Post by Titan8990 on 2008-12-18
Worked fine for me as well and I have not installed ANY codecs and am using gnash instead of adobe.

---

### Post by SwooshOU on 2008-12-18
> **linuxguymarshall said:**
> Works fine for me. Do you have flash installed?

I'm able to view YouTube videos... and those are flash, right?

I installed Ubuntu a few days ago so I'm completely new.

---

### Post by lovelyvik293 on 2008-12-18
I have adobe flash player installed and it's working great.
You can install the flash plugin from add or remove.

---

### Post by Titan8990 on 2008-12-18
Use prtscn to take a screenshot of the error and post it here.

---

### Post by SwooshOU on 2008-12-18
> **Titan8990 said:**
> Use prtscn to take a screenshot of the error and post it here.

I'm at work, but I will try doing that later this afternoon.

---

### Post by SwooshOU on 2008-12-18
I wanted to add, I can see the first part of the video... It's an advertisement.  When the ad is done, it loads a different type of format for the live radar.  That is the one I'm getting the message on.  The message says that I need a windows media compatible player and suggests downloading some plugins for windows or some plugins for Mac.

---

### Post by philinux on 2008-12-18
To get it to work I had to disable adblock plus. And yes it's flash based. although when I right click I got a moonlight settings box(same as windows silverlight).

---

### Post by SwooshOU on 2008-12-18
> **philinux said:**
> To get it to work I had to disable adblock plus. And yes it's flash based. although when I right click I got a moonlight settings box(same as windows silverlight).

Ah, I do have adblock.  I'll disable that and see if that works.

---

### Post by SwooshOU on 2008-12-18
I disabled adblock, that didn't work.

I disabled all video plugins except shockwave and while it loaded the video ad on the front end, it didn't load the radar video.

Here's the message I get...

---

### Post by SwooshOU on 2008-12-19
I still get the error when the radar tries to load.  Of course the flash ad before it loads just fine.

Here is what the application tab in my firefox preferences looks like...

---

### Post by philinux on 2008-12-19
The only thing I can think of is the silverlight plugin. As I said before I when i right clicked I got a silverlight preferences dialog box.

[http://www.infoq.com/news/2008/12/Moonlight-Beta-1](http://www.infoq.com/news/2008/12/Moonlight-Beta-1)

Click the link [http://www.go-mono.com/archive/moonlight-plugins/latest/novell-moonlight-1.0-i586.xpi](http://www.go-mono.com/archive/moonlight-plugins/latest/novell-moonlight-1.0-i586.xpi)

---

### Post by SwooshOU on 2008-12-19
> **philinux said:**
> The only thing I can think of is the silverlight plugin. As I said before I when i right clicked I got a silverlight preferences dialog box.

[http://www.infoq.com/news/2008/12/Moonlight-Beta-1](http://www.infoq.com/news/2008/12/Moonlight-Beta-1)

Click the link [http://www.go-mono.com/archive/moonlight-plugins/latest/novell-moonlight-1.0-i586.xpi](http://www.go-mono.com/archive/moonlight-plugins/latest/novell-moonlight-1.0-i586.xpi)

OK, now we're getting somewhere.

Firefox installed that plugin.  And now when I load the page, the radar actually loads.  However, it only displays one frame.  It's not moving.  I right clicked and brought up the properties.  The strange thing is that the framerate it shows is around 22 frames per second and it updates live in the properties window.  However, the video still just shows the one frame.

Any suggestions?

---

### Post by philinux on 2008-12-19
Yep same here. :confused:

---

### Post by SwooshOU on 2008-12-19
So, why would the video properties indicate that the video is actually playing when I don't see any motion at all on the screen?

Any tips?

---

### Post by SwooshOU on 2008-12-21
Well, I found the source link for the actual video file and manually opened it up in a video player.  It plays fine outside of the browser.  It just gets hung up in Firefox.

I guess that's what I"m gonna have to do.

---

### Post by SwooshOU on 2008-12-23
So, I've disabled all the media plugins that could pay a .asx or .asf file in Firefox except moonlight.  And it still hangs on the first frame of the radar.

Like I said, I can copy the link and watch the stream in a standalone video player, however, as others have been able to get this same link to work on their computers, I would like to try to get mine working.

Again, the link in question is:

[http://www.koco.com/weather/grid.html#HEARSTWX=http%3A//www.koco.com/weather/4071149/liveradar.html%3Fqs%3D%3Blongname%3DLive%3A%2520Advantage%2520Doppler%2520HD%3Bshortname%3DLive%2520Radar](http://www.koco.com/weather/grid.html#HEARSTWX=http%3A//www.koco.com/weather/4071149/liveradar.html%3Fqs%3D%3Blongname%3DLive%3A%2520Advantage%2520Doppler%2520HD%3Bshortname%3DLive%2520Radar)

Perhaps there are conflicting extensions, add-ons or plugins?

Thanks.

---

