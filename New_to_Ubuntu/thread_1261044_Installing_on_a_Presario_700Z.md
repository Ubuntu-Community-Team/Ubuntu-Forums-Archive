---
title: "Installing on a Presario 700Z"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by lavendje on 2009-09-08
I have been attempting to install Ubuntu 9.04 on my old 2001 laptop, a Presario 700Z.  The boot starts and I get to choose the language and it starts installing then it go into a constant loop of installation failed.  It repeats this over and over again.  I do not know what is preventing this from installing.  The install disc works fine on my main pc. It does not give an error code or something to check.:confused::confused:

Product: Compaq Presario 700Z 
Specifications: With 1.3-GHz AMD Athlon 4 1500+, 256MB SDRAM, 20GB hard drive, DVD drive, 14.1-inch XGA TFT display, Microsoft Windows XP Home

---

### Post by egalvan on 2009-09-08
This may be a RAM issue, a video issue or APCI issue

RAM issues can be permanently solved by adding more memory, which will speed up Ubuntu all around, and is a "Good Thing"...
It can be temporarily solved by using the Alternate Install CD,
which uses less RAM than the LiveCD.

The video/APCI issue may be solved with boot-time codes, which I don't have at hand.
Others will have to chime in.

---

### Post by lavendje on 2009-09-08
I noticed that other Presario 700 users have been able to install.  I was wondering if any of them had this problem and if so how did they get past it.  I have been looking at other threads and notice that they do not mention this problem and they do not specifically explain how they over came their problem.  It may be that I do not understand their explanations.  Can a PCMCIA card slot confuse the software and if so is it easy to overcome.  They had 128 ram and got it to work from the live cd.  Mine has more ram and a faster processor.  I get the same problem with a newer laptop an HP Pavilion.  What is an Alternate Install CD?

---

### Post by LewRockwell on 2009-09-08
unless you max the ram on that machine, you will probably not be satisfied with it's performance

.

---

### Post by lavendje on 2009-09-08
> **LewRockwell said:**
> unless you max the ram on that machine, you will probably not be satisfied with it's performance

.

That is stating the obvious.  I just want to run Ubuntu on my laptop.  Windows works fine until it gets all of its updates.  Then it bogs down and takes forever to run anything.  If I don't install any updates it runs fast enough.

---

### Post by rsiddharth on 2009-09-08
> **lavendje said:**
> I noticed that other Presario 700 users have been able to install.  I was wondering if any of them had this problem and if so how did they get past it.  I have been looking at other threads and notice that they do not mention this problem and they do not specifically explain how they over came their problem.  It may be that I do not understand their explanations.  Can a PCMCIA card slot confuse the software and if so is it easy to overcome.  They had 128 ram and got it to work from the live cd.  Mine has more ram and a faster processor.  I get the same problem with a newer laptop an HP Pavilion.  What is an Alternate Install CD?
See whether this link is helpful : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Jazzy_Jeff on 2009-09-08
I would recommend using the alternate install cd as well. That is all I use anymore. Here is a link [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate). Just make sure you get the .i386 version.

---

### Post by rsiddharth on 2009-09-08
lavendje , You may try xubuntu which is light on your Hardware . If your interested here is the link : [http://www.xubuntu.org/](http://www.xubuntu.org/) . 

The difference between ubuntu and xubuntu is that ubuntu uses Gnome Desktop Environment and xubuntu uses Xfce Desktop Environment .

---

### Post by unutbu on 2009-09-08
lavendje, this is a shot in the dark: The installer might be failing if there is an error in your partition table. Can you boot from a LiveCD, select the choice to try out the Ubuntu desktop (instead of installing), open a terminal (Applications>Accessories>Terminal) and then type
```

sudo fdisk -l
```

(note "-l" is a minus lowercase L).

Then post the output. This may reveal the problem, but then again, it might not.

---

### Post by Jazzy_Jeff on 2009-09-08
If I were installing linux on a computer with your specs I would be installing either Puppy Linux or Crunchbang Linux. They would both fly on your system.

---

### Post by lavendje on 2009-09-08
> **unutbu said:**
> lavendje, this is a shot in the dark: The installer might be failing if there is an error in your partition table. Can you boot from a LiveCD, select the choice to try out the Ubuntu desktop (instead of installing), open a terminal (Applications>Accessories>Terminal) and then type
```

sudo fdisk -l
```

(note "-l" is a minus lowercase L).

Then post the output. This may reveal the problem, but then again, it might not.

I will try that when I get home and I will let you know. Thanks

---

### Post by lavendje on 2009-09-08
> **rsiddharth said:**
> See whether this link is helpful : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Thanks for all the input.  It looks like I have a lot of different things i need to try when I get home.

---

