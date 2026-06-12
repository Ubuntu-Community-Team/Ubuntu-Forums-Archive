---
title: "Issue with ndiswrapper and usb wireless card"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by aswells on 2007-02-22
I have been trying to get my dwl-132 d-link wireless usb card working for the last few days. I have searched through the forms, and after following all advice I read about still have no luck. 

I pull the folder with the wireless drivers straight off of the installation cd that came with the adapter so that the .cab, .sys and .bin files are all still in the same folder as the .inf files. I change to that directory, and install both the athfmwdl.inf and neta5agu.inf drivers. The output fron ndiswrapper -l is 

```
Installed ndis drivers:
athfmwdl        driver present, hardware present 
neta5agu        driver present, hardware present 


```

I then run sudo depmod -a and get no errors, but when I use sudo modprobe ndiswrapper, it looks like the command executes fine, but I do not get any response from my wireless card. I am at a loss and cannot think of what is going wrong.

Any commands whos outputs I should post, let me know and Ill get them asap.

*EDIT* I also tried downloading the latest drivers from the D-Link website and had the same results. modprobe ndiswrapper appears to execute without any errors, but I get no response from the adapter.

---

### Post by teaker1s on 2007-02-22
try installing
ndiswrapper-utils-1.9
it revived my wireless on feisty

---

### Post by aswells on 2007-02-22
I searched in synaptic, but the closest I found was ndiswrapper-utils-1.8. I think this is because I am running Edgy Eft instead of Feisty. I still get the same result from modprobe ndiswrapper.

---

### Post by teaker1s on 2007-02-22
the latest kernel update has broken wireless for some people in terminal

```
uname -r
```


if its the   2.6.17-11 kernel 
[http://www.ubuntuforums.org/showthread.php?t=358004]("http://www.ubuntuforums.org/showthread.php?t=358004")

---

### Post by aswells on 2007-02-22
Im not sure if it is the same thing, but the output I got was

```
2.6.17-11-generic

```

Im reading the link you sent me right now.

---

### Post by aswells on 2007-02-22
Booting onto the older kernel seems to have solved my problem. Now, I put the usb card in, and it immediately lights up and I see the wireless option in the network manager. There arent any wireless signals available in my dorm room, but next time im at the library, which will be tomorrow morning, Ill give it a try and post the results. Thanks for your help!

---

### Post by aswells on 2007-02-23
After testing the wireless this morning, I think I am very close to having working wireless capabilities. When I plug in the usb adapter, it lights up and all is well. As soon as it picks up a signal and the second light starts to blink (thats how I know its connecting to a signal) my comp totally locks up. No keyboard response, touchpad goes dead, have to reboot by holding the power button. Reminds me of what I read happened when your kernel crashes. What could be causing this?

For the record, I am now using kernel 2.6.17-10 on Ubuntu Edgy.

*EDIT* I get the same result when I remove ndiswrapper from /etc/modules and load the drivers after the usb device is inserted. Im going to try installing a different set of drivers this afternoon, that might solve the problem. But if anyone thinks that there is a problem other than bad drivers, please let me know.

---

### Post by aswells on 2007-02-23
Installing different (older) drivers didnt yield any positive results. If there is some problem with the kernel not being able to deal with the new drivers, I am going to need some help on how to deal with that. Maybe blacklisting the native drivers?

---

### Post by aswells on 2007-02-25
After a few more tests, I can confirm that ubuntu deals with the wireless card fine, the lights turn on like they are supposed to. But as soon as it trys to connect with a network, the kernel crashes. Blacklisting the native drivers had no effect. 

This is the last think keeping me booting into windows after I got ventrilo and guild wars running in wine/cedega. I am willing to do all the research in the world on how to do what is necessary to make this work, but have no idea what I need to learn how to do. Any help would be greatly appreciated, and any outputs from the command line that are needed will be retrieved asap.

---

### Post by dxdemetriou on 2007-02-26
I had the same problem with my DWL-G132. If you go to tty1 you will see the message why crash. The first problem you have I solved it with the ndiswrapper-1.34.tar.gz that I compiled it myself. Then I have downloaded the shipping drivers (not from the cd). Check the supported devices rom site, and check with the lsusb. With the new release of ndiswrapper and the shipping drivers it solved the problem of crash, and also it works when I unplug and replug the usb.
Must be some modifications to /etc/modprobe.d/blacklist-ath (blacklist ath), and /etc/modprobe.d/blacklist (blacklist bcm43xx) .
Then I started to work with wpa, but I don't remember now. When I have all clean, I'll write them down.
Sorry about my english :)

