---
title: "Help needed with 3d games"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by doglike on 2010-01-13
When I run games like wolfenstein:enemy territory the play is extremely choppy at times and blocky.  I've tried changing settings in the game menu to fastest/highest to low resolutions, no textures, etc.  nothing has helped it still lags out in online play.  My ping goes from 90-100 when nothing is around me to 400+ when something happens like I'm getting shot at or I see someone in front of me even.
My card is a ati radeon x800 pro.  I don't know how to fix this, help please.

---

### Post by muddpup64 on 2010-01-13
How old is your computer/card?

---

### Post by doglike on 2010-01-13
My computer is a hp a330n.  I have 1gb ram installed and the card is from 2004.  [http://en.wikipedia.org/wiki/Radeon_R420](http://en.wikipedia.org/wiki/Radeon_R420)

---

### Post by tom.swartz07 on 2010-01-13
> **doglike said:**
> When I run games like wolfenstein:enemy territory the play is extremely choppy at times and blocky.  I've tried changing settings in the game menu to fastest/highest to low resolutions, no textures, etc.  nothing has helped it still lags out in online play.  My ping goes from 90-100 when nothing is around me to 400+ when something happens like I'm getting shot at or I see someone in front of me even.
My card is a ati radeon x800 pro.  I don't know how to fix this, help please.

What version of Ubuntu are you using/do you have a driver configured for your card?


I have a Radeon x1270, and, like yours, they no longer support it in Karmic. The latest version that has available drivers for your card is 8.10.

---

### Post by doglike on 2010-01-13
> **tom.swartz07 said:**
> What version of Ubuntu are you using/do you have a driver configured for your card?


I have a Radeon x1270, and, like yours, they no longer support it in Karmic. The latest version that has available drivers for your card is 8.10.

I configured the radeon driver for xorg, I'm pretty sure.  How do I check this?

If I want to go back to 8.10 how do I then find these drivers for my card?

EDIT: Using 9.04 ubuntu, I think. It was the latest one and I just installed it a few weeks ago.

---

### Post by tom.swartz07 on 2010-01-13
> **doglike said:**
> I configured the radeon driver for xorg, I'm pretty sure.  How do I check this?

If I want to go back to 8.10 how do I then find these drivers for my card?

EDIT: Using 9.04 ubuntu, I think. It was the latest one and I just installed it a few weeks ago.

I dont know if this is the same in karmic as it was in Jaunty, but you should be able to type in your terminal

```
sudo lshw
```
and look to see what your display adapters are

More concisely, you could use 
```
sudo lshw | grep display
```
to see if the display is claimed by your video card.

If you roll back to 8.10, you should be able to install it right from the restricted drivers app. If not- ATI definitely has the driver on their website. just search for the legacy support driver for your card. I had it working during my short stint with 8.10.

---

### Post by doglike on 2010-01-13
> **tom.swartz07 said:**
> I dont know if this is the same in karmic as it was in Jaunty, but you should be able to type in your terminal

```
sudo lshw
```and look to see what your display adapters are

More concisely, you could use 
```
sudo lshw | grep display
```to see if the display is claimed by your video card.

If you roll back to 8.10, you should be able to install it right from the restricted drivers app. If not- ATI definitely has the driver on their website. just search for the legacy support driver for your card. I had it working during my short stint with 8.10.

It says it is unclaimed
*-display:0 UNCLAIMED
           *-display:1 UNCLAIMED

Why do I have two? Is it because there is a built in graphics card also?  How do I "claim" the display?

---

### Post by tom.swartz07 on 2010-01-13
> **doglike said:**
> It says it is unclaimed
*-display:0 UNCLAIMED
           *-display:1 UNCLAIMED

Why do I have two? Is it because there is a built in graphics card also?  How do I "claim" the display?

Yeah, just as i suspected. Your graphics card isnt interfacing with Ubuntu.

There are a few threads on how to set up your ATI card with newer versions of Ubuntu, but most of them never worked for me.

BEFORE YOU TRY ANYTHING- look up and PRINT OUT how to restore your xorg.conf file. If something goes wrong, you will not be able to access any kind of graphical desktop to see how to fix it.

Here are some, you might have some better luck with them than I did.

[http://ubuntuforums.org/showthread.php?t=190133](http://ubuntuforums.org/showthread.php?t=190133)

[http://ubuntuforums.org/showthread.php?t=988596](http://ubuntuforums.org/showthread.php?t=988596)


Unfortunately, most of them all point to the same result; 'Just don't work'. You might be out of luck here, bud. Sorry.


I personally gave up looking after it crashed my xorg.conf file 3 times. :(

---

### Post by doglike on 2010-01-13
Thanks for the links and that info.
I think I'll roll back to 8.10, will 8.04 work also?  I have a cd of this already made.

---

### Post by tom.swartz07 on 2010-01-13
> **doglike said:**
> Thanks for the links and that info.
I think I'll roll back to 8.10, will 8.04 work also?  I have a cd of this already made.

8.04 will work even better! From some of the posts, 8.10 was the start of the 'tipping point' where people were getting problems. I only suggested it because its the LTS version, but if you have 8.04- go with that one! :D

---

### Post by doglike on 2010-01-13
> **tom.swartz07 said:**
> 8.04 will work even better! From some of the posts, 8.10 was the start of the 'tipping point' where people were getting problems. I only suggested it because its the LTS version, but if you have 8.04- go with that one! :D

Thanks I will try this, then.

---

