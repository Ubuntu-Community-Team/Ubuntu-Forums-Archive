---
title: "Minor issues in Karmic (Mplayer &amp; Pulseaudio)"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by gshockxc on 2010-01-06
I just upgraded to Karmic 9.10 ... love it so far, but I'm having issues with Mplayer.  More to the point, it doesn't play videos.  Where do I start?

Also, I get a warning that Pulseaudio isn't working or something when I start up.  The message disappears too quickly for me to capture it.  

I found a [thread]("http://ubuntuforums.org/showthread.php?t=1313253&highlight=removing+pulseaudio") about removing Pulseaudio in Ubuntu.  Should I follow the same steps for removing in Kubuntu?

Thanks for the help.

---

### Post by andrew.46 on 2010-01-07
Hi gshockxc,

> **gshockxc said:**
> I just upgraded to Karmic 9.10 ... love it so far, but I'm having issues with Mplayer.  More to the point, it doesn't play videos.  Where do I start?

An excellent start is to run the video from the commandline as follows:

```
mplayer -v **[COLOR="Red"]*myfile*[/COLOR]**
```

where you will of course need to substitute 'myfile' with the actual name of your own file. Copy the complete terminal output, including the command, and paste int a message. This will give more than a few hints as to what is going wrong.

Andrew

---

### Post by gshockxc on 2010-01-07
Andrew, here's the command I entered, and the output.
```

mplayer -v 116.flv

```

```

The program 'mplayer' is currently not installed.  You can install it by typing:
sudo apt-get install mplayer-nogui
mplayer: command not found

```

I've tried to reinstall Mplayer from Synaptic, but that didn't fix the problem.

---

### Post by andrew.46 on 2010-01-07
Hi gshockxc,

pulseaudio issues are a little beyond me I am afraid, hopefully someone else can help with this one. But now you have MPlayer installed could you try the commandline I suggested?

Andrew

---

### Post by gshockxc on 2010-01-07
> **andrew.46 said:**
> Hi gshockxc,

pulseaudio issues are a little beyond me I am afraid, hopefully someone else can help with this one. But now you have MPlayer installed could you try the commandline I suggested?

Andrew

What I posted earlier was the result of the command line you suggested.  I had installed Mplayer earlier from Synaptic, then tried you command line just a little while ago.  

'116.flv' is the name of the file I was trying to play.

Thanks.

---

### Post by andrew.46 on 2010-01-07
OIC my apologies :). Can I ask if you are running the 32bit version of Karmic or the 64bit?

Andrew

---

### Post by gshockxc on 2010-01-07
> **andrew.46 said:**
> OIC my apologies :). Can I ask if you are running the 32bit version of Karmic or the 64bit?

Andrew

np, I'm running 64-bit.  I had installed from the upgrade instead of a clean install.  So I copied my /home... to an external HD this morning and did a clean install. 

In addition to Mplayer, the desktop keeps going black.  I'll be browsing, or working on something, and "Poof", the desktop disappears, goes black.  The programs I'm using will stay open, but I loose my toolbars, icons, etc.  

I am not experienced enough to know how to restart the Desktop.  I think it's the X Server, right?  I know it's not tied to the OS, so I can keep working if I know the commands to use, but I figured there are more glitches waiting to be found.  I've heard a lot of people say in this forum that 9.10 is great, but not from the upgrade.  Clean install works best.  So that's what I'm doing now.

---

### Post by andrew.46 on 2010-01-07
Hi gshockxc,

I am a big fan for a clean install. When it is done can I suggest the following to get the best possible *repository* MPlayer package:

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install smplayer mplayer-nogui w64codecs libdvdcss2 libdvdread4 libavcodec-extra-52

```

This allows you to access the Medibuntu repository, downloads MPlayer and the frontend SMPlayer, a few extra codecs, a bumped-up libavcodec and the libraries to access commercial dvds, all in a single command. Then cross your fingers and open your troublesome file with SMPlayer :).

Andrew

---

### Post by gshockxc on 2010-01-07
Aboslutely.  Thanks for the tip.

I'll do that as soon as I get a chance to get back up and running.
It's installed, but I haven't rebooted yet.  Just finished the install and shutdown.

Thanks for the help.

---

