---
title: "I had a network...."
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by douggiephresh on 2008-08-23
When my desktop and laptop both had windows, they were networked together so I could access my desktops files off of my laptop. Now that both are on ubuntu 8.04, how do I set that up again? My wireless laptop is working on the internet, and my desktop is hardwired through the router.

---

### Post by Iowan on 2008-08-23
For Ubuntu>Ubuntu, you have several options - some listed [here]("http://ubuntuforums.org/showthread.php?t=889279").  Most require some additional setup.
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is another How-To I just located.

---

### Post by douggiephresh on 2008-08-24
Can some one take this ([https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)) and dumb it down for me, making it exact keystroke by mouseclick directions? Im guessing this is what I need, because both of my comps are running ubuntu 8.04, desktop is 32bit, laptop is 64 bit

---

### Post by douggiephresh on 2008-08-24
bump

---

### Post by douggiephresh on 2008-09-01
bump

---

### Post by mellowd on 2008-09-01
> **douggiephresh said:**
> Can some one take this ([https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)) and dumb it down for me, making it exact keystroke by mouseclick directions? Im guessing this is what I need, because both of my comps are running ubuntu 8.04, desktop is 32bit, laptop is 64 bit

This link is already dumbed down. What part of it do you not understand?

---

### Post by douggiephresh on 2008-09-01
for one, which machine do i do this on? the desktop with the printer and external drive, or the laptop?

---

### Post by douggiephresh on 2008-09-01
and what does this mean?

Usage

Now, assuming that you have an ssh server running on a remote machine, simply run the sshfs command to mount the remote directory. In this example, the remote directory is /projects on remote host far. The local mount point is ~/projects.

---

### Post by douggiephresh on 2008-09-02
any help??

---

### Post by Iowan on 2008-09-02
Sounds like SSH-server is installed on the  system with the shares, SSHFS is installed on the client. Having never actually installed SSHFS, I'm probably not the best advice, but,,,
I'll try installing it - I'll let you know what I find out.

Update: Been there - done that - it works!  My server already has SSH-server installed.  
**sudo apt-get install sshfs** loaded the required packages onto this (client) workstation. 
**sudo adduser $USER fuse** added my current logged-on username to the fuser group.
I logged out of the terminal, then back in - but had problems until I did **su myusername**. 
After that, I built a mountpoint on this machine **mkdir ~/sshfs** (not very original). 
**sshfs myusername@myserver:/home/myusername ~/sshfs**
**cd ~/sshfs**, then **ls** shows the same files as when I **ssh** into **myserver** and **ls ~**

**fusermount -u ~/sshfs** unmounts  - **cd ~/sshfs**, then **ls** shows the mountpoint "sshfs directory" is empty.

---

### Post by douggiephresh on 2008-09-07
`Is there a step by step instructional of what i have to do? and one that I can understand? (click the red looking thing and hit space 3 times then enter the number 1) For example, Iowan, I dont know what the hell you just said. I am new to this.

---

### Post by Iowan on 2008-09-08
OK... On the top bar, click on the red ball with blue "comma" (that's Firefox Web Browser).  It should open a page that begins "Welcome to Ubuntu..." and a three digit number. What is that number (Ubuntu version)?

---

