---
title: "Compiz not running with all features enabled"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by SandyM on 2009-06-08
I have been using Ubuntu along with compiz for about a year. Then I migrated to Jaunty and entered new compiz repositories along with the required Key.following are the repositories.--

[B]Compiz Fusion Latestdeb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main 
#deb*src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main 
[/B]

But the problem is that instead of upgrade, I find many features which were otherwise available in prior editions of Ubuntu (i.e 8.04 LTS and 8.10) are not available in the compiz I am currently running on my Jaunty machine.I have used compiz fusion repositories in Hardy as well as in Intrepid, and every time I found new plugins and updates on the compiz already availble  in default Ubuntu repositories.

But this time I see many of my animation and utility plugins that were there in 8.04 and 8.10 go missing in 9.04 edition of compiz.

Many prominent plug-ins like **fire** and **air plane** are no where to see.** I can easily say that there are only half the no of animation plug ins as compared to what I used to have . Same is the case with FLIP window plugin. There are other plug ins also which I don't clearly remember.**

**Please tell me the way I can get back these astonishing plugins as I really miss them. Also tell me if this problem persist due to new compiz repositories I entered and if there are better compiz repositories available than the one I already mentioned**

THANK YOU

---

### Post by rustutzman on 2009-06-08
Do you have the "Additional Animations" checked in compiz config?

---

### Post by SandyM on 2009-06-09
> **rustutzman said:**
> Do you have the "Additional Animations" checked in compiz config?

Thats more amazing I have not come across anything like "Additional Animations" in this version of compiz, however I used to have one such plug-in in my prior version of Compiz & Ubuntu (8.04 & 8.10)

---

### Post by Steelmourne on 2009-06-09
If you search for compiz in add/remove and install it it has all the options, at least it did for me, including fire etc. The package is in advanced desktop settings (ccsm). I didn't add any repositories.

---

### Post by prvteprts on 2009-06-09
Try uninstalling compiz and then reinstall it using add/remove as Steelmourne suggested. If that still doesn't solve the problem,  try installing compiz-fusion-plugins-extra & compiz-fusion-plugins-main from the terminal using apt-get.

---

### Post by rIcHrDx on 2009-06-17
I am in exactly the same situation. Tried installing packages from synaptic (the unsupported package) to no avail.

Removed the settings manager (ccsm) from Add/Remove programs and reinstalled - didn't help. I'll try removing compiz fully (after disabling), but I have the feeling that won't work either.

A very peculiar problem, since I like my burn effects.

Ah well, one of those bugs. Hope someone finds a solution!

---

### Post by prvteprts on 2009-06-17
In my case, I just installed ccsm from add/remove and I did not encounter any problems out of all the machines I have installed it on. The burn and airplane effects are found in the "Animations add-on" plugin. You have to enable that and then configure the Animations plugin to use a particular effect for an event (open, close, minimize, etc). You could also have it randomized from a bunch of effects. 

Check this out: [http://www.youtube.com/watch?v=Zl5bUmHFrUU&feature=PlayList&p=985EE6FB1093CBF5&index=4](http://www.youtube.com/watch?v=Zl5bUmHFrUU&feature=PlayList&p=985EE6FB1093CBF5&index=4)

It is just a matter of setting it up. Also, from what I gather, some plugins which used to be installed by default have been excluded from default. Not totally gone, just in a different plugin package.

---

