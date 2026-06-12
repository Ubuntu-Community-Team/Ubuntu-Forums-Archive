---
title: "Better Music Playing Application"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by xenogia on 2009-07-30
Hi guys just wondering what music application people recommend.  I felt that Rhythmbox was somewhat lacking and would love to know what peoples thoughts are?

---

### Post by nhasian on 2009-07-30
I really like [Songbird]("http://getsongbird.com/").

---

### Post by zeroseven0183 on 2009-07-30
Me, I like [Banshee Media Player]("http://banshee-project.org/") 

> Play your music and videos. Stay entertained and up to date with podcasts and video podcasts. Discover new music with Last.fm radio. Sync your G1 phone, iPod, and other devices. We think you'll love the new Banshee!

[IMG]http://banshee-project.org/theme/images/features/video.png[/IMG] Video Support - All the power of Banshee, now for your videos
[IMG]http://banshee-project.org/theme/images/features/g1.png[/IMG] Device Support - Sync your music and videos to your G1, iPod, or other device
[IMG]http://banshee-project.org/theme/images/features/podcast.png[/IMG] Podcast Support - Download or stream podcasts and video podcasts
[IMG]http://banshee-project.org/theme/images/features/lastfm.png[/IMG] Last.fm Streaming Radio - Listen to favorites and discover new music with free, streaming music from Last.fm
[IMG]http://banshee-project.org/theme/images/features/playqueue.png[/IMG] Play Queue - Queue up songs, videos, and podcasts on the fly
[IMG]http://banshee-project.org/theme/images/features/album.png[/IMG] Album Art - Artwork is automatically fetched as you listen
[IMG]http://banshee-project.org/theme/images/features/album.png[/IMG] Artist/Album Browser - Filter your library or playlist by selecting artists or albums
[IMG]http://banshee-project.org/theme/images/features/smartplaylist.png[/IMG] Powerful Search, Smart Playlists - Find exactly what you want, fast

---

### Post by ktrnka on 2009-07-30
I Second Songbird.

---

### Post by zeroseven0183 on 2009-07-30
And don't forget also VLC

---

### Post by synapsys on 2009-07-30
> **nhasian said:**
> I really like [Songbird]("http://getsongbird.com/").

+1 you can also get a nice pre-compiled .deb from [getdeb.net]("http://www.getdeb.net")

---

### Post by nhasian on 2009-07-30
VLC is one of the first things I install on a pc regardless of OS, i wouldnt recommend it as a music player.  

> **zeroseven0183 said:**
> And don't forget also VLC

---

### Post by xenogia on 2009-07-30
> **synapsys said:**
> +1 you can also get a nice pre-compiled .deb from [getdeb.net]("http://www.getdeb.net")

I downloaded and installed Songbird from the precompiled deb on Getdeb, and the program doesn't boot up. 

Says starting songbird and then just quits.

---

### Post by credobyte on 2009-07-30
Banshee ( features ) & Audacious ( simplicity ) :)

---

### Post by nhasian on 2009-07-30
try launching songbird from the terminal.  what error messages does it show in the terminal?

---

### Post by xenogia on 2009-07-30
> **nhasian said:**
> try launching songbird from the terminal.  what error messages does it show in the terminal?

