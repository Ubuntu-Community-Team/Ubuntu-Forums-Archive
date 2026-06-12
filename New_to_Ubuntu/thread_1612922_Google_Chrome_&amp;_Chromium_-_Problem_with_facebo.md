---
title: "Google Chrome &amp; Chromium - Problem with facebook"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by amjjawad on 2010-11-03
Hi everyone,

I had Google Chrome installed in Ubuntu for more than 3 weeks if I'm not mistaken. I installed it from Google's website not from any other location/tools.

I love Chrome, it's so fast and I can't use Firefox only, have to use both at the same time.

Anyway, last couple of days, I noticed that Chrome is acting weird with Facebook. I can't post anything. I click on "Share" to set a status but nothing happens whatsoever.
I tried to re-install Adobe Flash again but it says that I already have the latest one.
Today, I couldn't take it anymore so I un-installed Chrome and installed Chromium instead.
Well, Chromium is acting in a very funny way, even worse than Chrome.

I didn't check other sites. I use Chrome and Chromium now for facebook and some other websites. My main browser is Firefox.

Any idea how to fix that? Am I the only one with this problem? or it's a general issue? 

Thanks in advance :)

P.S.
Sometimes, I have to refresh the page twice or three times just to read the content of the page (facebook) probably. However, when I need to post something, I can't no matter how many times I refresh the page.

---

### Post by amjjawad on 2010-11-03
I forgot to mention:  

1) With Firefox, I don't have any issue. It's only with Chrome and now with Chromium.  

2) I removed/un-installed Chrome from Synaptic and Installed Chromium from Synaptic  

3) I installed Epiphany Browser before installing Chromium but apparently the same problem happened.

---

### Post by waynefoutz on 2010-11-03
did you try emptying the cache? This one has me stumped. 

Try installing Midori browser through synaptic. It's another Webkit browser like Chrome. See if you get the same errors in it.

---

### Post by amjjawad on 2010-11-03
> **waynefoutz said:**
> did you try emptying the cache? This one has me stumped. 

Actually the whole thing started after I did that few days back.
So, I didn't do it again, I just removed Chrome and Installed Chromium but the result was even worse.

> 
Try installing Midori browser through synaptic. It's another Webkit browser like Chrome. See if you get the same errors in it.

I'll give it a try now.

Thanks!

---

### Post by amjjawad on 2010-11-03
> **waynefoutz said:**
> Try installing Midori browser through synaptic. It's another Webkit browser like Chrome. See if you get the same errors in it.