---

### Post by aswells on 2007-02-27
After recompiling the newest version of wine, blacklisting bcm43xx(I was trying to figure out the native drivers for days, thanks for the tip) and installing the shipping drivers downloaded from the D-Link website, my wireless card works very nicely : ) Dont worry about your english,dxdemetriou, I had no problem reading what you were saying.

Thanks for the help everyone!

---

### Post by dxdemetriou on 2007-03-01
The only problem I have now is that I have the Airplus Xtreme 108G router (DI-624), and the usb don't reach that speed, even with the booster, but it show 108Mbits. Anyway, somehow I'll find why this happens..

---

### Post by frafu on 2007-04-18
@aswells


Could you please tell me whether wpa with psk also works with your dwl-g132? 


Concerning the blacklisting: is this right: 

- I have to write 
blacklist bcm43xx
in /etc/modprobe.d/blacklist 

- I have to write 
blacklist ath
in /etc/modprobe.d/blacklist-ath

Is the above right concerning the blacklisting? 


Further, is there a way to make the configuration persistent also through the updates of ubuntu? (for example for kernels or ndiswrapper updates)


Many thanks in advance. 

Francesco

---

### Post by aswells on 2007-04-18
I cant tell you about wpa, none of the signals I use around here are encrypted using it. Those are the correct steps to take to blacklist bcm43xx and ath.

As far as I know, every time you upgrade ndiswrapper or change kernels you will need to re-install the drivers, but the changes you make to blacklist and blacklist-ath should stick around.

---

### Post by frafu on 2007-04-18
@aswells

Thanks for your reply.

---

### Post by scrooge_74 on 2007-04-23
Guys, I had to install this wireless card for a friend today,

After installing ndiswrapper, getting the drivers from a windows dir (which I had to get using wine since I did not had any Windows PC around)
Installing the two drivers with ndiswrapper
Then modprobe ndiswrapper
add ndisprapper to /etc/modules

It works like a charm

All of this on an Xubuntu 6,10 laptop

---

### Post by frafu on 2007-04-24
@scrooge_74

Could you please tell me whether wpa with psk also works with your dwl-g132?

---

### Post by scrooge_74 on 2007-04-24
Can tell you since in the hotel they just use WEP, for work arounds I have been using wifi-radar and Network-manager applet 

I still has some issues, it will boot and be able to use the card fine, other times it will not let it use it, I have to modprobe -r ndiswrapper and later modprobe -i ndiswrapper for it to work.

any ideas?

---

### Post by frafu on 2007-04-25
Thanks for your feedback and I hope that you get your issues solved. (When I tried to configure it several weeks ago on a friends computer, I was not successful.)

---

### Post by scrooge_74 on 2007-04-25
Did not had to much luck, it seems even when I took out any trace of drivers, aliases, etc the card will not come back to live, it will even lock the computer when booting until I removed the card from the slot,  Also USB ports will not read any usb stick after

---

### Post by aswells on 2007-05-14
Having the usb adapter in when you boot your computer will cause it to either lock up or cause all sorts of problems. For best results, boot your computer completely before inserting the adapter.

That same thing happened to me before I blacklisted the native drivers, be absolutely sure you did that (I misspelled one of them at one point).

---

