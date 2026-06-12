---
title: "burning iso in ubuntu 7.4"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Laddumonk on 2008-12-28
I'm trying to burn the iso to do full upgrade to 8.10. I have a good iso and when i click to 'write to cd' everything comes up fine. It burned once but I did not do it slow enough and now I have the option to burn it at every speed imaginable(1x, 2x, 3x, 4x, 5x.....). This was not the case before and now none of these work at all. Please let me know what I can do to get it back to the 5 options I had before. Thanks for any help.

---

### Post by Laddumonk on 2008-12-28
anyone out there to help. any other info I can provide?

---

### Post by soloman498 on 2008-12-28
I burn all my ISO files with Brasero and have no problems .It picks the speed also.:P

---

### Post by Laddumonk on 2008-12-28
where would I find that. Very new to ubuntu here

---

### Post by taurus on 2008-12-28
It should be in Applications -> Sound & Video.

---

### Post by Laddumonk on 2008-12-28
serpentine is the only thing in there

---

### Post by logos34 on 2008-12-28
> **Laddumonk said:**
> It burned once but I did not do it slow enough and now I have the option to burn it at every speed imaginable(1x, 2x, 3x, 4x, 5x.....). This was not the case before

whoa! when did they change that?  every imaginable speed from 1x on up!  haven't used nautilus in a while...overkill options seems to me

---

### Post by Laddumonk on 2008-12-28
it's 1x to 37x. don't know why it started doing that. any ideas?

---

### Post by logos34 on 2008-12-28
I looked in gconf-editor>apps>nautilus cd-burner, but it just allows you to set the 'default' burn speed (mine's '5560' or 10x)

---

### Post by zvacet on 2008-12-28
@ **Laddumonk**

Go to the apps>accessories>terminal and type

```
gksudo gedit /etc/apt/sources.list
```

and replace 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

with 


deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Now go to the synaptic and in search box type brasero and install it.

---