Almost the same. Little bit better (can post but can't remove posts) but almost the same.

Actually I don't want to install more browsers. I care about Firefox (which works perfectly fine as of now) and Chrome.

---

### Post by amjjawad on 2010-11-04
Any more thoughts?

---

### Post by gandaran on 2010-11-04
> **amjjawad said:**
> Any more thoughts?
try backup your existing chromium user profile (just change the (/home/user/.config/chromium/ folder name) do the same to chrome then start the browsers, they will make a new user profile again and if no work you can restore the old one.

---

### Post by amjjawad on 2010-11-04
> **gandaran said:**
> try backup your existing chromium user profile (just change the (/home/user/.config/chromium/ folder name) do the same to chrome then start the browsers, they will make a new user profile again and if no work you can restore the old one.

As I mentioned previously, I removed Chrome and I just installed Chromium (when I started this thread).
Chromium has already a new user profile.

I might install Chrome again and see what would happen.

It was working perfectly but I'm not really sure what happened.

---

### Post by TBABill on 2010-11-04
Are you using the latest Chromium? An update yesterday or the day before installed version 7.0.xxx.xx (not sure exactly but it's version 7). I had no issues using Chromium 6.whatever on Facebook but I can test 7 at home tonight and see how it works as a comparison. I'm wondering if you can get your hands on whichever version of Chromium you are not running and install along with the other and see if they act the same or if it could be a regression of some type (or just a breakage) that you are experiencing.

---

### Post by amjjawad on 2010-11-04
> **TBABill said:**
> Are you using the latest Chromium? An update yesterday or the day before installed version 7.0.xxx.xx (not sure exactly but it's version 7). I had no issues using Chromium 6.whatever on Facebook but I can test 7 at home tonight and see how it works as a comparison. I'm wondering if you can get your hands on whichever version of Chromium you are not running and install along with the other and see if they act the same or if it could be a regression of some type (or just a breakage) that you are experiencing.

Chromium - 7.0.517.41 (62167) Ubuntu 10.04

---

### Post by amjjawad on 2010-11-04
Google Chrome - 7.0.517.41

I just installed it and I'll keep them both (Chrome and Chromium) and will try to check whether the same issue will be back again or not.

---

### Post by amjjawad on 2010-11-04
On a side note, I also noticed that with Facebook, when I try to change the font and language settings, mainly when I increase the font size, nothing will happen on facebook and the font will remain the same. It happens ONLY with facebook. With other websites, say Gmail, once I change the font size (increase it), it becomes bigger but again, it happens with other websites not with facebook.

With facebook, I always have to zoom in to get bigger fonts.

I just don't get it.

[COLOR=Blue]** Any ideas?**[/COLOR]

---

### Post by amjjawad on 2010-11-05
I still can't POST anything on Facebook using Chrome while Chromium seems to be working without issues so far.
Both are the latest versions.

I tried to clear the browsing data and I removed everything. However, Chrome is still not working probably.

Is there any one who could possibly help?

Thanks!

---

### Post by ubunterooster on 2010-11-06
Okay, this is a bit odd. Try clicking the tool icon in chrome/chromium. Click preferences, then go to the "under the hood" tab. At the bottom of that tab and click "reset to defaults"

---

### Post by ubunterooster on 2010-11-06
> **amjjawad said:**
> I tried to clear the browsing data and I removed everything.By "removed everything", do you mean plugins and extensions?

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> Okay, this is a bit odd. Try clicking the tool icon in chrome/chromium. Click preferences, then go to the "under the hood" tab. At the bottom of that tab and click "reset to defaults"

Actually I did more, I un-installed it completely and re-installed it again but same old thing.

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> By "removed everything", do you mean plugins and extensions?

I don't have any plugins nor extensions. 
I went to Options > Under The Hood > Clear Browsing Data and I checked all the options, chose "**everything**" from the period option then **clear browsing data**.
I've done that after re-installing Chrome for the 2nd time. However, the problem is still happening.

---

### Post by ubunterooster on 2010-11-06
> **amjjawad said:**
> Actually I did more, I un-installed it completely and re-installed it again but same old thing.
Actually, uninstalling does *not* remove the data! Try running the following into the terminal (all bookmarks and passwords will be lost) May not work, but it might.
```
sudo apt-get purge chromium-browser -y
```
```
sudo apt-get install chromium-browser -y
```If this fails to work, I might consider using a newer version of chrome than is mainstream

---

### Post by ubunterooster on 2010-11-06
I can help you get the PPA for newer packages of chromium having found them now

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> Actually, uninstalling does *not* remove the data! Try running the following into the terminal (all bookmarks and passwords will be lost) May not work, but it might.
```
sudo apt-get purge chromium-browser -y
```
```
sudo apt-get install chromium-browser -y
```If this fails to work, I might consider using a newer version of chrome than is mainstream


Okay, haven't done that yet so I'll try it :)
I'm on Fedora now. I'll restart and try that in awhile.

In fact I already installed the latest version of Chrome. Not to mention, I installed the latest update today as well. Update Manager popped up and there was 20MB update for Chrome.

I'll do that and will let you know :)

Thanks!

---

### Post by ubunterooster on 2010-11-06
By "latest" Do you mean testing source? or "latest release"

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> By "latest" Do you mean testing source? or "latest release"

Latest release. I downloaded Chrome yesterday or the day before and it's version 7 something.

---

### Post by ubunterooster on 2010-11-06
I'm assuming that you have ubuntu-tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Go to Ubuntu tweak > source Center. Under the browser area, select ubuntu-chromium daily builds. They are ahead of the download you get from google and I have not met problems with it.

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> I'm assuming that you have ubuntu-tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Go to Ubuntu tweak > source Center. Under the browser area, select ubuntu-chromium daily builds. They are ahead of the download you get from google and I have not met problems with it.

I don't have it. I'm keen to keep everything as it's. That would be much easier for me to fix everything.
Whether it's a browser or OS, I don't install tweaks, extensions, etc :)

---

### Post by ubunterooster on 2010-11-06
LOL, I use it *because* that way it is "much easier for me to fix everything."

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> LOL, I use it *because* that way it is "much easier for me to fix everything."

Hahaha, then guess we have two different approaches ;)

Ok, I'm just trying to find one thing in Fedora then I'll log off, restart, login to Ubuntu and try to follow your instructions. Hope that would fix the issue :)

---

### Post by amjjawad on 2010-11-06
> **ubunterooster said:**
> Actually, uninstalling does *not* remove the data! Try running the following into the terminal (all bookmarks and passwords will be lost) May not work, but it might.
```
sudo apt-get purge chromium-browser -y
``````
sudo apt-get install chromium-browser -y
```If this fails to work, I might consider using a newer version of chrome than is mainstream

Hi again my friend,

The code above is for Chromium not Chrome :)
Anyway, I searched the forum and I found this: [http://www.uluga.ubuntuforums.org/showpost.php?p=9820858&postcount=24](http://www.uluga.ubuntuforums.org/showpost.php?p=9820858&postcount=24)

I managed now to completely remove both Chrome and Chromium.
I'm going to install Chrome only as the problem has started with it. I'll keep testing it and will report back.

I used this by the way to remove **Chrome**:
```
sudo apt-get remove google-chrome-stable
```

---

### Post by amjjawad on 2010-11-06
```
sudo apt-get install google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 libsnack2-alsa libvpx0
  linux-headers-2.6.32-24-generic tcl8.5 tk8.5 tcl-tls
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  google-chrome-stable
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.9MB of archives.
After this operation, 77.9MB of additional disk space will be used.
Selecting previously deselected package google-chrome-stable.
(Reading database ... 161331 files and directories currently installed.)
Unpacking google-chrome-stable (from .../google-chrome-stable_7.0.517.44-r64615_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up google-chrome-stable (7.0.517.44-r64615) ...
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.


```

Ok, it's installed via Terminal.
Let's see if that fixed the problem or not :)

---

### Post by ubunterooster on 2010-11-06
Having serious Hard drive problems; may be out of the support area for a while.

---

### Post by amjjawad on 2010-11-07
> **ubunterooster said:**
> Having serious Hard drive problems; may be out of the support area for a while.
Oh, I'm sorry to hear that my friend. Never mind, hope you'll fix it soon :)

