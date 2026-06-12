---
title: "Teamspeak 3"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by ChuckyZ28 on 2010-07-21
I am having issues running teamspeak 3, it seems to have installed correctly but when I click on the executable file absolutely nothing happens any ideas?

---

### Post by Zeike on 2010-07-21
What happens when you try to run it from a terminal?

---

### Post by ChuckyZ28 on 2010-07-22
I don't know how? When I run the update program it will launch after that

---

### Post by Zeike on 2010-07-22
> **ChuckyZ28 said:**
> I don't know how?
Open "Applications->Accessories->Terminal"
type cd /the/path/to/the/directory/where/the/executable/is
type ./executable-name

> When I run the update program it will launch after that
I'm not sure what you mean by this

---

### Post by Jazzy_Jeff on 2010-07-22
Make sure you are clicking on the the ts3client_runscript.sh file in the folder. You may have to right click on the file and goto properties and click on permissions and click the check box to allow executing file as program.

---

### Post by ChuckyZ28 on 2010-07-23
Cool that worked, thank you.

---

### Post by d.justins on 2011-04-19
Further on this issue, 

When installing TS3, it asked if i want to keep the config in user folders. I clicked yes. 

I'm trying to script a launcher for TS3 but when i launch it from the launcher, it says 

TeamSpeak 3 cannot write to the configuration file:
/home/username/.ts3client/ts3clientui_qt.conf

any ideas?

---

