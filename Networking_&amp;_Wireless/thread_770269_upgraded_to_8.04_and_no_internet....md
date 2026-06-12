---
title: "upgraded to 8.04 and no internet..."
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Nnako2 on 2008-04-27
Hi... You helped me before when I couldn't connect to the internet with 7.10 and wireless.

Here was the solution [http://ubuntuforums.org/showthread.php?p=4348362#post4348362](http://ubuntuforums.org/showthread.php?p=4348362#post4348362)

But now last night I uploaded to 8.04 and now I've restarted the computer and... oh-oh... Internet doesn't work again.. no connection... I can't switch on the little light on the keyboard of my laptop to receive wireless connections...
I tried to enable again the bcm43xx-fwcutter_006-4_i386.deb but an error appears and I must restart the computer...

I need your help, thanks!

---

### Post by Nnako2 on 2008-04-27
Please, I NEED help!!

I tried this: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

But when...



paula@paula-laptop:~$ cd ndiswrapper-1.52
paula@paula-laptop:~/ndiswrapper-1.52$ ndiswrapper -i bcmwl5.inf
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 186.
paula@paula-laptop:~/ndiswrapper-1.52$ -i bcmwl5.inf
bash: -i: command not found
paula@paula-laptop:~/ndiswrapper-1.52$ ndiswrapper -i bcmwl5.ing
install argument must be .inf file
paula@paula-laptop:~/ndiswrapper-1.52$ ndiswrapper -i /ndiswrapper-1.52/bcmwl5.inf
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 186.
paula@paula-laptop:~/ndiswrapper-1.52$ ndiswrapper -i /home/ndiswrapper-1.52/bcmwl5.inf
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 186.
paula@paula-laptop:~/ndiswrapper-1.52$ ndiswrapper -i /media/sda1/SwSetup/SP34152A/bcmwl5.inf
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 186.


What must I do???:confused:

---

### Post by gschoppe on 2008-04-27
add sudo as a preface for said commands, and theres a typo where you entered .ing instead of .inf


maybe?

---

