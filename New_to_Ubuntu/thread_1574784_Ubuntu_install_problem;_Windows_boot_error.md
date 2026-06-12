---
title: "Ubuntu install problem; Windows boot error"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by jpaddock on 2010-09-14
Total noob here. 

I seem to have Ubuntu 10.04 installed on my computer (using it now). However, it will not boot after a restart. 

Couple of tidbits: 
1. Last night I successfully installed and purposefully restarted a few times, each time reaching a small menu where I could select how I wanted to boot. Worked fine for a few restarts. 
2. One of the reasons I installed Ubuntu was because I was tired of Windows. My last problem occurred when I installed an Avast update and it corrupted my boot files. Now I get an error message on boot: 0xc000014C
3. I booted from disk and did an equal partition (I think).  
4. Now, anytime I restart, I get to the Windows boot error. 

The only way I can get back to Ubuntu is if I put in the CD, get to the install step, and then click off of install. However, then all of my downloads and updates are gone. 

This is what I would like to be able to do: 
1. Boot directly to Ubuntu when I turn on the power. 
2. Save all a lot of my files from Windows, as I have a lots of files that I would like to keep. 
3. Eventually get rid of the Windows operating system, as it's busted anyway.

I know how to retrieve the Windows files, but I'd like for any answer to allow me to retain access to those files. In other words, I don't want to erase the hard drive.

Help?!

---

### Post by Sef on 2010-09-14
Click [here]("https://help.ubuntu.com/community/Grub2") and go to Command Line and Rescue mode.

---

### Post by ezhik on 2010-09-14
jpaddock,

So you have problems accessing Ubuntu? Nevertheless, here is nice documentation on dual-booting Windows and Ubuntu: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).
If you wish to access windows partition from Ubuntu, you will have to mount it first. Usually it is done during installation.

---

