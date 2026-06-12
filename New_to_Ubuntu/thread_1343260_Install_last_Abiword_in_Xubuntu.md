---
title: "Install last Abiword in Xubuntu?"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by juanmafreelance on 2009-12-01
Hi! I'm sorry with my english! i am spanish.

I have installed Xubuntu in a laptop very old (512 ram, 1.4ghz).

It is posible install the last version of Abiword? I try to import a .doc document, and the tables see different and bad, in Microsoft Word it is see well. It is produced by the version of AbyWord? The version is 2.6.8?

If I install the last version, it is more big? more slow?

How Can I install the last version?

Thanks!

---

### Post by Sir Jasper on 2009-12-01
Hi,

I have Xubuntu 9.04 and AbiWord 2.6.6 and it will open the only .doc file I have.

If I try to Import it into AbiWord nothing happens.

You could perhaps try opening it in Open Office writer.

My regards

---

### Post by Daniel1994 on 2009-12-01
[http://abisource.com/wiki/Install_on_Ubuntu#Easy_Install](http://abisource.com/wiki/Install_on_Ubuntu#Easy_Install)

to install the latest Abiword.

However, if this doesn't work, you should try open office.

```
sudo apt-get install openoffice.org-writer 
```

TOO LATE ;)

---

### Post by juanmafreelance on 2009-12-01
Oh Thanks.

Open Office is more big and slow than Abiword, is it true?

---

### Post by Sir Jasper on 2009-12-01
Hi,

Yes Open Office is much bigger than AbiWord.

In your current AbiWord click Help, then,  Check for Updates, then follow the Ubuntu links until you see:

 Install AbiWord

If you don't already have the Ubuntu version of AbiWord installed, use Applications, Add/Remove Programs to install it, or click here to install AbiWord automatically.

Hope this helps.

---

### Post by juanmafreelance on 2009-12-01
Oh thanks you.

One question more.

The new version of Abyword is more bigger than old? or the last version is faster than the old version?

my regards

---

### Post by wilee-nilee on 2009-12-01
Which distribution of Xububtu do you have installed? How much extra open HD space do you have?

It seems your concerned about size, Open office can be tweaked to open fast and offers much more then abiword, but abiword does have the ability to save thinks in a nonformatted way. I have both for various reasons.

---

### Post by Sir Jasper on 2009-12-01
Hi,

I do not know but it is probably a little bigger and it is most unlikely to be slower.

With 512MB of RAM you should be fine (especially with a swap file or partition), but are you low on hard drive space?

My regards

---

### Post by juanmafreelance on 2009-12-01
> **Daniel1994 said:**
> [http://abisource.com/wiki/Install_on_Ubuntu#Easy_Install](http://abisource.com/wiki/Install_on_Ubuntu#Easy_Install)

to install the latest Abiword.

However, if this doesn't work, you should try open office.

```
sudo apt-get install openoffice.org-writer 
```TOO LATE ;)

> **wilee-nilee said:**
> Which distribution of Xububtu do you have installed? How much extra open HD space do you have?

It seems your concerned about size, Open office can be tweaked to open fast and offers much more then abiword, but abiword does have the ability to save thinks in a nonformatted way. I have both for various reasons.

I have the last version of Xubuntu, i installed this two weeks ago...

---

### Post by juanmafreelance on 2009-12-01
> **Sir Jasper said:**
> Hi,

I do not know but it is probably a little bigger and it is most unlikely to be slower.

With 512MB of RAM you should be fine (especially with a swap file or partition), but are you low on hard drive space?

My regards

Now I have more than 4 GB free

---

### Post by wilee-nilee on 2009-12-01
> **juanmafreelance said:**
> Now I have more than 4 GB free

I think at this point it will help us to know what your computer specs are. How big is the HD for one, the reason is that filling up the HD will cause your computer to run slow. Only having 4 gigs open to can be problematic.
It may be that you have stuff that you don't need which can be cleaned with two terminal commands.
sudo apt-get autoremove
sudo apt-get autoclean

---

