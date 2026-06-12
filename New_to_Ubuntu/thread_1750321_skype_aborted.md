---
title: "skype aborted"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by antonio_ing on 2011-05-05
Dear All

I have Ubuntu 10.04. I am experiencing some strange problem with my skype that it was working until some days ago and now it is quitting continuously after the login. Sometimes, and this makes me crazy, it does the login but after a while it close again. I have checked on the terminal this morning and there was this error when I was launching skype:

bt_audio_service_open: connect() failed: Connection refused (111)
Aborted

then I have followed some forum and did this command on the terminal:

sudo apt-get purge bluez-alsa

the error is gone, but the problem remains. There is only a synthetic string "Aborted" when I run skype from the terminal.  Any idea? I tried to uninstall it and re-install it from both skype website and ubuntu repository.

---

### Post by antonio_ing on 2011-05-05
sorry for the silly question. I have found the answer by myself. I have removed skype including its folder in ~/.Skype and then reinstalled it from the website

thank you anyway

---

### Post by antonio_ing on 2011-05-05
false alarm. It worked for 20 minutes then it quitted again...

also the microphone (when it was working) was quite low, even if the Ubuntu sound recorder was fine. Ideas?

---

### Post by antonio_ing on 2011-05-07
The problem has been solved by formatting the OS and upgrading to ubuntu 11.04. Not a clever solution but it worked.

---

### Post by John Bennett on 2011-05-26
Skype will *not* run on a fresh, clean Ubuntu 11.04 installation.

I just spent the last hour formatting my hard drive and re-installing Ubuntu 11.04 specifically to get Skype to work.

This issue is not solved.

---

### Post by SunnySan on 2011-05-26
same thing happened to me after an update on ubuntu 10.4

tried to re-installed Skype but it didn't work. (show the login page and then dissappear when I tried to enter the password)
must be some dependencies??

anybody?

---

### Post by lopcaf on 2011-05-26
I have the same problem :confused: :

lopcaf@XXXXX:~$ skype
Aborted

I'm running 11.04 updated from 10.10. The desktop version. 

Good luck!

---

### Post by pescez on 2011-05-26
Same here, natty, either on kde and gnome DE... today it stopped working and dies suddenly after starting, with the message "aborted"...

---

### Post by veefwoar on 2011-05-26
10.04 LTS and gnome here too.

Same issue. Just did an update about an hour ago and I get the "Aborted" message in terminal when i try to start skype.

---

### Post by ake-buntu on 2011-05-26
Same here
10.04.2
Aborted as running. and never start again.

---

### Post by dipish on 2011-05-26
**Found the solution here, worked for me! (Ubuntu 10.04 LTS)**
> mv ~/.Skype/shared.xml ~/.Skype/shared~.xml
No data will be lost!
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html)

You will have to re-enter your password when skype starts.

---

### Post by brendanpiater on 2011-05-26
Same "Aborted" error message. "SOLVED" should be removed from subject?

---

### Post by brendanpiater on 2011-05-26
> **dipish said:**
> **Found the solution here, worked for me! (Ubuntu 10.04 LTS)**

No data will be lost!
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html)

You will have to re-enter your password when skype starts.

Worked for me, so ignore my last post.

Thanks @dipish

---

### Post by Fedz on 2011-05-26
Nah all fine here skype up & working 1 day 0 hrs & 52 mins & counting :)

---

### Post by mastablasta on 2011-05-26
bad news (don't you like linux with it's updates that break the programmes?). If downgrading skype fixes the problem then i will lock packages for it.
 
 
or maybe it's Microsoft that decided it's time to fix linux skype verison... :-D

---

### Post by Fedz on 2011-05-26
> **mastablasta said:**
> or maybe it's Microsoft that decided it's time to fix linux skype verison... :-D
HaHa! I was going to post the same comment but, deleted it not wishing to start a panic ;)

---

### Post by veefwoar on 2011-05-26
I removed the .Skype folder and it worked but I think this thread might also help:

[http://ubuntuforums.org/showthread.php?t=974212](http://ubuntuforums.org/showthread.php?t=974212)

---

### Post by dipish on 2011-05-26
[COLOR="DarkRed"]Guys you don't really need to remove the whole ~/.Skype folder, just **remove/rename the ~/.Skype/shared.xml** file[/COLOR]

P.S. Funny or sad but with taking into account recent events this problem does look like Microsoft's sabotage against Linux users :)

---

### Post by ceverett on 2011-05-26
Yesterday, skype was working for me in 10.10.  This morning it failed.  I made no changes to my computer.

---

### Post by kleinebre on 2011-05-26
What worked for me was

  mv ~/.Skype ~/.Skype_old

which basically flushes any profile settings and allows Skype to start over clean. As most of the stuff (buddy lists etc) is on the server you'll be up and running again in no time, without lengthy, cumbersome re-installs required.

---

### Post by Burillo on 2011-05-26
yesterday it worked fine, today (i think i had a few updates, but they were firefox-related) it worked for a while and then same error. i just removed the whole .Skype folder and all works (for now)...

UPDATE: my brother (who has a Mac) has also told me that his Skype is behaving strangely today, so i think this isn't Ubuntu-related, it looks like it's a problem on Skype's end.

---

### Post by Hansholz on 2011-05-26
Yep

[http://breakingnewsrightnow.com/skype-down-may-26-service-unavailable-product-reviews/](http://breakingnewsrightnow.com/skype-down-may-26-service-unavailable-product-reviews/)

If you've had the problem in the last 24 hrs you should probabyl wait until they get the service up and running again before looking at your own machine for problems to fix.

---

### Post by tim73 on 2011-05-26
Just remove only the ~/.Skype/shared.xml. Then it asks for licence agreement, click ok and it should work then normally.

---

### Post by SunnySan on 2011-05-26
need to remove or move ./Skype/shared.yml
It worked for me

then the shared.xml is created again next start

Thanks

---

### Post by Qiaozhi on 2011-05-26
> **dipish said:**
> **Found the solution here, worked for me! (Ubuntu 10.04 LTS)**

No data will be lost!
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2963273.html)

You will have to re-enter your password when skype starts.

I've no idea how you found this solution ... but please go to the top of the class. :)
Thank you so much. This problem was driving me mad.

---

### Post by hasan.iskandar on 2011-05-26
> **tim73 said:**
> Just remove only the ~/.Skype/shared.xml. Then it asks for licence agreement, click ok and it should work then normally.
**WORKED** for me!
Thanks tim73 :)

Edit:
  Unfortunately skype closed again after logged in :(
  Any suggestion?

---

### Post by dFlyer on 2011-05-26
I've had no problems with skype today or yesterday, on either of my Laptops. They are both running 11.04, and I download the program from the archives using synaptic.

---

### Post by demarshall on 2011-05-27
I didn't have problems with Skype until today and deleting the shared.xml file worked. 

Thanks! :-)

---

### Post by reidar5 on 2011-05-27
Hello

 Someone in the forum managed to make skype work again by removing a  file called "shared.xml" I'm not quite sure if I've found it on my  computer,and don't know how to delete the one I've found.

---

### Post by vallvi on 2011-05-27
Solved! This worked for me in a breeze. Just copy the following into the terminal, sign in again & done![FONT=monospace]
[/FONT]mv ~/.Skype/shared.xml ~/.Skype/shared~.xml

---

