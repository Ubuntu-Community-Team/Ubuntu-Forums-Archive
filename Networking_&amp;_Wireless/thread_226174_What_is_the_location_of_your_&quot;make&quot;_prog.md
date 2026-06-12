---
title: "What is the location of your &quot;make&quot; program"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by usernamenone on 2006-07-30
Hi, I have installed the ubuntu server and am installing the vmware server software. 

I have done the pre install 

apt-get install gcc binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1

I had an error with the above section. "a package gcc-4.0 locales is not available but is refered to by another package."

Install instructions are from [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

with the exception of the error package gcc-4.0 locales is not available but is refered to by another package. I went on with my install. I am now stuck at What is the location of the "make" program on your machine? the step just before "Trying to find a suitable vmnet module for your running kernel." It is about 1/2 down the page.

Any help would be greatly appreciated. Sorry I am new to Linux but want to learn.

---

### Post by usernamenone on 2006-08-01
Hey, Thanks for all your help. I got it figured out. :D

---

### Post by danlac on 2006-08-02
I have the same issue.  Can you tell me how you got around this?



> **usernamenone said:**
> Hi, I have installed the ubuntu server and am installing the vmware server software. 

I have done the pre install 

apt-get install gcc binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1

I had an error with the above section. "a package gcc-4.0 locales is not available but is refered to by another package."

Install instructions are from [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

with the exception of the error package gcc-4.0 locales is not available but is refered to by another package. I went on with my install. I am now stuck at What is the location of the "make" program on your machine? the step just before "Trying to find a suitable vmnet module for your running kernel." It is about 1/2 down the page.

Any help would be greatly appreciated. Sorry I am new to Linux but want to learn.

---

### Post by usernamenone on 2006-08-03
Yes I will be able to help you. when I tried to install this section of instructions

[COLOR="DarkRed"]apt-get install gcc binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1[/COLOR]

You need to omit this 
[LEFT][CENTER][COLOR="DarkRed"][COLOR="DarkRed"]gcc-4.0-locales
gcc-4.0-doc[/COLOR][/COLOR][/CENTER]
[/LEFT]
It seems they are installed with gcc and are not needed. So the instructions should read:
apt-get install gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc  libc6-dev-amd64 lib64gcc1

You can install 1 by 1 by 
sudo apt-get install gcc 
sudo apt-get install binutils-doc
and down the line.

Then procede with your instructions. I received the error about the but gcc-4.0-locales
gcc-4.0-doc but thought everything else had installed but did not.

---

### Post by usernamenone on 2006-08-03
I forgot to mention that if you have exited your install before completing your instruction you will need to extract your program and start with step 1 again.

---

