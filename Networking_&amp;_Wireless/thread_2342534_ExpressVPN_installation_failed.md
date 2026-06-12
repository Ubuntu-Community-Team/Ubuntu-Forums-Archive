---
title: "ExpressVPN installation failed"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by corinja on 2016-11-07
Hello everybody, I wonder if someone could please help me.

I am trying to install ExpressVPN on ubuntu 16.10 yakkety (lubuntu flavour). I have downloaded the package but when I try to install it fails as follows:

```
corin@mia-Aspire-9420:~/Downloads$ sudo dpkg -i expressvpn_1.1.0_i386.deb 
[sudo] password for corin: 
Selecting previously unselected package expressvpn.
(Reading database ... 145783 files and directories currently installed.)
Preparing to unpack expressvpn_1.1.0_i386.deb ...
Unpacking expressvpn (1.1.0) ...
dpkg: dependency problems prevent configuration of expressvpn:
 expressvpn depends on initscripts; however:
  Package initscripts is not installed.

dpkg: error processing package expressvpn (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (231-9ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 expressvpn
```

If I try to install initscripts I get the following error:

```
corin@mia-Aspire-9420:~$ sudo apt-get install initscripts
[sudo] password for corin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package initscripts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  util-linux sysvinit-utils

E: Package 'initscripts' has no installation candidate
```

I can see ExpressVPN has installed but when I try to activate it I get an error regarding the expressvpnd daemon not running, but if I try to restart the service I get:
```

corin@mia-Aspire-9420:~/Downloads$ sudo service expressvpn restart
Failed to restart expressvpn.service: Unit expressvpn.service not found.
```

Can anyone suggest what I need to do to get ExpressVPN installed?

---

### Post by #&amp;thj^% on 2016-11-07
Hello corinja Have you installed "util-linux sysvinit-utils" as suggested by the terminal
> "However the following packages replace it:
  util-linux sysvinit-utils"
So install the needed package with:
```
sudo apt install util-linux sysvinit-utils
```
And install the "expressvpn_1.1.0_i386.deb" again.
But just one question here are you sure you are running a 32 bit OS?
To find that out...enter this in a terminal
```
uname -m
```
I run a 64 bit kernel so mine looks like this and would need to have a 64 bit .deb to install expressvpn.
```
x86_64

```
Also i found a nice Video How to that might be helpful to you here: [https://vzaar.com/videos/8360945](https://vzaar.com/videos/8360945)
Hope this is helpful for you.

---

### Post by corinja on 2016-11-08
Hi 1fallen, thanks for your reply.

Here is the result of trying to install util-linux and sysvinit-utils:
```

corin@mia-Aspire-9420:~$ sudo apt install util-linux sysvinit-utils
[sudo] password for corin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sysvinit-utils is already the newest version (2.88dsf-59.8git1).
util-linux is already the newest version (2.28.2-1ubuntu1).
The following packages were automatically installed and are no longer required:
  dkms libcuda1-304 libjansson4 libxnvctrl0 nvidia-opencl-icd-304
  nvidia-settings ocl-icd-libopencl1 pkg-config screen-resolution-extra
  xserver-xorg-legacy
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
```

I am definitely running 32bit. Result of uname -m is i686

I am going to watch that video now!

The video is just a re-iteration of what I've already done. There are clearly some dependencies missing in my installation that are required for the expressVPN install to work, I just can't figure out how to resolve them.

---

### Post by #&amp;thj^% on 2016-11-08
I'm sure you are aware I do not know what you have done or not done...So bear with me here.
Have you yet tried:
```
sudo apt-get -f install
```
Your last terminal showing states you have 4 packages that have not been upgraded. So it begs the question..are you fully upgraded?
Now if you are...And please do take this in a negative manner...just making sure all the necessary packages are installed is all...I do not know if you have these installed.
Most of the VPN Providers will need these packages also
```
sudo apt-get install openvpn network-manager network-manager-openvpn network-manager-openvpn-gnome 

```
And this also...if you wish to just get it running...Not the prettiest method but at least or should be able to get running this way.
```
sudo apt-get install openvpn easy-rsa
```

And there is this not so user friendly way of doing it. (Untill you get support from ExpressVPN Support Team) They have a Live Chat Box
Located here: [https://www.expressvpn.com/support/vpn-setup/manual-config-for-linux-with-openvpn/#collapseOne](https://www.expressvpn.com/support/vpn-setup/manual-config-for-linux-with-openvpn/#collapseOne)
And a manual method.... if you can not get the .deb installed properly
To configure OpenVPN, type: This after the above is installed and your network manager has been restarted. May I suggest a reboot for this.
```
sudo openvpn --config   ###Add a space after --config 
```
So it would now look like something along the line of this
**Note:** the space between --config and <your .ovpn file>
```
sudo openvpn --config <your .ovpn file>
``` 
Now leave the terminal open and drag one of the .ovpn files that you choose to use into the terminal and it should now automatically setup the path for you. If you install the packages i have shown you.
You will have to leave the terminal open to stay connected though...so again not the best method to use.
And to close the connection from that same terminal just use the keyboard combo of (Ctrl+c) and that will close the connection.
But i would just try and get a hold of their online support option. For the best user experience.
Good Luck.:)

---

### Post by corinja on 2016-11-09
Just to add, I did manage to get this to work using the openvpn option you described 1fallen, so thanks for your help with that.

I also heard back from ExpressVPN support who advised me to install using the option --ignore-depends=initscripts and this also succeeded in allowing me to install the client application. 

So, all working now. Thanks for your assistance.

---

### Post by #&amp;thj^% on 2016-11-09
Cool...Happy to hear this!
And thanks for posting your solution for a proper install also.
Happy Secure Browsing!:)
Regards

