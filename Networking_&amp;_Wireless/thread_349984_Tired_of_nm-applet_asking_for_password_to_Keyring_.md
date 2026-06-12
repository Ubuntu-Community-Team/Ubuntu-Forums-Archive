---
title: "Tired of nm-applet asking for password to Keyring? 2"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by manic007 on 2007-01-31
Appologise for effectively ripping off a previous post, namely this one:

[http://ubuntuforums.org/showthread.php?t=187874&page=9&highlight=nm-applet]("http://ubuntuforums.org/showthread.php?t=187874&page=9&highlight=nm-applet")

It's a great guide and all credit to s31523 for putting it up. But I felt the installation instructions could be a bit easier to understand for newbies and since that soddin nm-applet password is the undisputed Clippet(TM) of the Ubuntu World I thought I'd post [hopefully] easier to use instructions. I've taken all the information from the above post and condensed it here. I'm assuming that people use the keyring manager mainly for their wifi connection (but the instructions should be the same for other apps). Before you begin its important to know that this procedure won't work if you have autologin enabled for your computer (i.e. in gdm). Lets begin!

1) Make sure your password for nm-applet is the same as your username. You can do this by deleting the hidden file found in /home/<you_username>/.gnome2/keyrings Note however you will LOOSE all your current passwords. So make sure you know them all before doing this!

2)Open an application you know to use the gnome keyring (i.e. Network Manager, you may have to disconnect it first, then enable it). Follow the instruction for your app, when that's done a second dialog box will appear and asks you to "Create Default Keyring" make sure the password you enter is the same as your login password. Very important.

3)Restart computer to make sure it [still] asks you for your keyring password.

4)Go to Synaptic Manager and make sure you have these packages installed:

build-essential
checkinstall
auto-apt

5) Open a terminal and type this:
```
wget www.hekanetworks.com/opensource/pam_keyring/pam_keyring-0.0.8.tar.gz 
```

```
tar -xvzf pam_keyring-0.0.8.tar.gz 
```

```
 cd pam_keyring-0.0.8 
```

```
sudo auto-apt run ./configure --prefix=/usr --libdir=/lib
```

```
make
```

```
sudo checkinstall
```

A quick explanation of whats going on. Auto-apt is a neat little program that will try to find all dependencies needed by a source file, and install them! Great news for the newbie! More info click [ here ]("https://help.ubuntu.com/community/AutoApt"). Checkinstall (click [ here]("https://help.ubuntu.com/community/CheckInstall")) is another super program, it converts simple source files into .deb packages and installs them. You can then use Synaptic/apt-get/dpkg to uninstall it later on. Isn't Linux getting easier by the second? :)

6) Finally you'll need to edit one file. Type this in the console to open it:

```
sudo gedit /etc/pam.d/gdm
```

The file should be edited so it looks a bit like this, the last two lines are the one which do the magic, so make sure they're included:
```
#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```

7) Reboot your computer and it should no longer ask you for your keyring password. :guitar:

---

### Post by Fitzcarraldo on 2007-03-08
> **manic007 said:**
> 

1) Make sure your password for nm-applet is the same as your username.



username or password? I've read elsewhere that the password of the default keyring of Gnome Keyring Manager has to be the same as the user's ubuntu *password*.

---

### Post by Toddy on 2007-03-08
Are these instructions Edgy specific, or will they work for Feisty too?

---

### Post by malixor on 2007-03-10
You need more packages before installing the pam-keyring.

sudo apt-get install libtool
sudo apt-get install libpam-dev
sudo apt-get install libgnome-keyring-dev
sudo apt-get install libglib2.0-dev

Instead of "make" I had to do "sudo make" then everything worked.

cheers,
malixor

---

### Post by victorbrca on 2007-03-14
I ran 

```
sudo auto-apt run ./configure --prefix=/usr --libdir=/lib
```

