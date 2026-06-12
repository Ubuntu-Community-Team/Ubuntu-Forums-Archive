---
title: "Maverick upgrade causes browsers issues"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by growler24 on 2010-10-28
Hello all,*

This is my first post so apologies if i have left anything out, feel free to ask.

I've recently upgraded from karmic to lucid and then maverick soon after. *Since doing so, i have lost all reliability with my web browsers. *I have tried Chrome, Chromium, Firefox and Midori all are suffering either severe loading time issues or simply not loading pages, it does on occasion say the page has loaded but only presents me with a blank screen. *It is also very hit and miss if it loads a page, there doesnt appear to be any sites in particular which dont load or do load but take time to do so.

On Karmic, i upgraded to the latest version of Firefox (3.5 then 3.6 i think) from version 3.4 i think (sorry i cant say for certain if version numbers are correct). *I also upgraded to the latest version of Chromium (not sure what date, but it would be around the middle of april this year) *When i upgraded the browsers, this is when the problems first happened. *I rolled firefox back to 3.4 and it went back to normal speeds, now i'e moved to Maverick, the problems have resurfaced. *
I have tried opening the browsers via the terminal but received no error messages.

I'm on a 22.5 meg DSL connection using the latest generation BT home hub. *I have no problem with speeds in any other area such as downloading, plus i am able to browse at normal speeds on my phone when connected to WIFI.
Im using a Toshiba Satelite L30-113 Model number PSL33E-039031EN

Any help with this would be very much appreciated

---

### Post by oregonbob on 2010-10-28
You are not alone. I didn't even upgrade to 10.10. It is doing the exact same thing on my 10.04 after running perfectly for a year! My Chrome, once superb and supreme is now completely unusable. I have worked many hours trying to resolve it but I gave up and switched back to old Firefox. I think there must have been an update or a driver change that came in with the updates that spoiled my once-perfect system.

"say the page has loaded but only presents me with a blank screen. *It is also very hit and miss if it loads a page, there doesnt appear to be any sites in particular which dont load or do load but take time to do so."

I have the exact same symptom on Chrome.

---

### Post by Ctrl-Alt-F1 on 2010-10-28
There was a Firefox update that I pulled down just literally minutes ago.  It seems to already have sped things up for me going from Firefox 3.6.11 to 3.6.12 on Ubuntu 10.04.  It was almost unusable before.

As for chrome:

I've heard that if you delete /usr/home/.config/google-chrome that it speeds up significantly in some cases.  However this will delete all of your bookmarks and preferences (maybe even your extensions), so use at your own risk.

---

### Post by growler24 on 2010-10-28
I've just reinstalled FF and run my update manager, unfortunately it's still nigh on unusable. Everything else has gone fantastic with with the upgrade, which is why it's so annoying

Oregonbob, 
What version did you switch to and how? I've gone the google route but haven't found a reliable result as far as I can see.

---

### Post by oregonbob on 2010-10-28
Are you running 64 bit Ubuntu? I'm curious because my browser problems are on my 64bit machine only. I have a couple of 32bit with no issues. I ran Google's Chrome for a long time as it ran circles around every other browser. But about a month ago it went to hell starting with those pages that appear to load without error but then display only a blank. I tried everything, purges, removal, install, beta, stable, flash versions... working on it for hours/days. Nothing has fixed it.

Then I just returned to using standard Ubuntu install of FF and it is running OK. I dearly love Chrome with sync'd bookmarks, etc. so I sure wish they would fix it.

Is yours 64bit?

---

### Post by Ctrl-Alt-F1 on 2010-10-29
I run Google Chrome frequently on Ubuntu 10.04 x64 and I haven't had any of those problems.  I have heard that occasionally a corrupted profile will cause it to behave poorly but deleting the local user data as I mentioned, is supposed to fix that in most cases.  That's a bummer that you can't get it working because Chrome is quite faster than Firefox in my experience.

---

### Post by oregonbob on 2010-10-29
> **Ctrl-Alt-F1 said:**
> I run Google Chrome frequently on Ubuntu 10.04 x64 and I haven't had any of those problems.  I have heard that occasionally a corrupted profile will cause it to behave poorly but deleting the local user data as I mentioned, is supposed to fix that in most cases.

Yes I tried the method of deleting .config/google-chrome . It didn't help in my case. I tried removing the package with purge option then I manually hunted down anything google and deleted it also. Frustrating! Chrome is important enough that I will soon do a new install of OS and everything just to get it back.

---

### Post by growler24 on 2010-10-29
I'm running a 32 bit version, I've tried fresh installing 10.04 and 10.10 to see if it fixes anything but nothing.  I've seen on a few forums that its a corrupted profile, some mentioned addons being a cause also.  However i've not installed any addon's (only changed the theme) so dont think thats the issue.  And this started happening pretty much as soon as i switched to lucid/maverick from Karmic.
 
I've also tried the latest version as previously mentioned but again nothing.  I've tried Chrome again and it was even worse again, this time i couldnt get past the welcome pages.  I've now discovered that the only page that loads without fail is Google as its my homepage

---

### Post by Perseverance on 2010-10-29
> **growler24 said:**
> 


I've recently upgraded from karmic to lucid and then maverick soon after. *Since doing so, i have lost all reliability with my web browsers. *I have tried Chrome, Chromium, Firefox and Midori all are suffering either severe loading time issues or simply not loading pages, it does on occasion say the page has loaded but only presents me with a blank screen. *It is also very hit and miss if it loads a page, there doesnt appear to be any sites in particular which dont load or do load but take time to do so.


I have tried opening the browsers via the terminal but received no error messages.
Okay Common issue lately. Again :
> **Perseverance said:**
> If you are using mozilla , there is a  common issue with IPv6 settings. So once again the solution ( I have quite get use to writing  this):
In firefox in your address bar type about:config and find network.dns.disableIPv6 and set  it to true if it is not already set.Than go to [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) . Take the first calculated   DNS and place it in Here : Right click network icon -> Edit  Connections -> At auto eth0 click edit->IPv4 -> DNS Server. At  the tab IPv6 make sure it is set to Ignore.

Hope That helps
The explanation : 
The way your connection is behaving(not loading in different browsers but having a good speed of download) suggest bad dns server ( with either  slow response time or Only IPv6 settings enabled).To speed up your  firefox you need to disable IPv6 usage there.

Hope that helps

---

### Post by Perseverance on 2010-10-29
> **growler24 said:**
>  I've now discovered that the only page that loads without fail is Google as its my homepage

It does because it is cached to your browser and does not need process it but just see if there were changes.

---

### Post by oregonbob on 2010-10-29
Wow, I have thought I fixed it before and was wrong, but I disabled ipv6 on my 10.04 64bit and since have been trying to break Chrome. So far it has been running perfect. But I gotta go and will have to work it out later.

---

### Post by growler24 on 2010-10-29
I think i may have located the problem, I've just connected via a wired connection and its now working fine.  So it now looks like there's an issue with my Home Hub/Wireless.

I did try the DNS server suggestion and that didn't work either

---

