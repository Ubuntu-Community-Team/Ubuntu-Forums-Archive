---
title: "How Do You Create a Swap File in Ubuntu 9.04?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by joelrstevens on 2009-06-18
Great success in multi booting Ubuntu w/Vista!!!! Everything went well except I got a warning that I had not created a swap partition.  How do I do this?:confused:

---

### Post by TeoBigusGeekus on 2009-06-18
A swap partition is an auxiliary partition in linux systems that works as a pseudo ram: whenever things get rough - i.e. you run resource hungry apps - it is used to make your os breathe a bit.
If you have a brand new pc with something like 2 or 3 gigs of ram (or even more) you shouldn't have a problem.

---

### Post by joelrstevens on 2009-06-18
But HOW do I create one? Do I have to go back and reinstall again or can I do it from inside the Ubuntu OS?

---

### Post by TeoBigusGeekus on 2009-06-18
If you insist...
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
Look at the "How I add more swap section".

---

### Post by Krishna_Chaitanya on 2009-06-18
Swap partition can be created during installation of OS ....................
    Swap partition should be double the size of your RAM for better performance.....:KS
 
 
 
             Enjoy ...................... working Wid Ubuntu

---

### Post by joelrstevens on 2009-06-18
Okaaaaaay. Too much code for this newbie!!! (Teo, but it is appreciated) Can I do this through the GUI? If not, how do I create the swap during install? :confused:

---

### Post by TeoBigusGeekus on 2009-06-18
When you install, you are asked on which partition you want Ubuntu to be put. This is your root partition and it is mounted on /.
You can create a separate partition during install (choosing manual on the partition section) of about 1gb and edit this partition (right click -> edit? I don't remember) to be used as swap.

---

### Post by elysianfields44 on 2009-06-18
> **joelrstevens said:**
> Okaaaaaay. Too much code for this newbie!!! (Teo, but it is appreciated) Can I do this through the GUI? If not, how do I create the swap during install? :confused:

You don't need to re-install. Just create a swap file. It works the exact same way as a swap partition. Read this guide which was already mentioned and follow the steps for creating a swap file: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

EDIT: I just realized you wanted to do it through the GUI. But as you can see from the link, it only takes 4-5 lines of code which you can cut and paste into terminal, so I think you should give it a try instead of re-installing.

---

