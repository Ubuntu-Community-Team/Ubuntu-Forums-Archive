---
title: "How do I change the boot splash in Jaunty?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-05-11
I've been told that the Jaunty release eliminated Usplash, so all my custom usplash themes won't work any more. So, how do I go about customizing my boot splash?

I installed startup manager, but obviously that won't work if usplash won't work.

Any ideas are welcome!

Thank you!

---

### Post by LesterPalooza on 2009-05-11
Same here mate. Searched google for solutions to change boot splash in 9.04 but all I found were "Ubuntu 9.04 New Boot Splash" and "Change Boot Splash in Ubuntu <Insert Ubuntu Version Here>"

---

### Post by doctorbighands on 2009-05-11
> **LesterPalooza said:**
> Same here mate. Searched google for solutions to change boot splash in 9.04 but all I found were "Ubuntu 9.04 New Boot Splash" and "Change Boot Splash in Ubuntu <Insert Ubuntu Version Here>"

Exactly! That's all I've found after extensive searches. There are lots of articles about how great the new Jaunty boot splash is (personally, I disagree), but nothing about how to change it.

---

### Post by doctorbighands on 2009-05-11
...bump

There must be a way...

---

### Post by doctorbighands on 2009-05-12
I just tried using "sudo make" and "sudo make install" using the source code. Still no luck. It still dumps into verbose mode when booting.

There MUST be a way to change the splash screen. Why would the developers take away the simple, straightforward functionality of Usplash?

---

### Post by mojolobo on 2009-05-12
You need to install startup-manager . i used Synaptic . startupmanager . 1 word . 

After installing look under administration. You will see options here

Ive used it to disable my boot splash . I like to see whats loading

---

### Post by doctorbighands on 2009-05-12
> **mojolobo said:**
> You need to install startup-manager . i used Synaptic . startupmanager . 1 word . 

After installing look under administration. You will see options here

Ive used it to disable my boot splash . I like to see whats loading

No, startup manager doesn't do the job in Jaunty. I tried, and it didn't work. That's what's so frustrating!

---

### Post by TheSappy on 2009-05-12
> **doctorbighands said:**
> No, startup manager doesn't do the job in Jaunty. I tried, and it didn't work. That's what's so frustrating!

Same here.

---

### Post by doctorbighands on 2009-05-12
bump again

I still can't find an answer for this. I know it probably seems like a minor issue, but it also seems like there should be a relatively simple answer out there somewhere.

---

### Post by mikewhatever on 2009-05-13
What's the rash? Is someone dying from looking at the default splash?
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=usplash&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=usplash&sa=Search)

---

### Post by aniruddha on 2009-05-13
Hey, this is how I got some non-default themes working:

1. Install startupmanager 
2. install the usplash and usplash-dev packages (just search for usplash in synaptic)
3. download theme sourcecodes from gnome-look or wherever. Don't download the theme, the source code should do.
4. open up the terminal, go to the directory where you downloaded the theme source code 
5. run "sudo make"
6. run "sudo make install"
7. now open up startupmanger, and add and select the new theme you have compiled. 

footnote: it may be best to use themes which explicitly mention compatibility with jaunty. I haven't used any others and if you do try them, let me know if they work (am missing that beautiful sunrise...)

no worries

---

### Post by LesterPalooza on 2009-05-13
> **aniruddha said:**
> Hey, this is how I got some non-default themes working:

1. Install startupmanager 
2. install the usplash and usplash-dev packages (just search for usplash in synaptic)
3. download theme sourcecodes from gnome-look or wherever. Don't download the theme, the source code should do.
4. open up the terminal, go to the directory where you downloaded the theme source code 
5. run "sudo make"
6. run "sudo make install"
7. now open up startupmanger, and add and select the new theme you have compiled. 

footnote: it may be best to use themes which explicitly mention compatibility with jaunty. I haven't used any others and if you do try them, let me know if they work (am missing that beautiful sunrise...)

no worries

Will try that. I can't believe Startup Manager cannot change boot splashes in Jaunty. :( You think it's a bug? I'm just tired of the default splash. XD

---

### Post by doctorbighands on 2009-05-14
> **aniruddha said:**
> Hey, this is how I got some non-default themes working:

1. Install startupmanager 
2. install the usplash and usplash-dev packages (just search for usplash in synaptic)
3. download theme sourcecodes from gnome-look or wherever. Don't download the theme, the source code should do.
4. open up the terminal, go to the directory where you downloaded the theme source code 
5. run "sudo make"
6. run "sudo make install"
7. now open up startupmanger, and add and select the new theme you have compiled. 

footnote: it may be best to use themes which explicitly mention compatibility with jaunty. I haven't used any others and if you do try them, let me know if they work (am missing that beautiful sunrise...)

no worries

This worked for me, with one exception: When the new splash screen comes up, it has a giant black block near the top of the screen, like a blank space. I tried two different splash screens, and had the same issue with both.

One problem solved, another revealed...*sigh*

Thank you for the help, though!!

---

### Post by jdeppel on 2009-05-19
This same problem has been bugging me the last few days. Has anybody figured out what changed with 9.04?

---

### Post by Spacessj on 2009-05-23
first post here so hi all.

I've been messing with the usplash to and it doesn't change a thing. Well that's not entirely true: when I shut down (or reboot etc) I see the usplash I set in startupmanager, but i see it twice(my screen suddenly splits horizontally and shows everything twice) but the login box is just a black square.

Isn't there a way to find the original usplash theme, make a backup of it and then replace that with your preferred theme by giving the new theme the name of the stock one?

---

### Post by pseudo x nyn on 2009-05-30
Hey guys.

I'm trying to find a way around this one too. I'm running Jaunty UNR and compiling the source isn't working for me. I'm able to install it and select the theme ok, but there's no change at boot. So, I ran startupmanager in a terminal. I'll provide the entire sequence for context.

This is what I got:

> 
Using '/usr/lib/usplash/usplash-theme-elementary.so' to provide 'usplash-artwork.so'.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


It seems that startupmanager can't find the splash image at all [so how is it supposed to change it exactly?]. This isn't just the theme I have, as I received the same output from switching back to the ubuntu default. Any progress on your ends?

p.s. Has anyone tried using splashy? I noticed it in synaptic while I was poking around. I'll let you know how that goes.

---

### Post by pseudo x nyn on 2009-05-31
haha. I definately spoke too soon.

Splashy is Bug #328089      ](*,)
[https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089)

Please post if you have any more info for us. I'd hate to see this thread die on me. [Its the only one I could find that wasn't raving about the default theme!]

I also want to reiterate that while this is frustrating, the issue is entirely cosmetic. I'm lucky this is all I have to whine about. ^_^

rock on

---

