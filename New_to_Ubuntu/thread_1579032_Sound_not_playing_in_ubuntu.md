---
title: "Sound not playing in ubuntu"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by abrockster on 2010-09-21
hey .. i'm an absolute beginner ( well the forum says it ). i just downloaded and installed UBUNTU 10.4 version and ran the update manager. i've looked a round a bit and i absolutely love this OS . i found that the sound doesnt work. i've cheked the volume its unmuted and at the max volume i downloaded and installed the codecs and my os is fully updated. but still i find that there is no sound output on my headphones. i wud be greatful if someone cud help me out with this! i'm a really music dependent person and i'm looking forward to solving this problem.. :) appreciate ur help :)

---

### Post by lkjoel on 2010-09-21
> **abrockster said:**
> hey .. i'm an absolute beginner ( well the forum says it ). i just downloaded and installed UBUNTU 10.4 version and ran the update manager. i've looked a round a bit and i absolutely love this OS . i found that the sound doesnt work. i've cheked the volume its unmuted and at the max volume i downloaded and installed the codecs and my os is fully updated. but still i find that there is no sound output on my headphones. i wud be greatful if someone cud help me out with this! i'm a really music dependent person and i'm looking forward to solving this problem.. :) appreciate ur help :)
Follow Fix your sound! in my signature.

---

### Post by abrockster on 2010-09-21
thanks a lot .. that really worked like magic .. i got a few errors midway .. but i ignored them .. and luckily it worked in the end :):) thanks a lot .. :)

---

### Post by lkjoel on 2010-09-21
When you restart, you may not have sound.
To make it work, open up a Terminal (Applications->Accessories->Terminal) window.
Type in it:
```
cd
svn co https://osscpanel.svn.sourceforge.net/svnroot/osscpanel osscpanel
cd osscpanel/trunk
chmod 0555 CPanel.sh
ln -s ~/osscpanel/trunk/CPanel.sh ~/CPanel.sh

```
And every time you do not hear sound, type in:
```
cd
./CPanel.sh -r

```
There are a lot of more features with CPanel.sh.
Type in:
```
cd
./CPanel.sh -h
```
for a list of all the features.
To update CPanel, type in:
```
cd
cd osscpanel
svn up
```

Use the attached file if SourceForge.net is down.

---

### Post by frank cox on 2010-09-24
> **lkjoel said:**
> When you restart, you will not have sound.
To make it work, first download the attached file (It is in BETA state) in your home direcory, and open up a Terminal.
Type in it:
```
cd
chmod +x CPanel.sh

```And every time you do not have sound, type in:
```
cd
./CPanel.sh -r

```There are a lot of more features with CPanel.sh.
Type in:
```
cd
./CPanel.sh -h
```for a list of all the features.

When I get a minute I will try that, thanks again.

---

### Post by frank cox on 2010-10-26
Now I have everything, including the mixer working perfectly-thanks.

---

### Post by abrockster on 2010-11-17
hey sorry to bother u again ! but the sound stopped working again all on its own accord !1 after an update! i try launching the ossxmix command but it says waiting for sound system to load and never loads ! i tried following all ur steps again but to no avail ! hoping u can help me with the problem!

---

### Post by lkjoel on 2010-11-18
> **abrockster said:**
> hey sorry to bother u again ! but the sound stopped working again all on its own accord !1 after an update! i try launching the ossxmix command but it says waiting for sound system to load and never loads ! i tried following all ur steps again but to no avail ! hoping u can help me with the problem!
Have you tried
```
./CPanel.sh -r
```
If you did, and you still don't have sound, try:
```
./CPanel.sh -u
```
Though it is still in BETA.
Then restart, and try:
```
./CPanel.sh -r
```

---

### Post by abrockster on 2010-12-02
hey sorry for the late reply ... i tried it out but i got errors on themm i'll post the errors .. ! ```
 ./CPanel.sh -r
```this gives an error 
```
bash: ./CPanel.sh: No such file or directory
```the other code also gives the same error .. !! i'm really new to this .. so i'm hoping i'm not a source of irritation .. !!

---

### Post by mastablasta on 2010-12-02
similar issue - one of the updates downgraded alsa (yay for updates!!!).
 
you need to upgrade it again.
 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
edit: or do/repeat the fix your sound thingy again :-)

---

### Post by olyerickson on 2011-01-19
I ran **lkjoel**'s script to solve the "Dummy Output" problem on Ubuntu 10.10; worked perfectly. After a day of battling the problem, this is the only thing that worked! THANKS!!!! :)

---

### Post by lkjoel on 2011-01-21
> **abrockster said:**
> hey sorry for the late reply ... i tried it out but i got errors on themm i'll post the errors .. ! ```
 ./CPanel.sh -r
```this gives an error 
```
bash: ./CPanel.sh: No such file or directory
```the other code also gives the same error .. !! i'm really new to this .. so i'm hoping i'm not a source of irritation .. !!

Sorry for the late reply!
Type in a Terminal window:
```
cd
svn co https://osscpanel.svn.sourceforge.net/svnroot/osscpanel osscpanel
cd osscpanel/trunk
chmod 0555 CPanel.sh
ln -s ~/osscpanel/trunk/CPanel.sh ~/CPanel.sh
```
Check out Post-Fix your sound! in my signature.

---

