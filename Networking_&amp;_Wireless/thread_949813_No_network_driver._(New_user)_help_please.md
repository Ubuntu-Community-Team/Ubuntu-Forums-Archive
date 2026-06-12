---
title: "No network driver. (New user) help please"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by onikyo on 2008-10-16
Alright, I am new to linux and found a problem with the Dell Slim tower vostro 200. I have been looking and looking, guess I don't know the terminal enough yet to fix this problem with the other how-to posts. 


I am using Ubuntu 8.10 (2.6.27-4-generic)
Using lspci -nn I get info:

      Intel Corp. 82562v-2 10/100 [8086:10c0] (Rev 02)

I have a flash drive to transfer files from my mac, or windows to the ububtu computer. It's not a duel boot system I formatted windows completely off if it, so I don't have the .sys or .inf files for the driver. 

Not sure if this helps, I loaded ubuntu from a boot enabled flash drive that I made into a "live cd" is there a way to load the driver into the flash drive and reload the distro?

PS. use noob lingo please!
Thank you,
Onikyo

---

### Post by Mark_in_Hollywood on 2008-10-16
Whew! That's not much info. BUT, try this link:

[http://agileiscool.blogspot.com/2007/09/install-and-config-ubuntu-on-vostro-200.html](http://agileiscool.blogspot.com/2007/09/install-and-config-ubuntu-on-vostro-200.html)

if it doesn't work, get back here or try a new post in the Networking & Wireless forum, this site.

---

### Post by onikyo on 2008-10-16
ok what I found to do was: Listed in red
  [COLOR="Red"]  * Download e1000-7.6.5.tar.gz from [http://sourceforge.net/project/downloading.php?group_id=42302&use_mirror=internap&filename=e1000-7.6.5.tar.gz&63333463](http://sourceforge.net/project/downloading.php?group_id=42302&use_mirror=internap&filename=e1000-7.6.5.tar.gz&63333463)

    * tar xfvz e1000-7.6.5.tar.gz
    * cd e1000-7.6.5/src
    * sudo make install
    * sudo modprobe e1000

Now you should see a wired connection available.[/COLOR]

on imputing sudo make install
I get
make -c /lib/modules/2.6.27-4-generic/build SUBDIRS=/home/mike/e1000-7.6.5/src modules
make [1] :Entering directory `/usr/src/Linux-headers-2.6.27-4-generic'
make *** [Default] Error 2
then sudo modprobe e1000 does nothing that I can see.
still no network conection. 

I put the tar.gz file in the home folder,did that mess it up?

---

### Post by Mark_in_Hollywood on 2008-10-16
I'm out of ideas. I would suggest a new post in the sub-forum named: Wireless & Networking. Sorry I can't be of enough help.

---

### Post by Ayuthia on 2008-10-16
If your card really uses the e1000 driver, you might want to check the Intrepid section or post there.  2.6.27 did have a major bug with that driver and I am not for sure what the status is for it in Ubuntu.  Here is the link to Intrepid:
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

