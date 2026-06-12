---
title: "What's Wrong with my Wireless?!"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by NfF on 2009-06-26
ive got a problem here, probably basic problems encountered when using Ubuntu, as u could see from my screenshots, my wireless network has been disabled, and how do i enable it ? Do i have to command using terminal or is it a bug? I'm using Jaunty Jackalope, and i really want this simple problem to be fixed.Also,right clicking on the network manager in Screenshot 3, it seems there is no way to enable wireless! Pls help. )X
Ive posted this problem thrice bt the answers still doesn't solve my problem..

And one more thing, how do u make urself into "root" when commanding in terminal?

---

### Post by t0p on 2009-06-26
> **NfF said:**
> one more thing, how do u make urself into "root" when commanding in terminal?

If you want toi run a command as root, prefix it with **sudo**, eg

```
sudo nano /etc/ypops.ini
```

If you want to run several commands as root, you can initiate a "root" session with the command

```
sudo -s
```

Note: This is not true root.  It's Ubuntu's idea of an alternative.  Does the job and is less potentially dangerous to the beginner.

---

### Post by billgoldberg on 2009-06-26
Whenever I had this, I turned out I accidentally disabled wifi on my laptop.

Usually there is a switch or a keyboard shortcut to disable/enable it.

I once spend hours troubleshooting before I figured this out.

I'm just mentioning it to rule this possibility out.

---

### Post by porchrat on 2009-06-26
> **NfF said:**
> ive got a problem here, probably basic problems encountered when using Ubuntu, as u could see from my screenshots, my wireless network has been disabled, and how do i enable it ? Do i have to command using terminal or is it a bug? I'm using Jaunty Jackalope, and i really want this simple problem to be fixed.Also,right clicking on the network manager in Screenshot 3, it seems there is no way to enable wireless! Pls help. )X
Ive posted this problem thrice bt the answers still doesn't solve my problem..

Has your wireless ever run? Or has it always been disabled?

EDIT: Just noticed that you are running ndiswrapper. Why did you do that? As far as I am aware Jaunty ships with drivers for the ipw2200. In  my experience ndiswrapper is generally a good way to go with these ipw wifi cards/modules as it results in better range and stability, but did you try the Ubuntu drivers?

---

