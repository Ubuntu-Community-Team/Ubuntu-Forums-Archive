---
title: "Installing NetBeans Beta"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by EmperorNero on 2009-06-01
Would anyone help me through this? :)

I downloaded a .sh file.
Now I am supposed to:
For these platforms, you need to make the installer files executable by using the following command:
chmod +x <installer-file-name>

The file is named "netbeans-6.7rc1-ml-javase-linux.sh" and it's on my desktop, what do I type?
(Is there an easier way to getting to the file name than right-clicking and then rename?)

Thanks in advance dear Linux user.

[http://www.netbeans.org/community/releases/67/install.html#downloadoptions](http://www.netbeans.org/community/releases/67/install.html#downloadoptions)

---

### Post by netpro25 on 2009-06-01
Just do the following.

sudo chmod +x netbeans-6.7rc1-ml-javase-linux.sh
sudo ./netbeans-6.7rc1-ml-javase-linux.sh

---

### Post by EmperorNero on 2009-06-01
> **netpro25 said:**
> Just do the following.

sudo chmod +x netbeans-6.7rc1-ml-javase-linux.sh
sudo ./netbeans-6.7rc1-ml-javase-linux.sh

Tells me this:
chmod: cannot access `netbeans-6.7rc1-ml-javase-linux.sh': No such file or directory

---

### Post by Hospadar on 2009-06-01
You're in the wrong directory
if you  "pwd" it will **p**rint your **w**orking **d**irectory
You'll see that you are in /home/your_username (If you're not, you can "cd ~" to get to your home directory)
if you "ls" it will list the files in your current working directory, one of them will be a folder called "Desktop" (which is, as you might guess, your desktop, 
now "cd" (**c**hange **d**irectory) into that folder (use the command "cd Desktop" now you can do the chmod (which changes file permissions so that you can execute the file as a script) and then run the installer

A couple notes
"~" is shorthand for your home directory, "cd ~" will take you to /home/your_username
"." is shorthand for the current directory, that's why you have to do that **./**netbeans_installer (so the shell can tell you are trying to execute a file, not run an already installed program called "netbeans-6.7rc1-ml-javase-linux.sh"
".." is shorthand for the parent folder, for example if you are in /folder1/folder2, "cd .." will take you up a level to /folder1

I'd strongly suggest a quick CLI tutorial, there are a ton on the google machine, and they really help when you're getting started in linux.

---

### Post by EmperorNero on 2009-06-01
> **Hospadar said:**
> You're in the wrong directory
if you  "pwd" it will **p**rint your **w**orking **d**irectory
You'll see that you are in /home/your_username (If you're not, you can "cd ~" to get to your home directory)
if you "ls" it will list the files in your current working directory, one of them will be a folder called "Desktop" (which is, as you might guess, your desktop, 
now "cd" (**c**hange **d**irectory) into that folder (use the command "cd Desktop" now you can do the chmod (which changes file permissions so that you can execute the file as a script) and then run the installer

A couple notes
"~" is shorthand for your home directory, "cd ~" will take you to /home/your_username
"." is shorthand for the current directory, that's why you have to do that **./**netbeans_installer (so the shell can tell you are trying to execute a file, not run an already installed program called "netbeans-6.7rc1-ml-javase-linux.sh"
".." is shorthand for the parent folder, for example if you are in /folder1/folder2, "cd .." will take you up a level to /folder1

I'd strongly suggest a quick CLI tutorial, there are a ton on the google machine, and they really help when you're getting started in linux.

Thank you very much, netpro25 as well, it was partly the case sensitivity that threw me off, but all your information was very helpful.

I am going to spend some time reading a CLI tutorial now. ;)

Do programs usually get released on linux and windows at the same time?

---

### Post by EmperorNero on 2009-06-01
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9358-howto-install-software-readme.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9358-howto-install-software-readme.html)

I can't do the same with firefox, a .tar.bz2 file.
I got the .tar.bz2 file, I did this:
```
bunzip2 <filename>
```
Then I get a .tar file on my desktop. But the guide tells me there should be a directory.
When I unzip the tar file, I have a directory, but what to do with that.

As for the insructions I get from the mozilla webside,
```
# cd /opt
# mv firefox firefox.old
# cp /tmp/firefox-3.0.tar.bz2 .
# tar -jxvf firefox-3.0.tar.bz2 
```
I just get an error.

---

### Post by EmperorNero on 2009-06-01
I can get to the point where I extracted the directory and I have to ```
./configure
```, but it tells me: No such file or directory.

---

### Post by Nick Rhodes on 2009-06-03
From a terminal opened from your desktop:
Cd to the directory you downloaded the installer.

run "sudo sh netbeans-6.7rc1-ml-javase-linux.sh" (or whatver version of netbeans you downloaded).

I have just run these exact steps to install 6.7 RC1 on Jaunty.

Cheers, Nick.

---

### Post by niteshifter on 2009-06-03
Hi,

Netbeans can be had from the repositories, you can install it (2 clicks!) via Synaptic. It won't be the latest and greatest, but will be 6.0 or higher. Unless there is something essential you need in 6.7 getting it via Synaptic is far easier.

---

### Post by EmperorNero on 2009-06-03
> **niteshifter said:**
> Hi,

Netbeans can be had from the repositories, you can install it (2 clicks!) via Synaptic. It won't be the latest and greatest, but will be 6.0 or higher. Unless there is something essential you need in 6.7 getting it via Synaptic is far easier.

It has version 6.5 on the repositories I tried version 6.7 beta on win, and liked it. ;)

---

### Post by Nick Rhodes on 2009-06-05
6.7 RC1 is out and looking good.

---

### Post by QIII on 2009-06-05
The only real problem I had with the beta was that sometimes using the profiler would lock up the works and I'd have to shut down and restart the IDE.

Next time, it would work.

Later, it wouldn't.

Piddling little thing, considering it's a beta.

---

