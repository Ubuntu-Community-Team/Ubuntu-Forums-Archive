---
title: "[SOLVED] Cant install google Earth"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by carrcollero on 2008-12-09
very new to Ubuntu,trying to install googleearth with command line in the terminal window. Although the google installer is downloaded and on my desktop  I get a  message file not found. This is the first time of using a command line. do you have to type the commands in one long line then hit enter, or do you hit enter after every line?

---

### Post by binbash on 2008-12-09
enter after every line (for beginners)

---

### Post by ibizatunes on 2008-12-09
Add medibuntu to your repo's

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

this a good install guide here

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

---

### Post by lametike on 2008-12-09
i though you need to cd it to the right directory(if not wrong it is to cd to HOME)(cd is change directory)maybe you can go chk step by step on the google earth documemtary,thats wat i did XD

---

### Post by MenZa on 2008-12-09
I suggest using ibizatunes' method, which will allow you to install it with your favourite package manager:

Start by adding the Medibuntu packages to your repository list:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Also, add the GPG key and update your package lists:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now the repository is added. Next up, install Google Earth:

```
sudo apt-get install googleearth
```

---

### Post by taurus on 2008-12-09
Yes, he needs to be in ~/Desktop first since I assume that is where he saved the download file.

```
cd ~/Desktop  [COLOR="Blue"][Return][/COLOR]
chmod 755 GoogleEarthLinux.bin  [COLOR="Blue"][Return][/COLOR]
./GoogelEarthLinux.bin [COLOR="Blue"] [Return][/COLOR]
```

---

### Post by carrcollero on 2008-12-10
After the first line cd~/Desktop  hit return it says no such directory? Then Displays
len@len desktop$, Help!

---

### Post by taurus on 2008-12-10
> **carrcollero said:**
> After the first line cd~/Desktop  hit return it says no such directory? Then Displays
len@len desktop$, Help!

There is a space between the cd and the ~.

```
cd      ~/Desktop
```

---

### Post by carrcollero on 2008-12-10
it worked, just one space!!!

---

### Post by thepenguinonthetelly on 2008-12-16
> **MenZa said:**
> I suggest using ibizatunes' method, which will allow you to install it with your favourite package manager:

Start by adding the Medibuntu packages to your repository list:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Also, add the GPG key and update your package lists:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now the repository is added. Next up, install Google Earth:

```
sudo apt-get install googleearth
```

OK, I did this, and it had appeared to install (it's in the menu where it should be).  However, when I click on it, I get a "no such file or directory" error.  

I had tried to install the tar.gz from their site, and it only half-installed (even worse than this), so I was hoping this would work.  How can I fix it?

---

### Post by oldos2er on 2008-12-16
Does the program run when you type "googleearth" into a terminal?

---

### Post by thepenguinonthetelly on 2008-12-16
No.  What's hanging me up is that it wants me to agree to Google's EULA, but when I tried during install (from the terminal), it wouldn't let me click on anything or hit enter.  That's why it won't finish installing, it says.

---

### Post by philinux on 2008-12-16
Try using synaptic. Edit > Fix broken packages would sort it. Or just mark it for reinstall first to see if all goes well.

---

### Post by thepenguinonthetelly on 2008-12-16
I did it several times earlier without success, but right before this post, it suddenly worked, so that's fixed.  Now I just have to figure out how to install this damn Intel driver for my card so I can view it properly.

---

### Post by oldos2er on 2008-12-16
> **thepenguinonthetelly said:**
> No.  What's hanging me up is that it wants me to agree to Google's EULA, but when I tried during install (from the terminal), it wouldn't let me click on anything or hit enter.  That's why it won't finish installing, it says.

 Use the Tab key to highlight "ok" in the eula, then hit Enter.

---

