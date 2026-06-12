---
title: "Installation on an Old Dell"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by devilray on 2011-01-29
**Installing to a Dell Dimension 4550**             
                                                                I'm truly an absolute beginner to Ubuntu.  I'm trying to  install Ubuntu (*Maverick Meerkat)* on a Dell Dimension 4550 (Pentium 4, with 1 gig RAM).  I  burned the ISO from the main Ubuntu download page.  I place the CD in  the Dell and boot from the CD drive, it seems to be going through the  process, but after a couple of minutes it stops and all I see is a  purple screen with Ubuntu written in white.  Nothing else.  Am I missing  something?

I posted the same message on the Dell Ubuntu Support page in these forums and received no response.  

Thanks for any suggestions.

---

### Post by cairnzi on 2011-01-29
hey, what video card do you have?

---

### Post by irv on 2011-01-29
To trouble shoot: first check the CD for errors. Next try booting it in another computer to see if there is something wrong with the CD player. I had and older PC I got at a rummage sale, and I got Ubuntu to install but it took a long time. The first screen sat for some time before it went on so make sure you give it time to load into memory. As I remember it took over 15 minutes to boot to the install screen.

---

### Post by devilray on 2011-01-29
I checked the CD and it worked fine on another PC.  When I try to boot the Dell from Windows XP it says I'm missing a HAL32.dll could that be interrupting the Ubuntu install?  Since the dell is 9 years old I don't have the XP start-up disk.  

I'm not sure of the video card.  I do know it's an aftermarket card installed maybe 7 years ago??

Thanks I'll keep working on it.

---

### Post by scottmac112 on 2011-01-29
> **devilray said:**
> I checked the CD and it worked fine on another PC.  When I try to boot the Dell from Windows XP it says I'm missing a HAL32.dll could that be interrupting the Ubuntu install?  Since the dell is 9 years old I don't have the XP start-up disk.  

I'm not sure of the video card.  I do know it's an aftermarket card installed maybe 7 years ago??

Thanks I'll keep working on it.

No, anything on the hard disk will have no bearing on booting from a Live CD. Could you maybe try the alternate install CD? It might install a little smoother. What it sounds like is it's just taking too long to boot the Live CD and you're assuming it's hung at the splash screen.

---

### Post by irv on 2011-01-29
> **scottmac112 said:**
> No, anything on the hard disk will have no bearing on booting from a Live CD. Could you maybe try the alternate install CD? It might install a little smoother. What it sounds like is it's just taking too long to boot the Live CD and you're assuming it's hung at the splash screen.

I agree. I said this in post #3. It just might be sitting at the splash screen while the live CD loads.

---

### Post by devilray on 2011-01-29
Up and running smoothly.  Maybe I just needed to intimidate the Dell with a hammer.  

Thanks for the help!

---

### Post by Jerry N on 2011-01-29
Are you trying to install Version 10.10?  See [http://ubuntuforums.org/showthread.php?t=1673461&highlight=cmov&page=2](http://ubuntuforums.org/showthread.php?t=1673461&highlight=cmov&page=2) for a discussion about a CMOV instruction that doesn't exist on older processors.  You might try 10.04, which doesn't seem to depend on that instruction but I don't think any recent version of Ubuntu is going to perform very well on a 9 year old computer.  I know - some people think Ubuntu performs adequately on those older machines but different people have different view of what is acceptable.  Have you tried Puppy Linux?

Jerry

---

