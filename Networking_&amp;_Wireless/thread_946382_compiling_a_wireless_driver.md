---
title: "compiling a wireless driver"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by mez_ on 2008-10-13
This concerns the driver called "realtek rtl8187se" which is used in the MSI Wind laptop (netbook)

There is no official linux support for my wlan, but realtek is building a driver for it and every once in a while they release a new driver (not officially). I am currently on one such driver but it has a few issues. I believe they have to do with power management. sometimes the wireless module becomes unusable for a few days, after which it works for a few hours and so on. This is a common issue among people who are using this older driver. However they have released a new driver. But when I try to compile it I get some warnings, and when using a patch that is recommended on a ubuntu bug page I get errors, of which somebody on the IRC support channel told me that they are fatal.

I am using these instructions: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141/comments/72)

there are some others on the internet but they usually deal with older versions of the driver. The instructions at this link also use a patch.

Pastebin when compiling the driver without the patch:
[http://paste.ubuntu.com/56998/](http://paste.ubuntu.com/56998/) (i have not been told that the warnings in here are fatal)

Pastebin when compiling the driver with the patch:
[http://paste.ubuntu.com/56992/](http://paste.ubuntu.com/56992/) (i have been told in the irc channel that the errors in here are fatal)

Is the driver from either one of these pastebins usable?

Something else (this is possibly where it goes wrong):
The instructions on the link that I gave earlier in this post are:
> - sudo apt-get install build-essential
 - wget [http://www.mediafire.com/download.php?pavvaazisj1](http://www.mediafire.com/download.php?pavvaazisj1)
 - tar -xzvf rtl8187se_linux_26[1].1022.0904.2008_Release.tar.gz
 - cd rtl8187se_linux_26.1022.0904.2008
 - wget [http://launchpadlibrarian.net/18091767/rtl8187se_2.6.27.patch](http://launchpadlibrarian.net/18091767/rtl8187se_2.6.27.patch)
 - patch -p1 < patch_rtl8187se_2.6.27
 - ./makedrv
 - sudo ./wlan0up

However, when patching the patch command doesnt work. It says that there is no such file or directory.

So I changed the patch line to: "patch -p1 < rtl8187se2.6.27.patch", which does work. However as you can see, after that I get a bunch of errors when compiling it.

any ideas? I would really appreciate some help here.

before you ask, build-essential is up to date, as is linux-headers-`uname -r` (somebody in the irc channel asked me to try to update this last one but it was already up to date.

---

### Post by homemadejam on 2008-10-13
Hey,
I had a lot of problems when doing this last night too!
I'm sorry, but I can't quite remember what it was I had to do now... :S

But I can tell you what version of driver you need.

**rtl8187se_linux_26.1022.0904.2008**

and the **rtl8187se_2.6.27.patch** patch file

And I can remember having a look at this page:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141)

Sorry I can't be anymore help then that.


Jam

---

### Post by mez_ on 2008-10-14
any ideas?

---

