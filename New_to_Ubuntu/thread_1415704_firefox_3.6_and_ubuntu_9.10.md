---
title: "firefox 3.6 and ubuntu 9.10"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by norbert26 on 2010-02-25
I beleive i am still on firefox 3.5 the older version although i am still getting patches and updates for it. Will firefox update by itself in time thru the update manager without me messing with it maually ? Or would i need to do a manual upgrade to 3.6 ?

---

### Post by turin13 on 2010-02-25
[I]sudo add-apt-repository ppa:mozillateam/firefox-stable

sudo apt-get update

sudo apt-get dist-upgrade[/I]

And at the finish you should get the latest version of FF.

---

### Post by norbert26 on 2010-02-25
no good get an error  ill just leave it be.

---

### Post by turin13 on 2010-02-25
What error, after what? Can you explain?
And, which version of Ubuntu do you have? Solution is for 9.10 Karmic.

---

### Post by norbert26 on 2010-02-25
an argument is needed for reposatory it could be a typo on my part in the terminal .

---

### Post by norbert26 on 2010-02-25
Error ppa.mozillateam/firefox-stable invalid. 
this is using ubuntu 9.10

---

### Post by turin13 on 2010-02-25
Can you just copy and paste commands to terminal? To ensure mistyping. You can paste in terminal with Shift+Insert.

---

### Post by BrandonBan6 on 2010-02-25
> **turin13 said:**
> [I]sudo add-apt-repository ppa:mozillateam/firefox-stable

sudo apt-get update

sudo apt-get dist-upgrade[/I]

And at the finish you should get the latest version of FF.

I used: 
```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox

```
It uninstalled 3.5.x and installed 3.6.

---

### Post by norbert26 on 2010-02-25
RESOLVED it went in and is installed thanks all.

---

