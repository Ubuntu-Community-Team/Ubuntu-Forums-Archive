---
title: "Broadcom wireless help on dell, nothing is making sense!!"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by sdwinder on 2008-03-23
HI, i just recently installed ubuntu 7.10 on my dell laptop. And, well, the wired connection works, but the wireless does not, i have already gone through every guide that is posted on these forums and nothing is working. I have gotten to the point where the laws of physics and science are not agreeing with what is going on in my laptop, thats how confused and frustrated i am right now.

So, here is the issue, i have a broadcom wireless device, i know that for sure i have checked in the hardware info. I followed the guide on how to install the ndiswrapper and installing the bcmwl5.inf file. Now, im working off of a fresh copy of ubuntu, nothing installed yet, and when i try to run the inf, it says that it is already installed, which is impossible  because if gutsy came with the inf already installed, i wouldnt be here. So when i check to see if the driver is correct, it gives an invalid driver error in terminal. so basically, i have no idea where to go from here, ive tried everything there is to try and things that should be working arent working, my laptop is telling me i have things installed that i clearly do not. 

On a side now, i accidentally typed in bcmwi5.inf instead of l5 and ofcourse it said it couldnt find it, duh, but then i tried it again, and i got the same "already installed" error...which confused me even more...

So, please, someone help, i would really appreciate it because im at my wits end and it seems logic and reason dont work anymore.

---

### Post by caller#6 on 2008-03-23
I'm about ten minutes into researching the same problem, and you may be way ahead of me on this, but have you looked at the[ bcm43xx]("http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter") utility? More info[ here]("http://linuxwireless.org/en/users/Drivers/b43").

---

### Post by chuckH on 2008-03-23
Hey folks,

Before we jump to deep, have you checked your network settings?

System-Admin-network
Check to see if the wireless connection is enabled.
BTW, what model Dell laptop do you have?
Also, I've been down this road a few times, wrestling
with wireless drivers and changing wireless cards.
At times I had the Internet working but no access to file sharing.
The solution was to do a hard reboot to my D-Link DIR-625.
Anyways something to think about.
Cheers,
Chuck

---

### Post by sdwinder on 2008-03-23
There is no wireless connection to enable, all i have is modem and wired connection, thats it. I actually managed to get my wireless working once before on ubuntu, by doing the ndiswrapper installation of the bcmwl5.inf file, and it worked, even though it said invalid driver it still worked, but for some reason, now it says its already installed, even though it obviously isnt since i have a clean version of ubuntu installed.

---

