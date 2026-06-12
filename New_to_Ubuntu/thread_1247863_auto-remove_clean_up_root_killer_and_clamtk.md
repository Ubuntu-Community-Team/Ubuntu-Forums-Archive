---
title: "auto-remove/ clean up root killer and clamtk"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-08-23
i'm trying to use auto  remove and i keep getting this message:


E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

can anyone help me out? 

and  i don't know to code for clean up, root killer  and  clam

---

### Post by oldos2er on 2009-08-23
```
sudo apt-get autoremove
```

---

### Post by 289531.EXE on 2009-08-23
hey thanks, that code worked. do you know the code for:

clean up
chrootkiller (or something  like that, i forgot)
and, to install clam?

---

### Post by matchstich on 2009-08-23
go to package manager and type in rootkit.

that will show both rhunter and ck.

after you click on them and mark for installation and apply 

then go back to search and type in clam

thanks

---

### Post by Penguin Guy on 2009-08-23
> **289531.EXE said:**
> code to install clam?
Open synaptic ([COLOR="Green"]System -> Administration -> Synaptic Package Manager[/COLOR]) and type [COLOR="Green"]clamav[/COLOR] into the search box.

---

### Post by 289531.EXE on 2009-08-23
i downloaded  the rootkit hunter and scanner but where  exactly is  it?

---

### Post by oldos2er on 2009-08-23
> **289531.EXE said:**
> hey thanks, that code worked. do you know the code for:

clean up
chrootkiller (or something  like that, i forgot)
and, to install clam?

 By "clean up," do you mean removing package files? If so,
```
sudo apt-get clean
```
should work. ```
man apt-get
``` will give you more info.

---

### Post by matchstich on 2009-08-23
go back to package manager and install clamtk  that id the front end for it.

as for ckrootkit and rkhunter,

sudo chkrootkit

chkrootkit -d sniffer

What's chkrootkit?
chkrootkit is a tool to locally check for signs of a rootkit. It contains:

* chkrootkit: a shell script that checks system binaries for rootkit modification.

* ifpromisc.c: checks if the network interface is in promiscuous mode.

* chklastlog.c: checks for lastlog deletions.

* chkwtmp.c: checks for wtmp deletions.

* check_wtmpx.c: checks for wtmpx deletions. (Solaris only)

* chkproc.c: checks for signs of LKM trojans.

* chkdirs.c: checks for signs of LKM trojans.

* strings.c: quick and dirty strings replacement.

* chkutmp.c: checks for utmp deletions.

chkwtmp and chklastlog *try* to check for deleted entries in the wtmp
and lastlog files, but it is *not* guaranteed that any modification
will be detected. 

sudo rkhunter -c

sudo rkhunter --update

sudo rkhunter --checkall

---

### Post by 289531.EXE on 2009-08-23
i did the scan and i got  "warning in like 2  files, is there  a way to  fix that?

---

### Post by matchstich on 2009-08-23
well, if you rkhunter  go to here

# [email]rkhunter-users@lists.sourceforge.netrem[/email]ove contact

---

### Post by 289531.EXE on 2009-08-24
??????

---

### Post by matchstich on 2009-08-24
rkhunter has a help line thru sorceforge.   but, i do not know if ck has it or not.



if you got clam and  clamtk  then the gui should be on applications>>system  tools.  can run it from there.

found this for you

[http://www.chkrootkit.org/](http://www.chkrootkit.org/)

it shows a mailing list that you can join to learn about it. ask questions, etc.

---

### Post by matchstich on 2009-08-26
ok, here is another link

[http://www.google.com/linux](http://www.google.com/linux)

it is really helpful, have used  it quite a lot in finding solutions along with lurking in  the forums here.

---

