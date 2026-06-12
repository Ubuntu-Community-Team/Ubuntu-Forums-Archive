---
title: "problem with synaptic"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by linuxaholik on 2011-01-18
hi im new here and i have a problem when i go to the termina and write sudo synaptic an i press enter i found an error it write E:malformed line 3 in sources list /etc/apt/sources.list(URI sparse) and E:the list of sources could not be read
go to repository dialog to correct the problem
 what i need to do with this help me please

---

### Post by cavh on 2011-01-18
We need to see the content of your sources.list file. Type this into a terminal window and post the result here (use SHIFT-CTRL-C to copy text in a terminal window, not the usual CTRL-C)

```
cat /etc/apt/sources.list
```

---

### Post by cavh on 2011-01-18
We need to see the content of your sources.list file. Type this into a terminal window and post the result here (use SHIFT-CTRL-C to copy text in a terminal window, not the usual CTRL-C)

```
cat /etc/apt/sources.list
```

---

### Post by cavh on 2011-01-18
We need to see the content of your sources.list file. Type this into a terminal window and post the result here (use SHIFT-CTRL-C to copy text in a terminal window, not the usual CTRL-C)

```
cat /etc/apt/sources.list
```

---

### Post by cavh on 2011-01-18
We need to see the content of your sources.list file. Type this into a terminal window and post the result here (use SHIFT-CTRL-C to copy text in a terminal window, not the usual CTRL-C)

```
cat /etc/apt/sources.list
```

---

### Post by linuxaholik on 2011-01-18
deb http//update.eeepc.asus.com/p701 p701 main
deb http//update.eeepc.asus.com/p701/en p701 main
deb http//update.eeepc.asus.com/1.6/common main

---

### Post by linuxaholik on 2011-01-18
deb http//update.eeepc.asus.com/p701 p701 main
deb http//update.eeepc.asus.com/p701/en p701 main
deb http//update.eeepc.asus.com/1.6/common main

---

### Post by oldos2er on 2011-01-18
Which version of Ubuntu are you using?

The URLs in your sources.list are missing their colon: 

deb [http://update.eeepc.asus.com/p701](http://update.eeepc.asus.com/p701) p701 main
deb [http://update.eeepc.asus.com/p701/en](http://update.eeepc.asus.com/p701/en) p701 main
deb [http://update.eeepc.asus.com/1.6/common](http://update.eeepc.asus.com/1.6/common) main

Use ```
gksu gedit /etc/apt/sources.list
``` to edit the file, then run ```
sudo apt-get update
```

---

### Post by linuxaholik on 2011-01-18
i have asus eee pc 4g with xandros linux
and what i need to do whit these three files

---

### Post by oldos2er on 2011-01-18
What three files? Did you make the editing changes I suggested?

Edit: I think you would find better help here: [http://forums.xandros.com/](http://forums.xandros.com/)
I really don't know which desktop environment Xandros uses, nor much else.

---

### Post by linuxaholik on 2011-01-19
no but what i need to do i copy this missing file in terminal with this code that you post???

---

### Post by linuxaholik on 2011-01-19
no but i need to copy the missing file in the terminal and the code that you post

---

### Post by Paqman on 2011-01-19
> **linuxaholik said:**
> when i go to the termina and write sudo synaptic

Slightly off topic, but you shouldn't be using sudo for graphical apps like Synaptic. Sudo is only for command line apps. For graphical apps you want to use gksu or gksudo.

---

### Post by linuxaholik on 2011-01-19
but when i writhe  the command on terminal gksu or gksudo then the terminal write that the command not found what should i do now:confused:

---

### Post by linuxaholik on 2011-01-19
but when i writhe  the command on terminal gksu or gksudo then the terminal write that the command not found what should i do now:confused:

---

### Post by linuxaholik on 2011-01-19
gksu and gksudo when i write in the terminal it dosent work why

---

### Post by oldos2er on 2011-01-19
I think you would find better help here: [http://forums.xandros.com/](http://forums.xandros.com/)

---

