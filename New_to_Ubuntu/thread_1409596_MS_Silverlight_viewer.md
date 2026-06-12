---
title: "MS Silverlight viewer"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by bob brazie on 2010-02-17
Ubuntu 9.10 Firefox 3.6

I am trying to view video on MSNBC of the Olympic games.

/www.nbcolympics.com/video/assetid=ced6f75b-0402-49d7-be20-58881e0c880c.html#womens+downhill+pov

They us the MS Silverlight plug-in Every time I try to watch the video I am asked to install the updated package.

The package is installed and I still get asked every time.

Any ideas on how to make this work correctly?

Thanks, Bob.

---

### Post by jrusso2 on 2010-02-17
Thats 2.1 I think 2.9 is out.

---

### Post by bob brazie on 2010-02-17
That's the one that was available from the MSNBC site that i was directed to download.

Not sure why it wouldn't work......

---

### Post by bob brazie on 2010-02-17
I just did "find updates" from Firefox AddOns and no updated one's were found.

---

### Post by jrusso2 on 2010-02-17
Its 2.99 you have 2.1 according to your screenshot.

Also it works on  3.5 but  3.6 but with nightly tester tools you can make it work.

---

### Post by lovinglinux on 2010-02-17
[http://ubuntuforums.org/showthread.php?p=8835795](http://ubuntuforums.org/showthread.php?p=8835795)

---

### Post by wojox on 2010-02-17
I couldn't get it working on 3.6 either. While hunting around the web for answers the only thing that stuck out was to install 3.5 to run it.
I spent half a day moving, linking, and downloading different version of moonlight before I gave up. I didn't want to download 3.5 just to try.

---

### Post by lovinglinux on 2010-02-17
> **jrusso2 said:**
> Its 2.99 you have 2.1 according to your screenshot.

Also it works on  3.5 but  3.6 but with nightly tester tools you can make it work.

...or with [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003).

---

### Post by wojox on 2010-02-17
Thank you. I spent 6 hours of my life trying to get this to work on 3.6.2pre. Now it works. Thanks. :D

---

### Post by bob brazie on 2010-02-17
"3.6 but with nightly tester tools you can make it work."

Not sure what this is or what it means.

---

### Post by lovinglinux on 2010-02-17
> **bob brazie said:**
> "3.6 but with nightly tester tools you can make it work."

Not sure what this is or what it means.

It's an extension to override extension compatibility check, among other things, so you can use extensions that work with newer versions of Firefox, but haven't been updated by their authors yet.

I personally prefer and recommend Add-on Compatibility reporter, which is developed my Mozilla team.

---

### Post by bob brazie on 2010-02-18
> **lovinglinux said:**
> It's an extension to override extension compatibility check, among other things, so you can use extensions that work with newer versions of Firefox, but haven't been updated by their authors yet.

I personally prefer and recommend Add-on Compatibility reporter, which is developed my Mozilla team.

How would I use that so I can start viewing these videos before the Olympics are over?

---

### Post by lovinglinux on 2010-02-18
> **bob brazie said:**
> How would I use that so I can start viewing these videos before the Olympics are over?

[Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003)

---

### Post by bob brazie on 2010-02-18
Thanks, got that but it still does not allow me to watch the silverlight videos.

Any thoughts on how to do that?

---

### Post by bob brazie on 2010-02-18
I am still at a loss as to how to run silverlight using the Add-on Compatibility Reporter.

I did install the Add-on Compatibility Reporter and reported that silverlight was not working with Firefox 3.6.

---

### Post by cozmicharlie on 2010-02-18
> **bob brazie said:**
> I am still at a loss as to how to run silverlight using the Add-on Compatibility Reporter.

I did install the Add-on Compatibility Reporter and reported that silverlight was not working with Firefox 3.6.

You don't "run" silverlight.  It just works when you try and run the video.  In Linux you are actually installing Moonlight (the linux version of Silverlight) but it works.  Make sure you install Moonlight 3 ([http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx)).  Open tools>add-on and make sure Moonlight 3 is listed.  If not uninstall the version listed and reinstall Moonlight 3.  You may also need to clear your cache (clear history).  Make sure you restart Firefox.  You must also install the Microsoft codecs.  When I installed Moonlight 3 then tried to run the video I got a message that asked if I wanted to install the MS codecs - click on OK (you may have to restart FF). You should be able to watch the video now.

Hope this helps.

---

### Post by bob brazie on 2010-02-19
Thanks, that did the trick once I understood what you were trying to say and then installing the plug-in you suggested and not the one the site directed me too. I guess the answer was so simple and could be answered with one link as you did.

BTW my mention of "run" was meant to mean when I clicked on the video to play it.

Thanks to all, Bob.

---

