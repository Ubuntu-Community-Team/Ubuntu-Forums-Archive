---
title: "uninstalled virtualbox harddrive space still taken up"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-23
how do i ge the hd space i had dedicated to my vm back after i have completely removed virtualbox?

---

### Post by novafluxx on 2009-01-23
You'll have to find the folder where the virtual hard drive was stored. I'm willing to bet its something like .virtualbox im your /home directory. I'm not exactly sure of the correct location and/or name though.

try going to /home and doing ls a

I *think* that will show you the hidden files/folders

You probably should have deleted the virtual disk from within the VirtualBox program's disk manager (I've only used Vbox in Windows, so I'm not entirely familiar with its workings in Linux/Ubuntu)

---

### Post by mamamia88 on 2009-01-23
thanks it was a hidden file in home

---

### Post by novafluxx on 2009-01-23
> **mamamia88 said:**
> thanks it was a hidden file in home

You're very welcome! At last I'm able to help someone!

---

