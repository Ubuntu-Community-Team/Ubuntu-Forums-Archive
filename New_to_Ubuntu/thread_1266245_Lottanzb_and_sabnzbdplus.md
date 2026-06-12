---
title: "Lottanzb and sabnzbdplus"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by shadowlands on 2009-09-14
seem to have a lot of problems is there any guides that have been written for non computer people who do not what to be shafted by having to use Microsoft or who just wish to remain loyal to opensource products and learn how to use them?  The same holds true for Pan.  

Yep, I admit I am a nut a nut who is a bit ticked off and confused on how to use some of the products here.

---

### Post by oldos2er on 2009-09-14
[http://linux.softpedia.com/get/Office/News-Diary/LottaNZB-32098.shtml](http://linux.softpedia.com/get/Office/News-Diary/LottaNZB-32098.shtml)

[https://help.ubuntu.com/community/Pan](https://help.ubuntu.com/community/Pan)

---

### Post by shadowlands on 2009-09-14
I am locked out. I get the following message.

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
> **oldos2er said:**
> [http://linux.softpedia.com/get/Office/News-Diary/LottaNZB-32098.shtml](http://linux.softpedia.com/get/Office/News-Diary/LottaNZB-32098.shtml)

[https://help.ubuntu.com/community/Pan](https://help.ubuntu.com/community/Pan)

---

### Post by shadowlands on 2009-09-14
Can you help with the fact I am locked out and can you please explane the following :To install LottaNZB, the graphical front-end for HellaNZB, download and extract the source. Change into the LottaNZB directory (where setup.py is located), build and install it:

cd /path/to/the/lottanzb/source

./setup.py build

sudo ./setup.py install


Thanks:KS:KS:KS:popcorn::popcorn:

---

### Post by ohzopants on 2009-09-14
Usually the lock message means that another package manager is running.  Could be on the command line, or you have synaptic running.

---

### Post by oldos2er on 2009-09-14
In order to become root, prepend a command with **sudo**, e.g. **sudo apt-get install lottanzb**

---

### Post by shadowlands on 2009-09-14
nothing is running

---

### Post by shadowlands on 2009-09-14
new message:

torchwood@torchwood-laptop:~$ . sudo apt-get install lottanzb
bash: ELF: command not found


> **oldos2er said:**
> In order to become root, prepend a command with **sudo**, e.g. **sudo apt-get install lottanzb**

---

### Post by Lantash on 2009-09-14
It's much easier to use the Ubuntu packages provided at [http://www.lottanzb.org/downloads/ubuntu/](http://www.lottanzb.org/downloads/ubuntu/)

Download the one for your Ubuntu version and install it by clicking on it

"sudo apt-get install lottanzb" will only work if you use Ubuntu 9.10 (which has not been released yet).

---

### Post by shadowlands on 2009-09-14
Thanks

---

### Post by madman100 on 2009-09-14
Hi i use sabnzbdplus witch is very easy to use and setup if you got hellanzb  setup on your system and all the packages install because sabnzbdplus uses most of the same packages to start sabnzbdplus open terminal and type sabnzbdplus that will open the interface

Madman100

---

### Post by oldos2er on 2009-09-14
My apologies; I didn't realise lottanzb was not in the repositories.

---

### Post by shadowlands on 2009-09-14
that is ok.  You did take the time to answer my questions.

---

