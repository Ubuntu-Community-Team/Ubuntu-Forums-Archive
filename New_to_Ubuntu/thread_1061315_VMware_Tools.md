---
title: "VMware Tools"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by philk949 on 2009-02-05
Hi everyone,
I'm running Intrepid Ibex in a virtual machine (VMware Workstation 6) and need to install VMware tools to increase functionality. The VMtools tarball is downloaded but I am at a loss as to how to install it. Could someone help me with this, please?
Thanks,
Phil

---

### Post by overlord.gaurav on 2009-02-05
Maybe [this]("http://cccarey.wordpress.com/howtos/howto-install-vmware-tools-on-ubuntu-810-intrepid/") would help.

---

### Post by philk949 on 2009-02-06
Thank you for the reply, Gaurav. I encountered a hurdle while trying to run the code provided in the link. I've attached a screenshot of the terminal error message.Perhaps you can see where I may have gone wrong and what I might do to correct it.
Thanks,
Phil

---

### Post by overlord.gaurav on 2009-02-08
I'm sorry for the late reply. I thought you could've got through the installation using the guide.
Anyway..the command mentioned in the guide says:
```
tar xvfz open-vm-tools-*.tar.gz
```
Here the symbol "*" means the version of the file that you have downloaded.

So, the command for you will be
```
tar xvfz open-vm-tools-2009.01.21-142982
```

If you see more of the astrix marks in the guide, just replace it with the file version.

---

### Post by philk949 on 2009-02-08
(SOLVED)
Thanks Gaurav,

Installation completed.:D
I'd mark it as Solved but I can't find anywhere on the page to do that. Thread Tools does not provide that option and I can't remember where else I might find it.
Phil

---

### Post by overlord.gaurav on 2009-02-08
> **philk949 said:**
> (SOLVED)
I'd mark it as Solved but I can't find anywhere on the page to do that. Thread Tools does not provide that option and I can't remember where else I might find it.

The 'Mark Thread As Solved' feature, and the 'Thanks' feature have been removed from the forums at the moment, due to some issues. So, you'll not find it anywhere! =)
Anyway, enjoy virtualization !

---

