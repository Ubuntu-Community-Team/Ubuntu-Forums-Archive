---
title: "how to make linux 11.04 default  os"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by samitrimal on 2011-06-29
hi i am using windows7 and ubuntu 11.04 64 bit. i want to make ubuntu a default os to load . How to do it i am new to ubuntu so i need your help .regards

---

### Post by amjjawad on 2011-06-29
> **samitrimal said:**
> hi i am using windows7 and ubuntu 11.04 64 bit. i want to make ubuntu a default os to load . How to do it i am new to ubuntu so i need your help .regards

I assume you installed Windows THEN you installed Ubuntu. If that's the case, you don't need to do anything because Ubuntu will be the first OS to boot from.

If that's not the case, From Terminal:

```
sudo apt-get update
sudo apt-get install startupmanager -y

```

After that, you'll find it in:

System > Administration > Start-up Manager

---

### Post by samitrimal on 2011-06-29
[I]hi amjjawad,
thanks for your reply
i followed your instruction and selected ubuntu linux generic.......
but it did not worked for me is there anything further i need to  do ?
regards
[/I]

---

### Post by amjjawad on 2011-06-29
> **samitrimal said:**
> [I]hi amjjawad,
thanks for your reply
i followed your instruction and selected ubuntu linux generic.......
but it did not worked for me is there anything further i need to  do ?
regards
[/I]

Hi,

What do you mean it did not work? before you install startupmanager, was it working? or you had no working Ubuntu from beginning?

We need more details so that we could help and offer the best advice :)

---

### Post by Mark Phelps on 2011-06-29
You didn't tell us HOW you installed Ubuntu.  If you did that using Wubi, you need to make the change inside Win7 because you're using a menu screen displayed by Win7, not by GRUB, to make your OS selection.

To do that in Win7, do the following:
1) type MSCONFIG in the start area
2) when System Configuration panel is displayed, select the Boot tab
3) Select the row you want as default and click the Set as Default button.
4) Click OK and exit.

Next time your reboot Win7, Ubuntu will be the default selection.

---

### Post by Tai89 on 2012-09-02
I know it has been over a year since the last post in this thread, but I am running into the same problem. I recently used the windows installer in Win7 to install ubuntu. I want to change ubuntu to my default os, but following the instructions to change it using msconfig did not help. When I got into msconfig, Win7 was my only option in the boot tab.

---

