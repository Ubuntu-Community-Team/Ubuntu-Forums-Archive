---
title: "MythTV: How do I USE it??"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-05
hi guys! I just downloaded mythTV (front end and backend). I have no idea how to use it.

I have a usb TV Tuner and an antenna. Myth TV doesn't seem to recognize that they are there, though. When I hit "Whatch TV" it directs me back to the menu screen by saying that I have no recordings. When I ask for a program guide it says there are none. 

I'm confused. I tried to open the backend for setup and it is all gibberish to me. 

Can anyone explain how this works?

---

### Post by jaythedogg on 2011-01-05
> **maryalesia said:**
> hi guys! I just downloaded mythTV (front end and backend). I have no idea how to use it.

I have a usb TV Tuner and an antenna. Myth TV doesn't seem to recognize that they are there, though. When I hit "Whatch TV" it directs me back to the menu screen by saying that I have no recordings. When I ask for a program guide it says there are none. 

I'm confused. I tried to open the backend for setup and it is all gibberish to me. 

Can anyone explain how this works?

I have no idea how to fix this, however I did find some help info here:

[https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

Then if all else fails, try doing a Google Search with Ubuntu MythTV [name of tuner hardware here] support

See if that turns anything up.

Hope this helps!

---

### Post by maryalesia on 2011-01-05
thanks for replying, but those guides read like chinese to me. :(

I uninstalled mythTV ... it just doesn't seem to be very user-friendly to the uninitiated. :( I guess I'll be returning the tuner, too.

---

### Post by srs5694 on 2011-01-05
MythTV can be difficult to set up; however, it's very powerful and reasonably user-friendly once it's installed.

You haven't said precisely what you hope to use it for. Be aware that MythTV is a complete DVR system. That is, it's best used something like TiVo, to seek out and record TV shows for viewing at your convenience, rather than for watching live TV. If you just want to watch live TV, there are much simpler programs that will do the job, like [tvtime.](http://tvtime.sourceforge.net/) If you've never used a true DVR, be aware that it fundamentally transforms TV. With a DVR, TV becomes something like a magazine subscription; you're no longer chained to the TV schedule, and you can watch what you want when you want, within the limits of whatever you've recorded.

If you want to continue trying with MythTV, you might try using a MythTV-centric distribution, such as [Mythbuntu](http://www.mythbuntu.org/) or [Mythdora.](http://www.mythdora.com/) These come with some of the necessary tweaking already done.

If you find even one of these distributions and MythTV too daunting, there are Windows-based DVR packages you could try. I don't have any experience with them, but they might be worth investigating.

---

### Post by Chronon on 2011-01-06
SMPlayer and Kaffeine both work well for me for watching TV.  I tried installing MythTV once and never quite got it set up properly either.

---

### Post by mastablasta on 2011-01-06
also plenty TV tunners are incompatible with linux. MythTV wiki & Mythbuntu website have the compatible ones listed.
 
mine for example was recognise but didn't work no matter what. eventhough people reported it to work well. after spending a few weekends searching and trying to set it up with different programmes i gave up on the tuner.

---

### Post by maryalesia on 2011-01-06
I intend to use it as a DVR. We have three fios DVRs at my house but as I am actively watching over 15 tv shows (i might have a tiny addiction problem) conflicts arise quite often. I rarely watch live TV because most of the TV I do watch is through the internet on sites of ... questionable legality.

I have NO IDEA how to set it up, and after buying the tuner (hippauge) I realized it came with software only compatible with vista. (Oddly, the computer on the front packaging was a macbook pro. hmm.:confused:)

I really wish it was capable of just detecting the hardware itself ... I'm lazy and computer illiterate. I haven't returned the tuner yet though, so if anyone has any (kindergarten simple) ways of explaining this to me ... go for it.

---

### Post by maryalesia on 2011-01-06
> **srs5694 said:**
> If you want to continue trying with MythTV, you might try using a MythTV-centric distribution, such as [Mythbuntu](http://www.mythbuntu.org/) or 

I installed the mythbuntu control center, and I'm still a bit confused. What is the difference between a primary back-end and a secondary back-end? :confused:

---

### Post by eriktheblu on 2011-01-06
There is no simple way to explain MythTV, because MythTV is not simple. It takes me several days to get it running from a fresh install, but is well worth it.

The basic steps as are roughly:
Install
Get the OS to recognize your hardware
Configure the backend based on your signal type and other preferences
Add your capture device to the backend and configure
Scan for channel frequencies
Import schedule listings (I think optional, but recommended)

Lot of work, but definitely worthwhile. Once it is properly configured, scheduling, recording, and playback are quite intuitive.

Check the MythTV wiki for the best advice [http://www.mythtv.org/wiki/User_Manual:Index]("http://www.mythtv.org/wiki/User_Manual:Index")

---

### Post by eriktheblu on 2011-01-06
> **maryalesia said:**
> I installed the mythbuntu control center, and I'm still a bit confused. What is the difference between a primary back-end and a secondary back-end? :confused:
Only one machine should be the primary backend. It will dictate to other backends who is recording what. If you only have 1 backend, it will be primary.

---

### Post by maryalesia on 2011-01-06
> **Chronon said:**
> SMPlayer and Kaffeine both work well for me for watching TV.  I tried installing MythTV once and never quite got it set up properly either.

how were you able to watch TV through SMplayer? I have no idea how to even begin setting that up  ...

---

### Post by maryalesia on 2011-01-06
> **eriktheblu said:**
> There is no simple way to explain MythTV, because MythTV is not simple. It takes me several days to get it running from a fresh install, but is well worth it.


while I haven't seen it up and running, I don't think anything is worth that amount of work. MythTV just seems to be a huge pain in the ***. I uninstalled and am returning the tuner.

It was worth a try, but I'm going back to a life of digital piracy.

---

### Post by albert s on 2011-01-06
try ME TV
its in the software centre,
much easier.

---

### Post by Chronon on 2011-01-06
> **maryalesia said:**
> how were you able to watch TV through SMplayer? I have no idea how to even begin setting that up  ...

I believe you need to scan for channels, resulting in a channels.conf that mplayer reads to tune the TV tuner.  The file should be stored at "~/.mplayer/channels.conf".

I used a scan program available in the dvb-utils package but I did it quite a while ago.  I'll try to find a link to some proper instructions when I get home.

Apparently, Kaffeine works without an existing channels.conf but I dont' know how you feel about installing KDE apps.

---

