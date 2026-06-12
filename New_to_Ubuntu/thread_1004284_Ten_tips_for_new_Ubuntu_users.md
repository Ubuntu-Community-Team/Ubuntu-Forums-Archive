---
title: "Ten tips for new Ubuntu users"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by catcharavind2003 on 2008-12-07
Ubuntu has become the most popular Linux distribution for new Linux users. It's easy to install, easy to use, and usually "just works." But moving to a different operating system can be confusing, no matter how well-designed it is. Here's a list of tips that might save you some time while you're getting used to Ubuntu. 
1. Getting multimedia to work 

The default Ubuntu install contains free software only, which means that it doesn't support some popular multimedia formats straight out of the box. This is inconvenient, but the Ubuntu folks have good reasons for not shipping with support for MP3, DVDs, and so forth -- including that software could cause them some legal headaches, or incur some serious fees.

Fortunately, as a user, you don't need to worry about fees (though some of the packages may not be legal due to patent restrictions or restrictions on circumventing copy protection, depending on where you live). The Ubuntu wiki has a page on restricted formats that explains how to get the packages you need. However, if you run Ubuntu on AMD64 or PowerPC hardware, you'll still be out in the cold for some of the packages, since some multimedia formats depend on proprietary software that's not available for those hardware platforms.

2. Changing the defaults 

Ubuntu comes with a number of defaults that may or may not be to your liking. For example, the default editor is set to Nano, which isn't optimal if you're used to Vim.

The easy way to change this is to use the update-alternatives program, which maintains the symbolic links under /etc/alternatives that determine the default programs for FTP, system editor, rsh, Telnet, window manager, and so forth. Look under the /etc/alternatives directory to see what programs are managed.

To change the default editor, run sudo update-alternatives --config editor. You'll see a dialog like this:


