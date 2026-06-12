---
title: "Ubuntu 10.04 new install, need streaming audio."
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Kellemora on 2010-08-04
Hi Gang

Yes I did a search and read what popped up first.

I need to be able to hear .ram files in 10.04
A movie player is popping up, instead of an audio player and says I need gstreamer.  I went to synaptic and loaded gstreamer.  Still no audio, and the pop-up keeps saying to install gstreamer.

I don't want a VIDEO PLAYER, I think it's Totem.

I can't remember or figure out exactly WHAT makes it work on 8.04, but it works just fine there.

Also, on a new 10.04 install, what all is missing that I should be installing?  I'm using Firefox, installed Flash, haven't got Java yet.
I'm trying to make notes of each program I need to install that was left out of the new install and the 250+ updates that came along with it.

Many of the programs I installed from Synaptic in 8.04 don't appear in the new OS, so maybe I need to POINT to different file servers, like Medibuntu and others?????  What are the basic ones I should point toward?

TTUL
Gary

---

### Post by blazemore on 2010-08-04
I suggest installing the application called VLC.
VLC will play nearly all media files and is also excellent at streaming over the Internet.
Search for it in Synaptic or the Software Centre, or [URL="apt:vlc"]click here to install it right now automatically.
[/URL]

---

### Post by LowSky on 2010-08-04
> **Kellemora said:**
> 
I can't remember or figure out exactly WHAT makes it work on 8.04, but it works just fine there.


You install the codec in your older verison too, between verison the way they had to be install changed and adds some confusion.

.RAM files are associated with Real Networks real audio.

VLC can play these files, so can REAL Player: [http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

---

### Post by audiomick on 2010-08-04
I'm guessing, but maybe you need to install ubuntu-restricted-extras. That includes a heap of codecs.

---

### Post by -kg- on 2010-08-04
What I always do that has worked for me every time I do a new installation is first to go to Synaptic and install "ubuntu-restricted-extras" (use the appropriate one for your installation..."kubuntu-restricted-extras" or whatever desktop environment you're using).  That installs the latest Flash Player, Java, and additional non-free codecs, etc.  If you intend to view commercial DVDs, you'll want to load the Medibuntu repos and install the libdvdcss2.

As far as players, there are a bunch of them.  I use MPlayer (likely the movie player you had pop up) and VLC.  There are quite a few more, like Banshee, Amarok, Audacious, and a whole lot more.  Take your pick.  I kind of like MPlayer for one reason...it has pretty good visualizations, but so do several of the others.

Though I haven't noticed the absence of software titles from one release to the next, it's likely only because I didn't use software which has been removed.  If you could list some of the titles...say the ones you are looking for the hardest...we might be able to help with that, as well.

<Edit> As an addendum (that I just thought of), GIMP is no longer included in the distro by default.  It is still included in the repos, though.  You can install it from Synaptic or the new Software Center.

---

### Post by Kellemora on 2010-08-04
Thanks Guys

Ubuntu Restricted Extras is what I totally forgot about!

MPlayer is what was working on 8.04 just fine.
But I'll try that VLC first this time.

I have a list of things I installed on 8.04 as I came to need them.
But didn't list the names of the repositories.
They are listed on the computers but all say hardy behind them.
I'm a little leary of putting them in with the name lucid behind them.

Again, Thanks gang!

TTUL
Gary

---

### Post by Kellemora on 2010-08-04
Hmmmmmm, the system CRASHED after using Synaptic to install the Ubuntu Restricted Extras package.
A COLD Reboot got it up and running.

I then installed VLC........

Still have no streaming audio.........

Do I need to install Mozplugger in 10.04?
I did in 8.04!

Even though Synaptic does not show MPlayer as being installed, THAT is what is still popping up, however, the streaming audio works now, which is what I was after.

Where ever VLC is HIDING, it's not in the drop down list of players!

And I don't like all the pop-up boxes that I never got with 8.04 to play an audio file.

TTUL
Gary

---

### Post by lovinglinux on 2010-08-04
VLC is an excellent standalone player, but the plugin not so much. Get gecko-mediaplayer instead. 

Follow the tutorial See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"). Never had any multimedia issue after following it.

BTW, although the plugin launched is a video player, it plays music too.

---

### Post by Kellemora on 2010-08-04
OK, Were up and running just fine now.  Thanks for all your help!

Marking it solved!

TTUL
Gary

---

