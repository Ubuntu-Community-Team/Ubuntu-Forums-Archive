---
title: "Thin client problem + videos"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by LucasLinard on 2006-07-16
Hi folks,
I'm sorry if what I'm asking is on the foirum already (i didn't find).
I have a AMD K6-2 500MHZ 128MB-RAM. It is not being used. I have a AMD AThlon xp 2000+ 1gb-RAM at my living room. 
1-Can Anyone send a solution on How can I use my k6-2 as a thin client?
2-What can a thinclient realy do? Play mp3, watch divx videos, web browse...???
3-I've found some thin client solutions, for windows and linux, witch way should I go?
4-FreeNX???
5-Any way to play divX videos on my k6-2 500mhz??

---

### Post by simonn on 2006-07-16
I have not done the thin client as media center thing, although I have looked into it several times and quite often run remote X sessions on my iBook running OSX to my Ubuntu box.

Audio is the main stumbling block.

If you are running a thin clent then everything actually running on the server, so sound will actually come from the server. The reason why this does not happen for video is that the X server forwards it to the X client on the thin client. So you also need some kind of audio client/server setup.

There is such a thing, NAS ([http://www.radscan.com/nas.html)](http://www.radscan.com/nas.html)), but I have heard not so good reports about it for video i.e. audio by itself is fine, but when playing videos sync can appraently be very BAD.

I have toyed with various ideas, until I decided, at the moment, it was easier just to plug my iBook into the TV - espeially as we really do not watch that much TV anyway :).

Perhaps the most promising was to hardwire the audio output of my PC to my TV/Hifi in the living room, either by using cables or one of those remote extender thingies (except living in a unit/flat/apartment the remote extender thingies have FAR too much interferance from cordless phones, wireless networks etc).

I am currently looking into is using myth/minimyth, although that will not help you as you need a VIA itx or using multiseat X (see [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)) using the TV as another monitor and hardwiring the video, through a monitor extender, and audio to the living room. The latter will screw up user switching (which we use a lot) though. It may end up easier just having the PC as a myth box and, again just using the iBook, when we want to watch recordings.

---

