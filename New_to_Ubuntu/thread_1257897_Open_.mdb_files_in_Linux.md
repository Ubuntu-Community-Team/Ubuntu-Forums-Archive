---
title: "Open .mdb files in Linux"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by dmcdaniel on 2009-09-04
Hello. 

Can anyone tell me if there is a way to open .mdb files for use in Linux?

I know you used to be able to do it in Open Office but I am using version 2.4 and can't figure out how to do it. 

Thanks,
dmcdaniel

---

### Post by xir_ on 2009-09-04
found this

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=40&t=5712](http://user.services.openoffice.org/en/forum/viewtopic.php?f=40&t=5712)

---

### Post by dmcdaniel on 2009-09-04
> **xir_ said:**
> found this

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=40&t=5712](http://user.services.openoffice.org/en/forum/viewtopic.php?f=40&t=5712)

I read that already. Just wasn't sure if there was another way to do the open office or if another program would work. I can do it in a virtual machine but its a pain in the butt. 

Thanks though.

---

### Post by aeiah on 2009-09-04
you should be able to open oo-base and select 'connect to an existing database' and select access database, and follow it through.

---

### Post by dmcdaniel on 2009-09-04
> **aeiah said:**
> you should be able to open oo-base and select 'connect to an existing database' and select access database, and follow it through.

That option is no longer available in Open Office 2.4 :(

---

### Post by aeiah on 2009-09-04
*no longer* available?

i havent got 2.4 to test, but it's available in version 3 if you choose to upgrade. i cant actually confirm whether it is included in linux open office since im on a windows machine right now but id be very suprised if it isnt.

---

### Post by dmcdaniel on 2009-09-04
> **aeiah said:**
> *no longer* available?

i havent got 2.4 to test, but it's available in version 3 if you choose to upgrade. i cant actually confirm whether it is included in linux open office since im on a windows machine right now but id be very suprised if it isnt.

I will upgrade to 3.0 and let you know my results. 

Thanks.

---

### Post by hal10000 on 2009-09-04
There are some other tools in the repoitories to handle mdb files.
**kexi-mdb-plugin** ---> to convert MDB database files to Kexi databases
**libmdbodbc** ---> the software driver to access JET / MS Access database (MDB) files through ODBC
**mdbtools** ---> command line utilities to list tables, export schema, and data, show file versions, sql queries etc.
**mdbtools-gmdb** graphical tool to export data and schemata from mdb files

You can get them via syaptic (or anotr package manager)

---

### Post by dmcdaniel on 2009-09-10
> **aeiah said:**
> *no longer* available?

i havent got 2.4 to test, but it's available in version 3 if you choose to upgrade. i cant actually confirm whether it is included in linux open office since im on a windows machine right now but id be very suprised if it isnt.

I tried updating to 3.0 and I have had some MAJOR issues. I can no longer even use O.O 2.4 or even 3.0 for that matter. I looked in Synaptic and I can not find Open Office but it says I can not install it due to dependencies. Any ideas?

---

### Post by philinux on 2009-09-10
mdbtools in synaptic

---

### Post by hal10000 on 2009-09-10
> I looked in Synaptic and I can not find Open Office but it says I can not install it due to dependencies. Any ideas?
I suppose you <re using uuntu 8.04 (hardy heron).
Just put this line into your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```
and runthis command:
```
gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add
```
Then you should be able to install openoffice 3.0 resp. openoffice 3.1 with all it's dependencies.

If you install openoffice 3.1, and you have lost your toolbar icons , then take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1260630](http://ubuntuforums.org/showthread.php?t=1260630)

---

### Post by dmcdaniel on 2009-09-10
> **hal10000 said:**
> I suppose you <re using uuntu 8.04 (hardy heron).
Just put this line into your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```
and runthis command:
```
gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add
```
Then you should be able to install openoffice 3.0 resp. openoffice 3.1 with all it's dependencies.

You my friend are a freaking LIFESAVER! I have spent probably close to 12 hours trying to figure this out. Thanks a lot!

---

### Post by hal10000 on 2009-09-10
> You my friend are a freaking LIFESAVER
If you want to put some other repositories into your sources.list, then take a look at te ubuntu sources.list generator: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

