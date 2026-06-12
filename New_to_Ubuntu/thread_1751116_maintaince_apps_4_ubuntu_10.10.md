---
title: "maintaince apps 4 ubuntu 10.10"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-06
plz tell me the maintaince software for ubuntu 10.10
for eg : for windows 7 i use apps for maintaince are ccleaner, diskdefrag, hardware diagnostic tools like qaplus, antivirus , malware byte software 

what is for ubuntu linux ....????????

---

### Post by Paddy Landau on 2011-05-06
Absolutely nothing! Linux cleans up after itself, and protects itself against viruses.

If you are desperately short of hard disk space, empty your Wastebasket, and use the following commands (from a terminal) about once a month.

[LIST=1]
[*]Uninstall old packages that are no longer needed.
```
sudo apt-get autoremove
```
[*]Remove package files that are no longer needed.
```
sudo apt-get clean
```
[/LIST]

But relax. Linux is really a clean system and doesn't need all the rubbish that Windows does.

You don't need antivirus, unless you are acting as a way-station for Windows users (e.g. you are providing an email server). If you're just a normal desktop user, forget about it. I know it's hard, coming from the Windows arena where you have to be paranoid, but Linux is safe. That's why (for example) banks use it for their servers.

---

