---
title: "Audio dropping out: SMB Edgy -&gt; XP (MP3)"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by marx2k on 2006-11-21
When I mount a shared samba folder from my wireless edgy box to this XP box, I am able to stream MP3s without any problems except one:

Every few minutes, the sound will cut out for 1/2 second to 1 second.  I can't tell if it's rebuffering or what.  With 128kbps mp3's, this really shouldn't be a problem.

Does anyone know how I would go about troubleshooting this issue?

Here's the IFConfig from the Edgy box:
```

ath0      Link encap:Ethernet  HWaddr 00:11:50:D4:FD:E8
          inet addr:192.168.11.5  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fed4:fde8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:615015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:636677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:427363915 (407.5 MiB)  TX bytes:556402420 (530.6 MiB)

eth0      Link encap:Ethernet  HWaddr 00:03:47:FE:1D:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:317514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:386050582 (368.1 MiB)  TX bytes:386050582 (368.1 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-50-D4-FD-E8-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4801800 errors:0 dropped:0 overruns:0 frame:979746
          TX packets:660222 errors:79 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:824676882 (786.4 MiB)  TX bytes:571575742 (545.0 MiB)
          Interrupt:193 Memory:f8a40000-f8a50000


```

---

### Post by marx2k on 2006-11-21
Also the iwconfig:
```

ath0      IEEE 802.11g  ESSID:"000740B6F60A"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:40:C4:3B:5E
          Bit Rate:48 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
          Rx invalid nwid:1604292  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by marx2k on 2006-11-22
So no one else has had this problem while streaming MP3 audio over a home LAN connection??

---

### Post by m47h3us on 2006-11-23
audio stream dont work at all on my computer videos do but not mp3s or **** :(

---

### Post by marx2k on 2006-11-23
So youre able to stream video form one computer to another flawlessly but not mp3? 

Are you able to play mp3 locally on the computer thats having issues? Are you sure its not just a codec issue?

---

### Post by cmileto on 2006-11-28
works okay for me. Ony thing I have different is some kde leftover from before edgy. Im assuming mp3's play fine local?

---

### Post by marx2k on 2006-11-28
MP3s play fine locally, yes. Im trying to figure out a good way to test if the wireless adapter is dropping at certain periods and why but I havent figure out a good way of testing that out.

I would need either a low or high steady stream that also marks when packets drop and for what length of time.

I wonder if there's a program to test that or if there's a good way to set that up?

Any ideas?:confused:

---

### Post by vroetman on 2006-11-28
I've been having the same problem with my mp3's over SMB over wireless.  Actually, I've found the whole SMB filesystem to lag somewhat, even with bash tab-completion.  It tempts me to try nfs instead.  The system monitor shows very little network activity (which makes sense).  I wonder if the audio players don't cache very much since they assumes it's a local filesystem.  I also sometimes have dropouts of the wireless connection (maybe from cordless phones at the neighbor's house?), so that could certainly be a factor.

---

### Post by marx2k on 2006-11-30
What Ive noticed is that WinAmp in XP, even though it has dropouts when streaming over my SMB server from the edgy box, continues streaming.  The pause is usually half a second.  As annoying as that is, it's a lot less annoying than when Beep Media Player, VLC or any other media player I use in edgy just drops the stream completely and I have to hit play again and start the track over again.

In lieu of fixing the dropout problem, is there a way to have the players NOT just totally drop the stream?

I tried to get Beep media player to up the buffer rate in the AVLS output plugin from 500ms to 1500ms and that didnt seem to help at all.

---

### Post by vroetman on 2006-11-30
I'm not sure how to answer your questions, but I got sick of it and started looking for alternatives.

[Jinzora]("http://www.jinzora.org/") looks pretty good and then you can use standard streaming from any app, but I didn't want to take the time setting up apache on my nslu2 right now, so opted for mt-daapd (iTunes music sharing daemon), which worked really well.

I tried Banshee, and had to deal with [minor avahi problems]("http://ubuntuforums.org/showthread.php?t=252925"), but it crashed when processing all the songs on my server, so I switched to Rhythmbox, which worked great, as did Java based [Get It Together]("http://getittogether.sourceforge.net/").

I cannot get my Windows iTunes to work with it for some reason, but Get It Together works just fine there.  And it seems to work much better than sharing via SMB.

So this doesn't really answer the questions, but it's what I did to do what I wanted.  I still get drop-outs, and maybe the network is more stable today, but it's definitely better than yesterday.

---

### Post by marx2k on 2006-11-30
Im going to try to use RhythmBox .. I have somewhere in the vicinity of 500GB of MP3s.. it's kind of ridiculous.. so Im guessing maybe I should just set RhythmBox to catalogue that overnight....

---

### Post by marx2k on 2006-11-30
Well, Im in the middle of cataloging my music over an SMB connection..

Im at ~12.5K songs now and RhythmBox dropped my available mem from 1 gigh to 180Megs and is hovering at around 180 while cataloging... I hope it releases it when it's done what it's doing..

---

### Post by marx2k on 2006-11-30
You can definately tell the wireless drops sometimes even while this process is going because RhythmBox will be doing its' thing and then all of a sudden.. boom.. nothing for a few seconds...it just ... pauses.  Then all of a sudden it will pick up again

---

### Post by marx2k on 2006-11-30
Still going... Up to 35.5K songs now... 
It seems to give RAM back as it goes.. Im at 607MB RAM now.

Will report when it ends

---

### Post by marx2k on 2006-11-30
Ok it finished and released all the RAM it was eating up, thankfully.

So Im currently testing streaming music through it.  While we're on the subject of it though, is there a program for Ubuntu that will equalize my sound with presets? (Like WinAmp's equalizer but set for systemwide)?

---

### Post by marx2k on 2006-12-01
Looks like RhythmBox totally did the trick.. Im 26 minutes into a continuous album (each track is 3 minutes in length) and so far, absolutely NO breaks...

Lovin' it!

Now all I need is a systemwide equalizer to make these 2 computer speakers sound a little better.

---

### Post by hl2040 on 2006-12-04
I have the same problem under edgy. Using amarok under gnome, I am playing mp3s over a wired network on a samba exported filesystem hosted by RAID. Just listed all those things because the original poster mentioned the question of it having something to do with wireless. I think the only things I have in common with him is mp3 and a samba client :-)

I think it must be something related to the samba client. I also get the problem when watching videos over the network as well. Either the samba server is under-powered or there's something funny going on with samba.

[This post]("http://www.google.com/search?q=samba+pause&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a") on the samba mailing list might be related...

One interesting point after googling this for awhile is that it seems that Windows only opens one connection to a samba server; thus multiple file requests can block on each other. So in the instance that this is happening under linux, maybe Ubuntu "pings" so-to-speak the samba mount periodically, and makes the mount block for a half or full second, resulting in the drop of audio.

Or maybe not, since one user reported that increasing his buffer size didn't help any.

---

### Post by marx2k on 2006-12-06
That sounds about right.

I've even installed XP via VMWare and stream MP3s through Windows Media Player in XP *IN* VMWare under Edgy and have no problems streaming MP3's.

How weird is that!

---

