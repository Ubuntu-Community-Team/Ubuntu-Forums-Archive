---
title: "(firefox-bin:2110): Gdk-WARNING **: XID collision, trouble ahead"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by mlnease on 2010-06-12
Hello,

Having some very odd problems with Firefox in Lucid (upgraded recently from Karmic)--smooth scrolling freezing system, taking several minutes to open links etc.  Terminal output:

** (firefox-bin:2110): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed

and reiterates many times:

(firefox-bin:2110): Gdk-WARNING **: XID collision, trouble ahead

I've completely removed Firefox via Synaptic and reinstalled it to no effect.

Anyone had similar difficulties?  Any suggestions?

Many thanks in advance.

mike

---

### Post by jmlaniel on 2010-06-13
I am getting the same thing with Chrome, Chromium, Opera and Firefox (all latest version). It seems to appear only when there is flash content on the displayed web page.

Can you see the same link with flash content?

---

### Post by mlnease on 2010-06-13
> **jmlaniel said:**
> I am getting the same thing with Chrome, Chromium, Opera and Firefox (all latest version). It seems to appear only when there is flash content on the displayed web page.

Can you see the same link with flash content?

Thanks for the quick response.  Sorry, I'm not sure I quite understand your question.  My problem seems to be--I think--java related; flash seems to work OK but for a very slow internet connection.

By the way, when this problem occurs, it also maxes out the cpu--the system monitor displays 'Processor: 100% in use'--when opened, though, it shows no single process using more than 15% or so (that being Firefox-bin).

---

### Post by jmlaniel on 2010-06-13
It's very simple, if I go on a web page with flash content, I get the Gdk-WARNING and the CPU goes to 100% (same as you). If I leave that page for one with no flash content, the CPU goes to 0% and everything is fine.

I have tried downgrading the latest flash update to no avail.

I have this problem on my laptop and my netbook (Both have Lucid Lynx installed and updated).

I have this problem for every browser I tried.

I have not seen any problem with java but I will try to see if there is a link...

---

### Post by mlnease on 2010-06-13
I see, yes, flash content does seem to be a factor.  If I experience this on a page without flash, I'll get back to you.  By the way, smooth scrolling also locks in motion for minutes at a time, also maxing the cpu.

Thanks again for your time and input.

---

### Post by jmlaniel on 2010-06-13
I can confirm now that it's not related to java since I don't have any java plugins activated in chrome (or chromium) and I have the same problem there (always related to flash content).

---

### Post by mlnease on 2010-06-13
OK, thanks.

---

