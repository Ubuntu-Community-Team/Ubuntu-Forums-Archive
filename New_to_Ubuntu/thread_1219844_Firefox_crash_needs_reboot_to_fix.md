---
title: "Firefox crash needs reboot to fix"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by tadcan on 2009-07-22
I have an issue with firefox crashing and the only way to fix it is to restart the computer. When I went to system monitor I am told that fire-fox bin is uninterpretable. I have been running firefox from the terminal, but it only seems to crash when I use the icon. However I have got the following from the terminal, but it hasn't caused a crash. 

Sometimes the crash prevents a proper shut down and I have to use the restart button on the computer.

```
*** FIXME: [Exception... "'[JavaScript Error: "this.skipHours.getProperty is not a function" {file: "file:///opt/firefox/components/FeedProcessor.js" line: 302}]' when calling method: [nsIFeed::normalize]"  nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)"  location: "JS frame :: file:///opt/firefox/components/FeedProcessor.js :: FP_sendResult :: line 1399"  data: yes]
argn=src, argv=http://blog.indianoceanrace.com/wp-content/uploads/2009/07/podcast_1707.mp3
argn=type, argv=audio/mpeg
argn=autostart, argv=FALSE
argn=loop, argv=FALSE
argn=height, argv=55
argn=width, argv=245
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/tadcan/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 272 modules
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000369] main interaction debug: thread 2626681744 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000369] main interaction debug: thread started
[00000371] main preparser debug: waiting for thread initialization
[00000371] main preparser debug: thread started
[00000371] main preparser debug: thread 2767186832 (preparser) created at priority 0 (playlist/thread.c:79)
[00000372] main fetcher debug: waiting for thread initialization
[00000372] main fetcher debug: thread started
[00000372] main fetcher debug: thread 2645556112 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000370] main playlist debug: waiting for thread initialization
[00000370] main playlist debug: thread started
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 0 items, index -1
[00000370] main playlist debug: thread 2750401424 (playlist) created at priority 0 (playlist/thread.c:117)
[00000373] main interface debug: looking for interface module: 1 candidate
[00000373] main interface debug: using interface module "hotkeys"
[00000373] main interface debug: thread 2516581264 (interface) created at priority 0 (interface/interface.c:168)
[00000373] main interface debug: thread started
[00000375] main interface debug: looking for interface module: 1 candidate
[00000375] main interface debug: using interface module "inhibit"
[00000375] main interface debug: thread started
[00000375] main interface debug: thread 2508188560 (interface) created at priority 0 (interface/interface.c:168)
[00000377] main interface debug: looking for interface module: 1 candidate
[00000377] main interface debug: using interface module "screensaver"
[00000377] main interface debug: thread started
[00000377] main interface debug: thread 2499795856 (interface) created at priority 0 (interface/interface.c:168)
*** LibVLC Exception not handled: No active input
Set a breakpoint in 'libvlc_exception_not_handled' to debug.
[00000370] main playlist debug: adding item `http://blog.indianoceanrace.com/wp-content/uploads/2009/07/podcast_1707.mp3' ( http://blog.indianoceanrace.com/wp-content/uploads/2009/07/podcast_1707.mp3 )
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 1 items, index -1
[00000001] main libvlc debug: removing all interfaces
[00000377] main interface debug: thread ended
[00000377] main interface debug: thread 2499795856 joined (interface/interface.c:188)
[00000377] main interface debug: removing module "screensaver"
[00000375] main interface debug: thread ended
[00000375] main interface debug: thread 2508188560 joined (interface/interface.c:188)
[00000375] main interface debug: removing module "inhibit"
[00000373] main interface debug: thread ended
[00000373] main interface debug: thread 2516581264 joined (interface/interface.c:188)
[00000373] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000371] main preparser debug: thread ended
[00000371] main preparser debug: thread 2767186832 joined (playlist/engine.c:521)
[00000372] main fetcher debug: thread ended
[00000372] main fetcher debug: thread 2645556112 joined (playlist/engine.c:523)
[00000370] main playlist debug: thread ended
[00000370] main playlist debug: thread 2750401424 joined (libvlc.c:993)
[00000371] main preparser debug: Destroyed
[00000372] main fetcher debug: Destroyed
[00000370] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000369] main interaction debug: thread ended
[00000369] main interaction debug: thread 2626681744 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: writing plugins cache /home/tadcan/.cache/vlc/plugins-04041e.dat

```

---

### Post by tadcan on 2009-07-23
anyone?

---

### Post by LewRockwell on 2009-07-23
sounds like you've got some conflicts with firefox and it's components and dependencies

you can use synaptic or the command line to remove firefox and it's orphans

this tutorial gives you some ideas(in case you're a little shy on the CLI)

[http://www.ubuntumini.com/2009/05/become-command-line-commando.html](http://www.ubuntumini.com/2009/05/become-command-line-commando.html)
(also makes a good cheat sheet so bookmark it if you like)

once you've completely cleaned it off and rebooted, then you can reinstall whatever you choose

.

---

### Post by llamabr on 2009-07-23
Sometimes I find that recent upgrades are just inconsistent with my old config files.  If you're not wedded to your bookmarks, etc, you can just try:

```
rm -rf ~/.mozilla/
```

Which will clean out any config, dependencies, setting, etc, and start you fresh.  It's overkill, but good as a last resort.

---

### Post by wojox on 2009-07-23
What command are you using to run Firefox from the terminal?

---

### Post by tadcan on 2009-07-23
I just type 

```
firefox
```

most programs start if you type in its name.

I'll have to remove songbird as well, according to synaptic it uses firefox as well.

I have xmarks, so I can just pull down the bookmarks after. I'll do a total clean, sound like the easiest plan.

---

### Post by tadcan on 2009-07-23
> **llamabr said:**
> Sometimes I find that recent upgrades are just inconsistent with my old config files.  If you're not wedded to your bookmarks, etc, you can just try:

```
rm -rf ~/.mozilla/
```

Which will clean out any config, dependencies, setting, etc, and start you fresh.  It's overkill, but good as a last resort.

Interesting that left shiretoko and the firefox3.5 intact but took out my bookmarks etc. I'll see if I get any crashes over the next few days. Or if that was caused by the the old version.

---

