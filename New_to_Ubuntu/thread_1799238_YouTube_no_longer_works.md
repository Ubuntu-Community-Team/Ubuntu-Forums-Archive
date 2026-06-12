---
title: "YouTube no longer works"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by Linux_Man on 2011-07-07
Randomly, yesterday YouTube stopped working for me, it doesn't work at all on the YouTube site in Firefox, neither on the default 3.6 Firefox installed on Ubuntu or on Firefox 5. Oddly enough though, it somehow works if I go to Facebook, click on a video, then click the YouTube button and it will play it on YouTube, otherwise, it just displays a blank screen, hangs on  waiting for, or loading from *.ytimg.com and if you right click the video it says "Movie not loaded". I've tried updating Flash and all sorts of things, but can't seem to figure it out. It does the same thing with and without Ad-Block. Do any of you guys know what could be the problem. Oh, and it also randomly works on Chromium and I haven't changed any Firefox preferences since before it worked and when it stopped working, I did install a few Ubuntu updates, but they were all security updates and didn't seem related to Firefox or Flash. And I'm running Ubuntu 10.10.

---

### Post by whatthefunk on 2011-07-07
Its more than likely a cookie problem.  Delete all the youtube cookies and then block cookies from [www.youtube.com](www.youtube.com).

---

### Post by dcsoldschool53 on 2011-07-07
It has stopped working for me too, in all of my browsers. I had tried it in opera, seamonkey, firefox, and google chrome. I had deleted the cookies, and the caches. I install flash aid. Nothing worked.
Now, I did find a way to still view them in my email account using hotmail.

Today I am proud to say Youtube came back on it own today!!!

---

### Post by srisharan on 2011-07-07
I had a same  problem once.I remove the flash plugins I installed completely and then reinstalled it afresh.that solved the problem.See if it works for you as well

---

### Post by Bootsy Collins on 2011-07-07
I'm also having this same problem.

> **srisharan said:**
> I had a same  problem once.I remove the flash plugins I installed completely and then reinstalled it afresh.that solved the problem.See if it works for you as well

How did you go about removing the plugins?  Through Firefox's add-ons screen, you can disable the plugin, but not remove it.  Did you do it from the package manager or apt-get (e.g. "apt-get remove adobe-flashplugin")?

---

### Post by Bootsy Collins on 2011-07-07
> **Bootsy Collins said:**
> I'm also having this same problem.



How did you go about removing the plugins?  Through Firefox's add-ons screen, you can disable the plugin, but not remove it.  Did you do it from the package manager or apt-get (e.g. "apt-get remove adobe-flashplugin")?

Well, to follow up, I went ahead and tried the above.  I killed off the browser, did an apt-get remove of adobe-flashplayer, apt-get install'ed it back, then fired up the browser.  The youtube player doesn't load -- just a black square.

---

### Post by srisharan on 2011-07-07
Go to synaptic package manager(Administration-synaptic package manager) and type flash or adobe flash.You will get a flash plugin entry with an indication that it is install.Completely remove (right click, mark for complete removal and apply)

---

### Post by no2498 on 2011-07-07
there is a problem with you tube

lovinglinux can help you fix it
he has a how to out already

---

### Post by no2498 on 2011-07-07
[http://ubuntuforums.org/showthread.php?t=1799217](http://ubuntuforums.org/showthread.php?t=1799217)

---

### Post by Linux_Man on 2011-07-07
Thank you all! It works now.

---

