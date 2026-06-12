---
title: "[SOLVED] Miro crashes on 2nd vid"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Zopiac on 2009-01-10
For some reason, Miro seems to run perfectly. Unleeessss you want to watch two videos...when i click on a second video to play it, the program crashes :(

output:

```
location: /usr/lib/xulrunner-1.9.0.5/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     OS:         Linux
INFO     Version:    1.2.8
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.2.8/tv/resources - 8366
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1225304414.86
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/zopiac/.miro/sqlitedb
TIMING   Database load slow: 2.064
TIMING   idle (finish startup) too slow (2.820 secs)
INFO     Spawning auto downloader...
INFO     *** Launching Downloader Daemon ****
TIMING   Icon clear: 0.015
INFO     Starting movie data updates
INFO     Displaying main frame...
INFO     Creating video display...
INFO     Finished startup sequence
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
WARNING  Error setting up drag and drop dummy element
INFO     got file:///tmp/tmphJGogd.html
INFO     First URL is https://www.miroguide.com/
TIMING   idle (select initial tab) too slow (0.669 secs)
INFO     got file:///tmp/tmpzjX1t4.html
INFO     First URL is https://www.miroguide.com/
INFO     *** Daemon ready ***
WARNING  eventloop: Interrupted system call
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got about:blank
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
INFO     unknown url type https://www.miroguide.com/channels/6381, not generating enclosure
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=1437&shiftDown=0&ctrlDown=0
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
INFO     got file:///tmp/tmpdz2Rzx.html
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=1436&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpYiwXPO.html
INFO     got action:handleSelect?area=itemlist&viewName=matchingItems&id=448&shiftDown=0&ctrlDown=0
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=448
INFO     got file:///tmp/tmp5MEl01.html
TIMING   gtkSyncMethod: <function getDisplay at 0x108a848> took too long: 1.260
TIMING   dispatch action playViewNamed too slow (1.454 secs)
TIMING   idle (dispatchAction() (using asUrgent)) too slow (1.454 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://www.g4tv.com/g4originals/podcasts/25/G4tvcom_Originals.xml)) too slow (0.609 secs)
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=1436&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpH8Oc5_.html
INFO     got action:playViewNamed?viewName=matchingItems&firstItemId=448
INFO     got file:///tmp/tmphOMRRk.html
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 44 error_code 8 request_code 161 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

```

---

### Post by billgoldberg on 2009-01-10
From what I remember of Miro, you can change the "video backend" of Miro.

I think the default is Xine, but you can change it to Gstreamer.

I had to change the default one because it gave me crashes.

Give it a try.

---

### Post by Zopiac on 2009-01-10
> **billgoldberg said:**
> From what I remember of Miro, you can change the "video backend" of Miro.

I think the default is Xine, but you can change it to Gstreamer.

I had to change the default one because it gave me crashes.

Give it a try.

thx a ton, it works :D

---