I'll keep monitoring Chrome and that might take a while too.

---

### Post by amjjawad on 2010-11-09
Alright, two days so far and I can post, delete posts, update my status, etc but every time I click on:
- My profile
- Home page
- Log off
(mainly these links)
I got a messed up page just like there's no Flash installed ... not sure how to explain that in words.

I just doubled checked Adobe and it says:

[COLOR=#000000][FONT=Kedage][COLOR=#333333][FONT=Arial]> [FONT=Arial][COLOR=#000000][FONT=Kedage][COLOR=#333333][FONT=Arial]Your Google Chrome browser already includes Adobe® Flash® Player built-in. Google Chrome will automatically update when new versions of Flash Player are available.

[/FONT][/COLOR][/FONT][/COLOR][/FONT][/FONT][/COLOR][/FONT][/COLOR]I noticed that even with Firefox (sometimes), I got the same issue but that's mainly when I download files from the internet but with Chrome, even if I'm not downloading, I got that problem.

I don't know whether it's Chrome or Facebook? I know facebook (I called it failbook) is always messed up but why with Chrome? again, it happens BUT LESS with Firefox.
Not to mention that whenever I open more than 3-4 active tabs, Chrome always crashes :(

Yeah, I know Firefox is better than Chrome but Chrome is faster.

Thoughts?

---

### Post by amjjawad on 2010-11-09
After I posted my last post, I got that issue so there you go:

---

### Post by amjjawad on 2010-11-11
Hello (echo) ... (echo) ... (echo)

I still have the problem, Chrome still crashing, Chrome still acting crazy and I'm wondering if ANYONE knows what to do?

---

### Post by amjjawad on 2010-11-13
I can't believe that NO ONE here in this forum knows how to fix this issue?!
If this issue can not be solved, please let me know.

Also, if there's a powerful Browser such as Firefox (please don't tell me Opera, I tried it and it's much slower than FF and Chrome), please let me know.
As I said, I love Chrome but as long as both Chrome and Chromium are acting crazy, I must find another browser.

This thread will not be marked as SOLVED because it's not solved yet.

Thank you in advance!

P.S.
If this is the wrong place to post such a thread, hope one of the moderator could show me the right place and move this thread in case I'm posting in the wrong place.

---

### Post by 3Miro on 2010-11-13
What exactly is the issue? If it that you are having trouble with Flash or Fonts?

I don't know Chrome, I don't use it, however, to get Flash working with Chromium, you have to install Ubuntu-restricted-extras (basically Chromium uses flash for FireFox). Test it with YouTube.

If the browser is crashing, you can go to Apps -> Accessories -> Terminal and start it with:
```
 chromium-browser 
```
it will hopefully output a message when/if it crashes.

---

### Post by I'mGeorge on 2010-11-13
You could try Galeon and see how it goes. I don't know about that chromium facebook problem, I use chromium for quite some time and to be sincere in my case it worked and had fewer flaws than Firefox. I believe it's about what kinda desktop/WM you're using. I believe some browser work better in a wm while others by the contrary were made for Desktops.

You could also try and install flash player manually. For x86-64 versions I believe it works better than the one from the repos. But I kinda doubt this could be the problem.

You could also try compiling it from source after you uninstall it. Some packages worked a whole lot better for me this way than installing them from the repos.

---

### Post by uRock on 2010-11-13
> **3Miro said:**
> If the browser is crashing, you can go to Apps -> Accessories -> Terminal and start it with:
```
 chromium-browser 
```it will hopefully output a message when/if it crashes.
+1 If you get an error message, then please post it here. I have recently installed Chrome and have had no problems with it.

---

### Post by I'mGeorge on 2010-11-13
I believe the problem it's not that chromium crashes or doesn't work, it's about that it doesn't behaves as it should on facebook, and probably some other web sites.

---

### Post by amjjawad on 2010-11-13
Long story short:

[http://ubuntuforums.org/showpost.php?p=10095058&postcount=32](http://ubuntuforums.org/showpost.php?p=10095058&postcount=32)

Beside, sometimes, I can't post, remove posts, update status, change profile picture, go to my inbox, open any messages, etc. ALL the functions or let's say all the links look like disabled. No matter how many times I click on a particular link or refresh the page, I just can't do anything.

I cleared the cash, I removed Chrome and Chromium completely and install them back, did everything I could ever think about but nothing happened.

---

### Post by uRock on 2010-11-13
If you open Chome/ium via a terminal, then go to Facebook the terminal should start showing errors.

Does Firefox give you these problems? What about Opera?

---

### Post by amjjawad on 2010-11-13
> **I'mGeorge said:**
> You could also try and install flash player manually. For x86-64 versions I believe it works better than the one from the repos. But I kinda doubt this could be the problem.


That was the first step I've tried and failed. It said I already have the latest one when I tried that manually from Adobe's website.


> 
You could also try compiling it from source after you uninstall it. Some packages worked a whole lot better for me this way than installing them from the repos.
How?

---

### Post by nirmal3326 on 2010-11-13
though this is not a problems solved but here is what happened with me
i tried installing chromium from adding PPA From chromium-daily .. it was near fatal.. infact some good advice from forum helped me.. my package manager went packing.

regards 
nirmal

---

### Post by amjjawad on 2010-11-13
> **uRock said:**
> If you open Chome/ium via a terminal, then go to Facebook the terminal should start showing errors.


Had to type:

```
google-chrome

```Because I don't have Chromium anymore. I removed it because no one was replying my thread and it was acting even worse than Chrome so only Chrome is left.

So far nothing but I'll keep an eye on the Terminal.

> 
Does Firefox give you these problems? What about Opera?Firefox is almost perfect and I've never ever experienced any problem with it. If Firefox is trying to act weird, facebook will be a bit slow but I know it's not because Firefox anyway. Rather than that, no problems at all.

Opera's website says it's the fastest browser but it was the slowest browser on my PC. When I tried to login to facebook, it took 10-15 seconds or even more just to login. It was so slow comparing to Firefox and Chrome. I know Chrome is crashing a lot when I open 5-6 tabs (mostly when Youtube is one of these tabs) and it's giving me that problem with facebook (while I'm using facebook, I have only two tabs, one for facebook and other for gmail) but it's overall performance (speed-wise) is much faster than Opera.
However, I'm keeping Opera and not removing it for now but honestly I don't use it.
I'm still using Chrome despite all these issues.

---

### Post by 3Miro on 2010-11-13
I think most people here would be using Chromium since it is included in the Ubuntu repositories by default. It is possible that you have a mismatch in configuration files between Chrome and Chromium (I don't know if they share any). Also, you should try to use the official Chromium from the Ubuntu repository, the extra PPA are only if you have a specific problem and the daily builds are too unstable.

Every browser claims to be the fastest and I am sure for someone it is indeed the fastest. Use whatever browser works for you.

---

### Post by amjjawad on 2010-11-13
> **3Miro said:**
> I think most people here would be using Chromium since it is included in the Ubuntu repositories by default.


I used Chrome for many years now and I use it even before I know about Chromium.

> 
 It is possible that you have a mismatch in configuration files between Chrome and Chromium (I don't know if they share any). 


I don't think so at all. I guess I mentioned that in the beginning of my thread. I had this problem even **before** I install Chromium. Actually, I installed Chromium just to make sure the same issue won't happen again with it but it was worse than Chrome. Then, I removed them both, Installed Chromium, same. Removed Chromium and Installed Chrome again.

> 
Also, you should try to use the official Chromium from the Ubuntu repository, the extra PPA are only if you have a specific problem and the daily builds are too unstable.

As I mentioned, I tried it but it was worse than Chrome.

> 
Every browser claims to be the fastest and I am sure for someone it is indeed the fastest. Use whatever browser works for you.

Yes, I agree.
I'm trying to find the one that is good for me but couldn't find better than Firefox and Chrome despite all the problems I'm facing with it (Chrome).

---

### Post by amjjawad on 2010-11-13
> **uRock said:**
> If you open Chome/ium via a terminal, then go to Facebook the terminal should start showing errors.


uRock,

This is what I got:

```
[8098:8114:24547149569:ERROR:net/socket/client_socket_pool_base.cc(935)] No pending request for backup job.

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

(exe:8164): Gdk-WARNING **: XID collision, trouble ahead

```

I got these warning messages when I tried to open youtube links and videos within facebook.
I tried to produce more errors but couldn't find more.

Shall I keep monitoring it? or it became clear now what's wrong?

Thank you!

---

### Post by uRock on 2010-11-13
In this thread it says something about removing the libmoon package fixed the problem for someone else getting the same errors. [http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en)

---

### Post by 3Miro on 2010-11-13
I don't have Chrome, but I just tested Facebook with Chromium and it worked fine. Which means that the issue is probably with a setting of some sort. You can try to close Chrome, then go into your home folder (Places -> Home), hit Ctr + H to show hidden files, then look into .config and .cache folders and delete everything that has something to do with Chrome or Chromium. Log out and log in (an overkill, but just to be on the safe side) and try it again.

---

### Post by amjjawad on 2010-11-13
> **3Miro said:**
> I don't have Chrome, but I just tested Facebook with Chromium and it worked fine. Which means that the issue is probably with a setting of some sort. You can try to close Chrome, then go into your home folder (Places -> Home), hit Ctr + H to show hidden files, then look into .config and .cache folders and delete everything that has something to do with Chrome or Chromium. Log out and log in (an overkill, but just to be on the safe side) and try it again.

I have already done that and nothing worked :)

---

### Post by amjjawad on 2010-11-13
> **uRock said:**
> In this thread it says something about removing the libmoon package fixed the problem for someone else getting the same errors. [http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en)

First of all, THANK YOU so much for that link :)
I feel much better now ... I thought I'm the only one with this problem. However, I'm confused as apparently no one knows what's going on.

> 
[[IMG]http://www.google.com/s2/photos/public/AIbEiAIAAABDCMvJ0efbu97BSiILdmNhcmRfcGhvdG8qKDlkYjBlY2VhOWNmN2FiZTI4OGZhMjNiOTA0NzUwZDQxNmU3MDdhYjMwAYYz-h_8c2LCqw0VopWwJkH0_IfF[/IMG]]("http://www.google.com/support/forum/p/Chrome/user?userid=06979104763763599831&hl=en")   [chaghaboo]("http://www.google.com/support/forum/p/Chrome/user?userid=06979104763763599831&hl=en")  Level 1
11/6/10 
 
     Tried everything, fresh install of Ubuntu, Chrome with all plug-ins  disabled, uninstall and reinstall adobe flash plug-in, but crashes  continues. Don't know what to do, I did everything suggested in forums. 

That was his last post. The problem is not solved even after disabling the plug-ins he mentioned.

About "libmoon" package, the guy who posted and mentioned it, didn't explain further so what exactly shall I do? any idea?

I didn't know this could be so complicated problem but I hope it's not.

---

### Post by amjjawad on 2010-11-14
> **uRock said:**
> In this thread it says something about removing the libmoon package fixed the problem for someone else getting the same errors. [http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en)

uRock, guess what? I just checked Synaptic Package Manager in Ubuntu 10.04 on my PC and ... I don't even have "***libmoon***". It's not installed.
At least, now, I know what does "libmoon" mean but it's getting more complicated.


I posted [here]("http://www.google.com/support/forum/p/Chrome/thread?tid=1146f09e6997052f&hl=en&fid=1146f09e6997052f0004950a332f77a9") and I'm waiting for some replies.
What else do you suggest to do?

Thank you!

---

### Post by onaridge on 2010-11-14
I installed Chrome and them Chromium from the Google site and not from the repositories as I didn't know any better at the time. I had problems especially with FB. When I deleted those installs and installed from the software center my problems went away. I have since updated to the latest and still have no problems at all with Facebook and am a very frequent user of it. Flawless for about 3 weeks now. Not sure if this will help but I thought I'd weigh in.

---

### Post by amjjawad on 2010-11-14
> **onaridge said:**
> I installed Chrome and them Chromium from the Google site and not from the repositories as I didn't know any better at the time. I had problems especially with FB. When I deleted those installs and installed from the software center my problems went away. I have since updated to the latest and still have no problems at all with Facebook and am a very frequent user of it. Flawless for about 3 weeks now. Not sure if this will help but I thought I'd weigh in.

I've already done that but got the same result.
No matter from which source I install Chrome and/or Chromium, they don't work probably.

Thank you :)

---

### Post by amjjawad on 2010-11-15
Still no replies from Google's staff and Chrome is still producing errors:
```

[1754:1771:10488701053:ERROR:net/socket/client_socket_pool_base.cc(935)] No pending request for backup job.

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead

(exe:1842): Gdk-WARNING **: XID collision, trouble ahead
[1754:1771:17403620117:ERROR:net/socket/client_socket_pool_base.cc(935)] No pending request for backup job. 
```


This time, I was tagging some friends into a picture in facebook. I got all the above non-sense lines.

---

### Post by ubunterooster on 2010-11-16
Related but not really helpful, so I hope I'm not considered spamming but I though it worth mention that Maximum PC gave Chrome the award for the most bugs :(

[http://www.maximumpc.com/article/news/and_buggiest_software_award_goes_tochrome](http://www.maximumpc.com/article/news/and_buggiest_software_award_goes_tochrome)

---

### Post by amjjawad on 2010-11-16
> **ubunterooster said:**
> Related but not really helpful, so I hope I'm not considered spamming but I though it worth mention that Maximum PC gave Chrome the award for the most bugs :(

[http://www.maximumpc.com/article/news/and_buggiest_software_award_goes_tochrome](http://www.maximumpc.com/article/news/and_buggiest_software_award_goes_tochrome)

WOW, IE has less bugs/problems than Firefox, Safari and Chrome? why it's so hard to believe that? :D

And yes, I'm still having problems.
I removed Chrome completely and deleted the folder (/home/user/.config/google-chrome). Then, I installed Chromium from the Terminal.

I lost counting. I can't even remember how many times so far I removed Chrome, Installed Chromium, removed Chromium and installed Chrome, etc?!


These are some of what I got so far with Chromium which are the same errors from Chrome:

```
[2820:2835:9948415654:ERROR:net/socket/ssl_client_socket_nss.cc(1531)] handshake failed; NSS error code -5938, net_error -107

(exe:3024): Gdk-WARNING **: XID collision, trouble ahead

(exe:3024): Gdk-WARNING **: XID collision, trouble ahead

(exe:3024): Gdk-WARNING **: XID collision, trouble ahead

(exe:3024): Gdk-WARNING **: XID collision, trouble ahead

(exe:3024): Gdk-WARNING **: XID collision, trouble ahead


```


**Chromium Version: 7.0.517.44 (64615) Ubuntu 10.04**

---

### Post by geoffmcc on 2010-11-16
Not in a ha ha it works for me but not you way, but I just wanted to point out I am using 10.10 x64 with chromium-browser installed threw package manager without a hitch, although i don't use chrome for facebook much.

Seeing as you mentioned you have firefox installed all ready, check out Prism, it in repository. I know its not a solution, but i came across it the other day and like it. You can make a facebook icon right on your desktop that will open in a minimal version of mozilla. Cant navigate out of facebook but you can go all threw facebook without a problem. If you hit home button in browser it will just take you back to main profile page. Only thing i would like to see added is the option to open a link in new tab as i also use prism for ubuntu forums and would like that option.

just a thought, not a solution. But if you do go that route. When the icon is placed on desktop for facebook after you created it dont forget to right click and set to allow open as program

---

### Post by amjjawad on 2010-11-18
> **geoffmcc said:**
> just a thought, not a solution. 

Thank you for your thought but I'm done with trying more browsers :)
I had like 5 which I've never heard about and didn't like any.

Looks like there's no solution for my issue. I guess I have to live with it until Google fix it or until I find a better browser.

---

### Post by amjjawad on 2010-11-26
The problem is still exist. I can't Poke Back, can't comment on any status, can't change mine, same old crap.

No response from google until now and no response from here as well.

[I]Chromium
7.0.517.44 (64615) Ubuntu 10.04[/I]

---

### Post by amjjawad on 2010-12-11
Just to let you know (all), that the problems with Chrome/Chromium are STILL exist.

While Firefox **is working perfectly**, Chromium is **NOT**.

Yes, I got the latest version (8.0.552.215 (67652) Ubuntu 10.04).
NO, it's still acting crazy.

Seriously, can one find another clone to Firefox? something like Firefox? I'm sick and tired of Google so called the fastest browser. I run both on the same PC, same Internet, same OS, etc etc but Firefox is much more better in everything except the first time it starts and I don't care about that as long as it's giving me solid and great performance.

I hear you ... someone is telling me to remove Chromium and use Firefox only, right? well, I don't lose hope nor give up. There **MUST** be away to fix that.


P.S.
Yes, we reported that on Google's forum but NO ONE from Google's team replied yet.

---

### Post by amjjawad on 2010-12-12
[URL="http://scratch.mit.edu/static/icons/gallery/2759.png?t=2008-05-22+19%3A14%3A41"][IMG]http://findhitesh.files.wordpress.com/2009/12/ehhdoc1024wp.jpg[/IMG]
[/URL]

---

### Post by yh1000 on 2010-12-16
Clearing the cache solved the problem

---

### Post by amjjawad on 2010-12-16
> **yh1000 said:**
> Clearing the cache solved the problem

Have done that hundreds time already but nothing happened.

---

### Post by The Cog on 2010-12-16
Try this command:
> rm -rf ~/.config/chromium ~/.cache/chromium

Ggandaran suggested this four weeks ago but you refused to do it. I still think it may well fix your problems.

---

### Post by amjjawad on 2010-12-23
> **The Cog said:**
> Try this command:


Ggandaran suggested this four weeks ago but you refused to do it. I still think it may well fix your problems.

_[I remember I did that before]("http://ubuntuforums.org/showpost.php?p=10112599&postcount=49")_. Anyway, I have done it and since that time until now, the same issue is happening every day.
I've been monitoring it in different times (morning, nights, etc) and ... same. Nothing changed.

---

### Post by Frederich on 2011-01-02
I am somehow having the same problem, using the same version of Chromium you're using. For two days now, loading some pages, like Facebook, Gmail, or even Hotmail, is really, really slow.

I'd love to know if there is a solution to the problem !

Edit : Same with Midori. Now that's strange, ain't it ?

---

### Post by amjjawad on 2011-01-03
> **Frederich said:**
> I am somehow having the same problem, using the same version of Chromium you're using. For two days now, loading some pages, like Facebook, Gmail, or even Hotmail, is really, really slow.

I'd love to know if there is a solution to the problem !

Edit : Same with Midori. Now that's strange, ain't it ?

I don't think there's a solution for this problem.
I'm not going to bother with Chrome and Chromium anymore. I'm using Firefox only and keeping Midori for Gmail.

I know facebook dev are changing their website more than they change their clothes but with Firefox, you won't face the same problem so Google has to do something about that. IMHO.

For those who have not seen this thread before: YES, I have tried everything had been suggested here but nothing happened :)

---

### Post by Kirboosy on 2011-01-03
This is a wild stab but try installing the plugin/extension "Beautify Facebook" I really like what it does to Facebook and it might just solve some of your problems.

---

### Post by Frederich on 2011-01-03
> **amjjawad said:**
> I don't think there's a solution for this problem.
I'm not going to bother with Chrome and Chromium anymore. I'm using Firefox only and keeping Midori for Gmail.

I know facebook dev are changing their website more than they change their clothes but with Firefox, you won't face the same problem so Google has to do something about that. IMHO.

For those who have not seen this thread before: YES, I have tried everything had been suggested here but nothing happened :)

I've been reading this thread, to see if I could find a solution about this issue. What's really strange is that this "sluggishness" appeared just like that, without any rational explanation (at least, not one we know). I've checked many pages to see that some people were actually bothered by the same problem, but honestly not that much. What was also strange, was that on another Ubuntu distro I have on the same hard disk, the problem wasn't there. And the only difference between these distros was the version of Chromium - same as yours on the problematic one.

You might find this strange, but updating Chromium through Synaptic - version 10.0.627.0 (70364) Ubuntu 10.04 - seems to have done the trick. Also, disabling some experimental functions of Gmail did it. So far, no unusual slowness for the last 48 hours now.

---

### Post by amjjawad on 2011-01-09
> **Frederich said:**
> I've been reading this thread, to see if I could find a solution about this issue. What's really strange is that this "sluggishness" appeared just like that, without any rational explanation (at least, not one we know). I've checked many pages to see that some people were actually bothered by the same problem, but honestly not that much. What was also strange, was that on another Ubuntu distro I have on the same hard disk, the problem wasn't there. And the only difference between these distros was the version of Chromium - same as yours on the problematic one.

How fast is your internet connection? after all that time since I have started this thread until now and no real solution has found yet to fix that issue, the only thing I could suspect about is my slow internet connection. However, I don't have any problem with Firefox but maybe Firefox instead of showing a messed up page, it shows an error message.
My Internet Connection is ADSL 265kbps
The max download rate is 30KB/sec


> 
You might find this strange, but updating Chromium through Synaptic - version 10.0.627.0 (70364) Ubuntu 10.04 - seems to have done the trick. Also, disabling some experimental functions of Gmail did it. So far, no unusual slowness for the last 48 hours now.

My problem is not with Gmail so I don't think it has to do anything with facebook.
As for upgrade, as far as I know, it does not matter whether you do it through Terminal or Synaptic. All the same. Synaptic is a Graphical Interface whole The Terminal is CLI.

:)

---

### Post by amjjawad on 2011-01-21
Finally, Firefox did it. I got something like this: [http://ubuntuforums.org/showpost.php?p=10095058&postcount=32](http://ubuntuforums.org/showpost.php?p=10095058&postcount=32) (attached image).

However, I can post and do everything else, unlike Chrome/Chromium which did not let me do anything (post, remove post, etc).

After all these days, the only things I could think about are:
1- Slow Connections. My Internet is slow (265 kbps).
2- Facebook Problems. Well, I call it FAILbook for a reason.
3- Might be something else.

I'm back to Chromium (8.0.552.237 (70801) Ubuntu 10.04).

By the way, I have noticed that facebook has changed something in their website. Before, it used to take few seconds until my post go through and be there. Now, once I post, it's immediately there.
My main problem with Chromium was any post never go through so I have to switch to Firefox to do it.
I'll keep an eye and hopefully this new thing from facebook will last longer :)

Thought to keep you updated. However, this is not solved yet.

**Edit:**
Okay, I got it.
New comments are LIVE now. You don't have to refresh the page or do anything. For example: if you post something on someone's wall and you stay on that page then if that person will post back, you'll see his/her reply/new post or comment LIVE. 
Well, that's really impressive :)

I hope this will fix the issue.

---

### Post by Robert Lutken on 2011-02-08
> **amjjawad said:**
> Alright, two days so far and I can post, delete posts, update my status, etc but every time I click on:
- My profile
- Home page
- Log off
(mainly these links)
I got a messed up page just like there's no Flash installed ... not sure how to explain that in words.

I just doubled checked Adobe and it says:

[COLOR=#000000][FONT=Kedage][COLOR=#333333][FONT=Arial]

[/FONT][/COLOR][/FONT][/COLOR][/FONT][/FONT][/COLOR][/FONT][/COLOR]I noticed that even with Firefox (sometimes), I got the same issue but that's mainly when I download files from the internet but with Chrome, even if I'm not downloading, I got that problem.

I don't know whether it's Chrome or Facebook? I know facebook (I called it failbook) is always messed up but why with Chrome? again, it happens BUT LESS with Firefox.
Not to mention that whenever I open more than 3-4 active tabs, Chrome always crashes :(

Yeah, I know Firefox is better than Chrome but Chrome is faster.

Thoughts?

Im having exactly the same issue, not only with chrome but firefox as well it seems to me that, as you say its javascript of flash causing the issue .

---

### Post by bturrie on 2011-03-12
I'm having a similar problem with Chromium in Lucid 64bit. I cannot share Facebook updates from Chromium 9.0.597.107 but I can from Firefox. I can also share Facebook updates from Chrome on my work Windows 7 laptop (how embarrassing is that). Clearing my Cache doesn't help. I haven't tried anything else yet other than looking for oddities in my preferences.

This isn't a major problem for me since I do most of my posting from gmail via Posterious. Mostly It's just annoying. If I happen to stumble across something that helps, I'' post back here.

---

### Post by amjjawad on 2011-03-14
> **Robert Lutken said:**
> Im having exactly the same issue, not only with chrome but firefox as well it seems to me that, as you say its javascript of flash causing the issue .

Hi,

Do you still have the same issue?

As for Firefox, very rarely I have some issues but it's the prefect choice for me, can't use anything else as my main browser.

---

### Post by amjjawad on 2011-03-14
> **bturrie said:**
> I'm having a similar problem with** Chromium in Lucid 64bit**. I cannot share Facebook updates from Chromium 9.0.597.107 but I can from Firefox. I can also share Facebook updates from Chrome on my work Windows 7 laptop (how embarrassing is that). Clearing my Cache doesn't help. I haven't tried anything else yet other than looking for oddities in my preferences.


Hi,

Are you still having the same issue? have you tried to update your Chromium? I have 10.0.648.127 (76697) now and I'm using Lubuntu 10.04 32-bit.

Honestly, I see some improvements. I can now post easier than before but I still do have some issues like **Blank White Page **with only the header (Home Profile Account). I'm using Facebook much less than before but looks like there are some improvements with the new update.

I'm not quite sure whether it has to do with the OS or not?!


> This isn't a major problem for me since I do most of my posting from gmail via Posterious. Mostly It's just annoying. If I happen to stumble across something that helps, I'' post back here.

It's annoying indeed.
Thank you so much!

---

### Post by Mikster on 2011-04-21
> **yh1000 said:**
> Clearing the cache solved the problem

I had this problem (Facebook acting strange, chat broken, etc.) start happening to me just a day or so ago.

Cleared the cache, restarted chrome, and all was well again. Am using the current stable Chrome version.

HTH

---

### Post by Mark O on 2011-04-23
I just updated Natty, and now Facebook won't let me enter anything in the To: field when I want to send a message (in the Chrome browser)...I can enter in the other fields, and it works fine in Firefox...I can dual boot over to xp, and Facebook works fine in IE, Firefox, and Chrome...Can't tell whether it's a Facebook issue,Chrome issue, or an Ubuntu issue...The last 2 times I updated Natty, the screen went all weird on me and locked up, but it worked fine when I rebooted...Any ideas?...

---

### Post by Mark O on 2011-04-23
Ahh...I got it...it was a Chrome issue...I'm using the beta, and when I reinstalled it, my issue cleared up...Hope I didn't waste anyone's time...

---

### Post by amjjawad on 2011-04-25
> **Mark O said:**
> Ahh...I got it...it was a Chrome issue...I'm using the beta, and when I reinstalled it, my issue cleared up...Hope I didn't waste anyone's time...

You did not waste anyone's time :)

I think the problems mentioned in this thread are almost fixed with the latest version of Chromium but I can't confirm that now ... I haven't logged in to my PC for a very long time ... I've had some health problems and I'm using my friend's laptop now which SADLY has Win7.

WOW, did not post anything in this forum for 3 weeks :S

---

### Post by Jechem on 2011-05-21
Hi all,

I have a similar problem with Facebook but I only see the blue bar and nothing else. It won't load anything else on Google Chrome(11.0.696.68 ) 64-bit (screenshot). Facebook loads properly on Firefox 4 and on Windows 7 Chrome and Ubuntu 10.04 32bit Google Chrome(11.0.696.68 ). I have tried uninstalling it a couple of times but still the problem persists. The bug is still there I think. I don't mind about Facebook not loading but I can't stop thinking why the same Google Chrome Stable Build behaves differently.

---

### Post by amjjawad on 2011-06-07
> **Jechem said:**
> Hi all,

I have a similar problem with Facebook but I only see the blue bar and nothing else. It won't load anything else on Google Chrome(11.0.696.68 ) 64-bit (screenshot). Facebook loads properly on Firefox 4 and on Windows 7 Chrome and Ubuntu 10.04 32bit Google Chrome(11.0.696.68 ). I have tried uninstalling it a couple of times but still the problem persists. The bug is still there I think. I don't mind about Facebook not loading but I can't stop thinking why the same Google Chrome Stable Build behaves differently.

Hi,

Have you tried to install Adobe Flash 64-bit???

---

### Post by amjjawad on 2011-06-29
I see many improvements with Chromium these days. Each release is better than the previous and I think the problem is fixed now.

I disabled my Facebook account and this thread will be marked as SOLVED until further notice :D

Thank you everyone who did their best to help but apparently the problem was from Google Side and it's fixed as of now.

---

