---
title: "Greasemonkey doesn't work for me"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by lokisapocalypse on 2010-05-20
Hello all, 

I am running the latest version of Ubuntu (10.04?) and I can't seem to get Greasemonkey (Firefox add-on) to work. It works just fine on my Windows box. I am able to install scripts with no troubles but they just don't do anything. I've tried several popular user scripts to make sure it isn't a problem with the scripts themselves. Any ideas on how to fix this?

---

### Post by lovinglinux on 2010-05-20
Create a new FF profile using the profile manager. To do that, start Firefox from terminal with the command below:

```
firefox -P
```

Install Greasemonkey on that profile and test it. If it works, then you might have something wrong with your current profile. Then use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) extension to backup important stuff and restore them on the new profile, then delete the old one.

---

### Post by lokisapocalypse on 2010-05-28
Thanks for your reply. I did what you suggested in creating a new profile but the Greasemonkey scripts still did not work. However, I did notice some output in the terminal:

> (firefox-bin:2172): Gdk-WARNING **: XID collision, trouble ahead

A quick Google search produces an Ubuntu bug page ([https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823))

Although I'm not exactly sure how to read that page. It seems the bug has been triaged which I'm guessing means it has been fixed to a point where the browser still works, just not exactly like it is supposed to. Would this be accurate?

---

### Post by lovinglinux on 2010-05-28
> **lokisapocalypse said:**
> Thanks for your reply. I did what you suggested in creating a new profile but the Greasemonkey scripts still did not work. However, I did notice some output in the terminal:

A quick Google search produces an Ubuntu bug page ([https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823))

Although I'm not exactly sure how to read that page. It seems the bug has been triaged which I'm guessing means it has been fixed to a point where the browser still works, just not exactly like it is supposed to. Would this be accurate?

I don't think that is the cause of the Greasemonkey issue.

Can you provide a link for a script that you use?

---

### Post by lokisapocalypse on 2010-05-28
[http://userscripts.org/scripts/show/28952](http://userscripts.org/scripts/show/28952)

I've tried using a YouTube one that has 100000s of users but that one did not work either. 

I've been using the above script on my PC for a long time with no problems.

---

### Post by lovinglinux on 2010-05-28
> **lokisapocalypse said:**
> [http://userscripts.org/scripts/show/28952](http://userscripts.org/scripts/show/28952)

I've tried using a YouTube one that has 100000s of users but that one did not work either. 

I've been using the above script on my PC for a long time with no problems.

I have one YouTube script that isn't working. I guess is the same as yours. If you want to replace YouTube flash player with another plugin, then see [FlashVideoReplacer](http://flvideoreplacer-extension.blogspot.com/).

To check your GM issue, try this one: [http://userscripts.org/scripts/show/77762](http://userscripts.org/scripts/show/77762)

It is working here, so we can determine if it is a script issue or Greasemonkey issue.

---

### Post by lokisapocalypse on 2010-06-08
Sorry for the late reply. I added that script you recommended and it doesn't work either.

---

### Post by lovinglinux on 2010-06-08
Are you installing Greasemonkey from the repositories or from Mozilla web site?

---

### Post by lokisapocalypse on 2010-06-09
From the repositories.

---

### Post by lovinglinux on 2010-06-09
> **lokisapocalypse said:**
> From the repositories.

Remove it and [install from Mozilla add-ons site](https://addons.mozilla.org/en-US/firefox/addon/748/).

---

### Post by lokisapocalypse on 2010-06-10
I tried that and then installed the original scripts I has having trouble with as well as the YouTube script. I still cannot get Greasemonkey to work.

---

### Post by lovinglinux on 2010-06-10
> **lokisapocalypse said:**
> I tried that and then installed the original scripts I has having trouble with as well as the YouTube script. I still cannot get Greasemonkey to work.

After starting Firefox, go to Firefox menu, click Error Console and check if there is any Greasemonkey entries.

---

