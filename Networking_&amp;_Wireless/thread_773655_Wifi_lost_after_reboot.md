---
title: "Wifi lost after reboot"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by ali.gilani on 2008-04-29
I followed the instructions on these forums for setting up the wireless on a dell inspiron 6400 laptop and they worked perfectly. However every time i boot, the wifi indicator goes off and I have to put these two commands into the terminal where i unzipped the drivers:

sudo ndiswrapper -m
sudo modprobe ndiswrapper

why cant i make it permanent?

---

### Post by Alldan on 2008-04-29
install and use ndisgtk (ndisgtk is a GTK+ based frontend for ndiswrapper, allowing an easy way to install Windows wireless drivers).

---

### Post by ali.gilani on 2008-04-29
I tried installing ndisgtk, but it said its already installed. I could not find it however in the applications menu. I still have to type sudo modprobe ndiswrapper in the terminal everytime i boot to get the wireless to work.

---

### Post by Alldan on 2008-04-29
type ALT+F2 then gksudo ndisgtk

---

### Post by |{urse on 2008-04-29
or make a small bash script 

make a blank text file

```

cd Desktop
touch ndiswrapper
sudo nano ndiswrapper
[CODE]

#!/bin/bash
# type all this in the text file
cd /place/where/you/normally/go/to/do/this
sudo ndiswrapper -m
sudo modprobe ndiswrapper


```
press ctrl + k to save the document
save modified buffer = y
[/CODE]

click the menu > system > preferences > sessions and add the script you just made to it by clicking the add button and browsing to it.

now these action will be performed every time you log in

---

### Post by ali.gilani on 2008-05-01
hi, it didnt work fully.

before i would have to open the terminal and type in the commands, after which the light on my laptop for wifi would come on and then  the computer icon in the task bar would start searching for networks.

But now after i put in the bash file, the light is lit when i boot, but i have to go thru the entire process again to get the computer icon to start searching for networks.

heres how i put in the bash file.

I created a text file in my documents folder and added the code u gave me and put it under sessions option under the system menu.

---

