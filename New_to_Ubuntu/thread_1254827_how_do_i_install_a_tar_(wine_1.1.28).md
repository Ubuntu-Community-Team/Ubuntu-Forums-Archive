---
title: "how do i install a tar (wine 1.1.28)"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-31
hello i am trying to install wine 1.1.28 tar i extrcted it to my desktop and fooled around with it for a wile but i can't seem to figure out how to install it i looked ft there piont me in the right direction or post ho to do this thank you.

---

### Post by nhasian on 2009-08-31
do you just want to install a tar for fun or practice?  there are debs for ubuntu already built for that version of wine.  and its super easy to install too:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by NoaHall on 2009-08-31
You need to use 
```

cd /home/$USERNAME/Downloads/Wine1.1.28
./configure
make
make install

```
And install anything that make comes up with a error in.

---

### Post by zvacet on 2009-08-31
You wil find instructions [here.]("http://www.winehq.org/docs/wineusr-guide/installing-wine-source")

---

### Post by R3fr4cti0n on 2009-08-31
> **NoaHall said:**
> You need to use 
```

cd /home/$USERNAME/Downloads/Wine1.1.28
./configure
make
make install

```And install anything that make comes up with a error in.

i got this when i did that

```
julian@Abriella:~$ cd /home/$USERNAME/Downloads/Wine1.1.28
bash: cd: /home/julian/Downloads/Wine1.1.28: No such file or directory
julian@Abriella:~$ ./configure
bash: ./configure: No such file or directory
julian@Abriella:~$ make
make: *** No targets specified and no makefile found.  Stop.
julian@Abriella:~$ make install




```

---

### Post by zvacet on 2009-08-31
Did you download it at DEsktop?If you did then 

```
cd Desktop
```

To get dependencies run 

```
sudo apt-get build-dep
```

Now you can follow instructions from link I posted to you.

---

### Post by R3fr4cti0n on 2009-08-31
> **nhasian said:**
> do you just want to install a tar for fun or practice?  there are debs for ubuntu already built for that version of wine.  and its super easy to install too:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

i tried this one but when i get to:
 **[Download and save Scott Ritchie's key]("http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg")** (right click -> save as) to your desktop.  Then open the **Authentication** tab, click **import key file**, and  select the key file you just saved (*Scott Ritchie.gpg*).  It is safe to  delete this file after doing this step.


i right click and i have no option to "save as" also when i acualy click the linc it says:
Failed to Connect 
Firefox can't establish a connection to the server at wine.budgetdedicated.com


Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by NoaHall on 2009-08-31
I think the wine servers are down - they are for me, anyway. Try again tomorrow.

---

### Post by R3fr4cti0n on 2009-08-31
darn been down for a week or so now

---

### Post by Bölvaður on 2009-08-31
I do not see why you would want to compile wine (ok.. ok some programs actually randmly work tiny bit better on wine if it is compiled) but that aside I recommend that url you were given

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

*added*

just skip the step about *Download and save Scott Ritchie's key *, it will only give you an annoying announcement that you dont have a key for the wine repo (it will be annoying) so I would recommend after installing wine to keep trying to get the key.

---

### Post by R3fr4cti0n on 2009-08-31
Bo, i just want to get wine working so i can use ms Office 2007 i tried virturalbox but it did not work properly for me and i have been waiting for around a week for th e severs to come back on, if any one knows of anothe place that i can get wine 1.1.14 or higher please send linc

---

### Post by Bölvaður on 2009-08-31
> **R3fr4cti0n said:**
> if any one knows of anothe place that i can get wine 1.1.14 or higher please send linc

[http://www.getdeb.net/app/Wine]("http://www.getdeb.net/app/Wine")

but doesnt the one in the ubuntu repos work? I know it is old but is it too old for ms office to work?

---

### Post by R3fr4cti0n on 2009-08-31
THANKYOU i have been trying to get this thing working for like a week!

---

