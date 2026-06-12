---
title: "natty narwhal questions"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by robgraves on 2011-04-26
i just installed ubuntu 11.04 beta 2 natty narwhal and having a few issues:

1) i tried to set up compiz for the 3d desktop cube like i had in 10.10 and now i don't have that working or the deault desktop switcher doesn't work, i can't get either functioning now, so i'm wondering if there's a way i can just reset the default settings?

2) when i have a window open, say the terminal or even compiz settings manager, everything is "hanging" off the top panel and under it, hence i can't see some of my options underneath the top bar. is there a way to free the window from the top panel?

3) Lastly, i was glad there was an option to have Ubuntu classic loaded from the login screen to give me an option other than this new interface and i used it that way for a little bit, but now whether i login on "ubuntu" or "ubuntu classic" i get the new interface, and seem to have lost the classic layout completely.  any insight?

thank you.

---

### Post by wolfen69 on 2011-04-26
Did you install 3D drivers?

---

### Post by robgraves on 2011-04-26
> **wolfen69 said:**
> Did you install 3D drivers?

yup

---

### Post by matthew.parlette on 2011-04-26
> **robgraves said:**
> 
1) i tried to set up compiz for the 3d desktop cube like i had in 10.10 and now i don't have that working or the deault desktop switcher doesn't work, i can't get either functioning now, so i'm wondering if there's a way i can just reset the default settings?


I tried the same thing this weekend. When enabling the cube, it disables the unity interface. This froze everything for me and when I booted next time, there was no interface at all.

To resolve this, I deleted the following folders in my home directory:
[INDENT].apps/compiz-1
.apps/compizconfig-1[/INDENT]


I don't understand why there was a -1 on them, you may have that or may not. By deleting this, it restored the default compiz settings, getting me back to my unity interface.

---

### Post by robgraves on 2011-04-26
> **matthew.parlette said:**
> I tried the same thing this weekend. When enabling the cube, it disables the unity interface. This froze everything for me and when I booted next time, there was no interface at all.

To resolve this, I deleted the following folders in my home directory:[INDENT].apps/compiz-1
.apps/compizconfig-1[/INDENT]
I don't understand why there was a -1 on them, you may have that or may not. By deleting this, it restored the default compiz settings, getting me back to my unity interface.

in home? i have show hidden files enabled, but i don't see those

---

### Post by matthew.parlette on 2011-04-26
> **robgraves said:**
> in home? i have show hidden files enabled, but i don't see those

Well, in /home/matt for me, so the full path was /home/matt/.apps/compiz-1. Do you have that path? If not, I'll have to dual boot to it in a bit and check out the path again for you. I'm doing it from memory now.

---

### Post by robgraves on 2011-04-26
ok, my username is robgraves, so my path is /home/robgraves/ but i still don't see those in that path, there's a .compiz folder but nothing else related

---

### Post by matthew.parlette on 2011-04-26
> **robgraves said:**
> ok, my username is robgraves, so my path is /home/robgraves/ but i still don't see those in that path, there's a .compiz folder but nothing else related

Hm, well I'm not quite sure why mine is .apps, was it an upgrade maybe from an earlier version of Ubuntu? I see my 10.04 install has a /home/matt/.compiz as well, so that may be the difference.

I think that's the folder you'd want to delete (/home/robgraves/.compiz) to restore default for compiz, maybe just renaming it would be safer just in case, so this:
```
mv /home/robgraves/.compiz /home/robgraves/.compiz-backup
```

I think you only need to logout and back in for that to take affect, but you might as well just reboot to be safe (unless someone else can chime in on that)

---

### Post by 5149.5 on 2011-04-26
My compiz folders are in ```
/home/dan/.config
```

---

### Post by beew on 2011-04-26
I got the cube working since natty alpha 2 with the help of mc4man.
[http://ubuntuforums.org/showthread.php?t=1701732](http://ubuntuforums.org/showthread.php?t=1701732)

There is a newer article about how to enable the cube in Natty.

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29]("http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29")

---

