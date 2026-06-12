---
title: "Update Problem"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Jayzee23 on 2010-05-08
I recently bought an asus eee pc 701 with ubuntu 9.04 in it. Now i tried to upgrade it to 9.10 and a few was installed and some was not because an error has occured it says that i dont have enough disk space. Now i cant connect through the internet because i think that the Network Manager is not installed due to the lack of disk space The Network Applet says NetworkManager is not running. some problems that i am also having is that when i click on the trash it opens then closes immediately, then my icons disappears.

PLEASE HELP ME!!!
ANY HELP WILL BE APPRECIATED!!!
THANKS!!!

---

### Post by Sealbhach on 2010-05-08
Cleaning out old packages might give you more disk space:

```
sudo apt-get clean
```

Booting into recovery mode should give you an option to do that as well.

You should still be able to connect to the internet with a wired connection, even if you don't have network manager installed.

See [these links]("http://www.google.co.uk/#hl=en&safe=off&q=+site:ubuntuforums.org+connect+to+internet+without+network+manager&ei=IijmS8yxNYru0gTGz8CiAg&sa=X&oi=forum_cluster&resnum=1&ct=more-results&ved=0CCEQrQIwAA&fp=5aee61a2088141ec") too if you can't get access to a wired connection.
.

---

### Post by Jayzee23 on 2010-05-08
Hi i tried to write sudo apt-get clean on terminal and it say sudo: unable to resolve host (none), [sudo] password for owner:

---

### Post by Sealbhach on 2010-05-08
> **Jayzee23 said:**
> Hi i tried to write sudo apt-get clean on terminal and it say sudo: unable to resolve host (none), [sudo] password for owner:

Sounds a bit broken, what happens when you enter your normal password?

.

---

### Post by Jayzee23 on 2010-05-08
It wont let me type anything thou. I dont think its broken thou because  i was using it fine with 9.04 just today but then i updated on update manager for 9.10 but since i dont have enough disk space it did not finish the whole update.

---

### Post by Sealbhach on 2010-05-08
> **Jayzee23 said:**
> It wont let me type anything thou. I dont think its broken thou because  i was using it fine with 9.04 just today but then i updated on update manager for 9.10 but since i dont have enough disk space it did not finish the whole update.

It just hides the password, it will accept your commands.

.

---

### Post by Jayzee23 on 2010-05-09
Do you know any way to fix it please let me know.
and Thank You for Replying on the post!!

---

### Post by Sealbhach on 2010-05-09
The best thing is to get a wired connection, so that you can install network-manger, are you able to do that?

.

---

### Post by Jayzee23 on 2010-05-09
Nope. Every time i connect my wire nothing comes up.

---

### Post by Sealbhach on 2010-05-09
> **Jayzee23 said:**
> Nope. Every time i connect my wire nothing comes up.

You seem to find this a bit too difficult, maybe you could find a Linux User Group near you and bring the netbook in to them so they can fix it for you?

If you want to continue trying to fix it yourself, please open a terminal (while you have the wired connection available) and run

```
sudo apt-get update
```
```
sudo apt-get install network-manager-gnome
```

You will need to enter your password for these commands.

If you get some reply from the terminal, please copy and paste it here.


.

---

