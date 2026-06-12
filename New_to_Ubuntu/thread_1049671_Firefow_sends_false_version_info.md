---
title: "Firefow sends false version info?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-01-24
I try to get to my Website Tonight (GoDaddy) account to diddle with my website and their system tells me I'm using Firefox 1.0.9 which is not compatible.

I have v 3.0.5 which should work.

I spent half an hour talking to their tech guys and they can't help me!!!!! Their only suggestion is that I do a "user agent mask"?

Does anyone know if Firefox can be sending out false info about itself and how to fix it?

Thanks many.

---

### Post by Fass on 2009-01-24
[http://mybrowserinfo.com/](http://mybrowserinfo.com/)

That page should tell you what Firefox reports itself as. The easiest way to change the User Agent String is with this extension: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) or to edit the settings in about:config, looking at the general.useragent.extra.firefox string.

---

### Post by kansasnoob on 2009-01-24
One thing comes to mind. Try the actual Mozilla build of Firefox!

The easiest way is Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Just be certain that your current Firefox app is closed when you run the installation! I use Opera while I'm installing but you can also copy-n-paste the instructions to Abiword or Open Office.

---

### Post by vandorjw on 2009-01-24
in the URL type: about:config

It will give you a message, read it, and continue. (your not going to change any configurations, I just want you to look at something)

scroll down to : general.useragent.extra.firefox
The value should be set to; Firefox/3.0.5

is it?

Cheers - CC7

---

### Post by mikewhatever on 2009-01-24
It could be that 1.9 is the engine version, while firefox is still 3.0.5.

---

### Post by hambone79 on 2009-01-24
My suggestion is to drop GoDaddy and go with someone else. I had a GoDaddy account for over a year and it was the worst hosting experience I ever had...nothing worked as advertised, software was outdated, and getting support was a joke. Also, they have the worst website layout in the history of hosting companies. In most cases you can find data on their site through Google faster than you can find it through their own search function.

---

### Post by tahitiwibble on 2009-01-26
> **Fass said:**
> [http://mybrowserinfo.com/](http://mybrowserinfo.com/)

That page should tell you what Firefox reports itself as. The easiest way to change the User Agent String is with this extension: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) or to edit the settings in about:config, looking at the general.useragent.extra.firefox string.

Thanks Fass, that was a useful link. If you look at the browser info, I can't help but notice that "1.9.0.5", but don't know what it means. (Your Browser User Agent String is Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5)

> **kansasnoob said:**
> One thing comes to mind. Try the actual Mozilla build of Firefox!

The easiest way is Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Just be certain that your current Firefox app is closed when you run the installation! I use Opera while I'm installing but you can also copy-n-paste the instructions to Abiword or Open Office.

kansasnoob, I will try this regardless, thanks.

> **cc7gir said:**
> in the URL type: about:config

It will give you a message, read it, and continue. (your not going to change any configurations, I just want you to look at something)

scroll down to : general.useragent.extra.firefox
The value should be set to; Firefox/3.0.5

is it?

Cheers - CC7

CC7, everything looks OK. That is the value in about:config. 

> **mikewhatever said:**
> It could be that 1.9 is the engine version, while firefox is still 3.0.5.

mikewhatever, is that what the "1.9" is in part of my reply to Fass?? Hmmmm.

---

