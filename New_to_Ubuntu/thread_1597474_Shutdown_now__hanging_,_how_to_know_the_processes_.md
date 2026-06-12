---
title: "Shutdown now:  hanging , how to know the processes that block linux?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-15
Hello

Shutdown is not working, there is some processes that hangs. What is going on with linux ?

:(
   
Anynoe knows how to fix that? The box is well installled and packages are defaults.

---

### Post by TeoBigusGeekus on 2010-10-15
Do you get any messages with
```
sudo shutdown -h now
```
?

---

### Post by honeybear on 2010-10-15
> **TeoBigusGeekus said:**
> Do you get any messages with
```
sudo shutdown -h now
```
?

it hangs, so no control anymore

---

### Post by jeremyjc on 2010-10-15
Installing this wireless driver fixed it for me

[http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb](http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb)

---

### Post by endotherm on 2010-10-15
if you absolutely can't get it to shutdown, you can get the kernel to shutdown gracefully (if it is responsive) by holding Alt + Prntscrn and slowly typing r e i s u b. when you hit the 's' keystroke, your hdd light may come on for a sec. be sure it is off before you hit 'u', as the s tells it to synch the disks write buffer, whereas u unmounts the disks, and remounts them as readonly. the b shuts down the system without unmounting, so haveing them remounted as readonly is critical to ensure you don;t lose data or hash your disks.

[https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key](https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key)

---

### Post by honeybear on 2010-10-15
> **endotherm said:**
> if you absolutely can't get it to shutdown, you can get the kernel to shutdown gracefully (if it is responsive) by holding Alt + Prntscrn and slowly typing r e i s u b. when you hit the 's' keystroke, your hdd light may come on for a sec. be sure it is off before you hit 'u', as the s tells it to synch the disks write buffer, whereas u unmounts the disks, and remounts them as readonly. the b shuts down the system without unmounting, so haveing them remounted as readonly is critical to ensure you don;t lose data or hash your disks.

[https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key](https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key)

I am not sure that the linxu has umounted the disks

it seems that it is before. there is a process that linux cannot kill :(

---

### Post by endotherm on 2010-10-15
> **honeybear said:**
> I am not sure that the linxu has umounted the disks

it seems that it is before. there is a process that linux cannot kill :(
well that is what the 'r' is for. it sends the kill signal to all running processes. 
keep in mind, my advice is only for situations where it just won;'t shut down, but you don;t want to hurt your filesystem by pulling the plug.

---

### Post by Kouki on 2010-10-24
Just to add, my computer also hangs on shutdown.  It reaches the splash screen with Ubuntu and the moving squares below it and just stays like that.  I have to pull the power everytime I shut my PC down, which isn't good.  It's only started doing it in the last couple of weeks or so and I've not installed anything new, so it must be one of the updates.

---

### Post by honeybear on 2010-11-04
reishub, for thanks a lot

A question, how can one know whihch process hangs at boot?

I see some killing operation and retemptatives.

```
echo somethign > ... 
and some hangs writen
some 10 lines about
 
```

how to fix that [Doc]("http://www.davemackey.com/animation/wb/titlecards/whatupdc.jpg") ?

---

