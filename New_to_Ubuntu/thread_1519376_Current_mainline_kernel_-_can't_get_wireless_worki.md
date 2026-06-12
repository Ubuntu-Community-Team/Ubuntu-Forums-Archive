---
title: "Current mainline kernel - can't get wireless working"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by anewguy on 2010-06-28
Due to hot-plug USB not working correctly in the current 10.04 kernel 2.6.32-22 generic, I had to install the current mainline kernel 2.6.35-999 generic (it's a documented bug in launchpad and the "solution" was to go to the mainline kernel).

I got the kernel installed along with the headers okay.  On the first boot my monitor shut off, so I rebooted and edited the boot line to find it has vga=789 on the line so I just deleted that and did ctrl-x to boot and that works.  Once I actually got it booted, my network manager icon shows the red "x".  It eventually came up and asked for the keyring password, but it just stays on the red "x" and never shows it trying to connect.  I clicked on the network manager and the "Enable Wireless" doesn't even show, nor does the "Wireless" networks option.  Thinking it was my driver, I started ndisgtk, deleted my existing definition, then re-added it using the same .inf and .sys files.  Ndisgtk then shows it there, but nothing in network manager for wireless.  I went through the hardware test just for the network, and it came up with a report it wanted to send to launchpad (I think basically just stating that it wasn't connected to the internet) but of course it couldn't.  I have no way to hard wire as my desktop is in the basement where I live but my router is hooked up to my brother inlaws' DSL modem upstairs in his office.

Immediately on the boot there are 2 error messages - one about some table not being found and another with something about ACPI.  Since it did boot, I figured I could go back and fix those after getting everything else running the way I need.

Anyone have any ideas why network manager doesn't even show the "Enable Wireless" option or the wireless networks option?  To me it sounds like the driver - perhaps the messages from ndiswrapper about needing some kind of config files is actually a fatal in the new kernel?  Anyone know what those config files would be called and what the contents should be?

I know this is a little beyond just an Absolute Beginner question, but I'm not that smart about Linux (see all the questions I ask!) so I was hoping I might get an explanation that is a little easier to follow by posting here.  I know it will require more than just other beginners to answer.

Thanks in advance!!

Dave ;)

---

### Post by anewguy on 2010-06-28
Okay, an update, and now I am lost.

I ran lshw -C network and it showed the wireless as unclaimed and no driver specified.  I thought "hummmm....ndisgtk said it was there", so I manually did the ndiswrapper things to remove any known devices and then install my driver again.  Ndiswrapper claims it did and shows the device.  So, I did the depmod -a followed by a modprobe ndiswrapper.  The modprobe failed, saying the ndiswrapper module wasn't found.  I did a lsmod and found no ndiswrapper there - explains why it wasn't coming up to begin with.

So, I'm stuck with the need to use ndiswrapper, but can't load the ndiswrapper module.

Does that give anyone any ideas?

Thanks again!

Dave ;)

---

### Post by anewguy on 2010-06-28
Well, since this is a new kernel, and I had to download the kernel headers, would it make sense that I need to rebuild ndiswrapper?  I find it strange that ndiswrapper runs, there just apparently isn't a kernel module file to be loaded for 2.6.35-999.

Dave ;)

---

### Post by anewguy on 2010-06-29
Anyone?

Thanks
Dave ;)

---

### Post by gzarkadas on 2010-06-29
I don't know if I will be able to help, but I noticed in the ubuntu kernel sources that I downloaded following [this guide]("http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/"), that there is an `ubuntu' directory where ubuntu additions to kernel reside. Among these is ndiswrapper too.

I think that you'll have to merge the upstream kernel sources with the ubuntu ones to get a fully functional kernel. The only thing I don't know is how to do that. You 'll have to get a git branch from [http://kernel.ubuntu.com/git](http://kernel.ubuntu.com/git) that is close to your target kernel version; perhaps  [http://kernel.ubuntu.com/git?p=abogani/ubuntu-lowlatency-maverick.git;a=summary ]("http://kernel.ubuntu.com/git?p=abogani/ubuntu-lowlatency-maverick.git;a=summary")(version is 3.6.35-6.8). Use the [Ubuntu Kernel Wiki]("https://wiki.ubuntu.com/Kernel") to find information about this and perhaps try to ask the ubuntu kernel developers for assistance.

---

### Post by anewguy on 2010-06-29
I followed this wiki:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds")

Because of this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564459]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564459")

Personally, I think it has a lot to do with some of the wierd USB device problems people have been reporting lately.

However, I'm getting nowhere.  I even put a post in the Maverick forum because I read on the net that this kernel was going to be used with Maverick.  My reception there was, should we say, less than enthusiastic.  Heck, I even offered to just be an idiot user who could install it if it would help in testing, but that part was ignored.

