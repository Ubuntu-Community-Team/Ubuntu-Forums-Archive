---
title: "video playback problems"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by misterbiskits on 2010-05-26
Hi everyone, I am a brand new ubuntu user.  I have played around with ubuntu in previous versions but never really tried to accomplish anything with it until now.

I am struggling to get a media center/htpc set up here at home.  My system specs are:
Ubuntu 32 bit
Athlon 64 3200+
2 GB RAM
[Gigabyte motherboard]("http://www.ncix.com/products/index.php?sku=44632") with onboard ATI graphics 
and using the proprietary ATI driver.  
Box is connected to my tv via hdmi (video & sound)
Screen resolution is 720

Avi or MKV videos play well enough using mplayer or VLC. 
When I try to play these same files using elisa, xbmc, or boxee the video does not play.  I get sound, the software even correctly makes a thumbnail (preview) out of the video file, but the video portion of the playback does not work - what I get is full screen flickering of solid colours, usually brownish or tan tones.

I am not sure what I can do here...it's odd that one software plays it fine while another does not.  Any advice or explanation would be appreciated.

---

### Post by anewguy on 2010-05-26
Did you install all of the gstreamer add-ins and the ubuntu-restricted-extras packages?

Dave ;)

---

### Post by misterbiskits on 2010-05-26
thanks for pointing me in the right direction.  i installed the restricted extras package (to no effect), and then did a search for gstreamer.  Not knowing which of the very many results would do the trick, I went hog wild and installed everything that looked like it had the slightest chance of being related.  I'm sure I installed a lot I don't need =)

video now plays in enna (i incorrectly called it elisa in my first post) and xbmc.  it didn't work for boxee but maybe i need to install something else.

thanks again.

---

### Post by misterbiskits on 2010-05-26
double post to say I found[ someone with exactly the same problem]("http://forums.boxee.tv/showthread.php?t=17619") with playback in boxee, so I came here to link to the solution.

Isn't linux great!

---

