---
title: "Moody Ubuntu?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by gatucar on 2008-12-31
Hey Guys,
I am going to need a little help here. I am new to Ubuntu and probably that is the main part of my problems. Here are some of my issues:
-One out of 5 times my computer does not boot. It starts booting but the precess gets interrupted and a black screen is the only thing I get. After a forced shot down I can the computer boots like nothing happened before.
-Sometimes after the computer hibernates it does not "wake up", again a black screen and a forced computer turn off is needed.
-The shell behaves moody. Sometimes it does not allow me to become root with sudo su. It asks me for the current user password and then it tells me that the user it is not listed in the sudoers file. However, sometimes it does ask me for my root password and let me become root (after reboot). 
-Similarly a week ago trying to learn the mv command. Nothing, permission denied and a lot of crap, after checking the line I wrote several times I got frustrated, rebooted the computer, wrote the very same line and like magic everything went OK.

Linux is supposed to provide a very stable OS but not in my case. I am using Ubuntu 8.10. in a laptop and I use dual boot to keep my version of vista, which has been so far a good idea!  
Am I doing something wrong, should I do a fresh install, should I change the Ubuntu 8.10 to 8.04?:confused:

I would appreciate ideas and comments. 

Gatucar

---

### Post by mikewhatever on 2008-12-31
Not quite sure what's wrong, but posting you computer specs and checking the iso and installation cd integrity would be steps in the right direction.

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

Trying out Hardy or another distro wouldn't hurt either. This may show if the problem is Intrepid/Ubuntu related or not.

---

### Post by jimmy the saint on 2008-12-31
As far as the su issue, you shouldn't need to do that at all.  If you simply preface the command you need to run with "sudo"  as in "sudo <make me a sandwich>" you will be able to perform tasks with root powers.

The hibernate issue could be a lot of things.  Is it hibernating (saving the state to the HD) or suspending (saving state to ram)?  Is it a desktop or a laptop?

the mv command issue could also be a lot of things, most likely is a typo or an ownership issue.  If you are used to operating as root (which is a very bad idea) you may have been trying to transfer a file as usual, but happened to not have root privilages at the time.

Like any OS, linux needs to be learned.  This is especially true if you are jumping into it with a lot of habits and ideas from long use of another OS.  Linux is NOT Windows or OSX.  Ubuntu is designed to be used a particular way, which has been pretty well thought through.  We also have a great community here at the forums filled with people to help you get going!

Good Luck

---

### Post by gatucar on 2008-12-31
Mikewhatever,
THanks for you reply,
I will check for the cd integrity. I will search how to do it and I will post the results later.
My computer is a laptop HP G50. 3 Gb of RAM but only 20 Gb of hard drive assigned to Ubuntu (I read that that should br OK).
Thanks again.

---

### Post by gatucar on 2008-12-31
Hello there,
I have an extra problem to report. My computer stopped responding after I tried to switch users. Another forced turn off!
Please help!!!!!

---

