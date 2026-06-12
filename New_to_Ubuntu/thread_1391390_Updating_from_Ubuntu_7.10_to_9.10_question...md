---
title: "Updating from Ubuntu 7.10 to 9.10 question.."
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Shadyboy on 2010-01-26
So I have given up on running slackware on my labtop, beacuse I lack the knowledge on many of the settings and configs in linux.

So I have decided to install Ubuntu on my labtop. 
But I know that I have to install 7.10 beacuse of mye graphic card, ATI Radeon Xpress 1100. I have allready downloaded the driver install file for my graphic card.

The thing I am wondering on is this :

I am thinking on installing the drivers right after I install 7.10
and after that I am thinking of uppgrading to 8.04 and then to 9.10 if its possible.
And the thing is, will I keep my ATI drivers installed if i update?

---

### Post by Merk42 on 2010-01-26
7.10 is no longer supported so I don't think the repos are available to upgrade.
I suggest installing 8.04 or 9.10 from scratch.

If you feel you NEED to install 7.10 first, you can use the alternate CD of 8.04 or 9.10 to upgrade but again, I'd recommend installing from scratch.

---

### Post by adam814 on 2010-01-26
Who says it's "needed" for your video card?  The ATI proprietary drivers dropped support for it after Catalyst 9.3 (which was about a month before the Jaunty release so it should work fine out-of-the-box in Hardy or Intrepid).  In any case you don't absolutely need the ATI drivers to run Linux, just if you need hardware 3D support.  If that's not an absolute must you should even be able to run Karmic if you want.

---

### Post by theozzlives on 2010-01-26
7.10 has long since reached end of life, best thing to do is back up /home and re-install.

---

### Post by howefield on 2010-01-26
> **Shadyboy said:**
> I am thinking on installing the drivers right after I install 7.10 and after that I am thinking of uppgrading to 8.04 and then to 9.10 if its possible.

You'd need to go through all the intermediate version, 7.10 > 8.04 > 8.10 > 9.04 > 9.10, that is a lot of opportunities for things to go wrong.

If you can't install 9.10 straight off, might be better going with 8.04, which is supported and then upgrading when 10.04 which you will be able to do without the intermediate steps as you will be going from LTS to LTS.

Can't answer on the graphics drivers specific question.

---

### Post by theozzlives on 2010-01-26
> **howefield said:**
> you'd need to go through all the intermediate version, 7.10 > 8.04 > 8.10 > 9.04 > 9.10, that is a lot of opportunities for things to go wrong.

If you can't install 9.10 straight off, might be better going with 8.04, which is supported and then upgrading when 10.04 which you will be able to do without the intermediate steps as you will be going from lts to lts.

Can't answer on the graphics drivers specific question.

+1

---

### Post by kansasnoob on 2010-01-26
> **adam814 said:**
> who says it's "needed" for your video card?  The ati proprietary drivers dropped support for it after catalyst 9.3 (which was about a month before the jaunty release so it should work fine out-of-the-box in hardy or intrepid).  In any case you don't absolutely need the ati drivers to run linux, just if you need hardware 3d support.  If that's not an absolute must you should even be able to run karmic if you want.

+1!

---

### Post by zipperback on 2010-01-26
> **Shadyboy said:**
> 
So I have decided to install Ubuntu on my labtop. 
But I know that I have to install 7.10 beacuse of mye graphic card, ATI Radeon Xpress 1100. I have allready downloaded the driver install file for my graphic card.


There isn't any need to install 7.10 first.
I have an Acer Laptop with the same video as yours.
The current version of Ubuntu will support it just fine.

- zipperback
:popcorn:

---

### Post by Shadyboy on 2010-01-26
Oh how funny. 
Not running linux ATM. 

The thing is that 7.10 is the last Ubuntu that I can install my drivers in. Beacuse newer ones have Catalyst 9.4 in them. And my drivers are in Catalyst 9.3

[http://ubuntuforums.org/showthread.php?t=1109768]("http://ubuntuforums.org/showthread.php?t=1109768")

And since I am a gamer, and while I wait for my new computer, I need to at least mannage to play on something. And in the same time, run Linux.

--------------------------------------------

And after reading this post : [http://ubuntuforums.org/showthread.php?t=1363504]("http://ubuntuforums.org/showthread.php?t=1363504")
I dont know what to think any longer...

---

### Post by mechro on 2010-01-26
[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)

---

### Post by Shadyboy on 2010-01-26
> **mechro said:**
> [https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)

Will I still be able to game? And now I am thinking of games like, Half life and WOW

---

### Post by mechro on 2010-01-26
> **Shadyboy said:**
> Will I still be able to game? And now I am thinking of games like, Half life and WOW

I've no idea.

Are those Linux games?

Try the LiveCD before installing.

---

### Post by Shadyboy on 2010-01-26
Okey. Then I ask this another way then. How "good" are the open source drivers then? Can they be compared to the ones from ATI?

---

### Post by adam814 on 2010-01-26
I hadn't even counted on the Xpress 1100 being an r500 series card.  It has 3D support using the open-source driver.

From my experiences (as long as your hardware is supported and yours is) they perform far better than the drivers from ATI.  True, I still don't have hardware 3D for mine (RV620 chipset), but at least with the open-source drivers it doesn't take 2 full seconds to do something as simple as minimize a window.  And I don't have nearly the video tearing problems I did with fglrx.

---

### Post by 3rdalbum on 2010-01-26
> **Shadyboy said:**
> Okey. Then I ask this another way then. How "good" are the open source drivers then? Can they be compared to the ones from ATI?

Why not try from a live CD.

---

