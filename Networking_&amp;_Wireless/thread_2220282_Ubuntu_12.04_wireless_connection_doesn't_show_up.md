---
title: "Ubuntu 12.04 wireless connection doesn't show up"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by anthony32 on 2014-04-27
I'll explain in great details what's happening. Very frustrating.

Yesterday my internet worked fine ( I turned my computer off at around 12 pm ).

I wake up this morning all like : " another beautiful ubuntu morning " but ubuntu said : "no way lil happy guy ".

Ok so in the top right corner there's this icon for wireless ( I guess ). Habitually it's filled compared to the strength of your internet connection. Mine is empty. When I click it  there's a matk on the left that says: " network activated". But, no network connections show up. Habitually my network ( and all other network close to mine ) show up, there's none of them ( nothing ).

So I decided to restart my computer. Still nothing. ( repeated this process 4 times ).

I don't know if my switch is on or off ( but I can guess it's on since "activated network" is not grayed out and it has a checkmark beside it.

Also " information about connexions" is grayed out.

Thanks if can answer ! I've been searching for 2 hours to find a fix but nothing.

Oh and please don't link me to another thread or another website. I'm a beginner and don't quite understand terminal stuff.

Obviously I can't connect to the internet with my laptop.

---

### Post by anthony32 on 2014-04-27
Anyone please ?

---

### Post by Iowan on 2014-04-27
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
>     Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

---

### Post by anthony32 on 2014-04-27
Alright sorry it's just that I can't work with my cellphone .. 
Also when I run the command iwconfig it says " no wireless extensions."

---

### Post by wildmanne39 on 2014-04-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by anthony32 on 2014-04-27
Thanks I will run the script when I plug my laptop in. I'll back up a few things first because I'll upgrade to 14.04 if this can solve the problem :p

---

### Post by anthony32 on 2014-05-05
[ATTACH]252902[/ATTACH]

here is the runned script ! I hope you'll find something to fix this (I now have a wireless helper (Like some kind of USB where it help my computer to conect))

---

### Post by fernandojosecabral on 2014-05-06
Wild Man

I have a similar problem (wireless not working with ubuntu 14.04) so I ran your script and attached its output goes.
A curiosity: I installed the ubuntu package using the wireless connection. So, hardware is ok, driver is ok and I know ubuntu can
work with it (because I installed several packages before rebooting). But, once I rebooted the machine, wireless did not work
any more. Wired is working flawlessly.

Any help will be much appreciated.

Thank you

- fernando

---

### Post by anthony32 on 2014-05-08
Let's get this thread up !!!

---

### Post by anthony32 on 2014-05-09
And again ! up up up

---

### Post by anthony32 on 2014-05-11
AGAIN !!!! no one can solve this problem, I tough people were of better support !

---

### Post by Hadaka on 2014-05-11
being demanding is not a good way to get help.
ok..I read your wireless script..but you used a usb dongle
to connect and send the data..so its invalid. you also mentioned
you were going to load 14.04...did you do that? mean time..
with your computer powered up....does it connect ethernet?
lastly...please post...WITH ANY AND ALL usb dongles unplugged..
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```
thanks

---

