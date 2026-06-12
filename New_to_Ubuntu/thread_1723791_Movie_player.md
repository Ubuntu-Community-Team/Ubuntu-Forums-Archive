---
title: "Movie player"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by tashimee on 2011-04-07
:(Help! I'm trying to watch a dvd, and when I try to run it in the movie player it says: can't read from resource. Am I doing something wrong?

---

### Post by jmszr on 2011-04-07
tashimi,  

You need to add some codecs:

```
sudo apt-get install ubuntu-restricted-extras
```

and:
```
sudo apt-get install libdvdread4
```

and:
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

re: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You may need to reboot afterwards.

Also, I would suggest trying VLC or SMPlayer.

---

### Post by tashimee on 2011-04-07
I already tried that.

---

### Post by Anuovis on 2011-04-07
Try installing Ubuntu Restricted Extras from the Software Center. It's a bunch of packages for all sorts of proprietary formats.

You could also try VLC player which can play almost anything. 

If these things fail, there might be a problem with a DVD or something with your system. You could test several disks to see if the issue remains.

---

### Post by tashimee on 2011-04-07
:(Do I need to get a newer dvd drive? I have two dvd drives, one is really old (hp dvd writer dvd300i), and the other is pioneer sata drive I bought in 2009. Ubuntu recognizes that there is a disk in the hp, but when I put a dvd in the pioneer, it makes funny sounds and nothing shows up on the screen.

---

### Post by tashimee on 2011-04-07
I loaded RealPlayer.

---

### Post by tashimee on 2011-04-07
I installed libdvdread4.

---

### Post by tashimee on 2011-04-07
:popcorn:I installed the VLC player and it woks great. Thank you for all your help!!!:lolflag:

---

### Post by Anuovis on 2011-04-07
Happy watching.
You should mark this thread as *Solved* from the *Thread Tools*.

---

