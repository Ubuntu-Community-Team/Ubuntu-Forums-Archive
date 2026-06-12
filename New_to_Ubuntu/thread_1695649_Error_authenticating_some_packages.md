---
title: "Error authenticating some packages"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by kmkmahesh on 2011-02-26
i am getting the below error message while upgrading from 10.04 to 10.10 using alternate cd or using internet also

```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

and i am getting lot of package names under this

```

i just used the below commands to upgrade using alternatecd

```

sudo mkdir -p /media/cdrom

sudo mount -o loop /home/mahesh/Desktop/ubuntu-10.10-alternate-i386.iso /media/cdrom

gksu "/media/cdrom/cdromupgrade"

```

i just really want to upgrade this bcz i cant connect my phone to use internet using bluetooth, i am getting so many error while trying that, so plz help me abt this.

Thnx in Advance

---

### Post by LewRockwellFAN on 2011-02-27
Possibly it was a temporary problem reaching the servers? All sorts of reasons that could happen. Maybe try again. My internet connection is sometime off an on flaky and occasionally out for a day or so and I'm sure there are places with worse service than mine. Sorry if I'm stating the obvious but you didn't say over what time period this problem persisted or if you tried more than twice. And usually questions here get some sort of response sooner than this so I thought I'd throw my inexpert idea out for what it is worth. If it doesn't help, at least you've been bumped. :)

---

### Post by kmkmahesh on 2011-02-27
i solved my problem and upgraded sucessfully after a big effort,

i just made update of update manager(sorry i dont remember the correct name) and then in software sources, other softwares, i removed all the old links and selected an another working server, 

thnx to ubuntu forums for this great help

---

