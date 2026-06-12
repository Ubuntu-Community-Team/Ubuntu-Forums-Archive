---
title: "How do you install ipmsg?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by gprateek on 2009-08-07
[B]Pls pls help >>>    irritating problem

[/B]Hello all, i am at the initial stages of working with UBUNTU 9.04 cd edition.

1.
I wanted to install some of the application and even tried with WINE  , but they didnt work.

However , I got a substitute of one of the applications "ipmsg" and wanted to install it . So I downloaded the package built for Linux . its link is [http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz](http://www.ipmsg.org/archive/g2ipmsg-0.9.6.tar.gz) 

BUT ............  when I try to install it , it shows some errors and the setup does not complete ...... 
$./configure.sh : the process, after some time gives the msg that GNU tools are not available , i cant even find a GNU install in Add/Remove Applications 

 :sad:


Another time the $./configure was working fine , and when I run $ make install =>IT SHOWS SOME ERRORS WHICH SAID THAT IT DOES NOT HAS PRIVILEGES TO FORM ITS OWN DIRECTORY IN /usr/local ..... 

PLS ...... PLS HELP ME..............



PROBLEM VIEW:
./configure  ---works fine
make          ---works fine

make install      -----the following output is obtained

"
prateek@prateek-laptop:~/DOWNLOADS/g2ipmsg-0.9.6$ make install
Making install in src
make[1]: Entering directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make[2]: Entering directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'g2ipmsg' '/usr/local/bin/g2ipmsg'
/usr/bin/install: cannot create regular file `/usr/local/bin/g2ipmsg': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/prateek/DOWNLOADS/g2ipmsg-0.9.6/src'
make: *** [install-recursive] Error 1
prateek@prateek-laptop:~/DOWNLOADS/g2ipmsg-0.9.6$

":confused:

---

### Post by Perfect Storm on 2009-08-07
You didn't gave it permission to write there; do a **sudo** make install

---

### Post by Phobiac on 2009-08-07
I'd also suggest that when ./configure reports something missing that needs to be installed, look for it with
sudo apt-cache search yoursearchterm
You might run into situations where something is required and you see two packages, such as foo and foo-dev. If you're compiling something that requires it, you'll need foo-dev.

---

### Post by juancarlospaco on 2009-08-07
[*BTW Do you compile your programs on Windows...?*]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ipmsg")

---

### Post by aysiu on 2009-08-07
**Step 1**:
Forget about compiling from source

**Step 2**:
Make sure you have extra software repositories enabled
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 3**:
Learn how to install software in Ubuntu
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step 4**:
Using Synaptic, search for *ipmsg* and install the *xipmsg* package, as juancarlospaco suggested

---

### Post by gprateek on 2009-08-08
> **juancarlospaco said:**
> [*BTW Do you compile your programs on Windows...?*]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ipmsg")
Yes, compiling of programs using Turbo C in Windows.
 
Do u have any point inasking this?

---

### Post by gprateek on 2009-08-08
> **aysiu said:**
> **Step 1**:
Forget about compiling from source

**Step 2**:
Make sure you have extra software repositories enabled
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 3**:
Learn how to install software in Ubuntu
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step 4**:
Using Synaptic, search for *ipmsg* and install the *xipmsg* package, as juancarlospaco suggested
Thank You for all the information u have provided. Its very useful and very easy steps to finding and installing a software. 
 
Hope , u would continue to provide help like this in future too.

---

### Post by gprateek on 2009-08-08
> **Phobiac said:**
> I'd also suggest that when ./configure reports something missing that needs to be installed, look for it with
sudo apt-cache search yoursearchterm
You might run into situations where something is required and you see two packages, such as foo and foo-dev. If you're compiling something that requires it, you'll need foo-dev.
Thank you. I had been quite surprised by the commands of installing the software packages found on the net and had been thinking of how to obtain these.
 
Now I think you gave the answer.

---

### Post by oldos2er on 2009-08-08
> **Phobiac said:**
> look for it with
sudo apt-cache search yoursearchterm

 Just FYI, apt-cache search doesn't require sudo. Probably best not to use sudo unless absolutely necessary.

---

