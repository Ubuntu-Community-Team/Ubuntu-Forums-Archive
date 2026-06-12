---
title: "gstreamer install didn't work"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by JerryC on 2011-04-20
Trying to get mp3 to work on a fresh install of 10.10.  I did a search here and saw I needed to install some gstreamer files, so I did.  To my surprise it installed 80 some files.  Anyway when I click on an mp3 file it starts the movie player which was a surprise.  It shows the error message: pa_stream_writable_size() failed:connection terminated.  When I start rythhmbox, it loads the file but won't play it. No error displayed this way.  I went to Synaptic Package Manager and it shows several gstreamer files installed and many that aren't.  As you look at the list in the package manager, the first column has the boxes that show green for installed and blank for not installed.  The second column (no heading) has a little red circle by some, not all, of the gstreamer files, some of which are installed and some not.  What do I need to do to get mp3 files to play?  And what do the little red circles mean?

JC

---

### Post by kaldor on 2011-04-20
try running:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by HermanAB on 2011-04-21
Depends...

If you want absolutely *all* multimedia to work, including encoding and decoding DVDs, then you need Medibuntu, which is a fork of the Mandriva Penguin Liberation Front (PLF) repositories in France (Medibuntu never admitted their caper and the PLF guys are too nice to complain loudly, but it is obvious when you compare the web sites that Medibunti is a wget copy and paste job).

One way to get multimedia to work, is to install video playing and editing tools like Cheese, Mplayer, Totem, Xine, VLC, Cinelerra and Avidemux.  Once all those are installed, you will have almost everything working, since these tools will each pull in a whole bunch of support libraries and CODECs.

---

### Post by JerryC on 2011-04-21
Thank you all for your time.  Installing mplayer did the job.

JC

---

