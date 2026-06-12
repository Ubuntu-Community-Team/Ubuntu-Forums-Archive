---
title: "won't run after install &quot;inside&quot; windows xp"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by gscratch on 2010-07-31
I am a new newbie (less than 5 minutes with ubuntu).
 
I have a Windows XP sp3 machine with generic hardware (AMD chip). I downloaded the 10.04 desktop, burned it onto a cd (on another machine). I put the CD into the running WXP machine and it auto-ran. From the choices, I picked "install inside Windows". It took about 5 minutes to complete. I rebooted immediately on that screen when given the choice. I picked ubuntu from the boot.ini screen
 
I get the "ESC to select boot options" prompt (I did nothing), then the screen goes blank, the harddisk spins. Nothing happens for at least ten minutes when I finally gave up, rebooted, selected Windows from boot.ini, opened a browser and posted this question.
 
I apologise if this is answered elsewhere. A simple search of this forum did not find anything that seemed relevant. thanks for any advice.
Glen

---

### Post by sikander3786 on 2010-07-31
Hi.

Seems like a hardware issue. Which graphics chipset your machine has got? Intel, ATI or NVIDIA?

---

### Post by -kg- on 2010-07-31
First, you should have booted to the Live CD to see whether there *were* any hardware issues, or issues with the .iso download or burn.

When troubleshooting a problem, always eliminate the simplest things first.  Did you check the md5 checksum after download?  Did you burn the .iso at as slow a speed as possible to ensure an error-free burn?  Try booting to the Live CD Desktop (if you haven't already) to ensure that the problem isn't the fault of the CD itself.  That's the easiest possibility to check.

Other than that, most Wubi installations that I've heard of work without a hitch.  I have never done a Wubi installation (guess I ought to, for experimentation purposes), but perhaps you should have hit the escape key for the boot options.  Why it would go to a blank screen and have the hard drive running I don't know.

At any rate, I would try booting to the Live CD desktop first, to make sure the burn is good and that there are no hardware issues.  You also might want to check the md5 checksum.  If there are issues with the md5, you might want to try downloading 10.04 again using a torrent from the Ubuntu-supported torrents.

---

### Post by gscratch on 2010-08-01
Thanks for the replies.  It didn't occur to me that the ubuntu desktop CD itself could be bad.  I booted from the CD.  I get the red/white dots screen, then nothing.  I also have a ubuntu server, which boots directly into the list of choices.
 
I will download the desktop kit again.
Glen

---

### Post by gscratch on 2010-08-02
I have downloaded another copy of Desktop and its hashes are correct.  I will made another CD (burn as iso) and try again.
thanks,

---

### Post by gscratch on 2010-08-04
just to let you know that I have successfully installed and run Desktop.  I now have to get better monitor resolution, and I see a couple posts on that subject
 
thanks, again, for your help
Glen

---

