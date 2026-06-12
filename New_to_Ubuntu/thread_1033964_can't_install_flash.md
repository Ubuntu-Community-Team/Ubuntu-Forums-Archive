---
title: "can't install flash"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by hifen on 2009-01-07
i've installed flash on other computers with no problems, however i can't get it working on my old acer 3500.   I've tried downloading it from the site, and it either "downloads" or won't download saying a copy of the newest version is already installed, however when i got to a site such as youtube, it asks me to download the latest version.   

I've tried sudo apt-get install flashplugin-nonfree, however that just displays a 404 error, and 0 of 285 not upgraded.

Is there anything else i can do?:popcorn:

---

### Post by HotShotDJ on 2009-01-07
> **hifen said:**
> Is there anything else i can do?:popcorn:Try using your GUI tools... Applications --> Add/Remove...

Now, search for Flash.  You can choose to install Ubuntu restricted extras (you'll get a lot of other stuff, including the the flash plugin) or you can choose Macromedia Flash plugin.  As long as you are connected to the internet and you haven't messed with your repositories file, you should be fine.  If this gives you problems similar to your problem with apt-get, well have to take a look at your repositories (which can be handled from the desktop as well... there is no need to use the terminal for this kind of stuff anymore)

---

### Post by wolfen69 on 2009-01-07
the following may or may not work, but has worked for me. completely remove flash from your computer via synaptic. then
```
sudo apt-get clean && sudo apt-get autoremove
``` 
then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu. close firefox and click to install. hope it works for ya.

---

### Post by HotShotDJ on 2009-01-07
> **wolfen69 said:**
> download the .deb for ubuntu.There is no reason to do this.  Flash 10.0 is provided in the official ubuntu repositories.  Unless you have a specific reason for downloading from a third-party source (and there ARE times that it is the best solution), you would be better served using the repositories.

If there is some breakage somewhere in your package management system, lets diagnose and fix it rather than try to go around it.

---

### Post by kansasnoob on 2009-01-07
You didn't mention what version of Ubuntu you're using. 8.04? 8.10?

---

### Post by hifen on 2009-01-07
i've tried

sudo apt-get clean && sudo apt-get autoremove

with no use.  I have 8.04, i have tried installing flash a few times, from synaptic, from add/remove gui and terminal and directly from the site, i've downloaded the .tar.gz and removed and tried .deb, none of it works.

I go to youtube (with firefox)  and when i click on a video nothing displays.


When i tried with konqueror thats when it told me to download the latest flash.

i have an app i just installed (after i did my first most) that makes a button on the flash applet that you have to click to run it, i just wanted to see if my comp could detect the flash, and the button appears, but after i click nothing happens.

Could this maybe be a java problem, or would it strictly be a flash issue?

---

### Post by Excedio on 2009-01-07
I was experiencing this EXACT same problem this morning. I have a question first though....

Is your computer 32bit or 64bit?

---

