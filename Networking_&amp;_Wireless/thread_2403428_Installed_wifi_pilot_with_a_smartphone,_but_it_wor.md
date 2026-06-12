---
title: "Installed wifi pilot with a smartphone, but it works very bad"
date: 2018-10-11
forum: Networking &amp; Wireless
---

### Post by aubertinsylvain on 2018-10-11
Hi all ! Just after installing 18.04.1LTS, I had to install the wifi pilot. I am not at home and so wire link with web impossible. I tried to install wifi pilot with a smartphone. It is installed but works very bad. How to do for reinstalling a good wifi  pilot ? Thanks in advance.

---

### Post by aubertinsylvain on 2018-10-11
It seems to be a problem of antenna settings. Someone told me to put these 2 lines in the terminal:
sudo modprobe -r rtl8723de && sleep 5 && sudo modprobe rtl8723de ant_sel=2
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
I got the error message: sudo: tee/etc/modprobe.    command not found
My PC: @DESKTOP-N2A2JG7
Thanks in advance for your help

---

### Post by wildmanne39 on 2018-10-11
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by aubertinsylvain on 2018-10-12
I repeated the 2 lines on the terminal. Now every thing is OK.

---

### Post by coffeecat on 2018-10-12
> **aubertinsylvain said:**
> Someone told me to put these 2 lines in the terminal:
sudo modprobe -r rtl8723de && sleep 5 && sudo modprobe rtl8723de ant_sel=2
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
I got the error message: [color=red]sudo: tee/etc/modprobe.    command not found[/color]
My PC: @DESKTOP-N2A2JG7

> **aubertinsylvain said:**
> I repeated the 2 lines on the terminal. Now every thing is OK.

Have a look at the line I've highlighted in red in the quote from the earlier of your posts. If you copy-pasted the error message exactly, that means that you made an error in the command you quote in the previous line. Specifically there was no space between tee and /etc.

My guess is that when you repeated the two lines, there was no typo the second time. If you get an error message like that, look closely at it to make sure that the terminal command you are using is correct with no typos, missing spaces, or other errors. That's why it's a good idea to copy-paste terminal commands from published howtos to avoid typing errors.

---

