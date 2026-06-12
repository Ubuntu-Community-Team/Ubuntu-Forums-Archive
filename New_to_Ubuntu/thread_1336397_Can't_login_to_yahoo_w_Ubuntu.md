---
title: "Can't login to yahoo w/ Ubuntu"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by bobbygf on 2009-11-24
I recently installed Karmic Koala on my new computer build. I am having trouble logging in to several websites including yahoo, which is a major issue. I'm also having minor issues with media sites like youtube and hulu where some of the functions like play and fullscreen do not work. I just installed all of the new update packages and still experiencing these problems. After installing Ubuntu, all of these functions worked fine, they just started not working recently. Any advice?

Thanks.

---

### Post by wilee-nilee on 2009-11-24
So what makes you choose the UF for answers?

---

### Post by dca on 2009-11-24
Have you installed the 'ubuntu-restricted-extras' meta-package from the repos?  This should have latest version of Flash & Java which might be where your issues lie?

---

### Post by bobbygf on 2009-11-24
wilee nilee - i thought this was the best place, plus it's pretty urgent so I guess I didn't research too much in depth on where I should ask this question....

dca - thanks for the advice, but yes, and it didn't work.

let me add

after I login to yahoo, the same login screen pops up. Just for the heck of it, I put in the wrong info and it told me that I had an invalid password. So, when I put the correct info in it says nothing, when I put the wrong info it tells me. Either way, I can't get to my email. 

With the media sites, I can watch the videos, but in most instances, I can't do anything after initially hitting play. Like fullscreen, pause, change resolution, etc.

---

### Post by kansasnoob on 2009-11-24
> **wilee-nilee said:**
> So what makes you choose the UF for answers?

Where should (s)he ask?

---

### Post by gmjs on 2009-11-24
Perhaps this is a 'cookies' or Firefox profile issue?

If cookies are being allowed (Firefox: Edit>Preferences>Privacy>Accept cookies from sites) you could try clearing the History + Cookies.

If it's no different, you can rename your Firefox settings folder and Firefox will create a new profile for you.

At the terminal (having closed Firefox):
```
**$** cd ~
**$** mv .mozilla .mozilla.old
```

and open Firefox.  You'll need to set up connection settings and bookmarks etc. as you like them again.

To restore the old profile (if this still doesn't fix it, but you want your bookmarks back!):

```
**$** cd ~
**$** rm .mozilla
**$** mv .mozilla.old .mozilla
```

Hope this helps,

Graham

---

### Post by kansasnoob on 2009-11-24
I don't have an answer regarding Yahoo. I Yahoo everything with no problems. So that puzzles me.

The rest sounds Flash related so I'd start with installing the restricted-extras as previously instructed. You may need to go to Synaptic and type flash into search, then make sure no swfdec or gnash packages are installed.

The Yahoo thing has me puzzled.

---

### Post by dca on 2009-11-24
The only other thing that can stall it is if you have the 'NoScript' add-on in Firefox running...

---

### Post by kansasnoob on 2009-11-24
> **dca said:**
> The only other thing that can stall it is if you have the 'NoScript' add-on in Firefox running...

I'd not thought about that but yes, always try disabling add-ons!

---

### Post by bobbygf on 2009-11-24
Graham - thanks the terminal idea worked for the yahoo problems. somewhat bittersweet, but I'll take it!

kansasnoob - everything seems to be in order in Synaptic.

dca - i went to Tools>Add-ons in Firefox and didn't find anything NoScript related. 

So there's a handful of Media related plugin/add-ons in the firefox Tools>Add-ons>Plug-ins section. I disabled all of them individually and that didn't work.

Also, out of roughly 200 hundred clicks on the Fullscreen button on Hulu, it worked twice, both times was right when it started to play the intro ABC commercial. 

Thanks again for everyone's support.

---

### Post by emeraldgirl08 on 2009-11-24
I have a similar problem with 9.10. I have my Yahoo setup to go straight to My Yahoo and it won't load the page. I have to refresh it and it shows part of the page with no background. I have to click on the Mail link then it will take me to the Mail page which is it's normal self. I attempt to go back to My Yahoo and the same thing happens. 

Pretty strange stuff.

My other laptop with Jaunty doesn't have this quirk.

---

