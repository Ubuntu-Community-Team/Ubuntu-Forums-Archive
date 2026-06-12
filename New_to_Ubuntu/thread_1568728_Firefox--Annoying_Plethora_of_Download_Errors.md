---
title: "Firefox--Annoying Plethora of Download Errors"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by daggoth8 on 2010-09-05
I often save webpages with firefox, to read them later when offline. But with certain urls, page-saving causes my firefox to generate lots of error messages. Yet without any helpful messages appearing on the firefox error console to tellme why. Where each error window is titled "Download Error", with a typical message like this one... 

   /home/nostromo/Downloads/depress-about-dot-com--feeds_files/slf.js could not be     
   saved,because the source file could not be read.

   Try again later, or contact the server administrator. 

So I'm guessing that firefox can't access some files, mostly .js and .css in this case. And that's okay, coz I do have a hosts file installed. Still, the pagesave quality seems okay enuf to me. But the main problem here is the annoying plethora of "download error" messages - I have to press 'enter' repeatedly to clear them  away, which is just slowing me down :-(  

So, can anyone plz tellme howto get rid of this plague of error boxes? Thanks... 
 
I am running Xubuntu Lucid, with Firefox 3.6.8. I have changed nothing in the about:config settings, and my installed addons are... 
 
DownloadHelper 4.8 
DownthemAll! 1.1.10 
Flashblock 1.5.13 
Readability 1.1 
Toolbar Buttons 0.6.0.8 
Ubuntu Firefox Modifications 0.9rc2

---

### Post by walt.smith1960 on 2010-09-06
This is strictly a guess so take it for what it's worth.  I'd uninstall one or both download extensions and try again.  I wonder if there's a conflict between the two?  Or some problem with the download extensions and Flashblock?  Good luck and I hope it's a simple problem.

---

### Post by uRock on 2010-09-06
I am wondering if there is a config file that can be altered to not dump the /tmp for a period of time, instead of at every shutdown/log off.

---

### Post by lovinglinux on 2010-09-07
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by viralmeme on 2010-09-07
> **daggoth8 said:**
> I often save webpages with firefox, to read them later when offline

Try using WGET ..

---

### Post by daggoth8 on 2010-09-09
Thanks everyone for your helpful replies...

I have solved the problem for now by removing the hosts file, and the adblock addon. For some reason, by blocking urls, they trigger the errors. 

As for using wget... I have used httrack in the past to download webpages. But nowadays, unless I'm downloading several pages from the same domain, I find the basic firefox pagesave is simpler.

Thanks again

---

