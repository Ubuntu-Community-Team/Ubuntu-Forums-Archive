---
title: "Installing from source code/tar"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by ColemanK on 2009-06-28
Today, I installed Ubuntu for maybe the third time. The other times I've had Ubuntu as an operating system, I've tried to avoid .tar files, but today I believe I'm ready.

I've read all of the tutorials, and looked far and wide for good tutorial videos, but it seems that my brain is too weak to comprehend the powers of the seemingly random terminal lines, and lack of youtube tutorial videos regarding the subject.

Can someone take time off their schedule to teach me exactly how to compile and install files from source? 

Maybe we could the latest firefox beta as an example? Please?

---

### Post by alphacrucis2 on 2009-06-28
> **ColemanK said:**
> Today, I installed Ubuntu for maybe the third time. The other times I've had Ubuntu as an operating system, I've tried to avoid .tar files, but today I believe I'm ready.

I've read all of the tutorials, and looked far and wide for good tutorial videos, but it seems that my brain is too weak to comprehend the powers of the seemingly random terminal lines, and lack of youtube tutorial videos regarding the subject.

Can someone take time off their schedule to teach me exactly how to compile and install files from source? 

Maybe we could the latest firefox beta as an example? Please?

I would advise against attempting Firefox. There is already a PPA for the daily builds. You will have much less grief if you use that:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

Note that it doesn't replace the standard firefox package but installs as an additional browser something like Shiretoko Web Browser.

In the simplest cases to compile from source you would do something like:

```
sudo apt-get install build-essential
```

Note that the above only has to be done once before you try and compile anything. It installs the compilers etc.

To actually compile from the extracted source - cd to the directory where you extracted the archive then:

```
./configure
make
sudo make install
```

The source usually includes a readme file which explains anything special requirements or instructions (if you are lucky).

---

### Post by oldos2er on 2009-06-28
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bodhi.zazen on 2009-06-28
1. Firefox is not a great example as it is distrubuted as a binary. Simply download the tar and extract it.

2. Otherwise see the links you have been given.

The only advice I would add is :

1. The most common source of compilation errors is missing dependencies. You will need to search for the dependencies yourself, sometimes in the -dev package.

2. Read the README

3. ./configure --help # will list all options.

4. ./configure --prefix=/usr/local # Will install in /usr/local so as not to interfere with other packages.

---

### Post by ColemanK on 2009-06-29
Thanks! I can always count on the Ubuntu forums to help me out!

---

