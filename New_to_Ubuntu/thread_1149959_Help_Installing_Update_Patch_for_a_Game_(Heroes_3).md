---
title: "Help Installing Update Patch for a Game (Heroes 3)"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Auzzie666 on 2009-05-05
Hey everyone.

A friend of mine has lent me a copy of Heroes 3 configured for linux.

I have successfully installed the game complete with sound, etc. via terminal.

However, I am having problems installing the patch, I have tried:

auzzie@ubuntu:~$ sudo bash
[sudo] password for auzzie: 
root@ubuntu:~# 

From here, I navigated to the folder where the patch file is, and:

root@ubuntu:~/Desktop/HeroesOfMightAndMagic3# sh heroes3-1.3.1a-unified-x86.run
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 814399959 1999548749

After that, I tried:

root@ubuntu:~/Desktop/HeroesOfMightAndMagic3# bash heroes3-1.3.1a-unified-x86.run
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 814399959 1999548749

Same deal. Anyone have any ideas as to how I can successfully apply this patch?

Sorry if this seems dummied-down, I have no idea what expected of a post.... I'm new!

Thanks :D

---

### Post by Insanity01 on 2009-05-05
i'm not sure but it's worth a shot, think there is an error in the patch so try redownloading it, check sums thing if it's like the checksum on a network there did something go wrong in the file itself...but then again that's a guess from me, worth a try maybe

sorry if it's completely wrong, but yeah, you just never know :p

---

### Post by Auzzie666 on 2009-05-05
I'll see if there's another version of the patch available.

---

### Post by randomjhovall on 2010-01-13
Hey,
I was having the exact same problem as Auzzie. I tried several times to extract the patch, but had the same results. So I removed the patch, redownloaded it from the mirror referenced [here]("http://ubuntuforums.org/showthread.php?t=189360").

However, now I am having a new problem:
> ~$ sh heroes3-1.3.1a-unified-x86.run --keep
Creating directory heroes3-1.3.1a-unified-x86
mkdir: cannot create directory `heroes3-1.3.1a-unified-x86': File exists
heroes3-1.3.1a-unified-x86.run: 126: Cannot create target directory: not found
heroes3-1.3.1a-unified-x86.run: 126: you should perhaps try option -target OtherDirectory: not found

~$ bash heroes3-1.3.1a-unified-x86.run --keep
Creating directory heroes3-1.3.1a-unified-x86
mkdir: cannot create directory `heroes3-1.3.1a-unified-x86': File exists
heroes3-1.3.1a-unified-x86.run: line 123: Cannot create target directory: command not found
heroes3-1.3.1a-unified-x86.run: line 124: you should perhaps try option -target OtherDirectory: command not found

~$ ./heroes3-1.3.1a-unified-x86.run --keep
bash: ./heroes3-1.3.1a-unified-x86.run: Permission denied

~$ sudo ./heroes3-1.3.1a-unified-x86.run --keep
[sudo] password: 
sudo: ./heroes3-1.3.1a-unified-x86.run: command not found


Then, another try:
> ~$ bash heroes3-1.3.1a-unified-x86.run -target
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 814399959 1999548749


Back to square one..
I apologize if this is way too much info! Linux newb looking for a guru.

---

### Post by Virus666 on 2010-01-13
You may try PlayOnLinux to install and update the game. It's using and maneging Wine and it's a bit easier.

[http://www.playonlinux.com/](http://www.playonlinux.com/)

---

