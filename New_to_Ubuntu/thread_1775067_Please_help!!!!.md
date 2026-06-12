---
title: "Please help!!!!"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by babymoon on 2011-06-04
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
I am so stupid . Could u explain me how to fix it?

---

### Post by Rubi1200 on 2011-06-04
Hi and welcome to the forums :-)

Open a terminal and use these commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by babymoon on 2011-06-04
thanks it works!!

---

### Post by Rubi1200 on 2011-06-04
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

If you need more help with anything, feel free to ask.

---

### Post by babymoon on 2011-06-04
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE

---

### Post by babymoon on 2011-06-04
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE

---

### Post by babymoon on 2011-06-04
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE

---

### Post by overdrank on 2011-06-04
Hi and welcome, please do not create multiple threads on the same issue. threads merged :)

---

### Post by babymoon on 2011-06-04
i really don't know how to do please help

---

### Post by babymoon on 2011-06-04
asus@asus-K42JE:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for asus: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

This time it does not work.Tell me please!!!:(
:(:(:(

---

### Post by plucky on 2011-06-04
> **babymoon said:**
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE

Post the output of ```
cat /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
```

---

