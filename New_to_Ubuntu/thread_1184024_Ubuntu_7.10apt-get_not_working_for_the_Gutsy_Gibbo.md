---
title: "Ubuntu 7.10
apt-get not working for the Gutsy Gibbon"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by GoCool on 2009-06-10
Hi Friends,
I have a very good stable machine with everything I need, but its 7.10.
Now all of a sudden I want to install amarok, but the question is how will I go about? I tried all the below and none worked.

1. 
> atp-get install amarok

did not work, it threw all sorts of error mostly 404 not found.

Even the following did not work
> sudo aptitude -t experimental install amarok
> sudo apt-get install amarok --fix-missing


2. I tried to get the source and compile, but wanted many components from kde 4 which I dont want to install, so is out of question

3. The only option I feel is to connect to the new repository for one time and just have amarok downloaded...BUT DON'T KNOW HOW.

4. I tried to go to the amarok site and chose the debian file, but that did not work either.

4. If there is any other option let me know.

Please any help on this would be highly appreciated.

:(

---

### Post by SunnyRabbiera on 2009-06-10
Support for Ubuntu Gutsy has halted, so you might be better getting a newer version like Hardy.

---

### Post by GoCool on 2009-06-10
But this machine is stable for all my other purposes, like my lightscribe works great...(it took really long time for me to figure out and configure it)...and I fear I have to redo it all over.

For now all I need is amarok...isnt there a way....there should be some way!!!

---

### Post by HotShotDJ on 2009-06-10
> **GoCool said:**
> For now all I need is amarok...isnt there a way....there should be some way!!!Ubuntu 7.10 reached its "end-of-life" on [April 18, 2009]("http://www.ubuntu.com/news/ubuntu-7.10-eol").  Please consider upgrading to 8.04 LTS.  If you stick with the "LTS" versions, you'll get an OS with a full 2 years of support before you have to worry about upgrading to the next "LTS" version.  In any case, once an old version of Ubuntu reaches its end-of-life, it really is necessary to upgrade, since there will no longer be any security updates and you won't be able to install any new applications using the repositories.  You are, quite literally, on your own.

Regarding LightScribe... setting it up is trivial now-a-days. See [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe).  I prefer the 4L labeler software from LaCie, but it is a little more difficult.  You need to get the RPM file and then use "alien" to convert it to a "deb" file.  But even then, it is pretty easy to do.

---

### Post by mortenkjeldgaard on 2009-06-10
Like others have said, the 7.10 distribution has ended, and thus the archives have gone offline. This is the reason for the "404" errors you are getting. The best thing you can do is upgrade to hardy. In your /etc/apt/sources.list file, replace "gutsy" with "hardy", then do "apt-get update" and "apt-get dist-upgrade".

Good luck!

---

### Post by unutbu on 2009-06-10
If security updates are not an issue, then it is possible to still access the gutsy repository:

[http://ubuntuforums.org/showpost.php?p=7167277&postcount=2](http://ubuntuforums.org/showpost.php?p=7167277&postcount=2)

---

