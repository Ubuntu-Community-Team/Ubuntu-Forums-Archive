---
title: "All video players crash after video is started!!!!!!"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-03-08
I installed Miro 2.0.1, but when I tried to play the videos Miro crashed immediately. I thought this was Miro, but when I tried playing videos I have had for a few months with VLC and totem player they crashed immediately. This never happened before. How do I fix this?? Please help.

---

### Post by st33med on 2009-03-08
What graphics card do you have?
```
lspci | grep VGA
```

Also, what video are you trying to play and do you have Desktop Effects turned on while watching a video?

---

### Post by Bigbob22 on 2009-03-08
The output is this
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
```
I played several different videos that I was able to play just yesterday. When ever I play videos I kill compiz.

---

### Post by Bigbob22 on 2009-03-08
I ran miro through the terminal and played a video. This is the output:
```
location: /usr/lib/xulrunner-1.9.0.7/libxpcom.so 
before 3
2009-03-08 00:07:18,458 INFO     Starting up Miro
2009-03-08 00:07:18,459 INFO     Version:    2.0.1
2009-03-08 00:07:18,463 INFO     OS:         Linux 2.6.24-19-generic i686
2009-03-08 00:07:18,463 INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.1/tv/resources - 9185
2009-03-08 00:07:18,464 INFO     Builder:    pbuilder@mercury
2009-03-08 00:07:18,464 INFO     Build Time: 1234395336.79
2009-03-08 00:07:18,464 INFO     Starting event loop thread
2009-03-08 00:07:18,492 INFO     Restoring database...
2009-03-08 00:07:18,492 INFO     Python version:    2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]
2009-03-08 00:07:18,493 INFO     Gtk+ version:      (2, 12, 9)
2009-03-08 00:07:18,494 INFO     PyGObject version: (2, 14, 2)
2009-03-08 00:07:18,494 INFO     PyGtk version:     (2, 12, 1)
2009-03-08 00:07:18,494 INFO     Language:          [('LANG', 'en_US.UTF-8')]
2009-03-08 00:07:18,495 INFO     set_renderer: trying to add gstreamerrenderer
2009-03-08 00:07:18,608 INFO     Connecting to /home/sanat/.miro/sqlitedb
2009-03-08 00:07:18,608 INFO     GStreamer version: GStreamer 0.10.18
2009-03-08 00:07:18,619 INFO     GStreamer videosink: gconfvideosink
2009-03-08 00:07:18,630 INFO     GStreamer audiosink: gconfaudiosink
2009-03-08 00:07:18,637 INFO     set_renderer: successfully loaded gstreamerrenderer
2009-03-08 00:07:19,408 TIMING   Database load slow: 0.915
2009-03-08 00:07:19,408 INFO     Database size on disk (in bytes): 2347008
2009-03-08 00:07:19,409 INFO     Database object count: 715
2009-03-08 00:07:20,107 TIMING   idle (finish startup) too slow (1.641 secs)
2009-03-08 00:07:20,108 INFO     Checking movies directory '/home/sanat/.miro/Movies/'...
2009-03-08 00:07:22,940 INFO     Starting auto downloader...
2009-03-08 00:07:23,000 TIMING   Icon clear: 0.000
2009-03-08 00:07:23,001 INFO     Starting movie data updates
2009-03-08 00:07:23,001 INFO     Checking for updates...
2009-03-08 00:07:23,284 INFO     No updates for this platform.
The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 56 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I don't understand it, but it might be useful.

---

### Post by st33med on 2009-03-08
nvm

Look at my next post

---

### Post by st33med on 2009-03-08
Try:
```
miro --sync
```

Let's see what that tells us.

That X error looks pretty serious, have you changed drivers recently?

---

### Post by Bigbob22 on 2009-03-08
I have not changed my drivers recently. The only change I can think of is the installation of miro. All my videos were working just today morning. This is the output of miro --sync
```
location: /usr/lib/xulrunner-1.9.0.7/libxpcom.so 
before 3
2009-03-08 00:15:05,159 INFO     Starting up Miro
2009-03-08 00:15:05,160 INFO     Version:    2.0.1
2009-03-08 00:15:05,163 INFO     OS:         Linux 2.6.24-19-generic i686
2009-03-08 00:15:05,164 INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.1/tv/resources - 9185
2009-03-08 00:15:05,165 INFO     Builder:    pbuilder@mercury
2009-03-08 00:15:05,165 INFO     Build Time: 1234395336.79
2009-03-08 00:15:05,165 INFO     Starting event loop thread
2009-03-08 00:15:05,166 INFO     Python version:    2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]
2009-03-08 00:15:05,191 INFO     Restoring database...
2009-03-08 00:15:05,192 INFO     Gtk+ version:      (2, 12, 9)
2009-03-08 00:15:05,193 INFO     PyGObject version: (2, 14, 2)
2009-03-08 00:15:05,193 INFO     PyGtk version:     (2, 12, 1)
2009-03-08 00:15:05,193 INFO     Language:          [('LANG', 'en_US.UTF-8')]
2009-03-08 00:15:05,193 INFO     Connecting to /home/sanat/.miro/sqlitedb
2009-03-08 00:15:05,194 INFO     set_renderer: trying to add gstreamerrenderer
2009-03-08 00:15:05,312 INFO     GStreamer version: GStreamer 0.10.18
2009-03-08 00:15:05,322 INFO     GStreamer videosink: gconfvideosink
2009-03-08 00:15:05,325 INFO     GStreamer audiosink: gconfaudiosink
2009-03-08 00:15:05,332 INFO     set_renderer: successfully loaded gstreamerrenderer
2009-03-08 00:15:06,118 TIMING   Database load slow: 0.926
2009-03-08 00:15:06,119 INFO     Database size on disk (in bytes): 2347008
2009-03-08 00:15:06,119 INFO     Database object count: 715
2009-03-08 00:15:06,814 TIMING   idle (finish startup) too slow (1.647 secs)
2009-03-08 00:15:06,815 INFO     Checking movies directory '/home/sanat/.miro/Movies/'...
2009-03-08 00:15:09,816 INFO     Starting auto downloader...
2009-03-08 00:15:09,872 TIMING   Icon clear: 0.000
2009-03-08 00:15:09,873 INFO     Starting movie data updates
2009-03-08 00:15:09,873 INFO     Checking for updates...
2009-03-08 00:15:10,171 INFO     No updates for this platform.
The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 56 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by Bigbob22 on 2009-03-08
I also tried uninstalling Miro, but it did not work.

---

### Post by Bigbob22 on 2009-03-08
Please help.

---

### Post by Bigbob22 on 2009-03-08
I figured it out. U have to type this in the terminal:
```
gstreamer-properties
```
Then change the settings till it works.

---

### Post by IceyBlack on 2009-03-08
I can't find a good video player from all 1000 ubuntu video players..in windows i used Gomplayer,who is the best,i need a replacement for that program.they are video players there but i need which one where i can sett up subtitles resize,align up or down etc..
can you recomand me one? in vlc how can i make subtitle up and down(to be in the bottom of screen)or other video nevermind.
Tnx.

---

