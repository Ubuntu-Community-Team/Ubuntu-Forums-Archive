---
title: "If it was W**dows, it would be blue-screening!"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Rover90 on 2010-05-06
Hi guys,

I really hoped it would take longer than two hours of using Linux before I had to go running for help..!

I have just installed Ubuntu 10.04 LTS (desktop i386 version) on a Dell Dimension 2400 PC (Celeron 2.4gHz). Having no experience of any distro of Linux, I've just reached the stage of looking around to see what I've got, but unfortunately, the screen keeps going blank, and can only be brought back with a reboot.

This blank screen alternates with the top half displaying vertical black and white bars every few seconds. It happens _every_ time I go to: System > Preferences > Screensaver, although it has happened at other seemingly random points as well. 

I've no idea whether it's relevant, but the first few times this happened, a text screen flashed up that began with "Speech dispatcher....." and ended with "Checking Battery State.....<OK>". Interestingly, the last time this problem occured, the screen never appeared, and it went straight to the black and white bars.

I'm wondering about re-installing it..? Is that worth a try, or am I ignorant (very :o) of something far more obvious?

Thanks for any help you can offer.

Regards
Roger V.

---

### Post by bumanie on 2010-05-06
Go to System --> Administration --> Hardware Drivers and see if there are any proprietary drivers that need enabling. It does it's own search for the appropriate drivers if this is the case and you just have to click 'enable' and they will be downloaded. This may not be the issue, but worth looking at rather than reinstalling.

---

### Post by Sealbhach on 2010-05-06
When you installed it, did you do it from a CD? I mean, did you boot up from the Ubuntu CD and enter a Live desktop session? Or did you use Wubi?

Also, it sounds like it might just be the screensaver not working correctly. Try going into Synaptic Package Manager (you'll find that in the System/Administration menu) and removing gnome-screensaver and any other screensaver packages you have installed.

Log out and log back in, and see if the problem persists.

.

---

### Post by bredman on 2010-05-06
Next time your system hangs, try the following combination of keys together
AltGr - SysRq - k
(you may have to stretch your fingers to hit all 3 at the same time)

This will restart your X server and should be much safer than any hitting the power-switch. The result should be to bring you back to the login prompt in a few seconds.

This won't fix your problem, but is better than rebooting. Also, if this works or doesn't work, please post the results. This may help to track down the scope of your problem.

---

### Post by Mark Phelps on 2010-05-06
According to the 10.04 Release Notes (which are always a good idea to read BEFORE installing anything), Intel 8xxx graphics-based machines are encountering display problems that are still in the process of being fixed.

So, until some fixed video drives come out from Intel, there may not be a fix for your display problems.

---

### Post by Rover90 on 2010-05-06
Thanks for the rapid response, Bumanie, Sealbhach, and Bredman! I'm now wondering if I've made an embarrassingly basic mistake..? Is Ubuntu dependent on an Internet connection? I inherited this particular PC due to it having a faulty modem - and I haven't replaced it yet...

As such, the suggestion that I check for proprietory hardware drivers just says that there aren't any, and I guess for the same reason I can't use Synaptec. I did a full install from a CD that I downloaded (and the md5sum checked out OK). I used the same CD to try out a 'Live CD' session on this Windows PC that I'm writing on now... It seemed good, so I went for it! As for restarting the x server - the key combination (I've got big hands!) resulted in a permanently blank screen, but the login prompt never re-appeared. I must admit, I'm not entirely sure what the x server is..? I did take a look at the Syslog in Log File Viewer, and there are a great many lines throughout the file that read: "...Serial 8250 : too much work for irq17". Now I don't know how to identify the irq's in Linux, but I'm wondering if this might be significant.

If it turns out I'm being a complete idiot about this, then I'm really sorry - but thanks again for your help and patience.

Best wishes
Roger

---

### Post by Sealbhach on 2010-05-06
Best thing is to attach a wired ethernet connection, to get it fully set up.

You don't need an internet connection to remove things in Synaptic, so go ahead and remove gnome-screensaver and any other screensavers you have (just to see if this fexes your problem).

.

---

### Post by Rover90 on 2010-05-06
That's an interesting point Mark. I must have missed any reference to Release Notes when I downloaded the software - I will go back and find them. Presumably an earlier release might solve my problem?

Thanks for your advice.
Roger

---

### Post by Rover90 on 2010-05-06
Amhran, you're a star! I've deleted the gnome screensaver, and it all seems to be holding up much better. Presumably this is down to the display problem referred to by Mark Phelps? If so, I guess I'll have to remember to switch off the monitor manually until the next release!! I'll broadcast the result to everyone tomorrow if it remains OK.
Thanks for your help. Much appreciated.
Roger

---

### Post by Sealbhach on 2010-05-06
That's good to hear Roger. Don't forget to hook up a wired connection if you can, so that you can install the display driver (you'll find that in System/Administration/Hardware Drivers). And also update your system to get the latest bug fixes.

.

---

