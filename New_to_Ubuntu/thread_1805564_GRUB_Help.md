---
title: "GRUB Help"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by apoorvumang on 2011-07-16
I have 11.04 installed on my computer. The other day, I installed 11.10 alpha 2 on another partition. Since then, the GRUB screen, where I choose which OS to load, shows 11.10 as the first entry.

How do I change the order of entries, so that my main OS, 11.04, boots as default?

---

### Post by redmaniac on 2011-07-16
First of all, this might be an interesting point of reference, if you should run into other problems with GRUB2 in the future:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

As for your problem: There are basically two ways of doing this: either you do it manually, or you use a tool to configure grub. If you want to do the configurations manually, just follow the link above and look at the section "Configuring GRUB 2". In a nutshell you have to edit the file /etc/default/grub and run sudo update-grub afterwards.

An easier way to solve you specific problem is to install a tool called startupmanager:

```

sudo apt-get install startupmanager

```You can select the tool from the menu System->Administration->StartUp-Manager or run it from a terminal using 'startupmanager &' .

HTH
redmaniac

---

### Post by apoorvumang on 2011-07-16
tyvm! startup manager worked like a charm.

---

### Post by amjjawad on 2011-07-16
> **apoorvumang said:**
> I have 11.04 installed on my computer. The other day, I installed 11.10 alpha 2 on another partition.

Ubuntu 11.10 is still on Alpha Stage and it's a BAD idea to install it on your internal HDD.

I'd suggest to install it some where else like an OLD HDD or USB Drive.

---

