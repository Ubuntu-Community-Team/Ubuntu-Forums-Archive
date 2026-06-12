---
title: "Can't access Ubuntu after update"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by SteelCore on 2009-02-23
2 days ago, I installed 8.10 on my laptop (dual boot with xp home ed). The installation was perfect, a big jump from my previous 7.10. Even the 3d desktop effects were activated by default (without any proprietary drivers) in spite my graphic card being ATI. 
The updates download was extremely slow so I changed the server from Administration>Software Sources and downloaed a huge amount of updates. All when fine till the end when I got this
[COLOR="Red"]W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb)
  404 Not Found
W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb)
  404 Not Found
W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.1_i386.deb](http://ftp.hostrino.com/pub/ubuntu/archive/pool/main/s/sudo/sudo_1.6.9p17-1ubuntu2.1_i386.deb)
  404 Not Found[/COLOR]
I went on with installing the updates and on restart I had a new entry on top of the Grub list
Ubuntu 8.10, kernel 2.6.27-11 -generic
so I choose that but the log in screen never appeared, just a dark screen as if it was switched off although I could hear the usual drum sound.  I even logged in  but still could not see anything on the screen.

---

### Post by ptn107 on 2009-02-23
The files apt is pointing to do not exist on that server.  Boot into the old kernel to see if you can login.  When your computer starts and says 'GRUB loading please wait...', press ESC before the countdown hits zero and select an older kernel (i.e. 2.6.27-9-generic or 2.6.27-7-generic) and press enter.  You should be able to login.  If you can, go ahead and double check your /etc/apt/sources.list file:
```
sudo gedit /etc/apt/sources.list
```
I'm assuming yours looks as follows if you continue using that server: _[http://ubuntu.pastebin.com/m1b2932e2](http://ubuntu.pastebin.com/m1b2932e2)_
and if it doesn't it probably should.
Then do a:
```
sudo apt-get update && sudo apt-get upgrade
```
to try again.

---

### Post by SteelCore on 2009-02-23
Thanks for the reply but I already installed 8.10 again on the same partition. Strangly instead of a fresh new install this sort of returned me to the older version (I left a file on the Desktop and found it there again and my wireless password was also still saved.
Anyway I'm now back to 2.6.27-7 generic. I checked the sources.list as you said but it wasn't identical to your link so I ran the apt-get update/upgrade command and it is still working.
Now my main concern to get the security updates without 2.6.27-11 generic (which probably caused the problem).  Is that possible?

---

### Post by ptn107 on 2009-02-24
Yes it is possible.  Just pop open System -> Administration -> Update Manager and click 'check'.  When it shows you the list of updates you can uncheck things from that list that you do not want upgraded (such as the newer kernel).

If you have future problems with that server I suggest you use the main Ubuntu servers:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

---

### Post by SteelCore on 2009-02-24
I actually have 2 problems here  The first is that I'm not 100% sure whether my blank screen problem is caused by the newer kernel or some other update.  Second is that this is a new installation and the update list contains about 270 items.

---

