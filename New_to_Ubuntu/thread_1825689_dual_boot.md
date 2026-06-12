---
title: "dual boot"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-15
Hello to all!
I have one partition of my disk with ubuntu and the other with windows. I dont have an option to start windows on my pc. How to configure grub in order to select during booting witch operating system to boot?
THANK YOU!

---

### Post by Mark Phelps on 2011-08-15
Boot into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB menu to include entries for MS Windows.  When you reboot, you should see a GRUB menu with selections in it.

---

### Post by vagelism on 2011-08-15
> **Mark Phelps said:**
> Boot into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB menu to include entries for MS Windows.  When you reboot, you should see a GRUB menu with selections in it.

No ...is not working!

---

### Post by Johnb0y on 2011-08-15
try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

this helped me with my xp/ubuntu issue... hope it helps you too :)

p.s. it is free for private use...

---

### Post by jeremy101 on 2011-08-15
Boot into Ubuntu, launch a terminal and type ```
sudo update-grub
```. Hopefully, upon reboot, you will see an entry for Windows. :)

---

### Post by Mark Phelps on 2011-08-16
> **vagelism said:**
> No ...is not working!

That tells me nothing useful.  If you want help, you need to provide us some details -- like what IS happening when you try to boot.

jemery101: Why repost the same thing I already said?

---

### Post by vagelism on 2011-08-16
With some commands in WIN7 installation dvd and 
sudo update-grub 
Everything works fine again!
Thank you all for the assistance!

---

