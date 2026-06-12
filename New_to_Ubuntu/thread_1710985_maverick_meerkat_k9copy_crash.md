---
title: "maverick meerkat k9copy crash"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-20
ok i just installed k9copy on maverick meerkat and when i try to copy anything it crashes is there a fix for this?

---

### Post by andrewthomas on 2011-03-20
When does it crash?

Does it open at all?

If it crashes when you open it, open it from the terminal and post the error.

---

### Post by mushroom08 on 2011-03-20
heres what i get in terminal
Error: "/var/tmp/kdecache-mushroomstamp" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-mushroomstamp" is owned by uid 1000 instead of uid 0.
KCrash: Application 'k9copy' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/mushroomstamp/.kde/socket-MushroomEmpire/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
Error: "/var/tmp/kdecache-mushroomstamp" is owned by uid 1000 instead of uid 0.

[1]+  Stopped                 sudo k9copy

---

### Post by coffeecat on 2011-03-20
> **mushroom08 said:**
> [1]+  Stopped                 sudo k9copy

Why are you running k9copy with sudo?

---

### Post by mushroom08 on 2011-03-20
so i can post the errors

---

### Post by coffeecat on 2011-03-20
> **mushroom08 said:**
> so i can post the errors

Most of the errors you got were **because** you ran it with sudo. For example:

> **mushroom08 said:**
> Error: "/var/tmp/kdecache-mushroomstamp" is owned by uid 1000 instead of uid 0.

Try running just 'k9copy'.

---

### Post by mushroom08 on 2011-03-20
i did it crashes at the same time either way as soon as i try copying somthing

and i get this- Executable: k9copy PID: 11860 Signal: 11 (Segmentation fault

---

### Post by coffeecat on 2011-03-20
Do you have libdvdread4 and libdvdcss2 installed?  If not, install ubuntu-restricted-extras for the first. Then go to the Medibuntu site:

[http://medibuntu.org/](http://medibuntu.org/)

Use the repository howto to enable the medibuntu repository, and then install libdvdcss2.

---

### Post by mushroom08 on 2011-03-20
ok now im getting this error

Executable: k9copy PID: 6080 Signal: 11 (Segmentation fault)

---

### Post by coffeecat on 2011-03-20
> **mushroom08 said:**
> ok now im getting this error

Executable: k9copy PID: 6080 Signal: 11 (Segmentation fault)

What did you do, if anything, between the first segmentation error and this one? You need to tell us what you are doing.

---

### Post by mushroom08 on 2011-03-20
went to medibuntu and used

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by coffeecat on 2011-03-20
From that I have to assume that you've enabled the medibuntu repository but that you haven't installed libdvdcss2, and neither have you installed ubuntu-restricted-extras.

OK.

---

### Post by mushroom08 on 2011-03-20
ubuntu-restricted-extras is one of the first things i installed and checked synaptic i have libdvdcss2

---

### Post by mushroom08 on 2011-03-23
i figured it out

---

### Post by IRONMAN-NC on 2011-04-05
And the solution was?

---

### Post by claven123 on 2011-04-15
[SIZE=3]What was the solution?

D[/SIZE]

---

### Post by kato223 on 2011-05-23
I have tried all the libdvdcss2 and the medibuntu, and k9copy was still crashing even if I launched the wizard first.  If you go to the properties for k9copy in the menu and change the command to *'kdesudo k9copy -caption "%c" %i %m  %u'* and you change the k9copy wizard one to *'kdesudo k9copy --assistant -caption "%c" %i %m  %u'* it no longer seems to crash. Hope this helps.

---

### Post by kato223 on 2011-06-02
Sorry for the last response, but I figured it out.  You need to make the .kde folder to your username then it works fine.

```
sudo chown -R ***username:username* **/home/***username***/.kde/
```

---

