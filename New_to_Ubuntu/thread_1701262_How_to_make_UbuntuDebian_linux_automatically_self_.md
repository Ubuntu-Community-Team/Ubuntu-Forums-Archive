---
title: "How to make Ubuntu/Debian linux automatically self update to internet ?"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by albertwt on 2011-03-06
Hi All,

is it possible to make Ubuntu/Debian Linux to get automatic update from internet ?

I tried to manually update by using the following command it failed ?

```
Serv0102:~# apt-get install updates
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package updates
```


I can ping to outside world but somehow update won't run ?

---

### Post by dionysius on 2011-03-06
> **albertwt said:**
> Hi All,

is it possible to make Ubuntu/Debian Linux to get automatic update from internet ?

I tried to manually update by using the following command it failed ?

```
Serv0102:~# apt-get install updates
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package updates
```


I can ping to outside world but somehow update won't run ?

You can use Update Manager from the Main Menu (or type update-manager in Terminal) for GUI

To update using the command line alone: 
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

If you want to edit automatic updates, e.g. automatically check for updates but do not download, click on 'Settings' in Update Manager, enter your password when asked, and select the 'Updates' tab.

---