```

*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f4ebabc87d0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f4ef2f81cb8]
/lib/libc.so.6(cfree+0x76)[0x7f4ef2f84276]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f4eb4c894ce]
/usr/lib/libvisual-0.4.so.0[0x7f4eb4c82646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f4eb4c827d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f4eb4c8f703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f4eb4eb0cb1]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd09a383]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7f4edd09af7d]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd0a69fb]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f4edd0a6b7e]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd05259b]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd052a09]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd052fd7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f4edd053568]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7f4eef350020]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f4edd051936]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f4edd051a23]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f4edaae1b04]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaae95e5]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0e9659f]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0e960e9]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaaf792b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaaf7958]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaaf7140]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaae802e]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f4edaae8601]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f4edaae9555]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0e9659f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f4ee010e613]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f4ee010e650]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f4ee010df32]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f4ee00f9154]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f4ee00f6729]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f4ee00f6b17]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0e76eba]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0e7738c]
/usr/share/Songbird/xulrunner/libxul.so[0x7f4ef0747f86]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7f4ef0745c57]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f4ef2f285a6]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 159371                             /usr/share/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:03 159371                             /usr/share/Songbird/songbird-bin
0170d000-0172e000 rw-p 0170d000 00:00 0                                  [heap]
7f4eb321b000-7f4eb321c000 r-xp 00000000 08:03 141016                     /usr/lib/tls/libnvidia-tls.so.180.44
7f4eb321c000-7f4eb331c000 ---p 00001000 08:03 141016                     /usr/lib/tls/libnvidia-tls.so.180.44
7f4eb331c000-7f4eb331d000 rw-p 00001000 08:03 141016                     /usr/lib/tls/libnvidia-tls.so.180.44
7f4eb4c70000-7f4eb4cad000 r-xp 00000000 08:03 10004                      /usr/lib/libvisual-0.4.so.0.0.0
7f4eb4cad000-7f4eb4eac000 ---p 0003d000 08:03 10004                      /usr/lib/libvisual-0.4.so.0.0.0
7f4eb4eac000-7f4eb4ead000 r--p 0003c000 08:03 10004                      /usr/lib/libvisual-0.4.so.0.0.0
7f4eb4ead000-7f4eb4eae000 rw-p 0003d000 08:03 10004                      /usr/lib/libvisual-0.4.so.0.0.0
7f4eb4eae000-7f4eb4eb4000 r-xp 00000000 08:03 12298                      /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4eb4eb4000-7f4eb50b3000 ---p 00006000 08:03 12298                      /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4eb50b3000-7f4eb50b4000 r--p 00005000 08:03 12298                      /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4eb50b4000-7f4eb50b5000 rw-p 00006000 08:03 12298                      /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f4eb50b5000-7f4eb50b9000 r-xp 00000000 08:03 156453                     /usr/lib/gstreamer-0.10/libgstefence.so
7f4eb50b9000-7f4eb52b8000 ---p 00004000 08:03 156453                     /usr/lib/gstreamer-0.10/libgstefence.so
7f4eb52b8000-7f4eb52b9000 r--p 00003000 08:03 156453                     /usr/lib/gstreamer-0.10/libgstefence.so
7f4eb52b9000-7f4eb52ba000 rw-p 00004000 08:03 156453                     /usr/lib/gstreamer-0.10/libgstefence.so
7f4eb52ba000-7f4eb52c8000 r-xp 00000000 08:03 156467                     /usr/lib/gstreamer-0.10/libgstjpeg.so
7f4eb52c8000-7f4eb54c7000 ---p 0000e000 08:03 156467                     /usr/lib/gstreamer-0.10/libgstjpeg.so
7f4eb54c7000-7f4eb54c8000 r--p 0000d000 08:03 156467                     /usr/lib/gstreamer-0.10/libgstjpeg.so
7f4eb54c8000-7f4eb54c9000 rw-p 0000e000 08:03 156467                     /usr/lib/gstreamer-0.10/libgstjpeg.so
7f4eb54c9000-7f4eb552f000 r-xp 00000000 08:03 9959                       /usr/lib/libtag.so.1.5.0
7f4eb552f000-7f4eb572e000 ---p 00066000 08:03 9959                       /usr/lib/libtag.so.1.5.0
7f4eb572e000-7f4eb5730000 r--p 00065000 08:03 9959                       /usr/lib/libtag.so.1.5.0
7f4eb5730000-7f4eb5731000 rw-p 00067000 08:03 9959                       /usr/lib/libtag.so.1.5.0
7f4eb5731000-7f4eb573c000 r-xp 00000000 08:03 156486                     /usr/lib/gstreamer-0.10/libgsttaglib.so
7f4eb573c000-7f4eb593b000 ---p 0000b000 08:03 156486                     /usr/lib/gstreamer-0.10/libgsttaglib.so
7f4eb593b000-7f4eb593c000 r--p 0000a000 08:03 156486                     /usr/lib/gstreamer-0.10/libgsttaglib.so
7f4eb593c000-7f4eb593d000 rw-p 0000b000 08:03 156486                     /usr/lib/gstreamer-0.10/libgsttaglib.so
7f4eb593d000-7f4eb5940000 r-xp 00000000 08:03 155313                     /usr/lib/gstreamer-0.10/libgstfestival.so
7f4eb5940000-7f4eb5b3f000 ---p 00003000 08:03 155313                     /usr/lib/gstreamer-0.10/libgstfestival.so
7f4eb5b3f000-7f4eb5b40000 r--p 00002000 08:03 155313                     /usr/lib/gstreamer-0.10/libgstfestival.so
7f4eb5b40000-7f4eb5b41000 rw-p 00003000 08:03 155313                     /usr/lib/gstreamer-0.10/libgstfestival.so
7f4eb5b41000-7f4eb5b44000 r-xp 00000000 08:03 155356                     /usr/lib/gstreamer-0.10/libgstvalve.so
7f4eb5b44000-7f4eb5d43000 ---p 00003000 08:03 155356                     /usr/lib/gstreamer-0.10/libgstvalve.so
7f4eb5d43000-7f4eb5d44000 r--p 00002000 08:03 155356                     /usr/lib/gstreamer-0.10/libgstvalve.so
7f4eb5d44000-7f4eb5d45000 rw-p 00003000 08:03 155356                     /usr/lib/gstreamer-0.10/libgstvalve.so
7f4eb5d45000-7f4eb5d8d000 r-xp 00000000 08:03 134365                     /usr/lib/libmodplug.so.0.0.0
7f4eb5d8d000-7f4eb5f8d000 ---p 00048000 08:03 134365                     /usr/lib/libmodplug.so.0.0.0
7f4eb5f8d000-7f4eb5f8e000 r--p 00048000 08:03 134365                     /usr/lib/libmodplug.so.0.0.0
7f4eb5f8e000-7f4eb5f91000 rw-p 00049000 08:03 134365                     /usr/lib/libmodplug.so.0.0.0
7f4eb5f91000-7f4eb6011000 rw-p 7f4eb5f91000 00:00 0 
7f4eb6011000-7f4eb6018000 r-xp 00000000 08:03 155326                     /usr/lib/gstreamer-0.10/libgstmodplug.so
7f4eb6018000-7f4eb6217000 ---p 00007000 08:03 155326                     /usr/lib/gstreamer-0.10/libgstmodplug.so
7f4eb6217000-7f4eb6218000 r--p 00006000 08:03 155326                     /usr/lib/gstreamer-0.10/libgstmodplug.so
7f4eb6218000-7f4eb6219000 rw-p 00007000 08:03 155326                     /usr/lib/gstreamer-0.10/libgstmodplug.so
7f4eb6219000-7f4eb621f000 r-xp 00000000 08:03 155355                     /usr/lib/gstreamer-0.10/libgsttta.so
7f4eb621f000-7f4eb641e000 ---p 00006000 08:03 155355                     /usr/lib/gstreamer-0.10/libgsttta.so
7f4eb641e000-7f4eb641f000 r--p 00005000 08:03 155355                     /usr/lib/gstreamer-0.10/libgsttta.so
7f4eb641f000-7f4eb6420000 rw-p 00006000 08:03 155355                     /usr/lib/gstreamer-0.10/libgsttta.so
7f4eb6420000-7f4eb6426000 r-xp 00000000 08:03 155330                     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f4eb6426000-7f4eb6625000 ---p 00006000 08:03 155330                     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f4eb6625000-7f4eb6626000 r--p 00005000 08:03 155330                     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f4eb6626000-7f4eb6627000 rw-p 00006000 08:03 155330                     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f4eb6627000-7f4eb662b000 r-xp 00000000 08:03 156457                     /usr/lib/gstreamer-0.10/libgstflxdec.sCould not initialize GStreamer: Error re-scanning registry , child terminated by signal

```
Something to do with the Gstreamer I imagine.. lol

