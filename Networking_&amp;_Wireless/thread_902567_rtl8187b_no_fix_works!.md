---
title: "rtl8187b no fix works!"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Abunai XD on 2008-08-27
Ok so its like this, i joined a few days ago and since then ive done almost EVERY fix possible on a few different os's (ubuntu,kubuntu,mint & fedora) yet my rtl8187B card wont work. No matter what i do the most i can get is to where it will show the wifi in Ubuntu but then it wont connect even if the wifi is open. Wep wont work at all even under manual, after restart all is lost and i have to redo everything to install the patch and/or driver.

Im stuck, i switched from Vista because of the issues and well now it seems as if im going to have to switch back until they can add a patch to fix the rtl8187b issues.

Im running off of a Gateway M-1625 if that helps

---

### Post by CJay554 on 2008-10-04
My gf has the same computer as you, the rtl8187b driver from post #7 here:
[http://ubuntuforums.org/showthread.php?p=4784343](http://ubuntuforums.org/showthread.php?p=4784343)

it worked on open or WEP encrypted wireless, it wont work on WPA (yet)
a problem i had was loading the wlan0up script on boot up, i just did this:


after installing the driver:

1. cd into the rtl8187b-modified
2. do "update-rc.d wlan0up default
3. then do "chmod +x wlan0up"

2 will add that script so that its run on bootup, 3 will make that script executable. So now when you startup the computer that script will automatically run and you should be able to connect to WEP or Open networks.

you should rename rtl8187b-modified to .rtl8187b-modified (with the . ) so that its hidden from public view and not modified

There is a limit with the rtl8187b driver.. But the ubuntu community will prevail with a perfect driver over time :guitar:

---