There are 3 alternatives which provide `editor'.

  Selection    Alternative
  -----------------------------------------------
        1        /usr/bin/vim
	2        /bin/ed
  *+    3        /bin/nano

Press enter to keep the default[*], or type selection number:

Just type 1 to switch to Vim. Note that on my system, I don't have Emacs or many other editors installed; if I did, the utility would offer the other editors as choices.

3. How to install packages 

Most of the application software you'll want to add to your system will be available through the Ubuntu repositories using Synaptic, Adept, or another package management tool. What if you want to install something like Opera that is available as a package for Ubuntu, but isn't in the repositories?

In that case, download the application's Debian package (.deb) and right-click on the file. At the top of the context menu, you should see an option to open the package with the GDebi package installer. GDebi will provide a description of the package, what files are included, and other details about the package. The package installer also has a Install Package button; just click that and it will install the package. Note that the package installer also checks to verify whether it can install the package -- if it has dependencies that can't be satisfied, GDebi will give an error and refuse to install it.

If you prefer to install packages at the command line, just use sudo dpkg -i packagename.deb.

4. Sudo and gksudo 

If you've used Linux for any amount of time, you might be used to running programs as root directly whenever you need to install packages, modify your system's configuration, and so on. Ubuntu employs a different model, however. The Ubuntu installer doesn't set up a root user -- a root account still exists, but it's set with a random password. Users are meant to do administration tasks using sudo and gksudo.

You probably already know how to use sudo -- just run sudo commandname . But what about running GUI apps that you want to run as root (or another user)? Simple -- use gksudo instead of sudo. For instance, if you'd like to run Ethereal as root, just pop open a run dialog box (Alt-F2) and use gksudo ethereal.

By the way, if you really must do work as root, you can use sudo su -, which will log you in as root. If you really, really want to have a root password that you know, so that you can log in as root directly (i.e., without using sudo), then run passwd when logged in as root, and set the password to whatever you want. I'd recommend using the pwgen package to create a secure password not only for root but for all your user accounts.

5. Add users to sudo 

When you set up Ubuntu, it automatically adds the first user to the sudo group, allowing that user to make changes as the super user (root) by typing in their password. However, it doesn't automatically add additional users to the sudo group. If you want to give someone else superuser privileges on your shared system, you'll have to give them sudo access.

To add new users to sudo, the easiest way is to use the usermod command. Run sudo usermod -G admin username . That's all there is to it. However, if the user is already a member of other groups, you'll want to add the -a option, like so: sudo usermod -a -G admin username .

If you prefer the GUI way of doing things, go to System -> Administration -> Users and Groups. Select the user you want to add to sudo, and click Properties. Under the User privileges tab, check the box that says "Executing system administration tasks" and you'll be all set.

6. Adding a new desktop 

Many users aren't sure what packages to add in order to run KDE or Xfce window managers on a stock Ubuntu system -- or what packages to add to run GNOME on Kubuntu or Xubuntu. You could add all of the necessary packages one at a time, but there's a much easier way to go about it.

To install all of the packages that come with one of the flavors of Ubuntu, such as Kubuntu, run apt-get install kubuntu-desktop (or edubuntu-desktop, xubuntu-desktop, or xubuntu-desktop).

If the GUI is more your style, the *desktop packages can be installed using Adept, Synaptic, or another package manager.

7. How to reconfigure X.org 

Most of the time, X.org -- that's the software that drives your video card and provides the foundation for the GUI, whether you're running GNOME, KDE, Xfce, or another window manager -- "just works" when you install Ubuntu. In fact, I'd wager that most Ubuntu users never even have to think about their video settings.

But, sometimes you need to reconfigure X.org because Ubuntu hasn't detected your video card and monitor properly, or maybe you've just purchased a shiny new video card and need to get it working with Ubuntu. Whatever the reason, it's good to know how to reconfigure X without having to edit your /etc/X11/xorg.conf by hand.

To run through the configuration, use dpkg-reconfigure xserver-xorg at the console or in a terminal window. Then you'll have a chance to specify your monitor and video card, the resolutions and color depths you want to run the server at, and so forth.

Since every setup is different, it's hard to give concrete advice for configuring X, but it's generally OK to accept the configuration defaults. Also, you'll be given a choice between Advanced, Medium, and Simple methods for giving your monitor's specifications. As a rule, it's probably best to go with Simple unless you really know what you're doing, or the Simple method doesn't work for you.

8. Log in automagically 

By default, when you boot up the computer, Ubuntu will give you a login screen before you get to your X session. From a security perspective, this is a good idea, particularly in multi-user environments or in any situation where other people have physical access to your computer. Still, many users are used to just being logged in automatically, and don't want to fuss with logging in each time they reboot their desktop.

To set this in Ubuntu, go to System -> Administration -> Login Window. You'll need to provide your password, then you'll get the Login Window Preferences window with five tabs. Choose the Security tab and click Enable Automatic Login. If you have more than one regular user, make sure to specify which user should be logged in automatically.

Again, and I can't stress this enough, this is only a good idea for home computers where only one person has access to the computer. I don't recommend this for work computers or laptop/notebook computers, when someone else might have access to the machine.

9. Compiling from source 

Ubuntu's package repository is huge, particularly when you factor in packages in the Universe and Multiverse repositories. However, many users find themselves needing to install packages from source, either because they want to use a newer package than is available in the repository, or they want to try something that's not in the Ubuntu repository at all.

If you want to install packages from source, you can use a few shortcuts to make life easier. First, you'll probably want to get the build-essential meta-package if you haven't installed any developer tools. Run sudo apt-get install build-essential; it will grab GCC, the Linux kernel headers, GNU Make, and some other packages that you'll probably need.

Next, if you're going to compile a package such as Gaim because a new version is out, you might be able to satisfy the new version's dependencies with the old version's dependencies. To do this, grab the package's build dependencies with sudo apt-get build-dep packagename . That will grab all of the development packages you need to build the package that's currently available in Ubuntu, and will probably satisfy dependencies for the new version you're compiling.

Finally, don't make install when you compile from source -- use CheckInstall instead. CheckInstall will create a Debian package and install it for you, so you can remove or upgrade the software more easily later on.

Grab CheckInstall with apt-get install checkinstall. After you've run ./configure ; make, just run sudo checkinstall and answer a few simple questions. Note that if you compile packages on AMD64, CheckInstall will select X86_64 as the architecture rather than amd64 -- which will cause the package install to fail, since Ubuntu expects amd64 as the architecture rather than X86_64.

By the way, the packages created by CheckInstall also make it easier to deploy the same package on several machines, if you happen to have several systems running Ubuntu. See Joe Barr's excellent CLI Magic feature on CheckInstall too.

10. A new kernel 

Ubuntu will install a 386 kernel for x86 machines, which probably isn't what you'd want if you've got a Pentium II or better CPU. The 386 kernel is compiled to work with just about any x86 CPU, but extensions that appear in later CPUs can give your system a boost, if they're taken advantage of. To replace the kernel, open Synaptic or Adept and search for linux-image. You'll see several choices. Pick the one that best suits your CPU -- probably the linux-image-686 package for Pentium II and later CPUs, and linux-image-k7 for later AMD processors. Note that if you're using the AMD64 line (or Intel's x86-64 CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll need to reboot. Another benefit to the 686 kernels is that they have SMP support, which is a bonus for multi-core and Intel HyperThread CPUs.

If none of the tips cover questions that you have about Ubuntu, try checking out the Ubuntu wiki, forums, and mailing lists. As a rule, the Ubuntu users are a helpful lot, and you'll usually be able to find someone who's run into the same situation that you have questions about.



source : [http://www.linux.com/feature/54945](http://www.linux.com/feature/54945)

---

### Post by nakama85 on 2008-12-07
Great tips

---

### Post by billgoldberg on 2008-12-07
Please post in the correct forum.

---

### Post by linux_tech on 2008-12-07
10 Things You Should Do Immediately After Installing Ubuntu 8.10

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

---

### Post by catcharavind2003 on 2008-12-07
> **billgoldberg said:**
> Please post in the correct forum.
i guess this forum is correct for my post...
Its "Absolute beginner talk" and i have posted something for beginners :)
If its not appropriate to post here guide me where i can post these data's :)

---

### Post by ugm6hr on 2008-12-07
Thread closed.

Post added to the Start here... sticky.

---

