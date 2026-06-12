---
title: "setting up a windows program"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-09-05
theres this little exe program that works with the im site chatango. it alerts me when i get a message (when im not on the site)

is it possible to get it to work in ubuntu?

---

### Post by justin43384 on 2010-09-05
you can try WineHQ
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Chesamo on 2010-09-06
As mentioned above, you can install WINE to run simple Windows programs like that. To install WINE, type ```
sudo apt-get -y install wine
``` into the Terminal, then right-click on the executable and click "Run with WINE Windows Program Loader". If the executable is compatible, then it will run.

---

### Post by sikander3786 on 2010-09-06
> **Proto_Blaze said:**
> theres this little exe program that works with the im site chatango. it alerts me when i get a message (when im not on the site)

is it possible to get it to work in ubuntu?

It might be, not surely possible to get it working under Ubuntu through Wine as mentioned above. See the link below before you get started.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Install using these commands.
```

sudo apt-get update && sudo apt-get install wine

```

Wine is not the ideal solution. You should always try to find some native Linux alternatives for other OS software. But, when you've got no choice, Wine might help.

> **Chesamo said:**
> ```
sudo apt-get -y install wine
```

Why the -y switch? Don't know...

---

### Post by Insomnia64 on 2010-09-06
> **sikander3786 said:**
> Why the -y switch? Don't know...

-y Selects 'yes' automatically when asked for upon installation.

---

### Post by dirghrabadia on 2010-09-06
You might have to change the permissions of the .exe file using 'chmod', if it doesn't run under wine in the first instance.
```

chmod 700 filename.exe

```

---

### Post by sikander3786 on 2010-09-06
> **Insomnia64 said:**
> -y Selects 'yes' automatically when asked for upon installation.

#-o Didn't know... :D

Still will never use it coz typing "-y" involves 2 key strokes, and typing "y" and hitting "Return" also involves 2 key strokes. Not much of a difference and I am used to the 2nd one. LOL

---

### Post by Insomnia64 on 2010-09-06
I'm not sure what the name of the program is that you are looking for, but it can be searched for on the [wine DB]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

> **sikander3786 said:**
> #-o Didn't know... :D

Still will never use it coz typing "-y" involves 2 key strokes, and typing "y" and hitting "Return" also involves 2 key strokes. Not much of a difference and I am used to the 2nd one. LOL

In all the instances i've seen of a yes or no question upon installation the yes option is capitalised, i.e. "[Y/n]". In which case simply enter will select the capitalised option, in this case yes. So that way only requires one key :)

---

### Post by jtarin on 2010-09-06
> **Insomnia64 said:**
> I'm not sure what the name of the program is that you are looking for, but it can be searched for on the [wine DB]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")



In all the instances i've seen of a yes or no question upon installation the yes option is capitalised, i.e. "[Y/n]". In which case simply enter will select the capitalised option, in this case yes. So that way only requires one key :)
You should get out more!:p

---

### Post by Insomnia64 on 2010-09-06
> **jtarin said:**
> You should get out more!:p

;) I was actually laughed at for not knowing that and typing 'y' all the time. Since then i just hit enter and it saves time when there are a lot of yes/no questions when you want the default options on most :)

---

### Post by jtarin on 2010-09-06
I usually go undecided.

---

