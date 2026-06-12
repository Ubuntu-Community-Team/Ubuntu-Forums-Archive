---
title: "stupid firefox...again !!"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-17
Firefox crash when i open [www.livescore.com]("http://www.livescore.com.Opera") Opera load this site with no problems,google chrome too,but always something wrong with firefox :mad:
I just want to use firefox and open all sites.Can anyone help me to do that? Thanks.
(sorry for my english)

---

### Post by Zintha on 2010-05-17
I don't know much but for me it loads alright.
Lots of Flash on there, maybe its a flash issue?

---

### Post by grobar87 on 2010-05-17
(firefox-bin:2025): Gdk-WARNING**: XID collision, trouble ahead

I got this in terminal...

---

### Post by grobar87 on 2010-05-17
After that...

"Segmentation fault"

and firefox quit.

---

### Post by timbounceback on 2010-05-17
That's strange, you shouldn't be encountering a segmentation fault. This sounds to me like a bug, follow the steps [here]("http://ubuntuforums.org/showthread.php?t=1011078") to report it.

---

### Post by kwacka on 2010-05-17
Which version of Firefox are you using?

This was reported as a bug in FF 3.5, I'm using 3.6.3 with no problems.

---

### Post by grobar87 on 2010-05-17
> **kwacka said:**
> Which version of Firefox are you using?

This was reported as a bug in FF 3.5, I'm using 3.6.3 with no problems.

Me too,i'm using firefox 3.6.3..
How to fix this bug?

---

### Post by lovinglinux on 2010-05-17
Although it doesn't show on your error output,  I would try removing libmoon. It is causing Firefox to crash.

If that doesn't work, then see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

EDIT: Well, it seems you have already solved the problem on the other thread.

---

### Post by Kobalt on 2010-05-17
+1, try removing the damn libmoon (Silverlight) libraries using Synaptic, it does provoque segmentation faults in Firefox.

---

### Post by grobar87 on 2010-05-17
I remove libmoon but still have this problem....
I think i solve in my other thread,but NO(everythink seems to be ok for an hour:confused:).
Any other way?? Thanks.

---

### Post by flyfishingphil on 2010-05-17
> **grobar87 said:**
> Firefox crash when i open [www.livescore.com]("http://www.livescore.com.Opera") Opera load this site with no problems,google chrome too,but always something wrong with firefox :mad:
I just want to use firefox and open all sites.Can anyone help me to do that? Thanks.
(sorry for my english)
FYI: I clicked on the link in your statement and got nothing. I then retyped it and removed the dot after com and added the slash and opera. For that I got a 404 error. I then removed cleared off the opera and slash so all I had was: [www.livescore.com](www.livescore.com) and it opened it immediately. 

You might want to check your links because it doesn't look like any problem but that.

(Currently using Vista because I messed up my 10.04 and had to start from scratch.)

---

### Post by grobar87 on 2010-05-18
> **flyfishingphil said:**
> FYI: I clicked on the link in your statement and got nothing. I then retyped it and removed the dot after com and added the slash and opera. For that I got a 404 error. I then removed cleared off the opera and slash so all I had was: [www.livescore.com]("http://www.livescore.com") and it opened it immediately. 

You might want to check your links because it doesn't look like any problem but that.

(Currently using Vista because I messed up my 10.04 and had to start from scratch.)

[www.livescore.com](www.livescore.com)  this is the link...i open with firefox but after 5 seconds firefox crash.
Problem is not just this site,same happens with some other sites:confused:

---

### Post by philinux on 2010-05-18
No problem at all here. Try running in safe mode.

```
firefox -safe-mode
```

---

### Post by grobar87 on 2010-05-18
> **philinux said:**
> No problem at all here. Try running in safe mode.

```
firefox -safe-mode
```

Same problem in safe mode...
I try reinstalling firefox,i create new mozilla folder in home partiton...but still the same problem.Any other way to solve this,or just reinstall ubuntu?:confused:

---

### Post by philinux on 2010-05-18
Is compiz active?

---

### Post by grobar87 on 2010-05-18
> **philinux said:**
> Is compiz active?

Yes,compiz is active.I need to remove compiz?

---

### Post by philinux on 2010-05-18
Just try disabling to test. System>prefs>appearance>visual effects - choose none. Then try that site.

---

### Post by grobar87 on 2010-05-18
Same,same... :( Problem still there.

---

### Post by philinux on 2010-05-18
Just try this.

In firefox Edit>prefs>content. Untick enable javascript.

---

### Post by lovinglinux on 2010-05-18
Try to re-install xulrunner. Is a long shot, but doesn't hurt to try.

---

### Post by grobar87 on 2010-05-18
> **philinux said:**
> Just try this.

In firefox Edit>prefs>content. Untick enable javascript.


I try that but still have this problem...:confused::(

---

### Post by grobar87 on 2010-05-18
> **lovinglinux said:**
> Try to re-install xulrunner. Is a long shot, but doesn't hurt to try.

I reinstall xulrunner too but notting,still have this problem...
:confused:

---

