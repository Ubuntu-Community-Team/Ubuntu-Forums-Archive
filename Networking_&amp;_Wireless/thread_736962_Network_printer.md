---
title: "Network printer"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by mastoul on 2008-03-27
Hello to everyone.I' m new in linux world so i encounter several problems.My question for the moment is how to share my printer with ubuntu 7.10 on a windows network?The printer is installed on another windows pc and shared

---

### Post by ajmorris on 2008-03-27
hi there, 
you can go to the 'add a printer' application. Name the printer etc, and in the location, instead of USB or whatever, put smb://<ip address of the pc the samba printer is on>/<printer name (named on windows)>

Also, i believe Printer Sharing must be enabled on the windows machine

---

### Post by superprash2003 on 2008-03-27
check this [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Print_Server_.28cupsd.29)

---

