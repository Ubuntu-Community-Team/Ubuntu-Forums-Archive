---
title: "screen went blank after boot"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by mahmater on 2009-09-08
hi friends. I've been using ubuntu for five yrs now,but today I was stunned when I booted into my 9.04 ubuntu and entered my username and psswd but all I get is a blank screen. I tried to boot in recovery mode but in vain. I didn't install anything recently except urban terror game (the first video game I played all in my life).would that have any relation ...?

---

### Post by Volt9000 on 2009-09-08
I'm afraid your screen is gone. Once they go black, they don't go back. :D

Seriously though, I don't think the game would have caused it. What happens if you try hitting Ctrl+Alt+F1 through Ctrl+Alt+F6? Do you get a command-line login prompt?

---

### Post by mahmater on 2009-09-08
u scared me friend!!!!!!!!!!!!!!
yeah I got a login prompt,but nothing happened after entering my username and pass ....a few lines talking about ubuntu version and directing me to ubuntu documentation website.

I 'd like just to remind u that I login prompt appears normally after booting but once I enter my username and pass the screen goes blank.

---

### Post by mahmater on 2009-09-08
I repeated ur instruction and I waited a little bit, then a sentence appeared saying : 
14 packages can be updated
reloading system log daemon...
I waited for about 1 hour now and nothing happened,but I'm optimistic.when there is life there is hope.


thanx for ur help.

---

### Post by mahmater on 2009-09-09
after about three hours,a command saying:

display all possibilities

when I hit "enter",a very very long list appeared after which the prompt shell was displayed again. I hit "exit" and everything went blank again

---

### Post by LewRockwell on 2009-09-09
use a LiveCD to rescue any valuable data then do a fresh install

.

---

### Post by mahmater on 2009-09-09
well,how can I use the live cd? am I going to use the terminal once I'm in live cd or what?
thanks again.

---

### Post by mapes12 on 2009-09-09
The only thing I can think of is that the urban terror game has somehow thrown out you video adapter settings.

If you follow LewRockwell's post the Live Ubu CD would enable you to boot into a GUI session from the CD. You could then save your important stuff in /home to an external device, then hit the install icon to carry out a fresh install. Copy back the important stuff once the fresh install is complete.

Do you by any chance have an NVIDIA video card and have you at some point installed the 185 driver for it? Because I did that yesterday I had the same blank screen issue you have described. Just a huntch.

---

### Post by mahmater on 2009-09-09
many thanks for the tip.I will boot from the live Cd and rescue my files first,great!
no,I don't have nividia.my laptop is core2duo inspiron 1545,but I don't know what's my graphic card type.

by the way, in windows,I used to right click on MY Computer and see my computer's properties(hard disk capacity,speed,ram,type ...).However,I couldn't find a way to get the same info in ubuntu.

---

### Post by Volt9000 on 2009-09-09
Wait, if you hit Ctrl+Alt+F2, then login, do you not get the bash login prompt?

---

### Post by mahmater on 2009-09-09
yesterday I used fsck in recovery mode and after the reboot,the login screen did not appear this time.only a black screen with the following:
checking filesystems....
dev/sda7/: superblock needs_recovery flag is clear,but journal has data.
           run journal anyway.

           unexpected inconsistency.fsck died with exit status4.

a log is being saved in var/log/fsck/checkfs if that location is writable.
please repair the file system manually.

root@username-laptop:~#

now may be the Live CD will be my savior.

---

