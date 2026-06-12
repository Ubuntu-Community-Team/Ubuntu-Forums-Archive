---
title: "Configuration Server &amp; Gnome Power problem"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by eyz4eva on 2010-05-28
i encountered some problem installing ubuntu.
 
i have the log file, but i dunno where to upload it for viewing.
 
basically, i was told tat permission was denied during the installation of ubuntu in windows.
 
when i tried to install as an individual OS by booting from the CD, the installation was not successful as well, however i was able to get to the login page. but from there, i encountered problem with the configuration server and the gnome power blah blah.
 
i dunno what really went wrong.
 
can anyone advice?

---

### Post by cariboo on 2010-05-28
It sounds like your installation didn't complete. After you've logged in go to Applications->Accessories->Terminal, once the terminal is open, type:

```
sudo apt-get -f install
```

you will be asked to enter your password, it will not ber echoed back to you. Once the above command has finished, type the following command in the same terminal:

```
sudo aptitude update && sudo aptitude -y safe-upgrade
```

The first command will install any missing dependencies, and the second command will install and update anything else that is missing from your installation.

---

### Post by eyz4eva on 2010-05-29
Thanks cariboo.

I will try installing again.

But i can only install ubuntu by booting from the CD. installing within windows is not possible.

Also, if i remember correctly, i was not able to enter the desktop after entering the password. it just hang there.

is there anyway to figure out the problem by looking at the installation log?

---

### Post by eyz4eva on 2010-05-30
The log file of my Ubuntu installation is as follow,
 
[http://pastebin.com/BrUtTZP5](http://pastebin.com/BrUtTZP5)
 
Hope someone can see what and where went wrong.

---

### Post by eyz4eva on 2010-05-30
I am currently using a 64bit Win 7.
 
And the ubuntu I'd download is a 32bit.

---

### Post by eyz4eva on 2010-06-04
Anyone?

---

