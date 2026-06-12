---
title: "cannot access folders"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by clevechan on 2010-01-11
Hi,

I am new to Ubuntu and this forum and need help.

I installed Ubuntu recently. Along with the installation, I installed wine and internet explorer as I needed to access some sites with explorer when firefox doesn't work.

After these installations, I noticed that most of my folder disappeared. 

I try to move to root using 

sudo -s
whoami
root

ls -a

most of the folders are in blue colour. I assume those are hidden files.

I need to access on folder .les4linux
permission denied

ls: cannot access .gvfs: permission denied

sudo chmod 777 .gvfs
chmods: cannot access .gvfs: permission denied

Please help

---

### Post by HermanAB on 2010-01-11
I'm not sure what you are doing exacly, but files and directories that start with a dot are 'hidden'.

So, if my user name is johndoe and the hidden directory is in my home directory, then I would do something like this:

First get rid of that dot:
$ sudo mv /home/johndoe/.les4linux /home/johndoe/les4linux

Now ensure that the directory and everything in it is actually owned by johndoe:
$ sudo chown -R johndoe:johndoe /home/johndoe/les4linux

Now, user johndoe should be able to see and access the les4linux directory.

---

### Post by clevechan on 2010-01-11
Herman,

Thanks for your prompt reply.

I am in root:

root@myname:~#

I then key in 

ls -a

.adobe
.bash_history
.gnome2
.ies4linux

How do I find out what path .ies4linux belongs to?

---

### Post by clevechan on 2010-01-11
Ok, thank Herman, I installed realpath and executed your set of commands.. seems to work alright..

However I encounter other problems.

I am trying to make wine work for explorer. I followed some instructions on this link

[http://ubuntuforums.org/showthread.php?t=670662](http://ubuntuforums.org/showthread.php?t=670662)

To follow this link, I am supposed to 

cd ~/ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg

1st and 2nd line went well

3rd line when I try to execute the command

gedit user.reg

(gedit:2573): Gtk-WARNING ** cannot open display

I then /ies4linux/ie6# ls

dosdevices(in blue)  drive_c(in blue)  system.reg(in white)  userdef.reg(in green)  user.reg

That is what I see

Any suggestions?

---

### Post by clevechan on 2010-01-11
The reason why I am doing this is because when I installed internet explorer in wine,

The explorer seems to be ok except there is no address bar.

---

