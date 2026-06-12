---
title: "Network configuration using adsl modem(d-link 2700u)"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by daniel180 on 2014-08-13
Hi Everyone
I am relatively new to ubuntu. I am using an ubuntu version 12.04 LTS. I have an ADSL modem(D-LINK 2700U). I am unable to configure the modem with ubuntu. I am also unable to change the network settings of the network adaptor. Tried ifconfig for configuration, but still no luck. Please help me with this. I have an installation CD which I got with the modem. That CD tells me to use a web browser and type the ip address 192.168.1.1, which I did but of no use. Please help me out.

Regards

---

### Post by varunendra on 2014-08-14
Welcome to Ubuntu Forums Daniel!

Please open a terminal (Ctrl-Alt-T), and post back the output of -
```
sudo lshw -C network
```
You don't need to post the full output if you have to type them by hand. I'm just interested in these parts -

1) Product name
2) Logical name
3) Size (how much Mb/s ?)
4) Capacity (how much Mb/s there?)
5) Driver, duplex, link, speed (all in the line starting with "configuration" at the bottom)

Make sure the cable is connected and in the state where it is supposed to be working while you run the 'lshw' command.

You can also just copy-paste the output from the terminal to a text file using your mouse cursor, then past the contents from the text file into your post here (make sure to choose "Line Ending" to "Windows" while saving the file if you are going to copy-paste the contents from a Windows machine, else the line breaks will be messed up). If you do this, please use **'Code' tags** while posting the output here. Please follow the "Use Code Tags" link in my signature below to see how.

---