And I got a bunch of errors right after it asked to me y/n/d for many selinux options (really a lot). 


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  perl-tk
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 2671kB of archives.
After unpacking 10.1MB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com edgy/universe perl-tk 1:804.027-5 [2671kB]
Fetched 2671kB in 26s (102kB/s)                                                
Selecting previously deselected package perl-tk.
(Reading database ... 122784 files and directories currently installed.)
Unpacking perl-tk (from .../perl-tk_1%3a804.027-5_i386.deb) ...
Setting up selinux-policy-default (1.26-7) ...
cat: /selinux/policyvers: No such file or directory
Building policy.conf ...
Compiling policy ...
policyvers value 0 not in range 15-20
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-20)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Setting up perl-tk (804.027-5) ...
Errors were encountered while processing:
 selinux-policy-default
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed [Z - exec shell to fix this situation]
```



```
sh: line 1: 14508 Segmentation fault      (core dumped) sudo apt-get -y install gawk
Failed [Z - exec shell to fix this situation]

```



```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pocketpc-binutils pocketpc-gas pocketpc-sdk
The following NEW packages will be installed:
  pocketpc-binutils pocketpc-gas pocketpc-gcc pocketpc-sdk
0 upgraded, 4 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 5850kB of archives.
After unpacking 21.5MB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com edgy/universe pocketpc-binutils 2.15-2 [2157kB]
Get:2 http://ca.archive.ubuntu.com edgy/universe pocketpc-gas 2.13.2.1-1 [414kB]
Get:3 http://ca.archive.ubuntu.com edgy/universe pocketpc-sdk 1.0.0-4 [60.2kB] 
Get:4 http://ca.archive.ubuntu.com edgy/universe pocketpc-gcc 3.4.2-2 [3220kB] 
Fetched 5850kB in 39s (149kB/s)                                                
Selecting previously deselected package pocketpc-binutils.
(Reading database ... 123750 files and directories currently installed.)
Unpacking pocketpc-binutils (from .../pocketpc-binutils_2.15-2_i386.deb) ...
Selecting previously deselected package pocketpc-gas.
Unpacking pocketpc-gas (from .../pocketpc-gas_2.13.2.1-1_i386.deb) ...
Selecting previously deselected package pocketpc-sdk.
Unpacking pocketpc-sdk (from .../pocketpc-sdk_1.0.0-4_i386.deb) ...
Selecting previously deselected package pocketpc-gcc.
Unpacking pocketpc-gcc (from .../pocketpc-gcc_3.4.2-2_i386.deb) ...
Setting up selinux-policy-default (1.26-7) ...
cat: /selinux/policyvers: No such file or directory
Compiling policy ...
policyvers value 0 not in range 15-20
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-20)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Setting up pocketpc-binutils (2.15-2) ...
Setting up pocketpc-gas (2.13.2.1-1) ...
Setting up pocketpc-sdk (1.0.0-4) ...
Setting up pocketpc-gcc (3.4.2-2) ...
Errors were encountered while processing:
 selinux-policy-default
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed [Z - exec shell to fix this situation]

```



```
sh: line 1: 16751 Segmentation fault      (core dumped) sudo apt-get -y install g77
Failed [Z - exec shell to fix this situation]

```



```
sh: line 1: 16795 Segmentation fault      (core dumped) sudo apt-get -y install kdelibs-data
Failed [Z - exec shell to fix this situation]

```



```
sh: line 1: 16791 Segmentation fault      (core dumped) sudo apt-get -y install fort77
Failed [Z - exec shell to fix this situation]

```



```
sh: line 1: 16845 Segmentation fault      (core dumped) sudo apt-get -y install gfortran
Failed [Z - exec shell to fix this situation]

```



Thanks,


Vic.

---

### Post by victorbrca on 2007-04-02
**SOLVED**

[**_Source_**]("http://ubuntuforums.org/showthread.php?t=343280")

> Run

dpkg --purge selinux-policy-default

to get rid of the broken selinux-policy-default package.

Maybe request the removal of the package from Ubuntu, and try to get some people together to start working on a decent SELinux support in Ubuntu. AFAICT it's pretty much nonexistent.

---

### Post by NotExcessive on 2007-04-05
I've implemented all of this with no errors, but when it logs me in, nm still asks me for my password. Clues? I'm using 6.10.

---

### Post by karhulitos on 2007-04-21
> **Toddy said:**
> Are these instructions Edgy specific, or will they work for Feisty too?

I just upgraded to Feisty yesterday and did this this way:
- installed libpam-keyring from Synaptic
- sudo gedit /etc/pam.d/gdm and added instructed lines
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
- (my wep key was already in default keyring)

and no longer keyring questions after logging in! Thanks for this thread. I was about bolt the key in interfaces file (never used network manager before).

---

