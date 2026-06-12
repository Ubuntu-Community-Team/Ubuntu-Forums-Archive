---
title: "Adobe Plash Player crashes"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-07-22
Hi,I am running Ubuntu 9.1.Just did the security updates for Ubuntu,and then I went to Paltalk,and when I try to type in my password,it says that Adobe Flash Player has crashed.This hasn't happened til this update.I tried uninstalling it, and resintalling,but that did not work.I then tried playing some videos with Flash Player, and it runs fine.How do I fix this? Oh,and this Paltalk is Paltalk Express,which runs in Firefox.It is not the regular Paltalk program.

---

### Post by lovinglinux on 2010-07-22
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by viking350 on 2010-07-22
One thing I have noticed Ubuntu does not like adobe flash so try Ubuntu-resticted-extra's install it in you terminal and boom there you go try it now :D and you can also download it on Ubuntu software center :p

---

### Post by lovinglinux on 2010-07-22
> **viking350 said:**
> One thing I have noticed Ubuntu does not like adobe flash so try Ubuntu-resticted-extra's install it in you terminal and boom there you go try it now :D and you can also download it on Ubuntu software center :p

This will install the same flash version installed by Adobe.

---

### Post by Ben_222 on 2010-07-22
Ok lovinglinux,here is the file path and version  

File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-07-22
Nothing wrong with your flash version.

It seems this is a bug:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/602215](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/602215)

---

### Post by Stigmata13 on 2010-07-22
Out of curiosity, are you running 32 bit or 64 bit? 64 bit has some trouble with flash as of now. An easy way to know, would be if you installed the "AMD 64" version of Ubuntu.

---

### Post by Ben_222 on 2010-07-22
32 bit

---

### Post by buckeyered80 on 2010-07-24
Yes, I have tried it on both Firefox and Google Chrome and they both crash when you try to enter your password on the sign-in page. It's probably not a firefox bug. Maybe Ubuntu, but it could also be something Paltalk needs to fix. I tried to report it to paltalk, but I don't think they care about Linux or Mac Users very much...Let me know if you figure anything out.

---

### Post by angelsguitar on 2010-07-24
I can confirm this too. I recently asked on the forums about this:

[http://ubuntuforums.org/showthread.php?t=1533122]("http://ubuntuforums.org/showthread.php?t=1533122")

I don't think it is an Ubuntu bug, but something in Paltalk Express itself. I'm using Puppy Linux 5, PCLinuxOS 2010.07 and Mepis 8.5 too, and Flash crashes in the same way, in both 64 bit and 32 bit (PCLinuxOS and Puppy are 32 bit, by the way).

I got it to work in Mepis 8.5 64 bit version by installing Flash from the debian-multimedia repos, which I believe is the 32 bit version of Flash running with the ia32 libraries. Maybe running Flash 32 bit on Ubuntu 64 bit could work, but have not tried it.

However, I believe we should try to "fill" Paltalk forums with requests about this matter.  Maybe they'll do something if a lot of people start bugging them with the same issue...

---

### Post by buckeyered80 on 2010-07-24
That's a good idea. Yeah, I am pretty sure it is Paltalk. It's too bad because it was working great with mic and sound until the upgrade to Adobe 10.1.

---

### Post by Pimpmobile on 2010-08-14
Sorry for grave digging but I found a workaround for this. Log into the paltalk.com site and you will be automatically logged into paltalk express when you go to express.paltalk.com. Therefore no crashes.

---

### Post by skarme on 2010-08-14
I was having issues with Adobe Flash too, until someone suggested this Add-On for Mozilla Firefox.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
It's a good Add-On and resolved my issues which I couldn't rectify myself.

---

### Post by angelsguitar on 2010-08-14
> **Pimpmobile said:**
> Sorry for grave digging but I found a workaround for this. Log into the paltalk.com site and you will be automatically logged into paltalk express when you go to express.paltalk.com. Therefore no crashes.

Thank you very much; this worked great! :D

---

### Post by buckeyered80 on 2010-08-22
Yeah that way does work. But the only problem is if you sign in that way, the buddy list doesn't show up. Is that happening for you all too?

---

### Post by buckeyered80 on 2010-08-26
I think paltalk fixed it. It's working now logging in from the login screen.

---

### Post by ruehara on 2010-08-26
I have a similar problem. I'm running a clean install of Ubuntu 10.4 32 bit with Firefox 3.6.8 and flash plugin 10.1.82.76ubuntu0.10.04.2.

Viewing a Youtube video works fine until I go to full screen when I get the "Adobe Flash Plugin has crashed" message. When I try this in Chromium I get a similar result .

Running Firefox 3.5.3 in a Linux Mint virtual box gives no problems at all.

I have Flash-aid installed in my Ubuntu Firefox and have run this a few times but the situation hasn't improved.

Where to from here?

---

### Post by ruehara on 2010-08-26
Following suggestions in Firefox help I modified my Firefox startup command to preload libGL.so.1 and then disabled video acceleration.

Now everything works a treat.

Thanks to all contributors - even your problems help !!

---

### Post by buckeyered80 on 2010-11-01
Hey Ruehara,

Do you have a link to those suggestions you followed? I might want to give that a shot too.

---

### Post by Joshimitsu on 2010-12-27
I'm on 10.10 and had this problem too but worked around it using Prism.  

Download Prism from the Software centre.

In the setup screen paste the Paltalk express url into the first field.  Give it a description in the second field.  Tick whatever preferences you want and select the "create a desktop shortcut" tickbox too.  

Finally, on the desktop icon, right-click, go to permissions and check the box to make it executable.  

I can now login to Paltalk Express without the flash player crashing.

Hope that helps.

---

