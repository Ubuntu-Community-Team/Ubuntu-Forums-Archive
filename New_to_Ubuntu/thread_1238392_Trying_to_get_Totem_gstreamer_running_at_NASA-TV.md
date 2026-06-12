---
title: "Trying to get Totem gstreamer running at NASA-TV"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by alienexplorers on 2009-08-12
I am trying to get the video and audio at NASA-TV to show up.  I have totem-gstreamer running, but all I get is a gray box where the video is supposed to be.  I have also tried running on-demand video's at the NASA home site at [http://www.nasa.gov]("http://www.nasa.gov")with no luck.  Anyone that can receive video's on these sites please let me know what you are doing to get it to play the video's.

---

### Post by MyR on 2009-08-12
totem-gstreamer sucks

use this command
sudo aptitude install totem-xine gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg && sudo aptitude remove totem-gstreamer

works for me in firefox 3.0

not in opera 10 beta 2 :[

peace

---

### Post by ajgreeny on 2009-08-12
If this is in a firefox plugin that you are having the problem, I recommend **gecko-mediaplayer** as the plugin.  It is superior to totem in every way, in my opinion.  It is the successor to mozilla-mplayer, which until jaunty worked brilliantly, but now crashes all the time when you start it, taking firefox with it, and is now not being developed further, apparently.

---

### Post by alienexplorers on 2009-08-12
Tried loading totem-xine like you suggested and still no luck running the NASA-TV site.  Must be some other problem with gstreamer itself.

---

### Post by alienexplorers on 2009-08-12
Removed totem and installed gecko-mediaplayer and everything works great.  Thanks ajgreeny!!!!!

---

### Post by ajgreeny on 2009-08-12
I'm very pleased that it worked for you as well.

---

### Post by virgoboy on 2009-09-10
I am having the same problem, with the NASA TV website as the initial poster.  I did install the **gecko-mediaplayer **plug-in however, i get either a gray box where the video should be (it had been white) embedded into the website and when i select either Real Or QT as the viewing option, it opens a new tab with white and no video or audio.  I did restart Firefox (3.5.2) a couple of times to no avail.  Should i uninstall the Totem plug ins?  Right now, i have them disabled.  

Thanks!

---

### Post by fatdadkev on 2010-02-06
I'm an avid fan of Nasa and like many wanted to get this running again.
After much searching I found some info that fixed my problems straight away.
It's possible most people like me have installed several media players and we like to "tinker" with Ubuntu, it's not unexpected when something is a little tricky to resolve.

I had installed gecko media player but this did nothing to help, quicktime and realplayer were installed, I had tried the helix version and so on, the only thing I knew was that in the past when I most likely only had mplayer NasaTV worked fine.

This post had all the info on I needed to resolve and bring back Nasa TV, I take no credit for the contents and therefore please let ubuntu-freak have some feedback.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

First of all I had completely removed gecko before doing any of this, restarted my system to ensure all plugins were loaded correctly etc and still no Nasa TV.

The section I followed was "Part 2/5 Audio and Video streaming".
I pasted his command in to remove totem and other plugins that might be conflicting or causing any issues BUT did not follow his first advice to install Gecko, instead I followed "option 2 - mplayer plugin", this worked perfectly.

I suspect the key was the mplayer configuration file in /etc i.e

gksudo gedit /etc/mplayerplug-in.conf
He has a list of parameters to put in and I am sure this was part of the issue that things were not working.
I stopped before part 3 as I have no problems with any audio and now Nasa TV streams in the browser on Ubuntu 9.10 with Firefox 3.5.7.

Outstanding post from ubuntu-freak and I hope this helps others who are interested in viewing this.

---

