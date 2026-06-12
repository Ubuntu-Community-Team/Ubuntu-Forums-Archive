---
title: "Installing Ubuntu 8.10 from Live CD"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mgm2010 on 2008-12-08
I was installing 8.10 from live CD and after removing the CD the system restarted. Upto this point everything appeared alright. After restart, the scroll bar did not indicate the portion of the ubuntu installed but scrolled to and fro a few times and the screen turned blank with  orange and yellow and some lines all over the screen. After waiting for nearly 20 minutes when the system did not restart of its own I restarted the system. 

2. I found ubuntu on the startup screen and I entered it. A DOS screen opened and on the prompt it was suggested that I enter 'help' to get a list of built in commands. 

3. On doing so, the commands opened which I did not understand since I am a total beginner. 

4. I am interested to know:

  (a) Why did not the desktop open ??

  (b) What am I to do with the commands ??

  (c) Have I gone wrong somewhere ?? Is it possible that since I entered 5 Gb (instead of 6 as in the default )in the second installation window that the system did not install fully ??

5. From the windows I could find a 5.8 Gb ubuntu folder in the selected drive.

---

### Post by Bölvaður on 2008-12-08
What you are describing is a broken X. [http://en.wikipedia.org/wiki/X.Org_Server]("http://en.wikipedia.org/wiki/X.Org_Server")
It is the program that makes you see stuff on your screen in gui mode (not terminal)

This is not called DOS(disk operating systems) as that is a totally different operating system. Please refer it to as CLI (command line interface).

This is probably not your fault, but your hardware's.
If we are optimistic, this problem can be solved by reinstalling it or installing older version of Ubuntu.
If not you might need to install some drivers or set VESA as the default graphic driver.


Please tell us about your hardware. Is it a laptop (probably is... almost only laptop users need help :)), what graphical card do you have?

---

### Post by Bölvaður on 2008-12-08
> **mgm2010 said:**
> 
5. From the windows I could find a 5.8 Gb ubuntu folder in the selected drive.

Oh I didn't realize what that means... Did you really use live cd?
Windows is not equipped to do anything else than detect Windows stuff, so that it shouldn't be able to see Ubuntu at all.

May you have used the Wubi installer? [http://wubi-installer.org/screenshots.php]("http://wubi-installer.org/screenshots.php")
Or did you use the live cd?[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by mgm2010 on 2008-12-08
From the links given it appears to be wubi installer although the CD I reveived from linux office had the hand written inscription on it that it is Live CD ubuntu 8.10.

2. Where do we go from here??

---

### Post by Bölvaður on 2008-12-08
I have no experience with Wubi so I can not know if that is the reason for your misfortune.

But I can help you to find what is wrong.

When yo start up your computer you are able to push a key like F2, F6,F8, F10, F11 or even the del button to get into BIOS. There you are supposed to change the boot order so the cd or dvd player are set as first in the boot order. Then save and quit BIOS.
> 
Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you which key to use.
This was from the link showing how to install from live cd.


After you change the boot order you are able to restart your computer and boot from a live cd. What that means is that you can test what hardware works and what doesnt.

Does it show you commandline from there?


btw are you installing on a laptop?
and what graphic card are you using?

---

