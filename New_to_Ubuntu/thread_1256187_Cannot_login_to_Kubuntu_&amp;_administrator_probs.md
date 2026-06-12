---
title: "Cannot login to Kubuntu &amp; administrator probs"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hungry bunny on 2009-09-02
Hello

I am using Kubuntu 7.10 with K Desktop Environment 3.5.8

My problem is that I can't login to Kubuntu. When I enter my username and password the screen goes black for about 1-2 seconds and then returns to the original login screen.

I was able to login in recovery mode and create a new user. I am able to login using this user but I can't access synaptic or adept or administrator mode. I noticed that I couldn't use administrator mode in the original user and was the reason why I restarted just before the problem occurred.

I have tried: 
-checking to see if my disk is full - it isn't (df -h)
-checking to see if my x has any errors under my newly created user - because I can't seem to get it right for my original user.
 (tail -20 ~/.xsession-errors)

This gives an error reading like this:

X Error: BadWindow (invalid window parameter) 3
 Major opcode: 20
 Minor opcode: 0
 Resource id: 0x2e0000e
kdecore (KProcess): WARNING: _attachPty() 11
X Error: BadAccess (attempt to access private resource denied) 10
 Major opcode: 2
 Minor opcode: 0
 Resource id: 0x2e0000e
khelpcenter: WARNING Main template file name is empty
X Error: BadAccess (attempt to access private resource denied) 10
 Major opcode: 2
 Minor opcode: 0
 Resource id: 0x2e0000e
X Error: BadAccess (attempt to access private resource denied) 10
 Major opcode: 2
 Minor opcode: 0
 Resource id: 0x2e0000e

I am a total newby to linux so I'm not sure if this information is of any use. 

-I did not install any new updates or packages and I don't think I changed anything. (therefore I don't think it is a language package problem as described in some other threads)

I am using tsch shell on my original user (the one that I can't login to and ordinary bash in my new user.

Please come to my rescue!
Thank you

---

### Post by LewRockwell on 2009-09-02
quickest fix:

scrounge up another hard drive and do a fresh install of the latest version of whatever *nix distro you desire

once you're up and running then you can recover anything of value from your other(original) hard drive via the normal and/or forensic methods described elsewhere(repeatedly) on this and other websites and forums

.

---

### Post by LewRockwell on 2009-09-02
regarding the above mentioned quick fix we assume the following:

one, you will be upgrading your operating system anyway since 7.10 is legacy

two, you cannot know(yet) whether your installation has been compromised(thus contributing to your present trouble-call)

as always, your mileage may vary

.

---

### Post by hungry bunny on 2009-09-02
Thanks for that, but the problem is that I need to be using 7.10 since I'm running a specific research program that does not work with later releases. I'm also dual booting windows on the computer and the disk that contains the Kubuntu install is already a new disk that has been partitioned.

Are there any other suggestions that would help? I thought about doing a gnome install (sudo apt get install ubuntu-desktop) since I thought the problem lay with the K desktop environment.

---

### Post by jerrrys on 2009-09-02
this may/may not help

[http://ubuntuforums.org/showthread.php?t=1146638&highlight=password](http://ubuntuforums.org/showthread.php?t=1146638&highlight=password)

---

