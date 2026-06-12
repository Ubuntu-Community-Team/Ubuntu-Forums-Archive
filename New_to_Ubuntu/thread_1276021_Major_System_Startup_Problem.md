---
title: "Major System Startup Problem"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by knarfman on 2009-09-26
I have Ubuntu running on dual boot on my Vista laptop.

For some reason, when I rebooted my computer to go into Ubuntu, I got a [major] error message on booting up: lib/init/rw/root dev contains file with errors, check forced. It went through testing things line by line and said in one part, "duplicate or bad block in use". Near the end of it all, it says root file system currently read-only. Maintenance shell will now be started. After performing maintenance, press Control D to terminate shell and restart. 

It says to give root password for maintenance but I have NO CLUE what it is. I also have zero idea how to fix this and now I'm screwed because I have a lot of stuff on my Ubuntu side I need. :(:(

If anyone knows what to do/how to proceed, I'd be very grateful. I tried using my password but that doesn't work. I also tried just entering and it didn't work either. 

I used the Wubi application to install Ubuntu - wondering if trying to reinstall Ubuntu would fix it or just screw things up and wipe out all my data.

Anyway, thanks for any help you can give me.

---

### Post by Diabolis on 2009-09-26
1.- set a root password
```
sudo passwd
```
*Note: Your user password is set as the default root password during ubuntu installation, its' strange that it didn't work.

2.- check the file system
```
fsck -y
```

Then press **<Ctrl>D** and the boot up process should resume and finish as usual. In some cases you can just ignore the maintenance shell by pressing <Ctrl>D.

---

### Post by scorp123 on 2009-09-26
> **Diabolis said:**
> 1.- set a root password
```
sudo passwd
``` You are in violation of the forum rules. Besides -- this is not even needed. OP could easily reboot into "Recovery mode" without needing to do what you suggest.

---

### Post by knarfman on 2009-09-26
GUYS - thank you _**VERY**_ much. I got it to work!! :P I was actually in a MASSIVE panic as I have work stuff I was about to transfer to my external HD when this happened.

As suggested, I tried sudo passwd command which asked me for a new UNIX pw. I however had to be at the *root@ubuntu:~#* prompt. I entered a pw however I got the following message: Authentication token manipulation error. Password unchanged.

Not sure what to do, I did the automatic file system check (fsck -y) and it went through a whole bunch of changes (perhaps checks rather?). I rebooted and now it is working.

Not sure at all what the hell happened or went on to get this corruption in the first place, however I am glad it is working.

Scorp123 - if I may ask, why is the previous poster in violation? I hope I didn't do/ask anything to get Diabolis in trouble. :confused:

---

### Post by Diabolis on 2009-09-26
Its discouraged, for security reasons, to use the system as root or to set a root password. Also, you could break the whole system with one very little command. Thats why during installation your user is added to the root group so you can perform administrative tasks with it, by using **sudo**, but since you said your own password didn't work before. I assumed that you messed with the OS before coming to the forums and somehow the pass was messed up. I've seen strange things like that in other user's posts.

In short avoid being root or enabling the root account. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scorp123 on 2009-09-26
> **Diabolis said:**
>  In short avoid being root or enabling the root account. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) Exactly. 


@knarfman:

"root" is God. At least on a Linux system. root's powers are unlimited in any way, he can do whatever he wants, anytime he wants. The "problem" here is if you don't really know what you do, e.g. if you are a beginner: A Unix-like OS such as Linux will always assume that you know what you are doing. You are the one with the 1 billion or so brain cells. The OS accepts that it is what it is: Just a stupid mindless tool. And stupid mindless tools do what they are told to do. Linux deep down does not question the decisions the human in front if it makes. So if you are "root" and if you just decided to delete the better portion of your harddrive ... then the system will do exactly that. No questions asked. As I said: You're the one with the 1 billion brain cells. You're the one who is supposed to know a thing or two. All the computer knows is that it just received a bunch of scary commands that it will execute now .... too bad if it was an "accident" on your behalf ...

The other thing is this: "root" is the one user account that exists on _EVERY_ Unix-like operating system. Just as every Windows system has an "administrator" account. So these are the first accounts hackers and crackers will go after. All that's left is finding the password ....

With "root" disabled that possibility is eliminated. Now a cracker would first need to find the one account name that can actually execute "sudo" .... and that's way harder.

So long story short: Don't enable "root". That account is way too powerful. One mistyped command, one stupid little thing ... and your installation is hosed. Please use "sudo". And only ever use "sudo" if you really really need it. Other than that: leave it be. :)

---

