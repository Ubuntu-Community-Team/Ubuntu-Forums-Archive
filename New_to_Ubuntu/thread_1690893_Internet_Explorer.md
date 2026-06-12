---
title: "Internet Explorer"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-02-19
Can IE be downloaded into Ubuntu.

I was trying to get Paint Shop Pro to upload using Wine but it starts to load and then the message pops up....................

IE needed to run this program. Dont know why cos I didn't have IE loaded when I used it in win7

---

### Post by Linyx on 2011-02-19
I think IE-8.0 can run fine on wine > [http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html]("http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html")

But a little configuration maybe needed(I think so)...

---

### Post by robsoles on 2011-02-19
I want to suggest [www.virtualbox.org]("http://www.virtualbox.org") to run a virtual machine with whatever flavour of Windows you hate least and then use the Paint Shop Pro software in that for surer likelihood of all functions of the software being supported.

This search of the WineHQ App DB has results from their forums and other sources that make it look like installing Internet Explorer shouldn't be to difficult (odd one makes it look nigh on impossible tho!) [http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=internet+explorer&siteurl=appdb.winehq.org%2F#1118]("http://www.winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=internet+explorer&siteurl=appdb.winehq.org%2F#1118")


BTW: Any installation of any version of Windows since Windows 95 that **doesn't** come with msie.exe/(whatever latest executable is named) installed is probably broken because Microsoft use their browser for too much, in my humble opinion, and in Windows XP file-browsing isn't possible without msie.exe (IE) to the absolute best of my knowledge.

<edit> Dunno where I am remembering msie.exe from but I see the name of the executable that I have been trying to refer to is iexplore.exe these days - I am not so ashamed my knowledge of Windows is getting outdated, probably should shut up more often though! :lol: </edit>

---

### Post by bikodog on 2011-02-19
Another option is to install Default User Agent Switcher add-on for Firefox. This solves the "IE required" issue in many cases.

---

### Post by grahammechanical on 2011-02-19
I am using Wine. When I go to the Wine menu and select browse C:Drive, I see a folder called Program Files. In that folder is another folder called Internet Explorer in which is a file called iexplore.exe.

I think that the Wine people are doing something to prevent the need to install Internet Explorer. Perhaps you need to update to the latest version of Wine.

Regards.

---

### Post by waynefoutz on 2011-02-19
If you install playonlinux from the repositories, it will install any version of IE you want. Recently they changed the look of it, it no longer looks like Microsoft's browser, probably due to legal reasons, I don't know. But the generic looking browser it installs is all IE under the hood.

---

