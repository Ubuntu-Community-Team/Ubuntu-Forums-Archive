---
title: "Lucent Winmodem ltmodem 2.6.12-9-386 solved!"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by finnish on 2005-11-22
Hi all. maybe i'll wrap this into a wiki article later but for now let's start with a post on this forum. I made my winmodem work. Here's solution:


**first of all:** check the version of compiler used to compile your kernel (cat /proc/version) because you will need such version of gcc to compile drivers yourself.

**UPDATED:**

Ubuntu 6.04 *(DD F1)*:
follow instructions for 5.10, except for 4 things:
1. you don't have to download gcc-3.4
2. download ltmodem-2.6-alk-8 driver sources as they have some fix
3. cd /lib/modules/`uname -r`/volatile ; rm lt*
4. replace /other/ with /volatile/ when copying compiled *.ko's

Works!

Ubuntu 5.10:

don't forget to SUDO everything :)

install build-essential and linux-headers-2.6.12-9-386:
apt-get install build-essential linux-headers-2.6.12-9-386

download
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)

install them:
dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb

make an appropriate link for compiling:
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc

download
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz)
update: currently available 2.6-alk-8 version!

unpack & copy:
mkdir /usr/src/modules
cd /where_you_downlaoded_.tar.gz
cp ltmodem-2.6-alk-7b1.tar.gz /usr/src/modules/
cd /usr/src/modules/
tar zxvf ltmodem-2.6-alk-7b1.tar.gz
cd ltmodem-2.6-alk-7c
make
mkdir /lib/modules/`uname -r`/other/
cp *.ko /lib/modules/`uname -r`/other/
cd /lib/modules/`uname -r`/other/
depmod -a
modprobe ltserial

then make a link:
ln -sf /dev/ttyLTM0 /dev/modem

now try pppconfig and then pon (poff) to connect.

To automate /dev/modem symlink creation put ltmodem.rules file into /etc/udev/rules.d/ this works just great.

if you use pppconfig to configure dial-up connection it will auto-dial it at every bootup just after alsa startup during network interfaces initialization. so use wvdial or System->Administration->Netwiorking to make connection.

*it's a product of huge investigation starting from linmodems.org, which took me 3 weeks :) i've read almost a 100 guides and readme's and none of them helped me fully. i had to find myself that 2.6.12-9-386 kernel is compiled with gcc-3.4, and it's required for proper modules compilation.*

thanks.

---

### Post by finnish on 2005-11-22
**removed**

---

### Post by ebonflame on 2005-11-25
Myself, I just recently got the ltmodem-3.81b1.tar.gz from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) to work as well using GCC 4.0  It seems to be a little more user friendly as it uses scripts to automate the process, during which it will run scanmodem to verify the modem, and then checks the system environment for kernel headers, the proper gcc, etc.  It then generates an install script to run.  The compliation did complain about .ltmdmobj.o.cmd missing, but the resulting module does dial up and connect.  I started with 2.12.9-k7 and also recompiled for 2.12.10-k7 and both work.

---

### Post by J.A. on 2005-12-08
Hello,

I've followed your detailed steps but always get the same error when I try to start the ltserial module:

/sbin/modprobe ltserial
**FATAL: Error inserting ltserial (/lib/modules/2.6.11-1.1369_FC4/kernel/drivers/misc/ltserial.ko): No such device**

I've tried countless versions of ltmodem and the same error is produced when trying to start ltserial.

