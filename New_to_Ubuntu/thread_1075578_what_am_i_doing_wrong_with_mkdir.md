---
title: "what am i doing wrong with mkdir"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-20
the following info was given to me by ajgreeny but i am lost i cant make the directory he says i have to: first here is his reply
 Re: backing up panel config
Your config is in ~/.gconf/apps/panel folder, so you need
Code:

cp /home/username/.gconf/apps/panel/* /media/ray/panel/

but you must make the folder /media/ray/panel first or you will get an error. If /media/ray is not owned by you sudo will be needed in front of the command. To restore the config just reverse the folder pathways shown.
okay i am having problems making the folder /media/ray/panel. what am i doing wrong see output
ray@ray-desktop:~$ sudo -i
root@ray-desktop:~# mkdir /media/ray/panel
mkdir: cannot create directory `/media/ray/panel': No such file or directory
root@ray-desktop:~# sudo mkdir /media/ray/panel
mkdir: cannot create directory `/media/ray/panel': No such file or directory
root@ray-desktop:~# sudo mkdir /media/ray/panel
mkdir: cannot create directory `/media/ray/panel': No such file or directory
root@ray-desktop:~# 



tks/cheesemaker

---

### Post by rustutzman on 2009-02-20
root@ray-desktop:~# sudo mkdir /media/ray/panel

Should be:

root@ray-desktop:~# sudo mkdir /media/ray/panel/

Notice the last forward slash.

Russ

---

### Post by taurus on 2009-02-20
How about

```
sudo mkdir /media/ray
sudo mkdir /media/ray/panel
```

Or remove the sudo if you log in as root which seems like you are!

---

### Post by Fire_Chief on 2009-02-20
Try making just /media/ray first. Then make /media/ray/panel.

This is assuming the /media directory already exists.

---

### Post by ChildOfMana on 2009-02-20
Do it one step at a time.

/media should already exist, so first you need to cd there:

```
cd /media
```

Then you need to make the *ray* directory in /media:

```
sudo mkdir ray
```

Then cd into *ray*:

```
cd ray
```

Then make the *panel* directory:

```
sudo mkdir panel
```

This is the long-winded way but will help you understand the directory structure.

---

### Post by binbash on 2009-02-20
NO wtf are you gonna do if you need to open 500 directories? are you gonna do cd mkdir cd mkdir etc?It is : 

sudo mkdir -p /media/ray/panel

It will create both ray and panel directory

---

### Post by ChildOfMana on 2009-02-20
[quote="binbash"]NO wtf are you gonna do if you need to open 500 directories?[/quote]

I did state this was the long-winded way. However, this approach helped me when I first started using Linux as it helped me understand the directory structure better.

Choice is the order of the day, and even the long-winded way is a valid choice if it helps.

Of course, it may not be what rburkartjo is after but at the end of the day they don't have to follow it. :)

---

### Post by rburkartjo on 2009-02-20
hey taurus, i think i created at least i got no error messages from terminal but cant access it????????????/ray

---

### Post by Dj Melik on 2009-02-20
```
sudo mkdir -p /media/ray/panel
```

As far as I remember "-p" creates any parent directories as well.

---

### Post by taurus on 2009-02-20
```
cd /media/ray
ls -la
```
And if you need to change the ownership of /media/ray from root to ray (your login name), then you can do

```
sudo chown -R ray:ray /media/ray
ls -la /media
```

---

### Post by rburkartjo on 2009-02-20
child what am i doing wrong just cant access
ray@ray-desktop:~$ cd /media
ray@ray-desktop:/media$ sudo mkdir ray
mkdir: cannot create directory `ray': File exists
ray@ray-desktop:/media$ cd ray
ray@ray-desktop:/media/ray$ sudo mkdir panel
mkdir: cannot create directory `panel': File exists
ray@ray-desktop:/media/ray$ 

it bites getting old brain cells must evaporate/cheesemaker

---

### Post by taurus on 2009-02-20
If you look at the messages, they said you already have /media/ray/panel.

```
ls -la /media/ray
```

---

### Post by rburkartjo on 2009-02-20
dj and taurus tks/cheesemaker

---

### Post by bodhi.zazen on 2009-02-20
> **Dj Melik said:**
> ```
sudo mkdir -p /media/ray/panel
```As far as I remember "-p" creates any parent directories as well.

> **binbash said:**
> NO wtf are you gonna do if you need to open 500 directories? are you gonna do cd mkdir cd mkdir etc?It is : 

sudo mkdir -p /media/ray/panel

It will create both ray and panel directory

I was going to post it, but I see I am too late ...

-p FTW

---

