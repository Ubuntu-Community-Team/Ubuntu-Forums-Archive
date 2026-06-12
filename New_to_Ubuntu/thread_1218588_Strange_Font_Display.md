---
title: "Strange Font Display"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Cola_Cartel on 2009-07-20
Hello all,
 
I've been having an issue with character display on Ubuntu, especially online. Certain texts are corrupted with unintelligible symbols replacing the proper characters. This has been an issue with firefox and opera, and has even appeared at the login prompt after pulling my computer out of hibernate. This problem seemed to appear after downloading a number of game packages one night, but that may merely be coincidental. Any ideas how I can get this working right again?
 
Thanks in advance!
 
--------------------------
 
Update: Problem has returned

---

### Post by LowSky on 2009-07-21
have you switch languages?
What font are you using for your system?

---

### Post by Cola_Cartel on 2009-07-22
Okay, this problem is recurring. It seems to get worse as a session goes on.

The System language is set to English, US, and the fonts in the "Appearance Preferences" window are Sans, Sans Bold, and Courier New. 

I am running on Jaunty, btw

---

### Post by Cola_Cartel on 2009-07-27
This issue remains unresolved. In addition to the above information, I will mention that the display problem can extend to any software running on Ubuntu. Hypertext links seem to be most susceptible. The text of forum posts, such as here on Ubuntu Forums tends not to be affected (though I'm fairly certain I've seen that be corrupted as well).
 
At present, the only solution has been to reboot the computer.
 
Also... bump!

---

### Post by desperado665 on 2009-07-27
do you have ttf-mscorefonts installed? If not: ```
sudo apt-get install ubuntu-restricted-extras
```

might fix the problem

---

### Post by Cola_Cartel on 2009-07-27
Looks like I had that installed. I reinstalled for good measure, but I'm going to assume for the time being that this problem persists.

---------------------------------------------------------------------

Edit: Problem persists, confirmed.

---

### Post by Soldeace on 2009-08-01
Could you please post a screenshot of your messed up font display?

---

### Post by padconnelly on 2009-08-18
I'm having the same issue. I tried the ttf-mscorefonts and it didn't seem to do the trick. Here are a couple screencaps:

---

### Post by padconnelly on 2009-08-18
On a side note, changing the default display fonts for Firefox seems to "reset" them and temporarily fix the problem within the browser. Sadly, I have to keep switching fonts every 10 mins or so.

Running 9.04 on an ancient Gateway laptop.

---

### Post by padconnelly on 2009-08-20
I recently installed all the newest updates and started running with FireFox 3.5. While there are still issues with some "blocking" of letters or corrupted fonts, they're happening much less frequently now and also tend to fix themselves after closing a couple tabs or windows.

I'm guessing it's a memory issue with Intel onboard graphics since most of the complaints I've seen about this fairly rare issue have generally been using integrated graphics cards.

As a side note, Compiz doesn't work with older Intel onboard graphics. However, "sudo compiz --restart" seemed to refresh all the fonts even though it wouldn't properly load up compiz on the blacklisted graphics card.

So, no real fix here, but hope it helps a bit.

---

