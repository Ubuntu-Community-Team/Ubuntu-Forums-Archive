---
title: "firefox not displaying web pages correctly"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ahelmick on 2009-01-19
After upgrading from Hardy to Intrepid I have noticed that Javascript and Java does not function correctly, most notably are photos or pictures that are part of a document object or string...

ie:  such as [www.plentyoffish.com](www.plentyoffish.com) or any site where photos are attached... the photos do not display.

This problem is NOT limited to any one site but it is a problem with Ubuntu Intrepid and Firefox... upon testing in other Operating Systems and browsers the problem does NOT occur.

This problem was not evident until I upgrade to Intrepid.

It appears from reviewing the source that the problem ONLY occurs when Firefox us parsing Javascript.

I tried to tie into some other threads about this but was unable... here is a link to one.

[http://ubuntuforums.org/showthread.php?t=644938](http://ubuntuforums.org/showthread.php?t=644938)

---

### Post by scragar on 2009-01-19
I would try a number of things, first I would temp rename the firefox settings, see if that fixes anything:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_back
```
If not then I would try reinstalling firefox, see if that solves anything:
```
sudo apt-get --purge autoremove firefox
sudo apt-get install firefox
```
Let me know how you get on.

---

### Post by paydaydaddy on 2009-01-19
Have you checked synaptic to make sure that you have sun java? It has to be reloaded after an upgrade.

---

### Post by ahelmick on 2009-01-19
the move (mv) seems to have worked!

The pages look SO much different, I didn't even realize how much content I was missing...

Yes, I tried re-installed Java and Yes I imported my profile from the previous Hardy install.

I will give it 24 hours and check back... seems to be working!

Thanks very much.

p.s.  I also tried clearing all cached and so forth before posting and that did NOT work... seems to be moving along now?  Now on to find a VRML plug in that will work... any ideas?

---

### Post by tahitiwibble on 2009-01-19
> **scragar said:**
> I would try a number of things, first I would temp rename the firefox settings, see if that fixes anything:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_back
```
If not then I would try reinstalling firefox, see if that solves anything:
```
sudo apt-get --purge autoremove firefox
sudo apt-get install firefox
```
Let me know how you get on.

Oh dear!!!!! I just did the mv code thinking it might help me and have now lost all my bookmarks, passwords etc etc. I'm in a cold sweat, please help.

---

### Post by scragar on 2009-01-19
> **tahitiwibble said:**
> Oh dear!!!!! I just did the mv code thinking it might help me and have now lost all my bookmarks, passwords etc etc. I'm in a cold sweat, please help.

Don't worry, it's just renamed the folder, I was assuming it was a plugin causing the problems, easiest way to get test it is to temp remove the firefox config file.

```

mv ~/.mozilla/firefox_back ~/.mozilla/firefox

```
will restore it. You might have to play about with your plugins till you find the one causing trouble.

---

### Post by ahelmick on 2009-01-19
Just reverse it tahitiawibble...

You know the mv statement, reverse...

mv ~/.mozilla/firefox_back ~/.mozilla/firefox

Yes, I lost all my goodies too, but my browser works and that is so much more important to me...

Sometimes you have to let go.

---

### Post by tahitiwibble on 2009-01-20
> **scragar said:**
> Don't worry, it's just renamed the folder, I was assuming it was a plugin causing the problems, easiest way to get test it is to temp remove the firefox config file.

```

mv ~/.mozilla/firefox_back ~/.mozilla/firefox

```
will restore it. You might have to play about with your plugins till you find the one causing trouble.

> **ahelmick said:**
> Just reverse it tahitiawibble...

You know the mv statement, reverse...

mv ~/.mozilla/firefox_back ~/.mozilla/firefox

Yes, I lost all my goodies too, but my browser works and that is so much more important to me...

Sometimes you have to let go.

lol oh boy! I just spent an hour in a state of total panic. Messed everything up and firefox wouldn't close, removed and reinstalled it, it said another instance was open and I couldn't start up the newly installed version, removed completely and reinstalled etc etc etc.

Anyway, a fresh copy of Firefox was like getting into a Ferrari after having driven a Beetle for the past 12 months.

ahelmick, you're right and I will let go of a lot but does anyone know where all my site passwords are stored so that I can get them back.

---

