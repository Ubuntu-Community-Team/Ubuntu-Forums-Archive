---
title: "Wifi Very Slow!"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by CompizDoDo on 2009-07-16
ok i just installed Ubuntu 8.10 on someones computer for them and when i connect the wifi to my network it is extremely slow when i look it has full bars and then it sais 1.0mbs a second but my computer is connected to the same exact network and im getting very fast speeds at 54mbs a second so any help would be nice thanks

---

### Post by NightwishFan on 2009-07-16
What is your card? Perhaps you can search for a review on how well it is supported in Linux?

---

### Post by CompizDoDo on 2009-07-16
i actually dont know is there a way to check inside of linux?

---

### Post by cariboo on 2009-07-16
Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

The above command will print on screen all the details of your network devices.

---

### Post by NightwishFan on 2009-07-16
I know you find out using the lshw command in a terminal. I am not sure what to grep to get easier results.
```
sudo lshw
```

If you want a graphical tool for hardware information run this command in a terminal.

```
sudo apt-get update && sudo apt-get install hardinfo && hardinfo &
```

There should be a network tab. If the program does not autostart with the command, it might be under System -> Admin in the menus.

---

### Post by CompizDoDo on 2009-07-16
i type in the first command and it sais my wireless product is ar928x wireless network adapter (pci express)

---

### Post by ptn107 on 2009-07-16
Try a back-ported driver.  Sometimes the newer drivers work a lot better:
```
sudo aptitude install linux-backports-modules-intrepid
```

---

### Post by CompizDoDo on 2009-07-16
i tryed that command and it came up saying it doesnt have permission

---

### Post by NightwishFan on 2009-07-16
I would avoid trying the intrepid drivers until we narrow down on the problem.

---

### Post by CompizDoDo on 2009-07-16
ok so than what should i do

---

