---
title: "deb package error-PLEASE HELP!"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by phoenixfire900 on 2010-01-06
I get an error when i try to install gdm 2.20 deb package and i wish to install it so i can downgrade the gdm.

---

### Post by Muttley99 on 2010-01-06
> **phoenixfire900 said:**
> I get an error when i try to install gdm 2.20 deb package and i wish to install it so i can downgrade the gdm.

what does the error say?

---

### Post by Buuntu on 2010-01-06
Can you post the error message?

Just in case you haven't done it already, try installing it in the terminal.
```
sudo apt-get install gdm-2.20
```Then post the error messages here.

(Things you could try in the meanwhile):
```
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by blazemore on 2010-01-06
[http://ubuntuforums.org/showthread.php?t=1374311](http://ubuntuforums.org/showthread.php?t=1374311)

---

### Post by phoenixfire900 on 2010-01-06
this is the error-  Error: A later version is already installed

---

### Post by Buuntu on 2010-01-06
Drop down to a virtual console, (<Ctrl> + <Alt> + <F2>).

Then you want to uninstall the latest version of gdm and re-install the older version.  To do so run this:
```
sudo apt-get remove gdm
sudo apt-get install gdm-2.20
```

---

### Post by phoenixfire900 on 2010-01-06
i did this and continued with 
[INDENT]cd /etc/gdm
 sudo sed ’s|X11R6/||’ gdm.conf >/tmp/gdm.conf
 sudo mv /tmp/gdm.conf .


when i did though the command prompt gave me errors it said no server was enable and the login screen was disabled


[/INDENT]

---

### Post by Buuntu on 2010-01-06
Did you try,
```
sudo start gdm 
```
after installing it?

---

### Post by phoenixfire900 on 2010-01-06
when i did

 sudo mv /tmp/gdm.conf .

it said no such file or directory

---

### Post by Buuntu on 2010-01-06
Did you run the above command?  It said no file or directory because you uninstalled it before copying over the .conf (if that is what you are trying to do... could you elaborate more on why you are running those commands?).  Anyways, I don't think there is much configuring that could have happened and should be very simple to replace, sorry for not giving you the heads up on that :(.  Still need to know what happens when you run 'sudo start gdm' once you've installed gdm-2.20.

---

### Post by phoenixfire900 on 2010-01-06
im trying to follow this:

[http://ubuntuforums.org/showthread.php?t=1331457](http://ubuntuforums.org/showthread.php?t=1331457)

and when i run those commands it says no file or directory found

---

### Post by Buuntu on 2010-01-06
Oh, it seems you have to manually edit gdm.conf for 2.20 to work in Karmic.  Anyways, try running this:
```
cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin
```After that, run 'sudo reboot' and see if things work once your system restarts.

---

### Post by phoenixfire900 on 2010-01-06
i did and when it rebooted i got 

screen init failed

---

### Post by Buuntu on 2010-01-06
And you have gdm-2.20 installed? Hmm... I don't know what I can do from here except to reinstall regular gdm and re-try the steps from here if you'd like: [http://ubuntuforums.org/showthread.php?t=1331457](http://ubuntuforums.org/showthread.php?t=1331457)

---

### Post by phoenixfire900 on 2010-01-06
i tried again and the same thing could you re-direct me to someone who might know? thanks so much for your help by the way

---

### Post by Buuntu on 2010-01-07
This might get a bit more in depth so I would recommend going to one of the channels on IRC.  A couple that you might find some help on are:
#ubuntu at freenode.net
#ubuntu-beginners-help at freenode.net

If you don't have an IRC client, I recommend either XChat or Pidgin, both of which are in the repositories.

---

### Post by Buuntu on 2010-01-07
Are you sure you followed the instructions EXACTLY from this thread (not the link from the thread, but the thread itself)? [http://ubuntuforums.org/showthread.php?t=1331457](http://ubuntuforums.org/showthread.php?t=1331457)

Just that I just tried it in a virtual machine and it worked flawlessly.  Try using "Method #2", that is the one I tried...

---

### Post by phoenixfire900 on 2010-01-07
i will try again

---

### Post by phoenixfire900 on 2010-01-08
I tried it again and I got the same thing.  

this time it said no usable theme for screen resolution 

then under it it said screen init failed

---

### Post by Buuntu on 2010-01-08
Well, in that case it looks like the error isn't gdm but has to do with the way your screen is configured.  Sorry, I can't help you any more, you might want to stick with the newer gdm for now until someone can help you.

---

### Post by ack47 on 2010-01-08
did you get answer on problem of how to manually fix manual sudo dpkg configure a, i am having the same problem

---

### Post by phoenixfire900 on 2010-01-08
no i didnt

---

### Post by phoenixfire900 on 2010-01-08
can anyone help me?

---

