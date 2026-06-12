---
title: "Firefox startpage problem"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by jeffbilling on 2009-08-17
When I open Firefox I always get three tabs opening (see attached screenshot). I have tried changing preferences to show 'Yahoo.com' as my homepage but it always reverts to 
'chrome://ubufox/content/startpage.html '
Can anyone help please.

---

### Post by Buuntu on 2009-08-17
How are you running firefox?  From the terminal or from a launcher?

Try reinstalling firefox, that should do the trick.```
sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox
```

---

### Post by jeffbilling on 2009-08-18
Tried that but got following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

---

### Post by jeffbilling on 2009-08-18
Don't know what happened but it is fixed!! Must have frightened Firefox. Thanks very much

---

### Post by Merk42 on 2009-08-18
Some addons, like VideoDownloadHelper and NoScript open up their homepages when you first install/update the addon. That's all that happens.

---

### Post by jeffbilling on 2009-08-19
> **Merk42 said:**
> Some addons, like VideoDownloadHelper and NoScript open up their homepages when you first install/update the addon. That's all that happens.

I thought I had cured the problem - the trouble is I get VideoDownloader and NoScript + Ubuntu Google every time I open Firefox. I want to open directly to my home page but it won't let me. 

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by philinux on 2009-08-19
What does this look like on your setup.

---

### Post by jeffbilling on 2009-08-19
Herewith a copy of before and after. 'Fire1' is what I get every time I load Firefox and 'Fire2' is what I change it to.

---

### Post by LewRockwell on 2009-08-19
> **jeffbilling said:**
> I thought I had cured the problem - the trouble is I get VideoDownloader and NoScript + Ubuntu Google every time I open Firefox. I want to open directly to my home page but it won't let me. 

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

We think what's happening is that the add-ons are updating when you first select the browser(even if it's automatic at start-up) and then after the add-ons have updated it restarts Firefox and sends you to the add-ons homepage so you can see what new bells/whistles/garters they've put on

Overall we acknowledge that there is a learning curve to any new browser and we are confident that you'll discover those settings and options which fit you best

.

---

### Post by LewRockwell on 2009-08-19
> **jeffbilling said:**
> Herewith a copy of before and after. 'Fire1' is what I get every time I load Firefox and 'Fire2' is what I change it to.

when we change our homepage we enter the URL and go to the webpage, then we go to the preferences area and select "use current page"

what we found out a long time ago was that when we just keyed in the URL we wanted in the preferences area it actually didn't change(reverted back to what it was before we keyed in the new URL)

hey, it's the little things...

wheeeeee.....

.

---

### Post by oldsoundguy on 2009-08-19
> **LewRockwell said:**
> We think what's happening is that the add-ons are updating when you first select the browser(even if it's automatic at start-up) and then after the add-ons have updated it restarts Firefox and sends you to the add-ons homepage so you can see what new bells/whistles/garters they've put on

Overall we acknowledge that there is a learning curve to any new browser and we are confident that you'll discover those settings and options which fit you best

.

I get those added pages every time some plug in I have selected UPDATES .. just as stated above.  It is nothing to be concerned with .. just x the tabs out!

---

### Post by jeffbilling on 2009-08-21
> **LewRockwell said:**
> when we change our homepage we enter the URL and go to the webpage, then we go to the preferences area and select "use current page"

what we found out a long time ago was that when we just keyed in the URL we wanted in the preferences area it actually didn't change(reverted back to what it was before we keyed in the new URL)

hey, it's the little things...

wheeeeee.....

.
That is what I have been doing for the past 6-7 years and never had a problem before. (I have used Mozilla since it first came out and never use anything else!).
I will do some more research on the offending three web pages that appear - I am not sure what the 'chrome' is doing at front of address so will check this out also.

---

