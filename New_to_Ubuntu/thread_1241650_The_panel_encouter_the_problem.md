---
title: "The panel encouter the problem"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by imran_khan on 2009-08-16
[SIZE=4][COLOR=black]
 when I Start the ubuntu I Get  this Error message 


 [SIZE=5]The panel encouter the problem "OAFIID:GNOME_Panel_TrashApplet".[/SIZE][/COLOR][/SIZE][SIZE=5]
[/SIZE]
[SIZE=4]Give the suggestion what  can I doing ????????
I am the biggner in Linux .....................plz give reply soon as possible
[/SIZE]

---

### Post by wojox on 2009-08-16
Try reinstalling the applets. Open a terminal and type:
```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by imran_khan on 2009-08-16
> **wojox said:**
> Try reinstalling the applets. Open a terminal and type:
```
sudo apt-get install --reinstall gnome-applets
```

sir,
when i use this command it give this information , i install my ubuntu in drive F .


The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>

---

### Post by colau on 2009-08-16
```

sudo apt-get update
sudo apt-get install gnome-panel
sudo ap-get install gnome-applets

```

---

### Post by imran_khan on 2009-08-22
> **colau said:**
> ```

sudo apt-get update
sudo apt-get install gnome-panel
sudo apt-get install gnome-applets

```


thanx for guide sir

---

### Post by TopEnder on 2009-10-23
> **colau said:**
> ```

sudo apt-get update
sudo apt-get install gnome-panel
sudo ap-get install gnome-applets

```
Thanks for your help in solving my problem

---

