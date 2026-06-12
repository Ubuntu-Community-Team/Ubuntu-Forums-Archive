---
title: "Help installing a bitnami .bin file 9.04"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by kevinsteger on 2009-10-07
I did a fresh install of 9.04 desktop which went fine.  I am now trying to install a stack from bitnami.org and I can't seem to execute the .bin file installer.

It downloads to desktop, I'm making darn sure that it's checked as "executable" and chmod 755, etc.

When I "sudo filename.bin" I get "no such file or directory.

Also.. an alternate method that was suggested on the bitnami forums was to rename the file removing the .bin extension, mark it as executable, and double click it.  This does nothing.  I have even watched via System Monitor and nothing happens when the file is double clicked or right click "open".

I have also tried a few different installer files from bitname and all have the same result.  Nothing.

Help?

Thanks.

---

### Post by alphaniner on 2009-10-07
You need to tell the shell where to look, otherwise it looks in the directories in your PATH variable.   Use ./ before the executable if you are in the directory where it is located, or use the full path, ie
```

sudo ./filename.bin
```
(**./** means 'here')

or

```
sudo /home/kevinsteger/Desktop/filename.bin
```

I don't know about executing through GUI, though, it should ask you if you want to execute I think...

---

### Post by wmcbrine on 2009-10-07
Check if a program is in the Ubuntu repositories (including Universe and Multiverse) before turning to bitnami.org. It looks like everything they carry is open source (?), which means it probably *is* in the repos.

---

### Post by kevinsteger on 2009-10-07
What I am doing is "sudo ./installerfile.bin"

which is what you are tell me.  It is spelled right, as +x, etc. I'm just dumbfounded

> **alphaniner said:**
> You need to tell the shell where to look, otherwise it looks in the directories in your PATH variable.   Use ./ before the executable if you are in the directory where it is located, or use the full path, ie
```

sudo ./filename.bin
```(**./** means 'here')

or

```
sudo /home/kevinsteger/Desktop/filename.bin
```I don't know about executing through GUI, though, it should ask you if you want to execute I think...

---

### Post by kevinsteger on 2009-10-07
We are trying to standardize everyone on the same stack, otherwise I would do just that.  I've been instructed to use this stack.

> **wmcbrine said:**
> Check if a program is in the Ubuntu repositories (including Universe and Multiverse) before turning to bitnami.org. It looks like everything they carry is open source (?), which means it probably *is* in the repos.

---

### Post by kevinsteger on 2009-10-07
```

kevin@nix1:~/Desktop$ ls
lampinstaller.bin  rubyinstaller.bin
kevin@nix1:~/Desktop$ chmod 755 rubyinstaller.bin
kevin@nix1:~/Desktop$ chmod +x rubyinstaller.bin
kevin@nix1:~/Desktop$ sudo ./rubyinstaller.bin
sudo: unable to execute ./rubyinstaller.bin: No such file or directory
kevin@nix1:~/Desktop$ 


```

Nothing happens at all.  Thanks for your help.

---

### Post by alphaniner on 2009-10-07
This is a shot in the dark, but what is the output of

```
file rubyinstaller.bin
```

Edit:

I found [this post]("http://ubuntuforums.org/archive/index.php/t-1141792.html").  Are you running 32bit or 64bit Ubuntu?

---

### Post by kevinsteger on 2009-10-07
> **alphaniner said:**
> This is a shot in the dark, but what is the output of

```
file rubyinstaller.bin
```Edit:

I found [this post]("http://ubuntuforums.org/archive/index.php/t-1141792.html").  Are you running 32bit or 64bit Ubuntu?


Running 64, and the output of that command is this:

rubyinstaller.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

I think you're on to something.  I'll report back on this.

---

### Post by smcclos on 2010-12-30
I fixed this problem by installing ia32-libs.  Cannot take the full credit for solving it myself, found off of another web site ([http://bitnami.org/forums/forums/drupal/topics/error-installing-in-ubuntu](http://bitnami.org/forums/forums/drupal/topics/error-installing-in-ubuntu))

---

