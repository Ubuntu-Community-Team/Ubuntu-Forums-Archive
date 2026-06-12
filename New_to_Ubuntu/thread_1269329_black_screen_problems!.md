---
title: "black screen problems!"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by nagasadow13 on 2009-09-18
black screen problems! i just recently installed ubuntu 9.04 as a second operating system on my asus eee pc 1000h i really enjoy it but i cannot seem to navigate away from the black screen. when i am booting up ubuntu 9.04 it is a black screen that starts off with a bunch of different stuff followed by
ubuntu 9.04 nagasadow13-laptop tty1
nagasadow13-laptop login:
password:
i type in the necessary information and then it reads
nagasadow13@nagasadow13-laptop:~$
i am aware of the various commands that are available for this but all i want to do is get back to the desktop and maybe learn how to go back and forth from the desktop to the black screen any help in this matter would be greatly greatly appreciated thank you!!

---

### Post by anewguy on 2009-09-18
Sounds like you need a video driver - without it, X is failing and you are falling back to the command line.

I would think there would be posts here already for the video on your netbook, but post back the output of the following:

(all done at the command prompt like you are getting)

lspci <press enter>

lsusb <press enter>

lshw <press enter>

Hopefully one of those will show the video adapter the PC is using and we can go from there.

Dave :)

---

### Post by abhiroopb on 2009-09-18
type "startx" that should take you to the desktop.

---

### Post by OffAxis on 2009-09-18
what version of ubuntu did you install?
The standard desktop version or the Netbook Remix Version?

According to this list:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201000H](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201000H)

Netbook Remix should work out of the box.

---

### Post by nagasadow13 on 2009-09-19
first off thanks to all of you for offering your help it is highly appreciated. to anewguy i tried all three commands there is a lot of information displayed but i dont know what in particular i should be looking for, any help? to abhiroopb i tried the 'startx' command but all it did was display 
'nagasadow13@nagasadow13-laptop:~$' 
also at the end of the line was a small box. it was displayed in a very small font size in the upper left hand corner of the screen i dont know what to do from here or if there is anything i can do, any suggestions? and to offaxis it is just ubuntu 9.04 generic and not the netbook remix. any help would be highly welcomed this whole thing is sort of driving me crazy! thank you

---

### Post by anewguy on 2009-09-19
I think I would follow offaxis' advice and download/install the netbook remix 9.04 edition - it is available at:

[http://www.ubuntu.com/getubuntu/download-netbook]("http://www.ubuntu.com/getubuntu/download-netbook")


Dave :)

---

