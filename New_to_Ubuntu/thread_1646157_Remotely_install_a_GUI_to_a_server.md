---
title: "Remotely install a GUI to a server"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by C23 on 2010-12-15
So I ordered a linux VPS (yay me!) thinking it would come just like any other computer. Well it didn't (kill me!).
So now I have a server with Ubuntu 9.04 and complete acces to its terminal. I don't know how I'm gonna pull this off, but I need to install a desktop environment, and then install TightVNC or something of the sort for remote connection to said Linux VPS.


First things first, I tried 
```
sudo apt-get install tightvncserver
```It couldn't find the package.

Then I found out that most VPS don't come with desktop environments, back to sqaure one.

So then I tried
```
sudo apt-get install ubuntu-desktop
```It couldn't find the package.

Now I'm stuck on editing the source.list file. Now, I don't know what sources to add, but I know I need to add some. When I run
```
sudo gedit /etc/apt/sources.list
```I get "sudo: gedit: command not found"

I really need help with this. Thanks.

edit: **[COLOR=Green]PROGRESS![/COLOR]**
So I've found out ```
sudo vi /etc/apt/sources.list
``` works. But looks very confusing.

---

### Post by NCLI on 2010-12-15
Please post the output of these commands:
```
uname -a
```
```
cat /etc/apt/sources.list
```

---

### Post by C23 on 2010-12-15
```
uname -a
```
Linux vps.survivorserver.com 2.6.18-194.17.1.el5.028stab070.7 #1 SMP Fri Oct 1 14:17:14 MSD 20
10 i686 GNU/Linux

```
cat /etc/apt/sources.list
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

I actually just added the last two with vi.

---

### Post by drdos2006 on 2010-12-15
Try webmin. 
You control your server from another machine with your browser through webmin. 

On you server type :
wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.520_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.520_all.deb)

then
sudo dpkg –i webmin_1.490_all.deb

and follow onscreen instructions.

regards

---

### Post by C23 on 2010-12-15
Thanks for the help, but I got it done.
Now, I really am stuck. I'm at the desktop through VNC, but the web broswer (Firefox) doesn't have internet access, while doing stuff from the terminal does.
What should I do?

Nevermind, I learned how to do what I need through the command line.

---

