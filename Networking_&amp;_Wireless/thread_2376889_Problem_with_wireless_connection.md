---
title: "Problem with wireless connection"
date: 2017-11-07
forum: Networking &amp; Wireless
---

### Post by pukiking- on 2017-11-07
Hi!
I've recently installed ubuntu, and I'm having tons of problems with it since. Although I have good Processor, graphic card etc. My laptop is working slowly. Wifi litteraly comes and goes. It usually works only a couple of minutes and then I need to restart wifi connection for it to work again or wait couple of minutes. Can you tell me which logs do I need to post?

[ATTACH=CONFIG]277441[/ATTACH]

---

### Post by slickymaster on 2017-11-07
[I]Thread moved to **Networking & Wireless**.

[/I]Using a wired internet connection download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself.

---

### Post by pukiking- on 2017-11-07
Ty for a fast reply, here's the file.
[https://pastebin.com/Q8Bd6VGn](https://pastebin.com/Q8Bd6VGn)

---

### Post by wildmanne39 on 2017-11-07
Please run these commands one at a time by copying and pasting for accuracy and watch for errors, warnings are okay.
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git 
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```
Reboot and let us know if that helps.

---

### Post by praseodym on 2017-11-07
For your hybrid VGA see here: [http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

I also recommend channel 6 or 13 in your router, 19 networks are on channel 1

---

### Post by pukiking- on 2017-11-07
I've experienced an error at make command
```
nikola@nikola-X550VX:/$ git clone http://github.com/lwfinger/rtlwifi_new.git
fatal: could not create work tree dir 'rtlwifi_new': Permission denied
nikola@nikola-X550VX:/$ sudo git clone http://github.com/lwfinger/rtlwifi_new.git
Cloning into 'rtlwifi_new'...
remote: Counting objects: 5257, done.
remote: Total 5257 (delta 0), reused 0 (delta 0), pack-reused 5257
Receiving objects: 100% (5257/5257), 8.25 MiB | 1.62 MiB/s, done.
Resolving deltas: 100% (4460/4460), done.
nikola@nikola-X550VX:/$ cd rtlwifi_new
nikola@nikola-X550VX:/rtlwifi_new$ make
make -C /lib/modules/4.10.0-38-generic/build M=/rtlwifi_new modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-38-generic'
arch/x86/Makefile:140: CONFIG_X86_X32 enabled but no binutils support
mkdir: cannot create directory &#8216;/rtlwifi_new/.tmp_versions&#8217;: Permission denied
  CC [M]  /rtlwifi_new/base.o
Assembler messages:
Fatal error: can't create /rtlwifi_new/base.o: Permission denied
/rtlwifi_new/base.c:1:0: error: code model kernel does not support PIC mode
 /******************************************************************************
 
scripts/Makefile.build:294: recipe for target '/rtlwifi_new/base.o' failed
make[2]: *** [/rtlwifi_new/base.o] Error 1
Makefile:1524: recipe for target '_module_/rtlwifi_new' failed
make[1]: *** [_module_/rtlwifi_new] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-38-generic'
Makefile:58: recipe for target 'all' failed
make: *** [all] Error 2 
```
Also had to use sudo for a seccond comand
Should I type the last command
```
sudo make install
```
or should I maybe do sudo make if the problem is only that permission was denied again?

---

### Post by wildmanne39 on 2017-11-07
It has failed. Did you run and watch for errors this command first, I do not see it listed in the output.
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git 
```

---

### Post by pukiking- on 2017-11-07
```
nikola@nikola-X550VX:/$ sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms git
[sudo] password for nikola: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-19 linux-headers-4.10.0-19-generic linux-headers-4.10.0-35 linux-headers-4.10.0-35-generic linux-image-4.10.0-19-generic linux-image-4.10.0-35-generic
  linux-image-extra-4.10.0-19-generic linux-image-extra-4.10.0-35-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-arch git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 3778 kB/4521 kB of archives.
After this operation, 28,7 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://rs.archive.ubuntu.com/ubuntu zesty/main amd64 liberror-perl all 0.17024-1 [23,0 kB]
Get:2 http://rs.archive.ubuntu.com/ubuntu zesty-updates/main amd64 git-man all 1:2.11.0-2ubuntu0.3 [769 kB]
Get:3 http://rs.archive.ubuntu.com/ubuntu zesty-updates/main amd64 git amd64 1:2.11.0-2ubuntu0.3 [2982 kB]
Get:4 http://rs.archive.ubuntu.com/ubuntu zesty/main amd64 build-essential amd64 12.1ubuntu2 [4758 B]
Fetched 3778 kB in 1s (2600 kB/s)         
Selecting previously unselected package liberror-perl.
(Reading database ... 272126 files and directories currently installed.)
Preparing to unpack .../0-liberror-perl_0.17024-1_all.deb ...
Unpacking liberror-perl (0.17024-1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../1-git-man_1%3a2.11.0-2ubuntu0.3_all.deb ...
Unpacking git-man (1:2.11.0-2ubuntu0.3) ...
Selecting previously unselected package git.
Preparing to unpack .../2-git_1%3a2.11.0-2ubuntu0.3_amd64.deb ...
Unpacking git (1:2.11.0-2ubuntu0.3) ...
Preparing to unpack .../3-build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) over (12.1ubuntu2) ...
Preparing to unpack .../4-dkms_2.3-3ubuntu1.2_all.deb ...
Unpacking dkms (2.3-3ubuntu1.2) over (2.3-3ubuntu1.2) ...
Preparing to unpack .../5-linux-headers-4.10.0-38-generic_4.10.0-38.42_amd64.deb ...
Unpacking linux-headers-4.10.0-38-generic (4.10.0-38.42) over (4.10.0-38.42) ...
Setting up git-man (1:2.11.0-2ubuntu0.3) ...
Setting up linux-headers-4.10.0-38-generic (4.10.0-38.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-38-generic /boot/vmlinuz-4.10.0-38-generic
Setting up liberror-perl (0.17024-1) ...
Setting up build-essential (12.1ubuntu2) ...
Setting up dkms (2.3-3ubuntu1.2) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up git (1:2.11.0-2ubuntu0.3) ...
nikola@nikola-X550VX:/$ git clone http://github.com/lwfinger/rtlwifi_new.git
fatal: could not create work tree dir 'rtlwifi_new': Permission denied
nikola@nikola-X550VX:/$ sudo git clone http://github.com/lwfinger/rtlwifi_new.git
Cloning into 'rtlwifi_new'...
remote: Counting objects: 5257, done.
remote: Total 5257 (delta 0), reused 0 (delta 0), pack-reused 5257
Receiving objects: 100% (5257/5257), 8.25 MiB | 1.62 MiB/s, done.
Resolving deltas: 100% (4460/4460), done.
nikola@nikola-X550VX:/$ cd rtlwifi_new
nikola@nikola-X550VX:/rtlwifi_new$ make
make -C /lib/modules/4.10.0-38-generic/build M=/rtlwifi_new modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-38-generic'
arch/x86/Makefile:140: CONFIG_X86_X32 enabled but no binutils support
mkdir: cannot create directory &#8216;/rtlwifi_new/.tmp_versions&#8217;: Permission denied
  CC [M]  /rtlwifi_new/base.o
Assembler messages:
Fatal error: can't create /rtlwifi_new/base.o: Permission denied
/rtlwifi_new/base.c:1:0: error: code model kernel does not support PIC mode
 /******************************************************************************
 
scripts/Makefile.build:294: recipe for target '/rtlwifi_new/base.o' failed
make[2]: *** [/rtlwifi_new/base.o] Error 1
Makefile:1524: recipe for target '_module_/rtlwifi_new' failed
make[1]: *** [_module_/rtlwifi_new] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-38-generic'
Makefile:58: recipe for target 'all' failed
make: *** [all] Error 2
nikola@nikola-X550VX:/rtlwifi_new$ 
```
Here's the whole code. I have, and I haven't seen any errors.

---

### Post by jeremy31 on 2017-11-07
Use terminal in your home folder and not root folder and it should work, do
```
cd ~
```
Then follow instructions from [https://ubuntuforums.org/showthread.php?t=2376889&p=13708631#post13708631](https://ubuntuforums.org/showthread.php?t=2376889&p=13708631#post13708631)

---

### Post by pukiking- on 2017-11-07
Ty for all the help

---

### Post by wildmanne39 on 2017-11-07
I am not sure why it failed with the headers look like they installed an you are in the right path it looks like.

---

### Post by jeremy31 on 2017-11-07
I would try again from the home folder

---

