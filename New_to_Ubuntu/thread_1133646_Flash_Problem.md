---
title: "Flash Problem"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Tweedicus on 2009-04-23
I've been using Ubuntu since 5.10 with no major problems. I've had no problem with Flash before.

Now, in Firefox, any Flash content is displaying as grey with a large 'play' sign which I have to press. This is ugly and annoying. Before the Flash content would load automatically.

I'm using adobe Flash 10g, or at least I think I am, I have installed it.

I'm using 9.04 RC.

Thanks.

---

### Post by scheuri on 2009-04-23
Hi there

Are you using and add-ons (plug ins) for firefox (like adblock, etc.)?
How did you install the flas plugin (manually or using apt-get/apitude)?
Since when do you have this problem? What did you do prior to this issue?

cheers
scheuri

---

### Post by tatw on 2009-04-23
sudo apt-get purge flashplugin-installer
 sudo apt-get install flashplugin-installer


tested works perfect under 9.04 rc

---

### Post by lisati on 2009-04-23
I had that big play button on another machine with adblock, solved by telling adblock to allow the content. Now I'm off to investigate another problem with playing Youtube.....

---

### Post by Tweedicus on 2009-04-23
Thanks for the replies.

The only add-ons I have are customizegoogle and zotero

I tried the purge and reinstall, nothing changed.

I installed flash through the Ubuntu restricted extras package

The problems seemed to have arisen when I tried out the 'free' flash player as opposed to adobe. I've unstalled this, but no luck

In firefox-edit-preferences-applications it says used the xine plugin, wondered if this was the problem?

---

### Post by mikewhatever on 2009-04-23
Actually, many sites that feature flash content put the play button on embeded windows, thus letting the user choose what to watch. That's not a problem, but rather is a very successful design solution.

---

### Post by Tweedicus on 2009-04-23
I wondered if it might help to make sure I've everything uninstalled connected to Flash, then start again

Any ideas how to do this?

---

### Post by tatw on 2009-04-23
Try remove firefox and all firefox settings, extensions, caches folders (i remember called .mozilla under home)
And reinstall it..

---

### Post by Tweedicus on 2009-04-23
> **mikewhatever said:**
> Actually, many sites that feature flash content put the play button on embeded flash content, thus letting the user choose what to watch. That's not a problem, but rather is a very successful design solution.


Sure, but it's not the videos I'm having problems with. I have a different play sign for those, the one embedded by the designers.

The problem is with the content on websites, the nice pictures, even the words.

So if you go to [www.mercedes.co.uk](www.mercedes.co.uk) for example

All I see is a grey strip at the top, a grey strip at the bottom, and a big black white space in the middle.

There's no videos, it a problem of the content.

I'm assuming this is Flash that's meant to handle this type of thing.

---

### Post by Cresho on 2009-04-23
flash does not work well in 9.04 especially with high definition videos.  It's plain choppy!

Perhaps this will be fixed in the final 9.04.  ALso, I noticed the kernel not optimized yet.  You may need to wait for a patch or the latest which will be released today.

---

### Post by Tweedicus on 2009-04-23
> **Cresho said:**
> flash does not work well in 9.04 especially with high definition videos.  It's plain choppy!

Perhaps this will be fixed in the final 9.04.  ALso, I noticed the kernel not optimized yet.  You may need to wait for a patch or the latest which will be released today.

For me it works pretty fine when I play it,

The problem is the big grey ugly play sign on so much of my webpage content, and it's not the one embedded by the designed.

See the screenshot of the lifehacker.com website I've attached for a typical example.

---

### Post by Linux_Kid66 on 2009-04-23
I had this problem on firefox when using the Better Youtube add-on, it affected my flash in a very negative way, if you have this add-on i reccomend removing it, as it seriously annoys the hell out of you.

---

### Post by Cresho on 2009-04-24
> **Tweedicus said:**
> For me it works pretty fine when I play it,

The problem is the big grey ugly play sign on so much of my webpage content, and it's not the one embedded by the designed.

See the screenshot of the lifehacker.com website I've attached for a typical example.

your not even using the official adobe flash 10

---

### Post by Cresho on 2009-04-24
never mind..

---

