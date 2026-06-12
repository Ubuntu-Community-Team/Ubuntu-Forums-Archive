---
title: "help with bcmwl5.inf"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by umdzig on 2005-07-25
I have installed ndiwswrapper. When i try to install the driver for my dell true mobile 1300, with the broadcom driver bcmwl5.inf all i get is this:  
[COLOR=DarkRed]
root@laptopmike:/home/zig # sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
ls: /etc/ndiswrapper: No such file or directory
Installing bcmwl5
cp: cannot stat `/root/Desktop/bcmwl5.inf': No such file or directory[/COLOR]


Any help is appreciated as this has been driving me crazy!

---

### Post by evilghost on 2005-07-25
~ is a shorthand representation for the home directory.  Since you're root, unless the .inf file is located on Root's desktop, this won't work.

Instead, use "/home/[username]/Desktop" in place of ~ where [username] is the username you use to login to Gnome/KDE.

---

### Post by umdzig on 2005-07-25
I took your advice and used /home/zig/Desktop/bcmwl5.inf instead of the ~ and this is what i got:

[COLOR=DarkRed]
root@laptopmike:/home/zig # sudo ndiswrapper -i /home/zig/Desktop/bcmwl5.inf
ls: /etc/ndiswrapper: No such file or directory
Installing bcmwl5
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter IBSSGMode|0 to IBSSGMode|2
[/COLOR]

I then tried sudo ndiswrapper -m and it said it created the alias Wlan0 however it is not in system> administration> networking or in netwrok tools. I tried  
sudo modprobe ndiswrapper and i got:

[COLOR=DarkRed]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/COLOR]

Thank you for your help

---

### Post by umdzig on 2005-07-25
Ok so i have done some searching in the forum and came accross a tutorial that if followed is supposed to help since it is for the driver i use (the site is [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) ). I followed the instructions and after i type "sudo modprobe ndiswrapper" i get:

[COLOR=DarkRed]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/COLOR]

So i decided to skip the part where it says to modify the conf file and everything works but i cant scan for an ap, so i cant connect to the network since i cant see them even though i know im in range.

This is a side note to what may be the problem (although im not a linux genious, but this part is bothering me and i dont know it means) After i install the driver it says: "ls: /etc/ndiswrapper: No such file or directory" but continues the installation anyway. Would this have to do with anything?

Again thanks for your help, as you are helping me gain more interest in linux.

---

### Post by umdzig on 2005-07-26
I have solved my wireless dilemma... for others that have the same problem:
type:
Do this for all the .conf files in your bcmwl5 file folder:

```
**sudo gedit /etc/ndiswrapper/bcmwl5/"your conf".conf**
``` (for me it's 14E4:4320.conf) and change radio state from** 1 to 0** and save.

next step: 

```
**sudo gedit /etc/modules**
``` and just add ndiswrapper to the list and save.

Next reboot your system. When you reboot it will probably say loading ndiswrapper, ignoring file 14E4:4320.conf...dont worry things should still work out fine! If that doesnt work turn off your other network connections. 
To fix the error when you boot up your machine saying ndiswrapper file XXXXXXX.conf~ is ignored:

This is done because gedit copys the old file and renames it with an ~ at the end, you can remove them with this:

```

**rm /etc/ndiswrapper/bcmwl5/"your conf".conf~**
```

Information from:
I found out all this by searching the [How To: configure wireless cards with Broadcom chipsets](http://ubuntuforums.org/showthread.php?t=25683&page=1&pp=10&highlight=bcmwl5)  and reading the post by andyk (post 97) as well as others.

---

