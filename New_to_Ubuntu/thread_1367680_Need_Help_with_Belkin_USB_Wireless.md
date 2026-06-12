---
title: "Need Help with Belkin USB Wireless"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Soolango on 2009-12-29
Hi Im a complete newb but I did search the forum and was not able to find an answer for my problem before asking. I just switched to Ubuntu 9.10 today and I am not able to get my Belkin USB wireless adapter to work. it is Model # F5D8053 . I know enough to know that its not "manufacture ready" for anything Linux and Ill probally need to change or download something but I havent a clue how to begin. If you can help that would be great but please remember there are alot of 12 yearolds who know more about computers then I do :) so PLEASE speak to me like I am an Idiot concerning this issue.
Thanks
Richard

---

### Post by RedSingularity on 2009-12-29
With the USB adapter plugged in go to 

System>Admin>Hardware drivers 

and see if you can activate the driver.

---

### Post by tom.swartz07 on 2009-12-29
Hi Richard.

Concerning your problem, I have a belkin f5d7050 wireless card that works right when you plug it in.

Lets make sure that youre up to date with everything, so that we're on the same page.

Go to system>administration>update manager and make sure that your computer is up to date.
Since you just installed your system, Im sure that there are a ton of updates waiting for you. 

Once thats all done, try plugging the WiFi card in, restarting (im sure that the update manager will ask you to restart) and see if the system recognizes the card from bootup.

If not, please open the terminal application (applications>accessories>terminal) and type 
```
ifconfig
```
and 
```
lshw
```

Paste the output of both back here.

---

### Post by bkratz on 2009-12-29
> **Soolango said:**
> Hi Im a complete newb but I did search the forum and was not able to find an answer for my problem before asking. I just switched to Ubuntu 9.10 today and I am not able to get my Belkin USB wireless adapter to work. it is Model # F5D8053 . I know enough to know that its not "manufacture ready" for anything Linux and Ill probally need to change or download something but I havent a clue how to begin. If you can help that would be great but please remember there are alot of 12 yearolds who know more about computers then I do :) so PLEASE speak to me like I am an Idiot concerning this issue.
Thanks
Richard

You might want to look at this page--

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

good luck

---

### Post by SeaJayEmm on 2009-12-30
First thing you need to do is hard wire your machine into your router, and update your system. Do this by going to terminal and typing "sudo apt-get update". After update is complete you need to get ndisgtk, do this by searching for it in synaptics package manager or by typing "sudo apt-get install ndisgtk" in terminal. 
Then you will need to get the install disc that came with the wireless adapter and copy over the .inf and .sys file from the winxp driver to a new folder on your desktop or to your home folder. Run ndisgtk buy typing "sudo ndisgtk" in a terminal, open the .inf file, click install. Reboot your machine and you should have wireless connection.

---

### Post by danastasio on 2009-12-30
oijeeze, I have that same adapter, I heard that there is a kernel patch for it but I couldnt get it to work, (this was also along time ago with Hardy). I'll keep an eye out for you.

---

