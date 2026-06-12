---
title: "Can't see chromecast on my wireless network"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by ManiacDan on 2015-05-27
Hello all,

I recently bought a Chromecast (which is not only awesome but Amazon has them for less than $30 now!) and it works with every Android and Windows device on my network...but not my Ubuntu box.

I'm running 12.04 and haven't done many modifications to it.  I don't believe I have a firewall installed (though it's possible since IT has taken my computer a couple of times).

I found [this thread](http://askubuntu.com/questions/324236/how-can-i-use-chromecast) on askubuntu but it's a couple years old and I don't want to start mucking with iptables unless someone more modern recommends it.

Google has some [basic troubleshooting](https://support.google.com/chromecast/answer/3249268?rd=1), but the most a Linux user will get out of that is "it's a problem with Linux."  

Any thoughts?  Has someone gotten ChromeCast working properly?

Thanks,
Dan

---

### Post by TheFu on 2015-05-27
You need a **DLNA client** to go with the **DLNA Renderer** that is chromecast. I have not found **any** DLNA clients for Linux that worked. Sorry.  VLC apparently worked a few yrs ago. It doesn't work anymore, at least not anytime I've tried it.

OTOH, any Android device with 1 of 20 different DLNA client apps will work fine. I use bubbleUPnP (free).

Had a chromecast for 18+ months now and have found a use for it about 3 times - for less than 4 hrs total. The limited decoding of older codecs makes it next to worthless.  OTOH, if you have a streaming service that it supports, it might be a good-enough option.  It **does not work** with Amazon Prime Streaming. It does not decode MPEG, AVI, XVID, or anything other than h.264/aac - so all my TV recordings with h.264/AC3 are worthless (without transcoding the audio first). Can't watch iZombies recorded last night. Boooo!

I knew all of this before getting the chromecast - hoped it would just be useful for playing youtube videos, but even the old official 2012 Olympics refuse to play on the chromecast. pfffft.

Sorry - I'm not a happy customer.  Ended up getting a Roku which supports Amazon Prime and can be controlled by android or a real remote. For APV, Roku is the only real choice and has the same issue with transcoding and extremely limited A/V codec support that the chromecast has.  

BTW, I have a plex server, but it doesn't have the CPU capacity to transcode on-the-fly to other formats needed by either of these devices. Plan to swap it out for a $120 newer system which should handle that easily. Just need to put the parts together and swap the HDD from the old box. 

IPtables is the current firewall on Linux. You can use any GUI tool you like as an interface to iptables. Just be consistent and use 1 tool only. Not sure how this matters for a chromecast. The DLNA client just needs to send commands TO the chromecast. It isn't exactly clear how you want to use ubuntu with the chromecast. Maybe you could explain?

Sadly, none of this helps you with a DLNA client on Linux. ;(
> 
"it works with every Android and Windows device on my network...but not my Ubuntu box."
Perhaps if you clearly explained what you mean by this?  Perhaps you don't want a DLNA client to control the chromecast, but want a DLNA server to feed it content?  Something like miniDLNA or Plex Server?

---

### Post by kerry_s on 2015-05-27
are you using google chrome with the extension ?

[https://chrome.google.com/webstore/detail/google-cast/boadgeojelhgndaghljhdicfkmllpafd?hl=en-US](https://chrome.google.com/webstore/detail/google-cast/boadgeojelhgndaghljhdicfkmllpafd?hl=en-US)

there's also a beta version.

my son stole my chromecast, so i grabbed a fire tv stick when they first came out, been using that instead

---

### Post by ManiacDan on 2015-06-09
Sorry for the delay guys, I actually forgot I had posted here until just now.

I am using chrome with the extension and it has seen the chromecast one time ever (though I was busy at the time so I didn't experiment).  I'm talking specifically about the official Chromecast extension to Chrome.  It was that extension's help document I linked to.  that extension can't see the chromecast.

I tend to use it for streaming/controlling Netflix and Pandora mostly (Pandora with the screen off, obviously).  I have used it briefly to stream movies and pictures not officially supported using the 'cast screen' feature, but sharing an actual tab on a real computer would be great.  It doesn't seem like it's in the cards though, from what I hear about overall support.

---

### Post by kerry_s on 2015-06-09
my son says he gave up trying to use the computer for chromecast, to iffy.
he said it's just so much easier to use his ipad mini & apps.

---

### Post by TheFu on 2015-06-09
For me, using Android to control the chromecast makes sense nothing else. I haven't found any good way to control a chromecast from any computer - even running Plex server.

This board allows you to be notified via email when anyone responds to a thread you created. Highly recommended.

---

### Post by ManiacDan on 2015-06-10
Yeah my notifications got screwed up when I switched to SSO all those years ago and I never bothered to fix it.  I'm trying to wean myself from being a forum junkie.

I've found that Kerry's solution is going to be the only thing that works for me: Uninstall the chromecast extension and pretend that feature isn't on the side of the box.  Android streaming (especially pandora) only works half the time anyway, I've had to unplug my chromecast more than I used to have to unplug my AppleTV.  Now I know why the price dropped out on the thing, it's not worth the $32 I paid for it.  Had I paid $100 I would be livid.

---

### Post by TheFu on 2015-06-10
Have to agree the chromecast is a toy. Got it for Xmas 18 months ago and have used it about 20 hrs total in all that time.

Spent years trying to use less-than-HTPC solutions for media playback. Found it frustrating since each had incompatible formats. Finally had an old Atom Asus Eee and loaded XBMC onto.  Gone were the incompatible formats - that thing could play anything with 600p or less resolution, but audio was only stereo. Still, I was addicted.

As we all switched to hidef, the lack of good video codec support and terrible drivers for the Eee convinced me to get something with good GPU drivers that had video and audio codec support built into the hardware for hidef content.  A $150 AMD E350 APU system solved that and I've been mostly happy the last .... 3 yrs.  It was a bargain and cheap. Wish I'd have bought 2 more at the time.  The HTPC uses a picoPSU, which is completely silent.

Then I forced to get a HW player for Amazon prime support and only the Roku was an option at the time. The incompatible format issues started all over again, since Roku is extremely picky about playback codecs.

Added a plex server to the E350 box and found the APU didn't have the power to transcode hidef video into the required format for the Roku or Android or Chromecast or ... (insert your current player).  The really sad thing is that the video **IS** encoded with the correct codec for these devices, but the audio is AC3 which none of them support. Transcoding just the audio through plex to AAC has eluded me so far. 

I have a solution for that, but just haven't gotten around to building it out yet. All the parts are here, but need to free up a case first. It has a Haswell Pentium CPU with Intel GPU, so the audio/video stuff should be handled nicely. We'll see.

Good luck to you.

---

