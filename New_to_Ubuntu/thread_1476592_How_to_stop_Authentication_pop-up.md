---
title: "How to stop Authentication pop-up?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by quuxbazer on 2010-05-08
Hi, I just installed ubuntu for the first time today. I'm finding it absolutely amazing. I've been a windows user all my life, and this is just stunningly different and awesome.

Only problem I'm having so far is I don't know how to stop the Authentication box from popping up every time I'm installing something. I tried making my profile an admin, but that didn't work. I know that you can go to the Terminal and do sudo su, and then use apt-get to get apps, but how I do just input my password one time and won't have to do it again till next boot up? Thanks!

---

### Post by lavinog on 2010-05-08
> **quuxbazer said:**
> Hi, I just installed ubuntu for the first time today. I'm finding it absolutely amazing. I've been a windows user all my life, and this is just stunningly different and awesome.

Only problem I'm having so far is I don't know how to stop the Authentication box from popping up every time I'm installing something. I tried making my profile an admin, but that didn't work. I know that you can go to the Terminal and do sudo su, and then use apt-get to get apps, but how I do just input my password one time and won't have to do it again till next boot up? Thanks!

It shouldn't pop up every time you install something.
It should only ask you the first time.  If you keep the software center open, it shouldn't ask you again.

If you are new to ubuntu, you should stay clear from operating as root all of the time.
Also showing users on how to run as root is not allowed on the forums...If you feel that you must have this information, you will need to ask google.  Be advised once you do this, and something breaks, you will likely not get much help from the forums, and the only advice would be to perform a reinstall.

---

### Post by cariboo on 2010-05-08
You don't want to stop the authentication box from popping up, it is part of the security system, that protects you from hackers and crackers. As a normal user, you only have rights to install programs in your home directory, and nowhere else. In order to install a package so that it is available system wide, you need to enter your password. For more info, have a look [here]("https://help.ubuntu.com/community/RootSudo").

btw **lavinog**, it is OK to tell someone how to enable the root account, as long as you fully explain the dangers of doing so. the restriction is instructing someone how to log into the desktop as root.

---

### Post by sir_nasty on 2010-05-08
I totally understand what you mean!  When I first tried a Mac I was ticked, it asked me a few times here and there to authenticate this and do that.... I was like WTF???? Then I installed Ubuntu and it was worse, I was like WTF?!? WTF???? Then I clicked a facebook link on my Windows box it auto-installed something and I had a virus.... 

That story is a small exaggeration but honestly one of the biggest reasons why you don't need to worry about viruses (as much) on an Ubuntu machine is because it requires you to allow it. Just press on friend, it will learn and so will you.

---

### Post by lavinog on 2010-05-08
> **cariboo907 said:**
> 
btw **lavinog**, it is OK to tell someone how to enable the root account, as long as you fully explain the dangers of doing so. the restriction is instructing someone how to log into the desktop as root.

Right, but the catch is fully explaining the dangers since some applications tend to be less predictable than others.

I was going to add this link: [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by doas777 on 2010-05-08
Welcome,

this is a pretty common first question.  
ubuntu, like windows vista and win7, allows you to run as a limited user, with the capability to run things as admin when you want to. since you only have admin powers when you explicitly request them, it is hard for malware to infect you, or attackers to break in, but it is easy for you to administer your system when you need to. 

here is the official word on the sudo system. 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

check it out, and if you still want to disable the popups, it will tell you how.

personally i find the sudo system rather elegant. for me, it just feels easier to use than the windows approaches.
post back if you have any questions.

good luck, and happy ubuntuing.

---

