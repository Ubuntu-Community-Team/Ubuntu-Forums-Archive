---
title: "how to reinstall firefox"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by garyed on 2009-01-14
I tried to upgrade from firefox2.0.. by running "apt-get update" & then
"apt-get install firefox" & got some errors. Ever since my internet has been running slow on only that machine & it never did upgrade my firefox.
I'm running Feisty & wired to my router. My other computers run fine on the same router. How I can do a complete flush of firefox & reinstall it like it was originally because it always worked fine or maybe upgrade it correctly?

---

### Post by indiekid97 on 2009-01-14
First off, you most likely don't need to reinstal Firefox, just flush the temp files by pressing Control+Shift+Delete, make sure to wipe the cookies!

Second, if you truly want to uninstall the Fox, you need to specify the version number, such as 
```
sudo apt-get remove firefox-2
```

As a personal preference, I highly suggest 3.0 over 2.0 :]

```
sudo apt-get install firefox-3.0
```

---

### Post by ajcham on 2009-01-14
> **indiekid97 said:**
> As a personal preference, I highly suggest 3.0 over 2.0 :]

```
sudo apt-get install firefox-3.0
```

Will that work?  I didn't think Firefox3 was in the Feisty repos.  In any case, Feisty is no longer supported, so you will not be recieving any security updates - bad idea.  I would recommend upgrading to Hardy (Gutsy is still supported, but only until April, and I'm not sure it has FF3 either).

---

### Post by garyed on 2009-01-14
> **indiekid97 said:**
> ...

As a personal preference, I highly suggest 3.0 over 2.0 :]

```
sudo apt-get install firefox-3.0
```

I didn't think that would work since I'm only running Feisty. 
I guess it can't get much worse so I'll give it a try.

---

### Post by garyed on 2009-01-14
> **ajcham said:**
> Will that work?  I didn't think Firefox3 was in the Feisty repos.  In any case, Feisty is no longer supported, so you will not be recieving any security updates - bad idea.  I would recommend upgrading to Hardy (Gutsy is still supported, but only until April, and I'm not sure it has FF3 either).

I'm a little nervous about upgrading because I don't want to lose what I've already got. I've got the 8.10 iso but I'm trying to find out how to create a separate partition & install 8.10 so I can keep my current setup & be able to have a choice in Grub for either Ubuntu version.
I'm actually running Ubuntu studio/Feisty & don't want to lose any music or setup.

---

### Post by oldsoundguy on 2009-01-14
for older iterations of Ubuntu, you can not update Firefox or anything Mozilla thru the repositories.

BUT, you can update: [http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

Keeping it up to date is simple .. just follow their instructions after you get an update notice!

And, unlike Windows, where updating Explorer CAN do some damage to your computer .. updating Firefox .. NOPE!!

---

### Post by zvacet on 2009-01-15
@ **garyed**

If you have separtate home partition you will not lose your files and settings.If you don´t have one meke it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.Runing unsupported versions is not good idea.

---

### Post by earthpigg on 2009-01-15
> **garyed said:**
> I'm trying to find out how to create a separate partition & install 8.10 so I can keep my current setup & be able to have a choice in Grub for either Ubuntu version.
I'm actually running Ubuntu studio/Feisty & don't want to lose any music or setup.

1. boot from 8.10 live cd.
2. in a terminal start 'gparted'. shrink your existing partition, make room for 8.10.
3. install 8.10 in the space you just created.
4. 8.10 will automatically pick up other versions of ubuntu and put them on grub (ive done this myself - 8.10 picked up 8.04 and added it to grub on my system).

as always, make sure you backup just in case the power fails half way through or you click the wrong button ;)

---

