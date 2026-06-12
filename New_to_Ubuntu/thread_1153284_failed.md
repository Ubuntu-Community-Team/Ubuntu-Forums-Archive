---
title: "failed"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-08
to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libthml-tagest-oerl/libhtml-tagset-perl1_3.20-2_all.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libthml-tagest-oerl/libhtml-tagset-perl1_3.20-2_all.deb:)

how doi I correct this so theat the problem resolves itself?

---

### Post by taurus on 2009-05-08
Go into System -> Administration -> Software Sources and change to another server.  Then, run your update/upgrade again.

---

### Post by shadowlands on 2009-05-08
How I can not get in to the system.  I have a blank screen after I log in?

---

### Post by taurus on 2009-05-08
Are you logged in from a console?  You can edit your /etc/apt/sources.list and remove the us. in front of your repos.

```
sudo nano -Bw /etc/apt/sources.list
```
To save the changes, press <Ctrl>x and yes to the question.

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by shadowlands on 2009-05-08
0 upgraded 0 newly installed, 0 to remove and 0 not upgrades> **taurus said:**
> Are you logged in from a console?  You can edit your /etc/apt/sources.list and remove the us. in front of your repos.

```
sudo nano -Bw /etc/apt/sources.list
```
To save the changes, press <Ctrl>x and yes to the question.

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

