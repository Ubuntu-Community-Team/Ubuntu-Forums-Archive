---
title: "uninstall in terminal"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by 007casper on 2010-08-07
to install an application/software it is
sudo apt-get install libapache2-mod-perl2 libapache2-mod-python libapache2-mod-python.........

how do you uninstall in terminal?

also, if you do apt-get on an application that has been installed, does it just over writes it, or just updates it?

thank you

---

### Post by lisati on 2010-08-07
With sudo apt-get remove .....

---

### Post by Elfy on 2010-08-07
> also, if you do apt-get on an application that has been installed, does it just over writes it, or just updates it?

Reading state information... Done
*package* is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by 007casper on 2010-08-07
awesome thank you.

How do you get list of applications installed in the terminal? Just to have a quick overview...

I have been following the perfect server set up over at [how to forge]("http://howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p5")

I am a bit puzzled.  
> 
aptitude install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail

aptitude isnt same as apt-get ???

because I did aptitude install, and the terminal listed bunch of things, however, I was only able to view the end of the thread.  I followed the instructions and didnt get the same window as listed at how to forge. 

The end of the terminal was showing
> Postfix was not set up.  Start with
  cp /usr/share/postfix/main.cf.debian /etc/postfix/main.cf
.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

I figured I will try again and did apt-get remove postfix, and then I was going to install it again. It said postfix isnt found.  Then, I did apt-get install postfix.  

Reading state information... Done
postfix is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

???

---

### Post by inameiname on 2010-08-07
sudo aptitude install AND sudo apt-get install are very similar, and will, for the most part, do the very same things. BUT they are different, in which aptitude is better.

You can put the same 'install "whatever"' part over and over and it won't overwrite or anything, but it will search for any updates to the specific program, and will install them if need be.

Here's an example of the readouts using 'evolution':

```

~ $ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~ $ sudo aptitude install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done       
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done

```

AND an example for something that isn't installed:

```

~ $ sudo apt-get remove f-spot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package f-spot is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~ $ sudo aptitude remove f-spot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done       
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done 

```

As for your 'postfix' reinstall woes, did you install it another way than 'sudo apt-get install' or 'sudo aptitude install'? If so, and it's not in a repository, then after you've removed it and then try to reinstall it, it will of course say it's not found because it's not in the repositories.

---

