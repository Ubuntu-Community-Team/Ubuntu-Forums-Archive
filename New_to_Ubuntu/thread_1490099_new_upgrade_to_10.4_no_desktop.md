---
title: "new upgrade to 10.4 no desktop"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by akropaul on 2010-05-21
Upgraded to ubuntu 10.4 from 9.4,install seemed to go fine,but when
system reboots the desktop is completely blank except for background theme .
Also system is dual boot to win xp and now that wont work either.Not sure what to do
as I am a newbie.If I burn a live cd and reinstall will that fix my prob or is there an easier way?
Thanks in advance if you can help me.

---

### Post by venicequeen7706 on 2010-05-21
so you don't have the panels or anything? i'm relatively new myself but i would first try to see if the system works from the command terminal. you can press 'alt f2' then type in gnome-terminal to get to a terminal then try some basic commands. try 'firefox&' see if it opens firefox and if that runs well. maybe try 'gnome-open ~/Documents' to see if the documents directory opens. if the system is working fine you could use the commands in this thread to reset the panels and see if that works, if not i would say try to reinstall.
[http://ubuntuforums.org/showthread.php?p=9271869](http://ubuntuforums.org/showthread.php?p=9271869)

---

### Post by slibuntu on 2010-05-21
If you are unable to open a terminal as indicated in the above post, try hitting CTRL+ALT+F2 and you should be brought to a login terminal. If you can log in from here, let us know and we'll hopfully be able to help from there.

If nothing happens with the above key combination, then there is something pretty seriously wrong with the system.

---

### Post by akropaul on 2010-05-21
CTRL ALT F2 gets me into terminal no problem
I tried FIREFOX& and got an error of No Display selected.
Followed by some other errors
Then nothing
What next?

---

### Post by wilee-nilee on 2010-05-21
> **akropaul said:**
> CTRL ALT F2 gets me into terminal no problem
I tried FIREFOX& and got an error of No Display selected.
Followed by some other errors
Then nothing
What next?
 If you can get to the terminal then run sudo apt-get update then sudo apt-get dist-upgrade.
You may have some missing packages, You may also need to run the install for the desktop you want to make sure all the packages are there. The desktop install command is sudo apt-get install "put the desktop of your choice here"
IE; sudo apt-get install ubuntu-desktop

---

### Post by akropaul on 2010-05-22
> **wilee-nilee said:**
> If you can get to the terminal then run sudo apt-get update then sudo apt-get dist-upgrade.
You may have some missing packages, You may also need to run the install for the desktop you want to make sure all the packages are there. The desktop install command is sudo apt-get install "put the desktop of your choice here"
IE; sudo apt-get install ubuntu-desktop


I did these steps,and still the same result.Should I just try reinstall,I dont know.
Also why cant I boot into windows xp?

---

### Post by venicequeen7706 on 2010-05-22
I would reinstall, but that's just one opinion and i'm far from an expert. as for xp when you start your computer do you get a list of options to boot into like ubuntu, ubuntu safe etc? if not its possible that something got set to automatically boot into ubuntu unless you tell it not to. i think there is usually a keystroke combination that allows you to pick which one to run, but i don't know it.

---

### Post by akropaul on 2010-05-23
I reinstalled old version and I'm back in business.I tried a live CD of 10.4 and it wont
work either on this puter,works in another I have though.I am thinking it is a hardware issue now,as puter is fairly old maybe video card or something.I dont know enough to 
diagnose myself.I would still like to update though.
        Thanks for the help guys!

---

