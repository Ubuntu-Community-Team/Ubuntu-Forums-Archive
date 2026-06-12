---
title: "Firefox keeps crashing."
date: 2010-04-13
forum: New to Ubuntu
---

### Post by MikesGuitar on 2010-04-13
Tried to delete/remove and reinstall through Synaptic and the software center. Keep crashing and freezing on me when I browse. Anything else I can do?

---

### Post by us11csalyer on 2010-04-13
I have this problem only when trying to view some web pages in fedora forums. IDk about Ubuntu but back when I tried out Fedora isolved the problem you are having by installing yum extended and installing what I found in Yum exnteded for firefox.

---

### Post by switch10 on 2010-04-13
maybe it is extensions that are causing the problem.  Have you tried disabling all of them, and then one by one, re enabling them?

---

### Post by us11csalyer on 2010-04-13
No. I'm almost 100% sure that Yum extender just re-installed firefox completely. After yum was done I had to re download the extensions/plug-ins and install them all over.

---

### Post by philinux on 2010-04-13
> **MikesGuitar said:**
> Tried to delete/remove and reinstall through Synaptic and the software center. Keep crashing and freezing on me when I browse. Anything else I can do?

Run firefox in safe mode from a terminal.

```
firefox -safe-mode
```

That will show if an addon is to blame.

---

### Post by lovinglinux on 2010-04-13
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by MikesGuitar on 2010-04-14
Hey I have tried everything suggested by you guys and what is written in the tutorial. I still can't seem to figure it out, even completely removed firefox and flash through synaptic package manager - restarted and re-installed everything, and still have the issue
I do know that when I have shockwave flash enabled on my plugins screen it crashed every time, but does not crash when it is disabled (hence how I am able to type this).
I thought that completely removing flash as I did would remove that plug in as well; is there a different way to removed/re-install the plugin? 
Thanks for your help!

---

### Post by EssexEagle on 2010-04-14
> **MikesGuitar said:**
> Hey I have tried everything suggested by you guys and what is written in the tutorial. I still can't seem to figure it out, even completely removed firefox and flash through synaptic package manager - restarted and re-installed everything, and still have the issue
I do know that when I have shockwave flash enabled on my plugins screen it crashed every time, but does not crash when it is disabled (hence how I am able to type this).
I thought that completely removing flash as I did would remove that plug in as well; is there a different way to removed/re-install the plugin? 
Thanks for your help!

Have you tried running Firefox from a terminal:
```
firefox
```
Then when it crashes, see what error messages it throws out at you.

---

### Post by RazzyDaz on 2010-04-14
I have the same problem.  I have uninstalled 3.6 and still seems to load 3.6.  When I go to certain sites, such as My Yahoo, it's turns gray, then freezes.  It's not the extension, I think it has to do with Java.  I have given up and started using Chrome.  I really miss coolpreviews!   

Razz

---

### Post by cuberts on 2010-04-14
> **MikesGuitar said:**
> Tried to delete/remove and reinstall through Synaptic and the software center. Keep crashing and freezing on me when I browse. Anything else I can do?Aha I think that you are having some problems because You are using the newest version of Ubuntu and maybe an older version of firefox. So try installing the newest version of firefox , 3.6.3 and then if that doesnt work then i think that you should use a different web browser. I have also used google chrome, it is quite secure and it is great as far as I can see. :guitar:

---

### Post by MikesGuitar on 2010-04-16
I have officially given up on Firefox and moved onto Google's Chrome. So far I really dig it, not problems whatsoever and it looks/operates great too. Sorry Firefox, its been real...

---

### Post by lovinglinux on 2010-04-16
> **MikesGuitar said:**
> I have officially given up on Firefox and moved onto Google's Chrome. So far I really dig it, not problems whatsoever and it looks/operates great too. Sorry Firefox, its been real...

Good for you. If you was a Firefox extension addicted I guess you will probably download some Chrome extensions. Keep in mind Chrome extensions are not reviewed by Google developers like Mozilla does for every Firefox extension that goes public (not considering experimental or self-hosted). 