---

### Post by bearlake on 2016-11-09
Thanks for posting your results as to help others.

Now can you please mark this Thread as solved.

Just above your 1st post, select Thread Tools and click of solved.

---

### Post by slickymaster on 2016-11-09
*Thread moved to **Networking & Wireless**.*

---

### Post by nuakameba on 2016-12-03
> **corinja said:**
> Hello everybody, I wonder if someone could please help me.

I am trying to install ExpressVPN on ubuntu 16.10 yakkety (lubuntu flavour). I have downloaded the package but when I try to install it fails as follows:

```
corin@mia-Aspire-9420:~/Downloads$ sudo dpkg -i expressvpn_1.1.0_i386.deb 
[sudo] password for corin: 
Selecting previously unselected package expressvpn.
(Reading database ... 145783 files and directories currently installed.)
Preparing to unpack expressvpn_1.1.0_i386.deb ...
Unpacking expressvpn (1.1.0) ...
dpkg: dependency problems prevent configuration of expressvpn:
 expressvpn depends on initscripts; however:
  Package initscripts is not installed.

dpkg: error processing package expressvpn (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (231-9ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 expressvpn
```

If I try to install initscripts I get the following error:

```
corin@mia-Aspire-9420:~$ sudo apt-get install initscripts
[sudo] password for corin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package initscripts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  util-linux sysvinit-utils

E: Package 'initscripts' has no installation candidate
```

I can see ExpressVPN has installed but when I try to activate it I get an error regarding the expressvpnd daemon not running, but if I try to restart the service I get:
```

corin@mia-Aspire-9420:~/Downloads$ sudo service expressvpn restart
Failed to restart expressvpn.service: Unit expressvpn.service not found.
```

Can anyone suggest what I need to do to get ExpressVPN installed?

The solution is described above (install with the --ignore-depends=initscripts parameter), but without writing out the command - so for anyone who needs the extra help (like me), here is what worked for me: 

saturn@saturn-desktop:~/Downloads$ sudo dpkg -i --ignore-depends=initscripts expressvpn_1.1.0_amd64.deb

Installed fine and connected with no problem.

---

### Post by chaitan64arun on 2016-12-30
Worked perfectly!
> [COLOR=#000000]sudo dpkg -i --ignore-depends=initscripts expressvpn_1.1.0_amd64.deb[/COLOR]

---

### Post by markdavidoff on 2017-01-19
Thanks for this. I noticed that when I want to install any other package, apt-get sometimes stops and still complains about the unmet dependency.
To resolve this, use
> sudo nano /var/lib/dpkg/status
then find (CTRL+W) **expressvpn**
and remove initscripts from the Depends line.

It should read something like this:
> Package: expressvpn
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 24232
Maintainer: ExpressVPN Developers <release@expressvpn.com>
Architecture: i386
Version: 1.1.0
Replaces: expressvpn
Depends: init-system-helpers, iproute2
*etc....*

---

### Post by #&amp;thj^% on 2017-01-19
> **markdavidoff said:**
> Thanks for this. I noticed that when I want to install any other package, apt-get sometimes stops and still complains about the unmet dependency.
To resolve this, use

then find (CTRL+W) **expressvpn**
and remove initscripts from the Depends line.

It should read something like this:

Very Useful:) and thanks for posting it here...
Kind regards

---

