---
title: "Sound on Speakers even with Headphones in Karmic"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by dmaxel on 2010-01-07
Hi everyone!

I have a little sound problem going on. First, to clarify, I'm on a laptop, where the Fn keys for mute affect all sound, not just the speakers. Whenever I have my headphones plugged into my headphone jack, sound comes out of both the speakers and the headphones. I have looked around and only found complicated solutions for older Ubuntu versions. Any help for Karmic?

---

### Post by Darce on 2010-01-07
You only have this problem in Karmic and no other versions or OS's ?

---

### Post by dmaxel on 2010-01-07
I only have Windows installed with Ubuntu via Wubi. Windows has no problems whatsoever.

---

### Post by nikhilbhardwaj on 2010-01-07
it's oldfashioned
but you can use alsamixer to mute your headphone seperately

---

### Post by dmaxel on 2010-01-07
OK, I installed it, and it shows different streams like Front and LFE. However, whenever I mute one of them, it mutes both speakers and headphones. :( Am I clicking on the wrong ones or is there a different problem?

EDIT: After looking at the screenshot provided with ALSA Mixer in the Ubuntu Software Center, I figured out where Headphones should be located, but it doesn't show for me!

---

### Post by dmaxel on 2010-01-07
OK, I toyed around with it, and figured out that when I set Front on Mute/0%, that my headphones get muted but the speakers are still on. I want the opposite to happen though...

---

### Post by warfacegod on 2010-01-07
Complete shot in the dark. If there is a Back try setting that to mute not Front.

---

### Post by dmaxel on 2010-01-07
There's no Back lol. Only Master, PCM, Front, LFE, Line, CD, Mic, Mic Boost, Capture, Capture, Beep.

---

### Post by warfacegod on 2010-01-07
I'm going to guess that installing 9.10 as a dual boot with Windows would probably solve your problem. It seems extreme but I'm thinking there might be some translational problem with running ubuntu inside of Windows.

---

### Post by dmaxel on 2010-01-07
> **warfacegod said:**
> I'm going to guess that installing 9.10 as a dual boot with Windows would probably solve your problem. It seems extreme but I'm thinking there might be some translational problem with running ubuntu inside of Windows.
Even though that **might** be the problem, I actually have (or hope to have) doubts that that's the case. Could anyone else verify or at least comment?

---

### Post by VastOne on 2010-01-07
> **dmaxel said:**
> Even though that **might** be the problem, I actually have (or hope to have) doubts that that's the case. Could anyone else verify or at least comment?

Try this

[http://www.clububuntu.com/2009/01/how-to-fix-sound-comming-from-both.html](http://www.clububuntu.com/2009/01/how-to-fix-sound-comming-from-both.html)

---

### Post by dmaxel on 2010-01-07
> **VastOne said:**
> Try this

[http://www.clububuntu.com/2009/01/how-to-fix-sound-comming-from-both.html](http://www.clububuntu.com/2009/01/how-to-fix-sound-comming-from-both.html)
Like I already said, I tried muting Front, and it muted my headphones and not the speakers, where I wanted it the other way around.

---

### Post by VastOne on 2010-01-07
> **dmaxel said:**
> Like I already said, I tried muting Front, and it muted my headphones and not the speakers, where I wanted it the other way around.

Sorry, did not catch that.

How about disabling surround sound and see if that helps

---

### Post by VastOne on 2010-01-07
And there is this

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by dmaxel on 2010-01-07
Tried it, nothing happened. I didn't even get a Switches tab. I believe that was for 8.04, not 9.10.

---

### Post by danwosere2007 on 2010-01-07
Sorry for the belated reply dude, its easy to get sidetracked and what not. Sadly in this circumstance i am probably going to be about as useful as a pair of chopsticks at a rice convention though. You'd need one of the super mega technical dudes on the case i reckon the ones that say print your screen oh yeah i can see the problem its that "insert illegible computer lingo here" thats causing it.Now if you just "insert crazy computer speak here" then all will be good. Some day i aspire to be the dude handing out crazy computer language advice, but for now i suppose i shall have to be the dude making idle banter and attempting to be slightly humourous in the process ;)As some other dudes suggested it sounds like it could be a wubi emulating ubuntu as opposed to actually running it on your system sorta problem, but as ive found with problems theres usually some dude or another who can sort you out with a decent alternative/work around =P.  

good luck with your problem dude!

-Dan

---

### Post by dmaxel on 2010-01-08
Hmm, oh well. I'm just gonna have to see what I'm going to do, whether to keep the Wubi setup or to actually make a partition for Ubuntu, as well as if I might get Ubuntu on my desktop. We'll just have to see I guess. Thanks for all the effort to get this problem solved!

---

### Post by sandyd on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=780029](http://ubuntuforums.org/showthread.php?t=780029)

---

### Post by dmaxel on 2010-01-08
> **carlee said:**
> [http://ubuntuforums.org/showthread.php?t=780029](http://ubuntuforums.org/showthread.php?t=780029)
Sorry, but basically it offers the same solution as here:
> **VastOne said:**
> And there is this

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)
...and again, it might work for Hardy, but everything is different in Karmic.

---

### Post by sandyd on 2010-01-08
> **dmaxel said:**
> Sorry, but basically it offers the same solution as here:

...and again, it might work for Hardy, but everything is different in Karmic.
please read the whole thread.
esp post #7

---

### Post by dmaxel on 2010-01-09
> **carlee said:**
> please read the whole thread.
esp post #7
The first part of #7 didn't do anything, like I tried above, and the second part doesn't even go anywhere. Can't find ./alsaconf.sh

---

### Post by pastir on 2010-01-09
I have the same problem on my laptop and haven't been able to fix it.  Karmic sound is set up differently than older versions, so solutions that worked for me before don't work now.  I used these versions as dual-boot with XP and now have Ubuntu 9.10 as the only OS. (Acer 3050-1594, ATI Radeon Xpress 1100)

I was looking at my settings on the hardware tab of sound preferences and noticed that the profile for my device was set to Analog Stereo Duplex.  I tried all of the different options and only got sound for the analog output and duplex.  I then noticed that under the Internal Audio device that was selected it listed only 1 output and 1 input.  I think this is the problem.  My computer sees the headphones and internal speakers as only one device.  Unfortunately, I don't know how to change this.

---

### Post by J V on 2010-01-09
Under the output tab there should be another selectbox at the bottom, thats the one you should mess with...

---

### Post by pastir on 2010-01-09
Oh yeah.  I forgot that I checked that too.  With the connector set to Analog Output I get sound from the speakers and headphones.  When I change it to Analog Headphone I get no sound from either device.

---

### Post by J V on 2010-01-09
let me guess, your headphones are plugged into your speakers? They are both getting sound from the same source lol, plug them into different plugs and try again :P

---

### Post by pastir on 2010-01-09
My speakers are internal.

---

### Post by J V on 2010-01-09
ooh... no idea then, not sure how sound is hooked up...

---

### Post by dmaxel on 2010-01-10
Hmmm, I'm not seeing some of the things you guys are talking about...should I post screenshots of what I am seeing in my Sound Preferences?

---

### Post by dmaxel on 2010-01-10
Hmmm, well this is interesting. Instead of uninstalling my wubi setup and installing Ubuntu directly onto the hard drive just to try out if that's the problem, I came to the genius idea of using a Live CD >:D

Turns out that Wubi might be the problem.....either that or just a bad Ubuntu installation. Either way, I'm going to put it directly on the hard drive now, so no problems anymore!! Hooray!! I love Ubuntu now because it loves me :D

Thanks very much for everyone's efforts into solving this.

---

### Post by dmaxel on 2010-01-11
Well, this sounds like more fun.

After trying it out with the Live CD, I went ahead and installed Ubuntu directly onto the hard drive. However, it didn't work anymore! I re-inserted the Live CD and tried the headphones a couple of times, reloading every time. I found out that sometimes it works, sometimes it doesn't. I also noticed that whenever it did happen to work, Ubuntu also asked me for a password for the keyring whenever I entered the password to my LAN. Whenever Ubuntu just accepted the LAN password without asking for a keyring password, the speakers stayed on when headphones were in. Help? hehe

---

### Post by dmaxel on 2010-01-17
Bump?

---

### Post by dmaxel on 2010-01-17
Well, this is odd. After trying to reinstall Ubuntu, it finally works! Do not ask me how I did it, as I don't know myself. But it seems to work now. I'll call in case it starts failing on me again. :P

---

### Post by pastir on 2010-01-22
I still haven't gotten mine to work.  I wonder if it's related to the lack of support for my ATI graphics card.

---

### Post by Apollo22 on 2010-03-12
I just registered as i've been having the same problem. Running an ASUS laptop with Card: HDA Intel, Chip: VIA-VT1708S.

I tried other solutions and none of them worked, running 9.10. However after playing around i got this


my settings in alsa mixer (sudo alsamixer) are as follows

Master F: 100 100
Headphones: 100 100
PCM: 100
Front: MM (Muted "M" key when highlighted)
Front mi: 0 0
mic: 0 0 
Independent: off

Under the Sound Preferences for Gnome i have this from the default.

Hardware is set to output and not duplex.
Output Connector is set to Analog Headphones.

It seems setting it on Analog Headphones and playing with the alsa mixer reverses the role of being able to disable the headphones and not the speakers. I am running my headphones without my speakers doing any sound.

I'm not that technical and this was only after playing around, so if anyone has a more sophisticated fix. Or if this is old and i'm blind and missed the more sophisticated fixes. O well, i happy to get it working and wanted to share.

---

