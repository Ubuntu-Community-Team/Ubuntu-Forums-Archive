---
title: "Enter password for default keyring to unlock?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-11-12
everytime i log in, when ever i starup my computer, i get a window that pops up with the following message: ENTER PASSWORD FOR DEFAULT KEYRING TO UNLOCK

and, besides that, i always have to re-enter my password in order for my wireless connection to work.

how can i fix that?

thanks in advance!

---

### Post by fiver22 on 2009-11-12
User komputes posted this: [http://ubuntuforums.org/showthread.php?p=4377271](http://ubuntuforums.org/showthread.php?p=4377271)  -it may help.

---

### Post by CaptainMark on 2009-11-12
go to the directory /home/<your username>/.gnome2/keyrings and delete the file that should relate to your wireless network or network manager or something like that (just dont delete login.keyring) When you next restart your rig and it asks you to make a new password leave it blank and click okay, select use unsafe storage. presto.
This is only a good idea for home computers where your machine is safe from prying hands. 
ps. if you arent aware .gnome2 is a hidden folder and will be invisible unless you ctrl+H

---

### Post by MockY on 2009-11-12
> **Konbuntu said:**
> 
and, besides that, i always have to re-enter my password in order for my wireless connection to work.

how can i fix that?


Right-click on the NetworkManager icon on your panel and select edit connections. Click the Wireless tab and select your network. Click Edit and tick the checkbox on the bottom that says "Available to all users". Click apply.
From now on, you will automatically use your network when you boot your computer without having to enter your keyring password.

---

### Post by Konbuntu on 2009-11-12
> **CaptainMark said:**
>  delete the file that should relate to your wireless network or network manager or something like that (just dont delete login.keyring)

i have three files present in the folder: login.keyring, which, according to you, i should not delete,  default and default.keyring. now, my question is, which one should i delete?


thanks again guys!

---

### Post by CaptainMark on 2009-11-12
default.keyring

---

### Post by Tholley on 2009-11-12
> **MockY said:**
> Right-click on the NetworkManager icon on your panel and select edit connections. Click the Wireless tab and select your network. Click Edit and tick the checkbox on the bottom that says "Available to all users". Click apply.
From now on, you will automatically use your network when you boot your computer without having to enter your keyring password.
 
 
If you are running wireless,, do this one first!

---

### Post by fbotero on 2010-07-16
> **MockY said:**
> Right-click on the NetworkManager icon on your panel and select edit connections. Click the Wireless tab and select your network. Click Edit and tick the checkbox on the bottom that says "Available to all users". Click apply.
From now on, you will automatically use your network when you boot your computer without having to enter your keyring password.

Thank you MockY! This had being bugging me for a while and your suggested solution worked great for me.

---