---

### Post by nhasian on 2009-07-30
open up a terminal and type:

```
sudo apt-get remove libvisual-0.4-plugins
```

then try songbird again.

---

### Post by xenogia on 2009-07-30
> **nhasian said:**
> open up a terminal and type:

```
sudo apt-get remove libvisual-0.4-plugins
```then try songbird again.


That worked, why would those plugins cause those type of issues though?

---

### Post by cybergalvez on 2009-07-30
I really like Listen

---

### Post by pmlxuser on 2009-07-30
> **synapsys said:**
> +1 you can also get a nice pre-compiled .deb from [getdeb.net]("http://www.getdeb.net")

+1 to that as well

---

### Post by akrchstn on 2009-07-30
moc....

---

### Post by JohnLau on 2009-07-30
> **credobyte said:**
> Banshee ( features ) & Audacious ( simplicity ) :)

:popcorn:
Those are my choices too:P)
Not sure if it happens to everyone, I find songbird a bit laggy:confused:
John

---

### Post by alexandari on 2009-07-30
for GTK - Exaile
for KDE - Amarok
they`re almost the same :)

---

### Post by hyperAura on 2009-07-30
ive been using Amarok but i messed the library up.. so then i moved to rhythmbox which is nice and now i am using audacious as it reminds me of winamp which ive been using the last 10 years in windows.. songbird looks nice though as ive seen it a couple of times on other machines..

---

### Post by zeroseven0183 on 2009-07-30
> **nhasian said:**
> VLC is one of the first things I install on a pc regardless of OS, i wouldnt recommend it as a music player.

It all depends on your personal preferences. Some like VLC, others don't. You like Songbird, others prefer another thing.

---

### Post by Grenage on 2009-07-30
It's always down to personal preference, but I don't understand what anyone would see in VLC as a music player, especially when compared to apps like songbird.

---

### Post by wizard10000 on 2009-07-30
I just wanted something that will play my music collection and nothing else - I used to use xmms but now have used audacious for quite some time.  It uses my favorite winamp skin and IMO works just as well as xmms did.

---

### Post by Humanum on 2009-07-31
Hi,


You can also have a look at [www.moovida.com](www.moovida.com) which replaced elisa...

But it does more than just playing your music files...

:popcorn:

---

### Post by hissyfut on 2009-07-31
> **nhasian said:**
> I really like [Songbird]("http://getsongbird.com/").

wavpack only supported by an addon, which is sort of lame, no pun intended.

---

### Post by hissyfut on 2009-07-31
if you like command line tools.

madplay

for music cds it doesn't get
much simpler than workbone
[http://slackware.oregonstate.edu/slackware-current/source/ap/workbone/](http://slackware.oregonstate.edu/slackware-current/source/ap/workbone/)

---

### Post by andrew.46 on 2009-08-21
Hi hissyfut,

> **hissyfut said:**
> if you like command line tools.

madplay


Mind you if you are *really* keen on commandline tools and can commit to reading man pages and html documentation carefully there is little that cannot be done with the commandline, subversion MPlayer.

All the best,

Andrew

---

