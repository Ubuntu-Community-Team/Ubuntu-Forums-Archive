---
title: "Gedit"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by seandude on 2009-09-03
I was following the directions on a website on how to swap memory.  I've used the[FONT=Comic Sans MS] [FONT=Courier New]gedit[/FONT][/FONT] [FONT=Verdana]command before, but never thought anything was wrong.   This time, I used it, and got what I always did before, a blank window.  According to the website, I should be getting a folder with info on it.  What should be happening?  If something's wrong, how do i fix it?

Also, this is the website I was on, with the directions I was following.

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)
[/FONT]

---

### Post by drs305 on 2009-09-03
Normally when you get an empty file and you were expecting text it is because you typed the address incorrectly (perhaps *sysct**r**l.conf*). If gedit doesn't find the file you were looking for, it will create an empty one with the same name (the addresses would be different).

So either make sure you are entering the correct entry in terminal, or open gedit and browse to the location.

By the way, the command in the link for opening gedit with admin rights is not correct. Rather than *sudo*, you should use *gksudo* for graphical applications.

Looking at the link, I think what you want to run is:
```
gksudo gedit /etc/sysctl.conf

```

Here is a link on why we use "gksudo":
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by seandude on 2009-09-03
OOOOOKKKKAAAYYY that makes so much more sence.  I kept trying to use gksudo in nautilus, thinking that was the gui use that all the tutorials had talked about.  Thank you.

---

### Post by kansasnoob on 2009-09-03
> **seandude said:**
> I was following the directions on a website on how to swap memory.  I've used the[FONT=Comic Sans MS] [FONT=Courier New]gedit[/FONT][/FONT] [FONT=Verdana]command before, but never thought anything was wrong.   This time, I used it, and got what I always did before, a blank window.  According to the website, I should be getting a folder with info on it.  What should be happening?  If something's wrong, how do i fix it?

Also, this is the website I was on, with the directions I was following.

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)
[/FONT]


IMHO I get the sense that that's a very old article. At any rate it's horribly written!

They say, "One bottleneck of Linux the use of swap file", which is factually wrong now! A SWAP partition and a SWAP file are two very different things!

They use sudo where they should be using gksudo!

IMHO: The whole article is garbage!

---

### Post by seandude on 2009-09-03
> **kansasnoob said:**
> 

The whole article is garbage!

Do you have a suggestion as to where I should look for stuff like that?  Or any pointers as to how to avoid terribly written articles?  Bear in mind that I've only been using ubuntu for a month, and am only at basics.

---

### Post by kansasnoob on 2009-09-03
I'd ask questions here.

Why are you wanting to play with swappiness?

What version of Ubuntu are you running?

```
cat /etc/issue
```

What's the partition layout?

```
sudo fdisk -l
```

Regarding swap/memory:

```
cat /proc/meminfo
```

But most importantly what isn't working the way you want it to?

---

### Post by oldos2er on 2009-09-03
> **seandude said:**
> Do you have a suggestion as to where I should look for stuff like that?  Or any pointers as to how to avoid terribly written articles?  Bear in mind that I've only been using ubuntu for a month, and am only at basics.

 Stick with the community contributed help, or the official help: [https://help.ubuntu.com/](https://help.ubuntu.com/)

 You still may want to check here on the forums before running unfamiliar commands.

---