So, I'm doing something I wouldn't normally do, but this has really started to **** me off.  I'm closing both threads.  If I need hot-plug I'll boot Windows and wait for Ubuntu to catch up.  This basically means my external DVD/RW drive is useless in Ubuntu, and it also explains some of the problems I've had with USB flash drives not showing after I plug them in.

So, thanks for the 1 response I did get.

Marking as "solved" only because there is no "****** off, ain't going to fight it no more" option.

Sorry for being curt, but it just seems like a stupid problem that most definitely should have been caught before the kernel responsible for it causing these problems was ever released.

I realize I'm just an idiot with a bean count that looks like I know what I'm doing when in fact it is because I ask so many questions.  I just wish this one could have been answered in a simple way.

---

### Post by gzarkadas on 2010-06-29
Before giving up, follow the steps below. I am now compiling this kernel (which has full Ubuntu extensions support), so the chances are good that it will work.

1. Go to page [http://kernel.ubuntu.com/git?p=abogani/ubuntu-lowlatency-maverick.git;a=summary](http://kernel.ubuntu.com/git?p=abogani/ubuntu-lowlatency-maverick.git;a=summary) and download the `UBUNTU: Ubuntu-2.6.35-6.9 [master]' snapshot. Use the snapshot link at the rightmost part of the row.

2. Unpack the (tar.gz) archive in a directory of your choice. Make sure this directory is empty, since the compiled debs will be stored there. Say make ~/source/kernel and put the sources in a maverick subdir inside ~/source/kernel.

3. Use [this guide for lucid kernel]("http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/"). But since you are building from a snapshot and not from a git tree, you 'll skip all the git parts. To make things easy, I wrapped the sequence of needed steps in the code block below. Watch the comments for needed intermediate actions.

```

# save your self the need to repeatedly enter your password; remember to exit at the end
sudo -i

apt-get install fakeroot build-essential
apt-get install crash kexec-tools makedumpfile kernel-wedge
apt-get build-dep linux
apt-get install git-core libncurses5 libncurses5-dev

# note that I added the libdw-dev package; apparently it is needed for maverick
apt-get install libelf-dev libdw-dev asciidoc binutils-dev

# enough rooting; become ordinary again
exit

# this would be in my example cd ~/source/kernel/maverick
cd <your-snapshot-dir>

# from now on all paths are relative to this dir, so don't cd until you are ready to call dpkg

cp debian.master/config/i386/config.flavour.generic debian.master/config/i386/config.flavour.core2

fakeroot debian/rules clean
debian/rules updateconfigs
debian/rules editconfigs

cp debian.master/config/i386/config.flavour.core2 ../.

# check what the abi is and put it in two cp... commands below (in case you use another kernel).
ls debian.master/abi

cp debian.master/abi/2.6.35-6.8/i386/generic debian.master/abi/2.6.35-6.8/i386/core2
cp debian.master/abi/2.6.35-6.8/i386/generic.modules debian.master/abi/2.6.35-6.8/i386/core2.modules

# edit debian.master/etc/getabis, debian.master/rules.d/i386.mk, 
# per the guide linked above

cp debian.master/control.d/vars.generic debian.master/control.d/vars.core2

# OPTIONAL (performance tweak):
# edit Makefile (lines 233, 234) to use -O3 -mtune=native -march=native
# to become:
# HOSTCFLAGS = -Wall -Wmissing-prototypes -Wstrict-prototypes -O3 -mtune=native -march=native -fomit-frame-pointer
# HOSTCXXFLAGS = -O3 -mtune=native -march=native

# save your self the need to repeatedly enter your password; remember to exit at the end
sudo -i

fakeroot debian/rules clean
skipabi=true skipmodule=true fakeroot debian/rules binary-indep
skipabi=true skipmodule=true fakeroot debian/rules binary-perarch
skipabi=true skipmodule=true fakeroot debian/rules binary-core2

# if you get a config-check error, note down offending CONFIG_...
# and either rerun `debian/rules editconfigs' to correct them or issue
# nano debian.master/config/enforce
# and comment out the corresponding lines.
# Then rerun the last command and continue

# go one level up and install
cd ..
dpkg -i linux-headers-2.6.35-6-core2_2.6.35-6.9_i386.deb linux-headers-2.6.35-6_2.6.35-6.9_all.deb linux-image-2.6.35-6-core2_2.6.35-6.9_i386.deb

# enough rooting; become ordinary again
exit

```I don't know if this will be successful at the end, but since you have spent so much time till now, I guess you could afford to spend a little more for testing (finally) a solid case :).

---

