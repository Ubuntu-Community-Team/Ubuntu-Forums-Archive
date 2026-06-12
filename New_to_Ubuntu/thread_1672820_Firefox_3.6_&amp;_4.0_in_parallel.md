---
title: "Firefox 3.6 &amp; 4.0 in parallel"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Chowchilla on 2011-01-21
Hello there!

I've ran into a bit of trouble trying to have pre-release version of Firefox 4 (Minefield 4.0 to be exact) run along with the existing stable version of Firefox 3.6 which was already in place.

I initially installed Minefield 4.0 fine, via the mozilla daily ppa. However when I came to updating via the update manager, the stable Firefox 3.6 was updated to the unstable Namoroka 3.6.

After reading this ([http://ubuntuforums.org/showthread.php?t=1393533](http://ubuntuforums.org/showthread.php?t=1393533)) I decided to try adding the ppa for mozillateam stable and updating again. This didn't solve anything, and probably wasn't a great idea to add a third along with the mozilla daily and ubuntu mozilla ppas. I've since removed the mozillateam stable but at am a loss as to how to go about solving this problem.

Perhaps uninstalling Minefield and removing the daily ppa. Then running an update would convert Namoroka back to Firefox (stable & branded)? Then find a way of installing Minefield properly separate of Firefox?

I get the feeling I'm making this out to be more complicated than it actually is. If someone could point me the right direction I'd really appreciate it!

Kind regards,

Chow

---

### Post by Verbeck on 2011-01-21
try uninstalling namaroka > remove ppa > install firefox > in synaptic, select firefox and from the menu, select lock version

after that, install firefox beta from the daily ppa again

edit: you could also get it without using a ppa from [http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)
just extract the archive and run *firefox* from withing the folder

---

### Post by ajgreeny on 2011-01-21
The only problem I saw running FF4 a while ago was that the profile for 3.6 was completely messed up, and I had to restore a backup of that to get 3.6 to run properly afterwards.  Your problem sounds completely different, but I wonder if it is also a result of the profile change that may have occurred when you ran FF4.

---

### Post by bodhi.zazen on 2011-01-21
> **ajgreeny said:**
> The only problem I saw running FF4 a while ago was that the profile for 3.6 was completely messed up, and I had to restore a backup of that to get 3.6 to run properly afterwards.  Your problem sounds completely different, but I wonder if it is also a result of the profile change that may have occurred when you ran FF4.

OUCH !!!

I have not seen that problem (thank god) on any of my trials of ff 4.

I will back up my profile before I try ff 4 next.

---

### Post by ubudog on 2011-01-21
> **ajgreeny said:**
> The only problem I saw running FF4 a while ago was that the profile for 3.6 was completely messed up, and I had to restore a backup of that to get 3.6 to run properly afterwards.  Your problem sounds completely different, but I wonder if it is also a result of the profile change that may have occurred when you ran FF4.

I had the same problem.  I lost all my bookmarks because I had to reset the .mozilla directory (by removing it).  Anyway, from now on I will always have a backup... lol.

---

### Post by Vaphell on 2011-01-21
on my box there is a separate firefox-4.0 folder in .mozilla, i guess ff4.0 copied the profile from 3.6 as i have all the bookmarks and stuff but the changes made to 3.6 since then are not there in 4.0.

---

### Post by ubudog on 2011-01-21
> **Vaphell said:**
> on my box there is a separate firefox-4.0 folder in .mozilla, i guess ff4.0 copied the profile from 3.6 as i have all the bookmarks and stuff but the changes made to 3.6 since then are not there in 4.0.

Hmm...

---

### Post by Verbeck on 2011-01-21
> **Vaphell said:**
> on my box there is a separate firefox-4.0 folder in .mozilla, i guess ff4.0 copied the profile from 3.6 as i have all the bookmarks and stuff but the changes made to 3.6 since then are not there in 4.0.
same for me with the daily ppa
but the one from the mozilla site used the same profile (and perhaps luckily, didn't mess it up)

---

### Post by Vaphell on 2011-01-21
oh i see

---

### Post by Spr0k3t on 2011-01-21
When I installed 4.0b via PPA, along with it came the daily builds of 3.6.x (Namoroka).  There should be a menu option listed for Namoroka along with Minefield (4.0b{x}).  It's still Firefox, just under the codename of the daily builds.

---

### Post by ubudog on 2011-01-21
> **Spr0k3t said:**
> When I installed 4.0b via PPA, along with it came the daily builds of 3.6.x (Namoroka).  There should be a menu option listed for Namoroka along with Minefield (4.0b{x}).  It's still Firefox, just under the codename of the daily builds.

Ah.

---

### Post by hansolo4949 on 2011-01-21
You should probably just start back from scratch. Open up a Terminal, and type:```
sudo apt-get remove firefox
``` That will remove firefox 3.6. Then, type ```
sudo apt-get remove firefox-4.0
``` That will remove firefox 4.

Now, all you have to do is reinstall firefox, and you should be good to go! (you might have to remove the PPA's, I have found Ubuntu Tweak to be an excellent way to easily remove them)

---

### Post by ubudog on 2011-01-21
> **hansolo4949 said:**
> You should probably just start back from scratch. Open up a Terminal, and type:```
sudo apt-get remove firefox
``` That will remove firefox 3.6. Then, type ```
sudo apt-get remove firefox-4.0
``` That will remove firefox 4.

Now, all you have to do is reinstall firefox, and you should be good to go! (you might have to remove the PPA's, I have found Ubuntu Tweak to be an excellent way to easily remove them)

Also be sure to do:

```
rm -rf .mozilla
```

(Assuming you are starting from COMPLETE scratch)

---

### Post by Chowchilla on 2011-01-21
Thanks for the responses. Seems like there is consesus that removing both and respective ppas and reinstalling is the best course of action.

As far as profiles goes I didn't have any problems. Two separate folders, firefox and firefox-4.0, existed by default for me.

> **hansolo4949 said:**
> Now, all you have to do is reinstall firefox, and you should be good to go! (you might have to remove the PPA's, I have found Ubuntu Tweak to be an excellent way to easily remove them)

What I'm wondering though is how to reinstall both again, but this time such that the updating doesn't conflict. Someone mentioned locking the version of the stable firefox, but I still want to be able to update this when (stable) updates are available.

What I don't understand is why the daily ppa affected the stable installation. Surely it is the "domain" of the ubuntu mozilla ppa and thus should not be affected by the existence of the daily ppa?

---

### Post by ajgreeny on 2011-01-21
As a follow on to my post number 3, I should add that my use of FF4 was so long ago that things may well have improved with regard to the profile.

I also just ran it from the downloaded tar.gz from mozilla and did not install it properly.  I don't know if that latter point makes any difference to my profile problem, but just throw it in for good measure.

---

### Post by hansolo4949 on 2011-01-21
I would think that if you want to install the latest version of firefox 3.6 without messing it up, you could do ```
sudo apt-get install firefox
``` That should update firefox **_3.6_**, whilst leaving 4 alone (or vice versa, just use ```
sudo apt-get install firefox-4.0
``` for Firefox 4). I know that this is a sub-optimal fix, it should work, and well.

Thank you ubudog for adding that in for me, I have only been using Ubuntu for about 1 1/2 months, so I haven't learned ALL of the Terminal codes, though I have been browsing throughout this forum, and learning from trial and error (I had to reinstall Ubuntu on this computer once, and several times on an old laptop....nasty experience, especially JUST after you have set everything up).

---

### Post by bodhi.zazen on 2011-01-21
> **ajgreeny said:**
> I also just ran it from the downloaded tar.gz from mozilla ... 

That is what I do as well, I find it is rather trivial to do this.

In general I do not like to test ff as usually it is an exercise in extension inactivation.

---

### Post by Verbeck on 2011-01-21
> **Chowchilla said:**
> 
What I don't understand is why the daily ppa affected the stable installation. 
apt-get would always install the latest version available from the software channel

for example, the daily ppa holds firefox 3.6.*14* and the official repos has firefox 3.6.*13*
so firefox would updated to the latest available release (stable or not)

---

### Post by nm_geo on 2011-01-21
Natty 11.04 has FF4 beta installed in it and it works pretty well. There are a few changes that give you more screen to work with but make it a little more difficult to get around in. To insure you do not lose your bookmarks FF has a neat little sync add-on and can be used to keep all your various FF installs up to date with the same bookmarks. It will also carries over passwords, cookies and history if you choose. I started using it Ubuntu 10.04, applied it in my Xubuntu and Natty as well. O yeah I also sync my work laptop that has XP running FF 3.. All have the same bookmarks and so on.. No problems yet.

---

### Post by Chowchilla on 2011-01-21
Okay, so I've removed both Firefox and Firefox-4.0 along with the ppa and .mozilla folder.

I've also now reinstalled Firefox (3.6) via the Ubuntuzilla source.

How should I now go about installing Firefox-4.0?

I was thinking I might now be able to simply install as before (via the daily ppa) and not have the trouble with updates affecting Firefox 3.6 because the package is now firefox-mozilla-build (from Ubuntuzilla) not simply firefox? Or would the daily ppa result in 3.6 being updated to the latest Namoroka pre-release version regardless of whether it's firefox or firefox-mozilla-build?

---

