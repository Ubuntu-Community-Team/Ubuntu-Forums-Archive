---
title: "This code doesn't work"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by s3a on 2007-10-27
"Lets unpack, compile and install the drivers:

tar xfj rt2570-k2wrlz-1.3.0.tar.bz2
cd rt2570-k2wrlz-1.3.0/Module
make
make install

The last step has to be performed as root. Use su to change to root. Now we can load the module into the kernel:

modprobe rt2570"
_____________________________________________________________________________________
That code is for RPM or YUM Linux's, how can I make it work for Ubuntu? I downloaded this thing and don't know how to compile it...

Thanks!

---

### Post by kevdog on 2007-10-27
Which part of those commands doesnt work??

---

### Post by scorp123 on 2007-10-27
> **s3a said:**
>  ... The last step has to be performed as root. Use su to change to root. ...  On Ubuntu you'd use **sudo** instead .... e.g. ```
sudo NameOfCommandToRun
``` .... "sudo make install" in your example I guess.

---

### Post by s3a on 2007-10-27
kevdog, none of them work although the terminal shows some understanding of the commands which leads me to the question: where do I have to place the files to compile? On the desktop?

scorp123, I did use sudo. I think it didn't work in the first place because I probably haven't placed the files that I need to compile in the right location.

Thanks in advance!

---

### Post by kevdog on 2007-10-27
You are definitely not in the same directory where your tar.bz2 file is located.   The desktop is ~/Desktop.   Im not suggesting you use the desktop, however put the the tar.bz2 file in a folder you create and then change into that directory and run the commands.

---

### Post by s3a on 2007-10-27
> **kevdog said:**
> You are definitely not in the same directory where your tar.bz2 file is located.   The desktop is ~/Desktop.   Im not suggesting you use the desktop, however put the the tar.bz2 file in a folder you create and then change into that directory and run the commands.
I'm kinda stupid so can you please paste the terminal commands I've brought up initially with the location edited to desktop [that way I can learn how to change it as well as get the command I'm looking for]?

---

### Post by kevdog on 2007-10-27
Lets assume the file is on the desktop

cd ~
mkdir test-dir
cd Desktop
cp filename.tar.bz2 ~/test-dir
cd ~/test-dir

Then run the commands you listed at first.

---

### Post by s3a on 2007-10-27
> **kevdog said:**
> Lets assume the file is on the desktop

cd ~
mkdir test-dir
cd Desktop
cp filename.tar.bz2 ~/test-dir
cd ~/test-dir

Then run the commands you listed at first.
I did that except the last one and something went wrong as in something refused to work. I re-did it _all_ **(including the last command).** I then put in the terminal commands I've had initially and got this:
"
deniz@deniz-desktop:~$ cd ~
deniz@deniz-desktop:~$ mkdir test-dir
mkdir: cannot create directory `test-dir': File exists
deniz@deniz-desktop:~$ cd Desktop
deniz@deniz-desktop:~/Desktop$ cp filename.tar.bz2 ~/test-dir
cp: cannot stat `filename.tar.bz2': No such file or directory
deniz@deniz-desktop:~/Desktop$ cd ~/test-dir
deniz@deniz-desktop:~/test-dir$ tar xfj rt2570-k2wrlz-1.3.0.tar.bz2
tar: rt2570-k2wrlz-1.3.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
deniz@deniz-desktop:~/test-dir$ cd rt2570-k2wrlz-1.3.0/Module
bash: cd: rt2570-k2wrlz-1.3.0/Module: No such file or directory
deniz@deniz-desktop:~/test-dir$ make
make: *** No targets specified and no makefile found.  Stop.
deniz@deniz-desktop:~/test-dir$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
deniz@deniz-desktop:~/test-dir$ 
"

---

### Post by kevdog on 2007-10-27
I cant help you any longer, you need to find out how to copy your tar.bz2 file into whatever directory you want.

---

### Post by s3a on 2007-10-27
> **kevdog said:**
> I cant help you any longer, you need to find out how to copy your tar.bz2 file into whatever directory you want.

My tar.bz2 file is on the desktop and that's where I want it...

---

### Post by kevdog on 2007-10-27
cd ~/Desktop

Do a ls -la to see if the file is there.  Then proceed with the commands.

---

