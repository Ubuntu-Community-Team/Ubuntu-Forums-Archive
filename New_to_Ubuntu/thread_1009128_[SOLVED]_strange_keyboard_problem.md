---
title: "[SOLVED] strange keyboard problem"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jcats on 2008-12-12
here's a strange one. yesterday, the shift key stopped working.  i can't get capital letters, unless i use caps lock. and i can't get the top items on any keys with 2 functions. i've tried a couple different keyboards, all the same. when i do press the shift key, the cursor disappears, and whatever key i hit, nothing appears. i've gotten rid of any themes, returned to default fonts. same thing happens in my mail.
i'm running 8.04, with all the updates.
any help would be most appreciated.
jcats

---

### Post by drs305 on 2008-12-12
Just a bit of troubleshooting. If you run 'xev' in a terminal, make the popup window active, and then hit the Shift_L or Shift_R keys, does xev register them as "Shift_L" keycode 50 and "Shift_R" keycode 62?

---

### Post by Dr Small on 2008-12-12
My suggestion, just to see if it is really a keyboard problem, or rather a GUI problem, is to switch to the command line, and try the shift key.

To do so, press CTRL + ALT + F1.
You will be taken to the black command line, and prompted to login. You may just try the shift key here, and see if it works. If it works, or doesn't, you may report back to us.

To return to the GUI, press CTRL + ALT + F7

---

### Post by jcats on 2008-12-12
drs305-here's a sample of what  got. I never got the keycode 50 or 62. When you say 'shift-l or shift-r, i assume you mean shift, with the right or left arrows

-KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

dr. small,yes, i can get capitals when i tried to login.

so, what does this tell us.
thanks for your help
jcats

---

### Post by LowSky on 2008-12-12
> **jcats said:**
> drs305-here's a sample of what  got. I never got the keycode 50 or 62. When you say 'shift-l or shift-r, i assume you mean shift, with the right or left arrows

jcats

No he meant the left shift key (the one near CAPS LOCK)and the right shift key (one near ENTER)

---

### Post by jcats on 2008-12-13
Newbie Alert!
Well, after some poking around, I realized that I am the problem. While playing around in Compiz, I bound the shift key to one of the applications. So, it worked for Compiz, but nothing else. OOOPS!
Thank you to all of you that took the time to try and figure this out.
jcats

---

### Post by jesuspresley on 2009-01-10
I had the same issue.
I disabled Compiz and VOILA! Shift key works again. 
Thanks for having these troubles 3 weeks earlier then me. 

;)

---

### Post by jcats on 2009-01-10
> **jesuspresley said:**
> 

Thanks for having these troubles 3 weeks earlier then me. 

;)

Anything I can do for the team:P
If you had to disable Compiz to fix it, did you bind the shift key to something?

jcats

---

