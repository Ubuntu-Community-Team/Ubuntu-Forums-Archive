---
title: "HELP!Jack &amp;  Rosegarden installation HELP!"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by emiliec15 on 2009-12-13
I can't seem to get the jackd server to stay running and I apparently need to add a kernel or find some other way to get this program running.

I tried to start the jack server via the jack audio connection kit (available via repo) but it gives me these messages.  

 p, li { white-space: pre-wrap; }  jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1215939824, from thread -1215939824] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]20:10:18.151 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]20:10:18.152 Post-shutdown script...[/COLOR]
 [COLOR=#990099]20:10:18.153 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]20:10:18.623 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]20:10:19.553 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

If I proceed after the message about the jack server not running rosegarden gives me this message!


System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.

---

### Post by emiliec15 on 2009-12-13
Someone PLEASE HELP!!

---

### Post by 4Orbs on 2009-12-13
I think you need to install the realtime kernel for your version of xubuntu. You can find it listed in Synaptic under linux-image-xxxxx -rt and it should allow jack to work correctly with rosegarden. I've never used the rt kernel with xubuntu, but before you boot into the rt kernel you might want to set the screen resolution back to auto or default and maybe even deactivate your proprietary driver for the graphics card so you don't boot into a low-graphics mode error on the new kernel. You also might want to wait for someone else to come along with a better answer before trying the rt kernel. Something else that might interest you... the ubuntu studio desktop installs a bunch of good stuff, including the rt kernel and gnome desktop but it is a huge download and could take a log time to complete. It is cool though.

---

### Post by emiliec15 on 2009-12-14
Had an idea from your post.  I'm going to try installing the audio section of ubuntustudio AND then re-installing Rosegarden.  Perhaps it'll work then.

If it does I will just have to ferret out the packages I don't need, and if I screw up just reinstall everything and try again.  I am going to make a list of them.  Installing the audio section does not include rosegarden or the linux-image-xxxx-rt kernel.  Dunno.

Wish me luck.  It's only 180 non-essential packages to hopefully get Rosegarden to work.  Could be worse could be 1000!!

---

### Post by 4Orbs on 2009-12-14
I think the realtime kernel might be the most important part of it all. And there might be some crucial gnome dependencies also. Not sure.

---

### Post by emiliec15 on 2009-12-14
Currently downloading the rest of the ubuntustudio packages + the rt kernel.  I hope this works.  Even if I have to switch to ubuntustudio instead of ubuntu.  

I want my all of the apps I want!  In the end it will be probably much smaller than ubuntustudio, but I have to get everything working before I can remove the bloat!

---

### Post by 4Orbs on 2009-12-14
You also may want to run through [this how-to]("http://ubuntuforums.org/showthread.php?t=766683") so you'll be sure to have all the necessary codecs and other important pieces.

---

### Post by emiliec15 on 2009-12-14
Well, I'm now running on the rt kernel and I have ubuntu studio completely installed and I am still having no luck in getting the jack server/client setup to work.  

Grrr.... 500+ packages hoping I would get this to work and still nothing... bummer... any suggestions on what to do now would be appreciated!

---

### Post by madman559 on 2009-12-14
If you aren't using realtime you can just disable it. I had the same problem and that fixed it for me.

---

### Post by themusicalduck on 2009-12-14
Yeah, if you uncheck Realtime under Setup then you can use it on a normal kernel. You won't get great latencies but that won't really matter if you're just recording audio.

---

### Post by emiliec15 on 2009-12-14
Well that works but I can't use the notation editor and that is the part of the reason I am trying to get it installed!!  

I've got everything installed from ubuntustudio AND I have the rt kernel installed, however I can't seem to manage to get it running ON the rt kernel....

Your suggestions work on the regular kernel and if you can get the notation editor to play and notate on a regular kernel please let me know how!!  

Otherwise I need to figure out how to get this running on the rt kernel.:(

---

### Post by 4Orbs on 2009-12-14
Did you add the connections between jack and rosegarden? You need to manually add each program in and out to jack. You do it from the jack interface and you may need to point rosegarden to the jack server. The initial setup takes some time, but once you get the hang of it... it's a great and flexible tool. I haven't used these things for a long time or I would offer more help. Spend some time reading about it and you'll see that jack and the rt kernel are central to the whole process that drives most of the audio apps. I don't recall any of it hooking up automatically until after you've done the initial configuration.

---

### Post by emiliec15 on 2009-12-14
To 4Orbs, yes I have on the generic kernel, however on the rt kernel I can't get the jack gui to be visible so on that one no.   

When I ran rosegarden on the generic kernel (with realtime disabled) I couldn't use the note editor (note notation or whatever it's called in it).  

I'm currently running on the rt kernel but I don't have the menubar at the top that comes by default so I don't know what happened there so I need to get that back.
Also, whenever I try running the jack program from the menu AND get it to show up if anything happens (ie its own boxes cover each other up I can't see where to click for the buttons let alone if it is seeing rosegarden.

---

### Post by 4Orbs on 2009-12-14
If I understand correctly, the titlebars at the top of the application have disappeared (and probably those on nautilus, where the minimize, close buttons are located)? If that is the case, they should reappear if you turn off desktop effects in the Ubuntu Appearance mgr. Without the titlebar, you can't grab a window with the cursor and drag it around the desktop. If you are unable to restore the titlebar, I think you can hold the alt or ctrl button down and drag a window without a titlebar.

---

### Post by emiliec15 on 2009-12-14
I rebooted and went with the generic kernel because not being able to see the menubar at the top (just the menu bar at the top and bottom of the screen).  I can still see the titlebar on the apps with their name 'string' and the minimize, and close buttons.  I could drag them around without a problem except for the fact that doing so would leave a trial behind over whatever window I drug it over, except for the jack gui, the other applications THAT I COULD see I would clear themselves relatively quickly(less than a second most of the time [barely noticeable) but the jack gui never would which made it impossible (seeing as I don't have it memorized in the least) for me to configure jack for rosegarden.

When I tried to run rosegarden without configuring it nothing came up (even when it wasn't working I saw the splash screen at least for a second or two.)

I don't know what I need to do...

---

### Post by 4Orbs on 2009-12-14
Man, it sounds like the problems are stacking up rather than going away. First, the window and panel (taskbar) problems... if you deactivated the proprietary driver for your graphics card before installing all the studio stuff, you can reactivate it and with any luck it will play well with the rt kernel and you should get smooth non-buggy window action. If you'd rather try getting this stuff going on the standard kernel... the other posters said that's a better idea... then work with the standard kernel instead of rt for now. If the dependencies for jack and rosegarden have all been installed, they should work with either xfce or gnome. I'm assuming your computer has enough gusto to run these resource hungry apps.

---

### Post by emiliec15 on 2009-12-14
I think it has enough resources.... 

However, I need to either get it to work with the note notation function or I might as well forget it.  Without that function I might as well find a different app.  If its not going to be possible for me to get it work on with that feature does anyone know of any app that RUNS on the generic (standard) kernel that I can use to compose AND play music on.  I don't care if it is compose it in ONE and play it in another if it is what I need to do....

EDIT: I forgot to mention that if I can't I WILL find someway to get this to work.

---

### Post by 4Orbs on 2009-12-14
You also need to install kdebase-bin which includes kdialog so you'll be able to import projects and save your new projects... but that doesn't have anything to do with the need for high quality realtime source. I'm working with this bad boy now, and I'll be back tomorrow when and if I get anything figured out or not.

---

### Post by emiliec15 on 2009-12-14
4Orbs thanks for the help and if you figure out a way to get it work with xubuntu, please let me know.  I am going to begin removing the packages that I don't need.  Like agave, genpo, freebirth and the like.  I will try not remove any of the ones THAT MIGHT be helpful in getting this to work on xubuntu.

---

### Post by emiliec15 on 2009-12-14
Well, I am almost there.... no menus still.... and ONLY can't get the jack server to stay up and running but other than that I am done....  ONLY if it would stay up....  Anyone know how to get it to do that?

---

### Post by emiliec15 on 2009-12-14
AND NOW I find this:

[http://ubuntuforums.org/showthread.php?t=1345865&highlight=ubuntu+rosegarden](http://ubuntuforums.org/showthread.php?t=1345865&highlight=ubuntu+rosegarden)

Grrr... why couldn't I find that DAYS AGO!

---

### Post by 64Guitars on 2010-01-03
Have you edited /etc/security/limits.conf as described in the FAQ?

[http://jackaudio.org/faq]("http://jackaudio.org/faq")

That made the difference for me.

---

