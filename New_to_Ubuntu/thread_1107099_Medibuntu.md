---
title: "Medibuntu"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by herbertg on 2009-03-26
I installed medibuntu for 8.10 and I'm running 8.4 Is there any problems with this or should I uninstall it and install 8.4.

Thanks

---

### Post by leonardo_neo on 2009-03-26
Your question is not clear........what do you mean by 8.4 ?

---

### Post by BOZG on 2009-03-26
> **leonardo_neo said:**
> You question is not clear........what do you mean by 8.4 ?

He's installed the Medibuntu repos for 8.10 but he's using 8.04.

---

### Post by herbertg on 2009-03-26
Sorry 8.04 ubuntu

---

### Post by leonardo_neo on 2009-03-26
> **herbertg said:**
> Sorry 8.04 ubuntu

Well, let me tell you how the versions are named. The first digit represents the year of release (so 8 means 2008 ) and the digits after dot represents the month (so 04 means April). Most of the users know this, still for others who don't know.

Now, you ideally you should use the repository which is meant for 8.04 .

:)

---

### Post by ibuclaw on 2009-03-26
You can't **install** Medibuntu...

Medibuntu is a package repository, to which you can install software from.

There is nothing wrong with having the Intrepid repo in your sources list, but some things may refuse to install due to missing dependencies.

For this, I would recommend that you do this:

Go into **System->Administration->Software Sources**. You'll require your password.

Click on the **Third Party Software** tab, and locate the lines that say "**packages.medibuntu.org**", and select/edit them.

Change the **Distribution** line in the edit box from intrepid to **hardy** with all lower case letters.

Once done, close and reload your software list.

Regards
Iain

---

### Post by herbertg on 2009-03-26
Thanks tinivole worked out fine.

---

