---
title: "brasero"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by zenneth on 2009-03-10
brasero has will not burn cd/dvd since the 8th of march does anyone no of an upgrade which has corrupted brasero i am using 8.10 it has worked very well till then.

---

### Post by freesitebuilder on 2009-03-10
Last update seems to have been in September 2008 - [http://svn.gnome.org/viewvc/brasero/tags/BRASERO_0_8_2/NEWS?view=markup](http://svn.gnome.org/viewvc/brasero/tags/BRASERO_0_8_2/NEWS?view=markup)

But I used it for the first time in ages today (certainly for the first time on 8.10) and it failed. My error was:
Session error : failed to get the start point of the track. Make sure the media allow to add files (it is not closed) (brasero_burn_record burn.c:2524)

I used Nautilus in the end. Are you getting an error?

---

### Post by stchman on 2009-03-10
> **zenneth said:**
> brasero has will not burn cd/dvd since the 8th of march does anyone no of an upgrade which has corrupted brasero i am using 8.10 it has worked very well till then.

I have been reading that Brasero has had problems burning CDs in Intrepid.

The folks at Ubuntu will correct the problem.  I use K3b to burn all my CDs/DVDs.

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

You will find it a more feature rich program that Brasero.

---

### Post by zenneth on 2009-03-11
i dont get the option to burn. or if i try to erase it says the codecs are incorrect. i am using gnome baker and so far so good

---

### Post by Artemis3 on 2009-03-11
Yes, Brasero has been acting up lately, which is why i installed gnomebaker...

---

### Post by zenneth on 2009-03-11
> **stchman said:**
> I have been reading that Brasero has had problems burning CDs in Intrepid.

The folks at Ubuntu will correct the problem.  I use K3b to burn all my CDs/DVDs.

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

You will find it a more feature rich program that Brasero.

i will try this prog thanks very much

---

### Post by zenneth on 2009-03-11
> **Artemis3 said:**
> Yes, Brasero has been acting up lately, which is why i installed gnomebaker...

i have just loaded this prog and it works well thank you

---

