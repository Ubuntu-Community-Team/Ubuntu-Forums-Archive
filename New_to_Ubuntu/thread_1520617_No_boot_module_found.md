---
title: "No boot module found"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by ECET on 2010-06-29
hello all.....a friend at school tonite just installed ubuntu 10.04...64bit.....on a dell inspiron.
He got on ubuntu about 3 or 4 times made some changes like where to turn off os....nothing serious.....but when he re-tried to log in to ubuntu he gets the message: NO BOOT MODULE FOUND.....he can't get into ubuntu or his windows 7 that he has on there. I did forget to mention that he set this up as a dual boot system. OK.....any ideas???

---

### Post by friv_livs on 2010-06-29
Google "koala grub restore" and look for the method that uses LiveCD.

---

### Post by oldfred on 2010-06-30
This should tell what is mis configured: Run from liveCd.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

You can reinstall a windows style boot loader from the liveCD or use a windows repair disk if you have to get back to windows immediately.

---

### Post by ECET on 2010-06-30
the problem with these two help advice's is that NO OS comes up to allow him to do anything.....its a black screen that says No Boot Module Found.... so, he is going to do a reinstall sometime today....

---

### Post by sydbat on 2010-06-30
> **ECET said:**
> the problem with these two help advice's is that NO OS comes up to allow him to do anything.....its a black screen that says No Boot Module Found.... so, he is going to do a reinstall sometime today....How did he set up his "dual boot"? WUBI? Or a real partition scheme? If it was WUBI, then there is the problem.

---

### Post by ECET on 2010-06-30
he did like i did.....he ran the live cd.....was experimenting with the differences compared to windows...then did the install while in the ubuntu environment. He did the option side by side install, which i have......restarted ubuntu about 3 or 4 times and on his last attempt, he gets this black screen which states no boot module found: press any key.....and when he press's any key it just repeats the message......bummer....I have been bragging about ubuntu at school for a while now and he tries it and this happens......bums me out.......:confused:

---

### Post by sydbat on 2010-06-30
I'd follow oldfred's advice then.

---

### Post by varunendra on 2010-06-30
> **ECET said:**
> the problem with these two help advice's is that NO OS comes up to allow him to do anything...

....that's why oldfred suggested you to boot off a LiveCD. You can run the script in a Live Session with no difference (script running instructions are given on the page he gave you link of).
If you have any problem with CD, you can try booting off a Ubuntu Live USB stick.

> **ECET said:**
> I have been bragging about ubuntu at school for a  while now and he tries it and this happens......bums me out.......:confused:

It's no reason to get embarrassed. No OS can protect you from damage caused by mishandling. :)

---

### Post by ECET on 2010-06-30
ok....now i understand what you guys were saying.....I'll try and txt him to let him know to try....problem is i wont see this guy till next tuesday at school so he may have already reinstalled his win 7 and ubuntu before i get ahold of him....but hey....thanks for the input! I have been enjoying my ubuntu!!!!!:guitar:

---

### Post by varunendra on 2010-06-30
You're welcome!

By the way, it's always a good idea to take a [backup image]("http://www.dedoimedo.com/computers/free_imaging_software.html") of your installation partitions when you think the installation is working fine. It's an assurance that you can get back to that stage anytime in case something goes wrong.

---

