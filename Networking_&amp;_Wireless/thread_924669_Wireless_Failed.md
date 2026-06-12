---
title: "Wireless Failed"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by acmariner99 on 2008-09-19
Hey all, first I would like to thank those of you who helped me get wireless running. Problems are back. Background: Vista is going haywire and Ubuntu is installed within Windows. I installed Xubuntu successfully onto its own partition in case of an OS crash. I went through the same procedure as before to get wireless running there. I downloaded b43-fwcutter as I have a brodcom wireless card, and installed the proper firmware. I did have to link to an ethernet to download the program. When Xubuntu failed to get wireless I went back to Ubuntu to check how the setup was done there, to my surprise, wireless is down there as well. (I cant see how the two Linux OS's are linked as they are on seperate partitions and cant see each other)

All I had to do was input the following command in the terminal:

sudo modprobe b43 (It worked for about a month)

the pretty blue light comes on, but I have no internet access. Please help, Vista is giving me fits and I need consistant wireless for Linux.

---

### Post by Bucky Ball on 2008-09-19
They wouldn't be linked, this could possibly be your router. Nothing changed there? In a terminal, what happens when you type (or paste):

                                        ```
sudo /etc/init.d/networking restart
```

---

### Post by acmariner99 on 2008-09-19
This is incredibly odd. I restarted Ubuntu numerous times with changes in network configuration and i still would not connect. I now have a connection. (It was random) I went back into Ubuntu to run the command in the previous response and lo and behold my wireless is up and running. I ran the network restart command and everything appears in order in Ubuntu. To clarify what information should I look at to ensure that the connection will work. lshw shows the proper modules with or without a connection.

---

### Post by Bucky Ball on 2008-09-19
In System->Admin->Hardware Drivers make sure the Broadcom B43 driver is ticked and in use. If it is not in use, untick, close, open Hardware Drivers again and tick. That should put it 'in use' and it should stay that way.

---