Additionally, I would advice to use Chromium instead, since Chrome come with data-mining features from Google.

---

### Post by MikesGuitar on 2010-04-19
Thanks for the input, I am however somewhat of a novice when it comes to these things, but what is the deal with Chromium? I don't deal with many extensions, but a few, would Chromium be a better option?

---

### Post by Crazedpsyc on 2010-04-19
unfortunately Chrome is not as secure and it is a keylogger, so I hate it. My Firefox works great! but still, download the .tar.bz2 of firefox 3.6.3 and extract it. in a terminal run /path/to/extracted/firefox/firefox (the last firefox is inside the extracted firefox folder and will run it. if that crashes post everything it said in the terminal.

---

### Post by lovinglinux on 2010-04-19
> **MikesGuitar said:**
> Thanks for the input, I am however somewhat of a novice when it comes to these things, but what is the deal with Chromium? I don't deal with many extensions, but a few, would Chromium be a better option?

Chrome is based on Chromium, with extra data-mining stuff created by Google and a different logo. Chromium is also open source.

---

### Post by MikesGuitar on 2010-04-20
Okay, so if you were me what would you do to ensure you had a secure and properly working browser. I have been using Chrome for a week or so with absolutely no problems AND I like it better than FF. Should I get Chromium instead?

---

### Post by lovinglinux on 2010-04-20
> **MikesGuitar said:**
> Okay, so if you were me what would you do to ensure you had a secure and properly working browser. I have been using Chrome for a week or so with absolutely no problems AND I like it better than FF. Should I get Chromium instead?

IMO, is a better option.

---

### Post by MikesGuitar on 2010-04-20
I am interested in trying it out but I am having a tough time finding where/how to dl and install it haha

---

### Post by lovinglinux on 2010-04-20
> **MikesGuitar said:**
> I am interested in trying it out but I am having a tough time finding where/how to dl and install it haha

[Chomium ppa](http://www.google.com/search?q=Chomium+ppa+site:ubuntuforums.org)

---

### Post by Jerry N on 2010-04-20
I'm using 9.04.  I upgraded Firefox from 3.5.X to 3.6.4 and in the process it destroyed the original 3.0.X.  Now Firefox not only freezes, it freezes the whole machine, forcing me to reboot with the Reset button (home made computer, most machines don't have a reset anymore).  3.6.3 works perfectly for me in Win XP and Win 7.  Re-installing didn't help and I didn't find a way to reinstall 3.0.  No big deal I guess - it is almost time for the final version of 10.04.

Jerry

---

### Post by lovinglinux on 2010-04-20
> **Jerry N said:**
> I'm using 9.04.  I upgraded Firefox from 3.5.X to 3.6.4 and in the process it destroyed the original 3.0.X.  Now Firefox not only freezes, it freezes the whole machine, forcing me to reboot with the Reset button (home made computer, most machines don't have a reset anymore).  3.6.3 works perfectly for me in Win XP and Win 7.  Re-installing didn't help and I didn't find a way to reinstall 3.0.  No big deal I guess - it is almost time for the final version of 10.04.

Jerry

How did you install and upgrade Firefox 3.5?

I have to agree, just go for Lucid.

---

### Post by k3lt01 on 2010-04-20
> **lovinglinux said:**
> How did you install and upgrade Firefox 3.5?

I have to agree, just go for Lucid.I run Chrome in Lucid because FireFox is unstable and it keeps crashing. Now I am going to check out Chromium based on the info in this thread.

---

### Post by lovinglinux on 2010-04-21
> **k3lt01 said:**
> I run Chrome in Lucid because FireFox is unstable and it keeps crashing. Now I am going to check out Chromium based on the info in this thread.

You should try the new [Firefox Lorentz](http://ubuntuforums.org/showthread.php?t=1459076). It won't crash.

---

### Post by ddecator on 2010-04-22
Your profile may be corrupt. Run the following command:

firefox -ProfileManager

Then create a new profile and try running Firefox from there.

---

