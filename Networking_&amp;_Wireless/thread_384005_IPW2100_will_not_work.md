---
title: "IPW2100 will not work"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by dirtvoyles on 2007-03-13
I recently acquired a Dell D800 with the built-in IPW2100 wi-fi Centrino chipset. Unfortunately, I cannot get it to work no matter what I try. It was seen when I checked iwconfig, but would not transmit at all.

I know there is support for this chipset by googling and searching here on the forums, but I cannot get it working. 

I am here asking for your help to get this thing working. Please tell me what you need and/or what I should try.

---

### Post by gradedcheese on 2007-03-14
These chipsets (for now) require a closed-source regulatory daemon to be running, so there's more to them than just the driver.  You need, I believe, to have restricted-modules installed:

```

sudo apt-get install linux-restricted-modules-`uname -r`

```

Another option is to just download and build the full driver from source (it's actually not that hard), but I don't think you really have to.  You may need to enable multiverse and other repositories to get the restricted-modules package.

---

### Post by dirtvoyles on 2007-03-14
Well, I have the multiverse (and all other) repos enabled, and had the linux-restricted-modules installed. However, it was still not working.

I tried to compile the ipw2100 and ieee80211 from source, but now I get an error message about an "unknown character" (or something similar). 

I think I'm very close and just need to clean out remnants of the old ipw2100 ieee80211, but I'm not sure how and the instructions from Intel/SourceForge aren't very helpful. They are written so generically that I can't get them to work.

Any other ideas, or can you tell me how to remove the old junk?

---

### Post by gradedcheese on 2007-03-14
Do a "make clean" and then compile (make) and post whatever error messages you get...  I was going to have a similar card here to try but the new laptop I ordered showed up dead and has to be sent back :(  Hopefully I can help if you post the error messages though.

---

### Post by dirtvoyles on 2007-03-14
I'm at work now and have a Jaycees meeting right after. I will try as soon as I get home (~8:30CMT). 

I'm not familiar with compiling, TBH. I'm just good at copy/paste and following direction. What/where do I put in "make clean"? Just at the CLI?

---

### Post by gradedcheese on 2007-03-14
> 
I tried to compile the ipw2100 and ieee80211 from source, but now I get an error message about an "unknown character" (or something similar).


So, I assume you were compiling it.  ie: cd to a directory and run 'make' (and/or other commands) in the shell (CLI).  Run 'make clean' there instead and then follow the instructions, and let me know exactly the errors that you see.

---

### Post by dirtvoyles on 2007-03-14
Will do. I got in late, so it'll be tomorrow. 

Just so you know, I really do appreciate the help.

---

### Post by dirtvoyles on 2007-03-15
Okay, I'm going to reinstall as I've borked up the install. Any advice starting from the beginning?

---

### Post by gradedcheese on 2007-03-15
Just delete the ipw driver directories that you had made and start over by uncompressing the archives you downloaded.  Then proceed to building the driver as per their instructions.

---

### Post by dirtvoyles on 2007-03-15
Son of a crap. 

Support was automatic, I just needed to hit <Fn><F2> to turn on the power to it manually. I am so sorry for bugging you guys and wasting forum space. 

Maybe someone else will find this helpful.

---

