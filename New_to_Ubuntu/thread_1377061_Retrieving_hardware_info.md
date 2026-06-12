---
title: "Retrieving hardware info"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by lfpc2009 on 2010-01-09
Hi again,
 
Could somebody help me with the commands to retrieve the following harware information:
 
- sound card
- network card (I mean, PCI Card)
 
Thanks

---

### Post by CharlesA on 2010-01-09
Try using lspci.

```
lspci
```

---

### Post by starcannon on 2010-01-09
```

sudo lshw -html > ~/Desktop/hardware.html

```
This will give you a nice html formatted document with good information about every component in your computer.

lspci is also great as has already been mentioned.

GL, and come back and ask for more help if you need it.

---

### Post by AlexandreP on 2010-01-09
> **starcannon said:**
> ```

sudo lshw -html > ~/Desktop/hardware.html

```
This will give you a nice html formatted document with good information about every component in your computer.
I would add option *--class network,multimedia*, so only informations about the multimedia interfaces and the network interfaces will be put in the HTML report.

```

sudo lshw -html -c network,multimedia > ~/Desktop/hardware.html

```

---

### Post by Darce on 2010-01-09
Else, punch this into terminal :

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
``` 

and you'll have a html file called hardware_info in your home directory with all sorts of fabulous information !

Cheers,

Tim

---

### Post by lfpc2009 on 2010-01-10
Thanks a lot guys. I got all the info I needed and more!

---

