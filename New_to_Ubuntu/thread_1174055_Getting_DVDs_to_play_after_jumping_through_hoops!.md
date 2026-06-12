---
title: "Getting DVDs to play after jumping through hoops!"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by BastardNamban on 2009-05-30
8.04 Ubuntu. Been using for nearly 6 months now, I STILL can't get DVDs to play, and I'm f'ing sick of this! After all the tweaking I've done to make so many things work, really difficult things, I cannot believe I still can't get something as simple as the damn DVD playback to work properly!

Why can't this work out of the box? (yes, I know, there's no box, but still, you know what I mean) Why?

Ok, enough complaining. I've self taught myself linux everything trolling forums for months, reading FAQs written by people who never fully answer the question, read official FAQs that still manage to confuse, so I must be an absolute idiot.

I've been here: ([http://ubuntuforums.org/archive/index.php/t-712164.html](http://ubuntuforums.org/archive/index.php/t-712164.html))
and set my DVD drive back to region 1 (before, when I used XP, I switched to 2 to watch Japanese DVDs). I went here as well: ([https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)) and followed the instructions for 8.04.

My DVD drive now plays the FBI warning on a DVD, and the following company intro screen on an anime DVD. That's it.

What, exactly, do I need to do to watch a damn movie? I'm serious, I've tried everything and every FAQ I could find. Why is this so hard, and how do I watch a movie? DON'T REFER ME TO ANOTHER FAQ. I RTFF! All of them, conceiveably!

So recap, I have everything Gstreamer related from Synaptic installed, and the libdvdcss2 package. DVDs show up with the right name on my desktop, and opening them in Nautilus brings up the 2 folders (audio & video) for each, usually with the videos in the folders refusing to run.

I want to open a DVD, and navigate it with my mouse, in a normal DVD menu.
If that means removing Totem for something else, I'll do it, if it works.

Can someone please help me? I really am sorry to be so angry earlier, but this is unbelievably frustrating. Maybe, just maybe, things like this are why linux has such a small market share? Can we work to make this something simpler for others? Is it still this hard in 9.04? We aren't talking about compiling from source code here, it's a damn DVD. Apparently, I can actually compile from source, but I still can't get a DVD working. I feel like the world's biggest moron.

Help, anyone? This is driving me nuts!

---

### Post by Paqman on 2009-05-30
> **BastardNamban said:**
> 
Why can't this work out of the box? (yes, I know, there's no box, but still, you know what I mean) Why?


Because Ubuntu is not legally allowed to distribute the DVD codecs.

Generally all you need to do is connect to the [Medibuntu]("http://www.medibuntu.org/") repository and install libdvdcss. Have you tried it in VLC?

---

### Post by steeleyuk on 2009-05-30
You'll want to install Totem-Xine. The Gstreamer version is working on DVD menu support. You'll also find that Windows (up to XP at least) requires 3rd party DVD playback, so this isn't an Ubuntu specific problem.

sudo apt-get install totem-xine libxine1-all-plugins

---

### Post by -kg- on 2009-05-30
> **Paqman said:**
> Because Ubuntu is not legally allowed to distribute the DVD codecs.

Generally all you need to do is connect to the [Medibuntu]("http://www.medibuntu.org/") repository and install libdvdcss. Have you tried it in VLC?

It was my experience that VLC didn't work either, even under Jaunty.  The Medibuntu "driver" did work for me, though.  I also installed the restricted codec package.  After I installed these DVDs played like a champ.

Go to [this page]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions for your distro.

---

### Post by BastardNamban on 2009-05-30
Paq, I see. Well, hearing that, things make some sense now. Thank you.

Steel, I vaguely remember installing Totem Xine at some point. I can't remember what happened with that. Does that show up as a separate player from the Gstreamer version? I seem to remember being able to select between them somehow...

I reinstalled Totem Xine per your code. We'll see what happens. I've got another 30 minutes before I head to work till late tonight.

---

### Post by hansdown on 2009-05-30
Hi BastardNamban.

O.K, no faqs, just step by step.

Click system> administration> software sources.
Make sure the first 4 boxes are checked.
Close.
Click system> administration> synaptic package manager.
Search for , and install```
 ubuntu-restricted-extras
```

This should do it.
As Paqman said, VLC works way better for movies.

---

### Post by BastardNamban on 2009-05-30
Hans, thanks, but those 4 boxes are checked, and installing restricted extras is one of the first things I did over 6 months ago when I got Ubuntu. I figured that one out quick. And they are still installed, according to Synaptic, and DVDs still don't work.

Totem Xine is installed now. No idea yet how I switch to it from normal Gstreamer Totem.

Amazing DVDs are actually an industry, and that people seem to watch them at all from their computers, with all the ridiculous crap you have to go through to do so! Don't even get me started on the vile filth that invented region encoding.

---

### Post by steeleyuk on 2009-05-30
I should have added, to make xine the default:

sudo update-alternatives --config totem

Then press either 1 or 2 depending on which order they are in.

And the DVD/film industry is a joke, I agree with you. They bitch at people who download, but when you buy legally you're stuck with region encoding, PUO's, CSS encryption, copy protection and playback licensing. /end rant

---

### Post by BastardNamban on 2009-05-30
Steeleyuk, I frickin' love you. IT WORKS! IT WORKS! AFTER 6 MONTHS, IT FINALLY WORKS!!!!

YESYESYESYESYESYES

Not only does Totem Xine recognize the proper titles & chapters, but even my uber-strange Glashutte DVD from Germany, a double sided enigma till now, works properly! Everything with mouse clickable menus, working. BEAUTIFUL!

THIS is why forums exist- for helpful people like you, and idiots like me. Now that I know what to do, I can help my friend get his DVD playback working, who has had the same problem for over a year.

Thank you very, very much. I can now watch everything nicely! You rock!

---

### Post by steeleyuk on 2009-05-30
A couple of extra points.

Gstreamer support for DVDs has got better and is still improving, in future versions you should be able to play DVDs very well without having to install Xine. It works pretty well on Jaunty at the moment for most DVDs.

Another point is that some DVDs (Hitch with Will Smith is an example) have a dodgy copy protection system included which causes problems in Linux and even some older standard DVD players.

Just a couple of things to keep in mind in case a DVD is playing up in the future. Generally though, if you use Xine, you won't go wrong.

---

### Post by xeticus on 2009-05-30
It's great when you get it to work. I'm using Kubuntu 9.04 and after aa lot of fiddling I finally found out to install Medibuntu. After I rebooted my Dragon player and Kaffeine now play DVD's perfectly. So beautiful when it works.

---

