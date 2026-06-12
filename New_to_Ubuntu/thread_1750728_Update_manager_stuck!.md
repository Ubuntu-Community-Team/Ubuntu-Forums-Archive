---
title: "Update manager stuck!"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by hman469 on 2011-05-05
I am running 10.10 When I came in from work My update manager said there were updates available so I did as I always do and told it to install all updates. But after an hour it is still stuck in the 'applying changes' state. Below is a screen shot of the update window, I am afraid to shut mu computer off for fear of not being able to re-boot. I have been running ubuntu for a few years, but still consider myself a noob, more or less.  Any help is greatly appreciated!

---

### Post by jtarin on 2011-05-05
> **hman469 said:**
> I am running 10.10 When I came in from work My update manager said there were updates available so I did as I always do and told it to install all updates. But after an hour it is still stuck in the 'applying changes' state. Below is a screen shot of the update window, I am afraid to shut mu computer off for fear of not being able to re-boot. I have been running ubuntu for a few years, but still consider myself a noob, more or less.  Any help is greatly appreciated!That's just great!!! I'm running that same update at home now.:P
Well what I would do is open another terminal and use the command "xkill" and follow the directions.Look in your "/var/apt/cache/archive/partial" directory (if it exists) and remove anything there. Then try to run again and look for any errors. Can't wait until I get home.

---

### Post by hman469 on 2011-05-05
> **jtarin said:**
> That's just great!!! I'm running that same update at home now.:P
Well what I would do is open another terminal and use the command "xkill" and follow the directions.Look in your "/var/apt/cache/archive/partial" directory (if it exists) and remove anything there. Then try to run again and look for any errors. Can't wait until I get home.


Can this crash or harm my system? I haven't backed things up in a while and I have 2- 500 gig drives full of stuff.

---

### Post by jtarin on 2011-05-05
All it does.if you follow the instructions, is to close the window you click on.
Then back things up an try again. I use this xkill trick all the time. It's faster than TOP.

---

### Post by hman469 on 2011-05-05
> **jtarin said:**
> All it does.if you follow the instructions, is to close the window you click on.
Then back things up an try again. I use this xkill trick all the time. It's faster than TOP.

So its basically the same as a 'force quit'?

---

### Post by hman469 on 2011-05-05
Oops, I think I broke something!  I used the 'xkill' and it stoped the update manager, then I checked the var/cache/apt/archives/partial folder and it was empty. So I got the bright idea of shutting down the system and starting it up again.  It started to shut down like normal then the screen displayed "Ubuntu 10.10" with four white dots below it that alternated between whie and yellow as though it was counting down and froze there for 10 minutes.  Now the screen is blank but my puter is still running, or at least the cooling fans are and the hdd lights is slowly flashing!  What do I do now?:confused:

---

### Post by hman469 on 2011-05-05
OK!  Sorry, I ran out of patience and pressed the reset button and after logging in I got the notice in the first screenshot, then I got the notice in the second screenshot.  So I tried the 'sudo apt-get install -f' and got 'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.' so I ran 'sudo dpkg --configure -a' and then 'sudo apt-get install -f' and things seem ok now.  

:DThanks for your help jtarin!

So how do I mark this thread solved?

---