(btw, my 'make' of the ltmodem package always produces the same warning:

make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dauser/Desktop/ltmodem-2.6-alk-7c modules
make[1]: Entering directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
CC [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/lt_modem.o
CC [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/serial.o
/home/dauser/Desktop/ltmodem-2.6-alk-7c/serial.c: In function &#8216;lt_get_mctrl&#8217;:
/home/dauser/Desktop/ltmodem-2.6-alk-7c/serial.c:387: warning: unused variable &#8216;flags&#8217;
LD [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltmodem.o
LD [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltserial.o
Building modules, stage 2.
MODPOST
**Warning: could not find /home/dauser/Desktop/ltmodem-2.6-alk-7c/.ltmdmobj.o.cmd for /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltmdmobj.o**
CC /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltmodem.mod.o
LD [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltmodem.ko
CC /home/bbenny/Desktop/ltmodem-2.6-alk-7c/ltserial.mod.o
LD [M] /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltserial.ko
make[1]: Leaving directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'

)

Any ideas? (apologies for the FC4 os, but I haven't been able to find a solution anywhere - I am using an IBM R50e laptop. Thanks.)

---

### Post by Count Chocula on 2005-12-09
Thanks for the info. This is such a pain for breezy with the GCC situation and all. In hoary the drivers were included in the restricted modules package. I would like to ask if anyone would be so kind as to put up these precompiled drivers somewhere for download off the net? Maybe as attachments to this thread?

---

### Post by H4rm0ny on 2005-12-13
Seconded - this would be a great help. I need to get Breezy working on an older laptop for a mate. Going round there, compiling on the laptop, installing GCC just for this, etc, etc, will take ages and compiling on my newer system with different architecture and copying across will probably be also headache.

Can anyone tell me why the drivers were taken out of the restricted package? The description still lists them as included.

---

### Post by finnish on 2006-01-08
**J.A.**
> Warning: could not find /home/dauser/Desktop/ltmodem-2.6-alk-7c/.ltmdmobj.o.cmd for /home/dauser/Desktop/ltmodem-2.6-alk-7c/ltmdmobj.o
it's okay.

> /sbin/modprobe ltserial
FATAL: Error inserting ltserial (/lib/modules/2.6.11-1.1369_FC4/kernel/drivers/misc/ltserial.ko): No such device
not okay. are you sure you've got Lucent Winmodem? try scanmodem tool first.

**ebonflame** 
congratulations!

**H4rm0ny, Count Chocula**
i can't, since i deleted them, as i moved to 6.04 and so.. sorry :)

updated my first post.

---

### Post by finnish on 2006-01-08
currently working on 6.04 (flight1). it seems they returned restricted modules but it seems to me they're not working.. any ideas?

---

### Post by finnish on 2006-01-08
haha! i won 6.04 flight1, no doubt it will work in late versions:
3 main secrets:
delete /lib/modules/`uname -r`/volatile/lt*.ko that ship in linux-restricted-modules as they don't work
copy compiled drievrs not to /lib/modules/`uname -r`/other/ but to /lib/modules/`uname -r`/volatile/
use latest 2.6-alk-8 driver source

---

### Post by finnish on 2006-01-08
first post updated

---

### Post by ioannis.th on 2006-01-12
A word of warning. If you experience lockups or generally instability, make sure you don't have a SMP enabled kernel. This module sometimes causes synchronization problems on multiprocessor or pentium hyperthreading systems. I know that because it happened to me when I was using Gentoo.

---

### Post by Nikusan on 2006-01-31
I installed the five packages from the start of finnish's instructions but when it comes time to make the following happens:

```

dan@problemchild:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/ltmodem-2.6-alk-7c modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [module] Error 2

```

```

dan@problemchild:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo mkdir /lib/modules/2.6.12-10-386/build
dan@problemchild:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo make make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/ltmodem-2.6-alk-7c modules
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [module] Error 2

```

What am I doing wrong?

---

### Post by KOLE on 2006-02-09
I have one problem: I installed modem with file ltmodem-2.6.12-9-386_8.31b1_i386.deb and installation was sucesfull, but I can't connect to internet. Number is dialed, sound of connecting is the same as in Windows, but at the end it stops for ~10sec and reconnects.

Does anyone know how to fix this? (btw. I'm a begginer in Linux so make it step-by-step)

---

### Post by hajk on 2006-02-10
Firewall issue? Firestarter can handle only 1 interface at a time, so if it is already set up for eth0, say, then ppp0 won't come up. Lokkit can handle multiple interfaces... One more thing: if your ppp0 connection is going to use the nameservers specified by your ISP, then port 53 TCP/UDP must be opened in the firewall (read man lokkit).

---

### Post by Captain Mikee on 2006-02-24
So you have to download something to get the modem to work? Why were the drivers removed after Hoary?

Unfortunately, the computer I have with a working modem has no removable media. (iBook with OS9) Can anyone suggest a distro that will get the modem working from CD?

---

### Post by Dilutu on 2006-02-24
Hi. You could try Mepis 3.4.3.Its the first live cd to dial my LTmodem(Toshiba T8100) successfully.After a few days with Breezy,I can connect but my browser cant open any web pages...!!!???

---

### Post by HSSsb17 on 2006-02-27
Hey, I'm having a problem.  I successfully install the things, but then I get this:

FATAL: Error inserting ltserial (/lib/modules/2.6.12-9-386/.../ltserial.ko): Invalid Arguement

What does this mean, and how do I fix?

---

### Post by Creature on 2006-03-27
Hello. I'm having a problem doing the following steps:

on "apt-get install build-essential linux-headers-2.6.12-9-386"
I get a bunch of error messages saying: something like:
W: Couldn't stat source package list [http://security.ubuntu.com_ubuntu_disks_breezy_security_multiverse_binary-i386_Packages](http://security.ubuntu.com_ubuntu_disks_breezy_security_multiverse_binary-i386_Packages)) - stat (2 No such file or directory)

or instead of security.ubuntu... it's [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages ...

Is it trying to connect to the internet? If so how does that make sense?  If I could connect to the internet, I wouldn't be going through the steps to install a modem in order to connect to the internet.

Also on step:
cp *.ko /lib/modules/`uname -r`/other/

It says:
"cp: cannot stat '*.ko': No such file or directory.

What should I do?

(forgive me if my questions sound rediculous. I am very new to this linux thing)

Thank you in advance for your help.

---

### Post by Creature on 2006-03-27
Sorry for the double post, I couldn't figure out how to modify my previous one. And now I can't figure out how to delete one ^_^

I think I configured everything ok, but when I do pon command it says Connect script failed.  And when I do the wvdial it acts like it's trying to connect then says there is no dialtone.  But there is a dialtone.  The phone that is connected to the same modem has a dialtone, and I'm using the same phone line to be on the net now (w/ my windows laptop).  What did I do wrong?

P.S. the sudo wvdialconf /etc/wvdial.conf did say it found the modem when I did it.
I'm using Ubuntu version 5.10

---

### Post by finnish on 2006-03-29
HSSsb17
what version of Ubuntu do you use?
anyways, you should try deleting lt*.ko from /volatile folder i mentioned if you're on 6.04. then reboot. then compile and install (double check that there are no pre-compiled, shipped *.ko in volatile) drivers my way.
should work, had the same issue. ubuntu uses kernel that doesn't support module unloading, it means that you should reboot to unload modules. and delete them before reboot, to have them not loaded at startup. see?

---

### Post by finnish on 2006-03-29
Nikusan
i advice you to use 2.6-alk-8 version of drivers first.
then are you sure that you have all the header-sources for your version 2.6.10-286 kernel?

---

### Post by Creature on 2006-03-31
I think I configured everything ok, but when I do pon command it says Connect script failed. And when I do the wvdial it acts like it's trying to connect then says there is no dialtone. But there is a dialtone. The phone that is connected to the same modem has a dialtone, and I'm using the same phone line to be on the net now (w/ my windows laptop). What did I do wrong?

I'm using Ubuntu version 5.10

---

### Post by Plinybc on 2006-04-09
[EMAIL="pbc@mailaka.net"]I am very familiar with Windows, but am a newbie with Linux.  I loaded Ubuntu 5.10 on a separate machine with an Ltmodem installed.  Device manager sees it, but networking will not recognize it.[/EMAIL][EMAIL="pbc@mailaka.net"]](*,)[/EMAIL]

I've read and tried(as much as I understood) the info on the Linmodem site.  Since I'm not a programmer, I guess I need step-by-step instructions on this.  Reading your post I got lost with the instructions.  Is there a site that will simplify this process for someone with _**NO**_ linux experience?

Any help would be appreciated!

Thanks,
Greg
[email]pbc@mailaka.net[/email]

---

### Post by gr0kzer0 on 2006-04-22
Well I must say, after a lot of searching around, and poring over scanModem textfiles, installing the ltmodem driver turned out quite painless in the end.

First of all, I had to install build-essential and linux-headers, but they come with the install cd so that was ok. Then scanModem said I had the wrong gcc, and had to get BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink](http://phep2.technion.ac.il/linmodems/packages/smartlink). That installed trouble-free too.

And I also grabbed the drivers as a .deb. ltmodem-2.6.12-9-386_8.31b1_i386.deb to be precise.

My only bit of worry was, scanModem said that for Debian/Ubuntu, I needed something called kernel-kbuild-3.6, which I couldn't find _anywhere_. So, I decided to give it a go anyway.

sudo dpkg -i ltmodem-2.6.12-9-386_8.31b1_i386.deb

and it seemed to install ok.

A touch of panic when lsmod didn't show any new modules. I was getting "success" messages but it didn't look like it had worked.

Then I rebooted and ltserial and ltmodem were there in the lsmod output! And I ran wvdialconf and... Yes!! It found my "new" modem, /dev/ttyLTM0!!!

If you can use the .deb, do so. It seems to do most of the work for you. It's on that technion.ac.il site too, but not the same place as the gcc package. I went to [http://ltmodem.heby.de](http://ltmodem.heby.de) and found the link there.

---

### Post by blastus on 2006-04-23
I once had a Wiki page [Ubuntu 5.04 (Hoary) Lucent WinModem Setup](https://wiki.ubuntu.com/forum/hardware/lucent) for newbies on how to get a Lucent modem to work under Hoary. However, when Breezy came out, they clobbered the Wiki page, and now it ERRONEOUSLY claims that the precompiled kernel modules for Breezy are included on the distribution CD in the restricted-modules package. Anyone who has tried to compile the Lucent modules under Breezy knows that the CD does NOT include the precompiled kernel modules AND you have to manually install GCC 3.4. The author of the Wiki has obviously never tried to get the Lucent modem to work under Breezy.

See these threads:
[Breezy Badger - cannot compile Lucent modem drivers](http://www.ubuntuforums.org/showthread.php?t=77537)
[General - HOWTO: Install gcc-3.4 via apt-get without an Internet connection](http://ubuntuforums.org/showthread.php?t=79896)

When Dapper is released I'll create a HOWTO thread for newbies. Hopefully Dapper will at least include the GCC version that the kernel was compiled with, so we don't have to manually install it from the Web like we do with Breezy. I'm not contributing to the Wiki anymore--not if someone is just going to wipe out everything I contribute and replace it with USELESS instructions that WON'T WORK.

Like the OP said, as a newbie, it also took me hours and hours of searching for documentation on the Web to figure out how to get the modem to work. Unfortunately, the Wiki is now pretty much useless to newbies with Lucent modems running Breezy.

---

### Post by gr0kzer0 on 2006-04-23
Yeah, what the heck's that wrong gcc business all about anyway? It's obvious users are going to have to do some compiling at some point, when so many drivers don't come precompiled for us. Not including the correct gcc library is just careless... or dumb.

---

### Post by Coburn on 2006-05-03
As I replied to another post by gr0kzer0, it seems at first glance that the Ubuntu community is not very good at this Teamwork he speaks of.  

For starters, changes are made to the code, and documenters do not, for whatever reason, review the changes and update their instructions.  And we Gnubies are constantly confused by the Assumptions that we Know How to Do Simple Things.  Certain people have been too long in this Universe to remember what it feels like to adapt to it.  We are used to doing Everything with a Mouse.

Then, as I read his reply to my post (search "essential impossible", by Coburn, in Absolute Beginners), I realized We Are the Ubuntu community.  We are the ones who review changes, test them, and communicate the results.  

It takes a little getting used to finding your answers on the forums instead of in a Help file or through tech support, but so far it seems to be working well for me.

We'll see, after I try again to apt-get my linux-headers<HYPHEN>2.6.12-9.386!

Thanks,

Coburn

"Then the LORD said to Moses, 'Now you will see what I will do to Pharaoh."  --Exodus 6.1

---

### Post by thiagoms on 2006-05-14
sorry, wrong post

---

### Post by kevinlyfellow on 2006-06-01
It should be noted that this **does not work for the 686 kernel, only for the 386**.  Don't waste your time like I did ;)  .  This is due to bug [46685]("http://launchpad.net/46685").

---

### Post by kevinlyfellow on 2006-06-01
Everytime I reboot, only ltmodem (and not ltserial) would be inserted into the kernel.  I uninstalled the restricted drivers (in dapper btw) and put the new modules in and rebooted hopeing it would work.  But when I rebooted the files were gone!  What do I need to do to allow these modules to be inserted into the kernel and stay there?

---

### Post by blastus on 2006-06-21
Have you guys tried my guide [HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)](http://www.ubuntuforums.org/showthread.php?t=198730)?

---

### Post by Cloudy on 2006-07-11
Maybe I'm just daft, but what exactly am I copying when I reach the "cp *.ko /lib/mdoesul/`uname -r`/other/" step? :/ Every time I try the terminal spits some line out about how there is no *.ko file..

---

### Post by blastus on 2006-07-11
> **Cloudy said:**
> Maybe I'm just daft, but what exactly am I copying when I reach the "cp *.ko /lib/mdoesul/`uname -r`/other/" step? :/ Every time I try the terminal spits some line out about how there is no *.ko file..

That would copy the all the files in the current directory whose filenames end with .ko to the /lib/modules/`uname -r`/other directory. There are two files that you need for your modem to work; ltmodem.ko and ltserial.ko. The .ko part means kernel object--it is the binary code for the driver for your modem. 

You compile the source code or you use the pre-installed binary code that comes with Ubuntu, either way you have to copy the ltmodem.ko and ltserial.ko files into a directory where the kernel can pick them up when you enter in the modprobe command. The `uname -r` part gets expanded to a string that represents your current kernel release. If you type in ```
uname -r
``` you will see something like 2.6.15-23-386.

Have you tried my guide (in the post before yours?) What did you do exactly up until you entered the cp command?

---

### Post by Cloudy on 2006-07-11
I followed every step in finnish's guide, Blastus; everything worked fine until I got to that part. It said there weren't any .ko files to copy. :/ Are the .ko files in any of the packages I downloaded..?

---

### Post by Cloudy on 2006-07-12
Here's the terminal output, lots of trial & error and "file already exists", since I've done this a few times before:

> 
travis@ubuntu:~$ dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb
dpkg: requested operation requires superuser privilege
travis@ubuntu:~$ sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb
(Reading database ... 73341 files and directories currently installed.)
Preparing to replace cpp-3.4 3.4.4-6ubuntu8 (using cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Unpacking replacement cpp-3.4 ...
dpkg: error processing gcc-3.4base_3.4.4-6ubuntu8_i386.deb (--install):
 cannot access archive: No such file or directory
Preparing to replace gcc-3.4 3.4.4-6ubuntu8 (using gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Unpacking replacement gcc-3.4 ...
Setting up cpp-3.4 (3.4.4-6ubuntu8) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8) ...
Errors were encountered while processing:
 gcc-3.4base_3.4.4-6ubuntu8_i386.deb
travis@ubuntu:~$ ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
ln: cannot remove `/usr/bin/gcc': Permission denied
travis@ubuntu:~$ sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
travis@ubuntu:~$ mkdir /usr/src/modules
mkdir: cannot create directory `/usr/src/modules': File exists
travis@ubuntu:~$ cd /home
travis@ubuntu:/home$ cp ltmodem-2.6-alk-7b1.tar.gz /usr/src/modules/
cp: cannot stat `ltmodem-2.6-alk-7b1.tar.gz': No such file or directory
travis@ubuntu:/home$ sudo cp ltmodem-2.6-alk-7b1.tar.gz /usr/src/modules/
cp: cannot stat `ltmodem-2.6-alk-7b1.tar.gz': No such file or directory
travis@ubuntu:/home$ cd ~
travis@ubuntu:~$ sudo cp ltmodem-2.6-alk-7b1.tar.gz /usr/src/modules/
travis@ubuntu:~$ cd /usr/src/modules/
travis@ubuntu:/usr/src/modules$ sudo tar zxvf ltmodem-2.6-alk-7b1.tar.gz
ltmodem-2.6-alk-7c/
ltmodem-2.6-alk-7c/ltmdmobj.o-pre-8.31
ltmodem-2.6-alk-7c/lt_modem.c
ltmodem-2.6-alk-7c/linuxif.h
ltmodem-2.6-alk-7c/DEFINES
ltmodem-2.6-alk-7c/ltmdmobj.o-8.31
ltmodem-2.6-alk-7c/ltmdmobj.o
ltmodem-2.6-alk-7c/docs/
ltmodem-2.6-alk-7c/docs/ltmodem.diff
ltmodem-2.6-alk-7c/docs/patch_ltmodem_8.31b1_fix_wvdial.txt
ltmodem-2.6-alk-7c/docs/NEWS
ltmodem-2.6-alk-7c/docs/Examples.txt
ltmodem-2.6-alk-7c/docs/README_10MDK
ltmodem-2.6-alk-7c/docs/alk7b.diff
ltmodem-2.6-alk-7c/docs/udev-setup
ltmodem-2.6-alk-7c/docs/alk7b.txt
ltmodem-2.6-alk-7c/docs/patch_ltmodem_8.31b1_fix_wvdial.diff
ltmodem-2.6-alk-7c/docs/ltmodem.rules
ltmodem-2.6-alk-7c/docs/README
ltmodem-2.6-alk-7c/Makefile
ltmodem-2.6-alk-7c/serial.c
travis@ubuntu:/usr/src/modules$ cd ltmodem-2.6-alk-7c
travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo mkdir /lib/modules/`uname -r`/other/
mkdir: cannot create directory `/lib/modules/2.6.12-9-386/other/': File exists
travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo cp *.ko /lib/modules/`uname -r`/other/
cp: cannot stat `*.ko': No such file or directory
travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$


---

### Post by blastus on 2006-07-14
[quote=Cloudy]I followed every step in finnish's guide, Blastus; everything worked fine until I got to that part. It said there weren't any .ko files to copy. :/ Are the .ko files in any of the packages I downloaded..?[/quote]

Not if you are running Breezy Badger. The modules are stated as listed in one of the restricted packages, but they aren't there. So under Breezy, you have no option other than to compile the modules yourself. But before you can even do that, you need to install gcc 3.4. I wrote a [HOWTO: Install gcc-3.4 via apt-get without an Internet connection](http://www.ubuntuforums.org/showthread.php?t=79896) to explain the problem and provide a solution.

Alternatively, if you take a look at Post #20 of my other thread [breezy badger - cannot compile Lucent modem drivers](http://www.ubuntuforums.org/showthread.php?t=77537&page=2), the modules are attached to the post and you can download them and use them. They will work with the default kernel that Breezy comes with. Once you get an Internet connection with them, you can then install gcc 3.4 via apt-get, so that if you upgrade your kernel you can recompile the modules if you need to (i.e. if they aren't in the restricted packages.)

It is possible to get the modem to work under Breezy, it's just a lot harder than Dapper that's all. I would just upgrade to Dapper if I were you and then follow my guide [HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)](http://www.ubuntuforums.org/showthread.php?t=198730). You may find it a lot easier, since there's quite a few concepts you need to be familiar with to diagnose these kinds of problems.

---

### Post by Cloudy on 2006-07-15
Actually, Blastus, I think I know what I did wrong - I forgot the make bit before the 2nd mkdir command. :oops:

---

### Post by Cloudy on 2006-07-16
OK.. maybe I was wrong. :/

> 
travis@ubuntu:~$ sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb
(Reading database ... 73341 files and directories currently installed.)
Preparing to replace cpp-3.4 3.4.4-6ubuntu8 (using cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Unpacking replacement cpp-3.4 ...
Preparing to replace gcc-3.4-base 3.4.4-6ubuntu8 (using gcc-3.4-base_3.4.4-6ubuntu8_i386.deb) ...
Unpacking replacement gcc-3.4-base ...
Preparing to replace gcc-3.4 3.4.4-6ubuntu8 (using gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Unpacking replacement gcc-3.4 ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8) ...
travis@ubuntu:~$ sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc travis@ubuntu:~$ sudo cp ltmodem-2.6-alk-7b1.tar.gz /usr/src/modules/ travis@ubuntu:~$ cd /usr/src/modules/ travis@ubuntu:/usr/src/modules$ sudo tar zxvf ltmodem-2.6-alk-7b1.tar.gz ltmodem-2.6-alk-7c/
ltmodem-2.6-alk-7c/ltmdmobj.o-pre-8.31
ltmodem-2.6-alk-7c/lt_modem.c
ltmodem-2.6-alk-7c/linuxif.h
ltmodem-2.6-alk-7c/DEFINES
ltmodem-2.6-alk-7c/ltmdmobj.o-8.31
ltmodem-2.6-alk-7c/ltmdmobj.o
ltmodem-2.6-alk-7c/docs/
ltmodem-2.6-alk-7c/docs/ltmodem.diff
ltmodem-2.6-alk-7c/docs/patch_ltmodem_8.31b1_fix_wvdial.txt
ltmodem-2.6-alk-7c/docs/NEWS
ltmodem-2.6-alk-7c/docs/Examples.txt
ltmodem-2.6-alk-7c/docs/README_10MDK
ltmodem-2.6-alk-7c/docs/alk7b.diff
ltmodem-2.6-alk-7c/docs/udev-setup
ltmodem-2.6-alk-7c/docs/alk7b.txt
ltmodem-2.6-alk-7c/docs/patch_ltmodem_8.31b1_fix_wvdial.diff
ltmodem-2.6-alk-7c/docs/ltmodem.rules
ltmodem-2.6-alk-7c/docs/README
ltmodem-2.6-alk-7c/Makefile
ltmodem-2.6-alk-7c/serial.c
travis@ubuntu:/usr/src/modules$ cd ltmodem-2.6-alk-7c travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$ make make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/ltmodem-2.6-alk-7c modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/modules/ltmodem-2.6-alk-7c/.ltmdmobj.o.cmd for /usr/src/modules/ltmodem-2.6-alk-7c/ltmdmobj.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$ sudo cp *.ko /lib/modules/`uname -r`/other/ travis@ubuntu:/usr/src/modules/ltmodem-2.6-alk-7c$ cd /lib/modules/`uname -r`/other/
travis@ubuntu:/lib/modules/2.6.12-9-386/other$ sudo depmod -a
travis@ubuntu:/lib/modules/2.6.12-9-386/other$ sudo modprobe ltserial
travis@ubuntu:/lib/modules/2.6.12-9-386/other$ sudo pppconfig
travis@ubuntu:/lib/modules/2.6.12-9-386/other$ pon
travis@ubuntu:/lib/modules/2.6.12-9-386/other$ sudo ln -sf /dev/ttyLTM0 /dev/modem


At first, it wasn't dialing at all. 
Then, I configured wvdial and now it dials, finishes dialing, and when I open Firefox and type in an address it says that it can't be found and starts dialing again.

:S

---

### Post by blastus on 2006-07-16
> **Cloudy said:**
> At first, it wasn't dialing at all. Then, I configured wvdial and now it dials, finishes dialing, and when I open Firefox and type in an address it says that it can't be found and starts dialing again.

:S

What is the output from wvdial?

---

### Post by Cloudy on 2006-07-16
Off the top of my head - "bad init string". I added X3 to init2 but after I got the "bad init string" message I deleted X3 and saved the wvdial.conf file again. 

I'll get the exact output in a few minutes

EDIT:
It says that the password & username provided aren't valid?, however, when I sudo nano the wvdial.conf file I get this:

[IMG]http://img231.imageshack.us/img231/884/wvdialconfkr3.png[/IMG]

So there *IS* a username and password.. and it should be valid?

EDIT NUMERO DOS:
I should have been more specific; I was actually dialing using pon, but it will do the same thing sometimes when I try to use wvdial despite the password/username ordeal..

---

### Post by blastus on 2006-07-16
You have to create /etc/wvdial.conf with ```
sudo wvdialconf /etc/wvdial.conf
``` Then you have to put in your ISPs phone number, username, and password--removing the semicolons from the start of the relevant lines. Take out the semicolons from the last three lines. Every line in the file should be of the form```
propertyname = propertyvalue
```

---

### Post by Cloudy on 2006-07-16
Again - I feel like kicking myself because I'm not specific enough. I have an /etc/wvdial.conf file, but I /just/ realized what was wrong with it - I left the semicolons in. >.<

---

### Post by blastus on 2006-07-16
> **Cloudy said:**
> Again - I feel like kicking myself because I'm not specific enough. I have an /etc/wvdial.conf file, but I /just/ realized what was wrong with it - I left the semicolons in. >.<

I think everyone gets tripped up on the semicolons in /etc/wvdial.conf the first time. I know I did. ;)

---

### Post by favad on 2006-08-16
Sorry for this repeated post.

favad

---

### Post by favad on 2006-08-16
I upgraded to Ubuntu 6.06, although it installed the drivers itself but things do not work out correctly. the modem disconnected within seconds or probably just dialed and never got connected. I tried 2 different ISPs and they worked on my WIN XP 5 minutes later. I think I need to decrease the modem speed which is causing connection to break and not establish on my slow telephone line (I'll try this sudo wvdialconf /etc/wvdial.conf). Unlike Win XP Ubuntu dialer doesn't give the error messages, so it is difficult to trace the exact error.
My previous drivers were ltmodem-2.6.12-9-386_8.26b1_i386.deb which worked erronously in Ubuntu 5.10. Now I need them for kernel 2.6.15-23-386.

In case there is a problem with my dialer, could u please also tell me where to download it in Win XP and how to install in Ubuntu 6.06.

I did read through this thread but couldn't exactly find a solution to my kernel 2.6.15-23-386, although some of the problems were quiet similar. I'll be extremely thankful if someone could help me connect to the internet again.:sad:

---

### Post by blastus on 2006-08-17
You may want to try this guide: [HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)](http://www.ubuntuforums.org/showthread.php?t=198730)

---

