---
title: "Modem hookup"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by bvergie on 2009-10-05
I have just installed Ubuntu 9.04. I can not get my modem working. I have tried many different instructions and I am now ready to remove program and go back to Vista.
I am sending this through my Windows mail.
my modem is a USR V.92 USB and it is on COM4. I have my DNS address, ISP ph #, the user name and it's password.
I really need step by step instructions...type slow as I am in my 60's. I live in a area that only has a extremly slow dial up. any help will be great

---

### Post by lkraemer on 2009-10-05
Welcome to Linux......Don't let your age get in the way.....I'm 61!
You're in for an exciting time....It just takes a bit to get the other OS
out of your system.  After a year you won't go back.....I'm sure.

Don't be so fast to jump ship.....There may be Sharks in the water....

If you have a USB modem it should be easy.....But first you will need to
check to see if wvdial is included in 9.04.  (wvdial should find the proper port etc....)

Plug in your USB Modem.....

In a Terminal Window type the following: (cut & paste to prevent ERRORS!)
```

sudo wvdialconf /etc/wvdial.conf
lsusb

```

Post the output of the above commands.

If wvdial isn't installed you are going to have to either have a wired
connection, or use another computer to download the packages, then
install wvdial and all dependencies.

Once wvdial is installed you will need to edit the /etc/wvdial.conf
file to add your ISP's telephone number, login & password etc.
You can edit your personal information with:
```

sudo gedit /etc/wvdial.conf

```

A good step by step guide is posted here (Posting #4)
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial)
Starting at "These work wonderful with wvdial, etc."

So, check to see if wvdial is installed, then post the outputs of the two commands.

Here are the dependencies for wvdial.
debconf(>=0.5.00) | cdebconf
libc6(>=2.7-1)
libuniconf4.4
libwvstreams4.4-base
livwvstreams4.4-extras
libxplc0.3.13
ppp(>=2.3.0)

SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER

Just use Synaptic and search for each of these (minus the (>=2.7-1 etc))
to see which ones you need to download. (The ones that are installed
will have a box beside them that is filled in with a color....
probably green......if it is like my system.....) 
You will most likely find four are missing.......


If your using Windows consider using Keryx.
[http://keryxproject.org/](http://keryxproject.org/)
It will download all the dependencies for you.
I'd suggest downloading Gnome-ppp, wvdial first.


lk

---

