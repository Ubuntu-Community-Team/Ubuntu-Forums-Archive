---
title: "The sound is gone"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-12-19
My son's account on my computer has lost all sound.  I checked his settings on Alsa mixer and they were okay, so what could be the problem?

---

### Post by Sir Jasper on 2009-12-19
Hi,

Just in case you may not know.

Your Volume Control Screen will hopefully look like either the one on the top right or the one on the top left in the picture below.

[[img]http://i.imagehost.org/t/0611/volume.jpg[/img]](http://i.imagehost.org/view/0611/volume)

If it is the one on the right, if you see any tiny red crosses (especially in the first two columns) click to clear them and unmute your sound.

If it is the one on the left pressing m mutes and unmutes.

My regards

---

### Post by Mike3 on 2009-12-19
What sound card are you using?

---

### Post by Gulfvet91 on 2009-12-19
As I said in my original post, I checked to see if anything was muted and nothing was.

---

### Post by Gulfvet91 on 2009-12-19
The sound card is not the problem.  I am using the same sound card on the same computer and I have sound.

---

### Post by Mike3 on 2009-12-19
First, let's start with the simplest (possible) solution. Try going to Preferences -> Multimedia Systems Selector, and making sure that all of the settings are set to ALSA (or whatever your default sound driver architecture is) in addition to making sure that the output devices are correct. I think it could also be a bug in Pulseaudio. 
If your audio is booting to mute, and not changing at all, no matter what you do to change the volume level, you may wish to change the line that starts with
 # mute_and_zero_levels "$TARGET_CARD" First, open up Nautilus as root by entering in "gksudo nautilus" in the terminal. Navigate to "/etc/init.d/alsa-utils" Then, try to comment out the line of code I mentioned above. (CTRL+F to find it). Reboot. That *may* have been your problem. If this doesn't work, you can always check here:<http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala> Please, let me know if this works and if it doesn't I'll try to see if I can help some more.  [-o<

---

### Post by Chris Edgell on 2009-12-20
Sir Jasper,
I liked your post showing both in the terminal AND the mixer (would you call it "in the window"?).

Even though Gulfvet said he checked the Alsamixer, one cannot know if he was aware of the mute features there...I thought it was thoughtful to ask; so even though he must have known, anyone else checking for a sound problem can still benefit from your clear post about the mute.  (Remember how long it took me to find that mute?)

Luck to all
Happy holidays!

---

### Post by Chris Edgell on 2009-12-20
I MUST say, sometimes I think I don't click around enough -- then I click around TOO much.  Last time I didn't open those options listed at :  Applications > Multimedia > Mixer     I had struggled for some time to discover where that AlsaMixer had popped out from -- (and it apparently had popped out from the multimedia click).  Then it seemed so long until Ghost|BTFH pointed out those little red X's at the bottom of each slide (in the AlsaMixer)  --  indicated muted -- click red x to unmute.

So today after the subject had come up again, I said, "I'm going to click around and see what those other applications look like."  The first one I came to was the one in the screenshot, **aumix, it's called **..."What the heck is it?" I asked.  It looked like sound and volume, there was a word unmute, I clicked it... various little position markers all reset to ZERO.  I was quite sure I could click on the word "Mute" that the unmute had changed to, and that it would change back to how it had been.  But NOOO...The word changed back to unmute but all the zeros stayed at first position (instead of all the various positions on an imaginary horizontal scale).  I went to the AlsaMixer and the mute was not marked with the red X.....but there is now NO SOUND.  

Did you ever see this aumix, how do I get MY sound back?

---

