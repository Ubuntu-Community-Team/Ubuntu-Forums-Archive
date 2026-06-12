---
title: "Want to turn on and send files to a laptop via a ethernet cable"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by cgameing on 2015-01-14
So I want to turn on and send files to a laptop via a ethernet cable in ubuntu 14.04lts

and vicer versa

So basicly i want to turn on my desktop pc play some games or whatever and then turn it off. As it turns off it will send all the data to my laptop. 
Once my desktop is turned off i can take my laptop somewhere and i will have my data on it. Then when i get home i can open up the terminal type a command and it sends all the files back to my desktop.

I tried using wakeonlan but i dident know what do to if it was for the client or the server. I think i can use wakeonlan though, both devices seem to be able to. So a quick tutorial for what to do for both pc's would be helpful.
And anyhelp to connect both pc's via ethernet and send files would also be nice.

Thanks for any help/advice. :p

---

### Post by Hadaka on 2015-01-14
Hi, wake on lan is not really designed to do
what you are wanting, ssh is,,here is an easy
tutorial to get you started,
[https://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/](https://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/)
*also be sure to check **share desktop with others...on both machines,
DASH>>DESKTOP>>(ALLOW OTHERS TO VIEW).
Like anything new it will seem a bit confusing at frist, its really quite simple.
your ability to send data between the two can be done via automated script files
or manually.
have fun !

---

### Post by tgalati4 on 2015-01-14
*rsync* is helpful for keeping files syncronized between several machines.  There are lots of tutorials of how to use *rsync*.  You could write a cronjob (a script that executes a given time) on both machines.  This method works best when you have one machine running 24/7, as in a file server or network-attached-storage (NAS).  Trying to get both the laptop and desktop syncronized without a 3rd machine as a dedicated file server is tricky.

Some folks use an online service such as Dropbox or Google Drive as a dedicated file server to keep files up-to-date on all machines on the local network.

---

### Post by cgameing on 2015-01-14
I wasnt asking wakeonlan to send files. I just wanted wakeonlan to turn on my laptop when i turn on my desktop.
il look into ssh and rsync.

I cant use dropbox or google drive because i need to access files on the go and without a internet connection

Thanks for help

---

### Post by cgameing on 2015-01-19
il get a tutorial for anyone who wants to duplicate this soon

(Work in progress)

First you need to install rsync
sudo apt-get -f install rsync

---

