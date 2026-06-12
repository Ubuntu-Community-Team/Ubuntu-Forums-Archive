---
title: "Save"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by rwh824 on 2010-02-10
How do I save a sources list? I am completely new to Ubuntu. Is there something I'm missing because I can not find any way to save changes to my sources list.

---

### Post by switch10 on 2010-02-10
to make a backup of the "sources.list" file to /home/username/Desktop do this:

```
 cp /etc/apt/sources.list ~/Desktop/sources.list_backup 
```

it will appear on your desktop as "sources.list_backup".  you can move it to where ever you want from there

to make changes to it, you have to open it as "root", like this:

```
 gksu gedit /etc/apt/sources.list 
```

good luck.

Dave

---

### Post by coffeeaddict22 on 2010-02-10
Hi,
Welcome to Ubuntu!  

Saving sources is usually as simple as adding a source.  You'll need to have administrator access (if you're the only user set up, you've got it), and then you're away.  Open System/Administration/Software sources, and usually you're adding something on the second page.

You can do it via the terminal; for instance I keep this in a text doc and paste the lines starting with sudo into a terminal every new install I do to add medibuntu.

#medibuntu: 
#(gets the very latest versions of your packages).

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

---

### Post by Satoru-san on 2010-02-10
You probably shouldn't be editing manually if you dont know what you are doing.

However you probably did not edit it as root.

```
gksudo gedit /etc/apt/sources.list
```

or you could use command line (as I perfer)

```
sudo nano /etc/apt/sources.list
```

---

### Post by rwh824 on 2010-02-10
the reason I ask is because I've been trying to get snes to work on my ps3 all day. 
Look for the following lines:
Quote:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
Change them to look like:
Quote:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
Save the file and then run:
sudo apt-get update

This will update your repository and include all the files available in the universe.

I used this but can not figure out how to save it.

---

### Post by Cheezespread on 2010-02-10
Are you using Warty now ?

---

### Post by rwh824 on 2010-02-10
no it says imperial

---

### Post by 3rdalbum on 2010-02-10
[B]STOP!
[/B]
Do not edit the sources.list file manually. If you make a mistake editing it, then your package manager will not work until you've reversed the changes.

Ubuntu includes a GUI that allows you to do everything that the sources.list file can do, and when you go to add a repository it will check what you've typed to make sure that it won't cause problems. It's available in System > Administration > Software Sources. From the instructions you posted, all you really want to do is enable the Universe repository, which is a simple checkbox on the front page of this program.

---

