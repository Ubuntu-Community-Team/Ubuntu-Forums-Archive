---
title: "Netgear WNDA3100v2 install on Ubuntu 14.04"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by Richard_Ford on 2014-08-15
I am trying to install a Netgear WNDA3100v2 USB adaptor on my computer which is using Ubuntu 14.04. I have been trying to follow a thread by Chili555 and Mirianlibrarian about this. 

I have reached the point where I have the drivers on my desktop. While in the terminal I am trying to install them. I am using cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2. That is the name ofthe folder with the drivers. I keep getting a message saying that there is not such file or directory. Am I missing part of the path to the folder?

---

### Post by varunendra on 2014-08-15
Welcome to the forums Richard,

Can you give us link to the thread/post which you are following to install the driver? As well as the output of -
```
ls -l Desktop
```
The above code will show us the contents on your Desktop, you can edit the output before posting here. I just want to make sure the directory name is indeed Broadcom_bcm....

---

### Post by Richard_Ford on 2014-08-15
Hi, 

Thank you, I am sure I will be here quite a bit.

Here is the output:

mlpt@mlpt-HP-G72-Notebook-PC:~$ ls -l Desktop
total 24
drwxrwxr-x 2 mlpt mlpt 4096 Aug 14 22:24 Broadcom_bcm43xx_USB_32_64bit_v2
drwxrwxr-x 2 mlpt mlpt 4096 Aug 14 19:07 kali-linux-1.0.8-amd64
-rwxr-xr-x 1 mlpt mlpt  266 Aug 13 22:10 Notepad++.desktop
-rw-rw-r-- 1 mlpt mlpt  117 Aug 13 22:16 Terminal Commands.txt
drwxrwxr-x 2 mlpt mlpt 4096 Aug 14 19:24 Torrents
drwxrwxr-x 4 mlpt mlpt 4096 Aug 10 20:31 WNDA3100v2
mlpt@mlpt-HP-G72-Notebook-PC:~$ 

I forgot to put the thread in the post before, sorry about that, but here it is:

[URL="http://ubuntuforums.org/showthread.php?t=1964173"]http://ubuntuforums.org/showthread.php?t=1964173
[/URL]
I am at post #10...

---

### Post by Richard_Ford on 2014-08-15
Ok, I figured out that part, I did not need the end with amended. I am now in the right folder. 

I did sudo ndiswrapper -i bcmn43xx32.inf and this was the output:

mlpt@mlpt-HP-G72-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx32.inf
[sudo] password for mlpt: 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx32 ...
mlpt@mlpt-HP-G72-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ 

would the missing SourceDiskFiles section matter or is it ok ?

---

### Post by Richard_Ford on 2014-08-15
I was playing with it a little and I managed to install the 64 bit driver that I need. I am not sure now how to set it up so that I use the adaptor now

---

### Post by Richard_Ford on 2014-08-15
ndiswrapper -l :

mlpt@mlpt-HP-G72-Notebook-PC:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed
    device (0846:9011) present
mlpt@mlpt-HP-G72-Notebook-PC:~$ 

I did iwconfig like in post 10 on the thread I was following and got:

mlpt@mlpt-HP-G72-Notebook-PC:~$ iwconfig
wlan1     IEEE 802.11abg  ESSID:"Pri"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: B4:75:0E:57:04:38   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      no wireless extensions.

lo        no wireless extensions.

mlpt@mlpt-HP-G72-Notebook-PC:~$

---

### Post by varunendra on 2014-08-15
So it seems the problem is fixed? If not, what is it now?

---

### Post by Richard_Ford on 2014-08-15
lol, I guess the problem now is my computer is not detecting the adaptor when I try to set it up...

---

### Post by varunendra on 2014-08-15
> **Richard_Ford said:**
> lol, I guess the problem now is my computer is not detecting the adaptor when I try to set it up...
Then what was this -
> **Richard_Ford said:**
> ndiswrapper -l :

```
mlpt@mlpt-HP-G72-Notebook-PC:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    [COLOR="#0000CD"]**device (0846:9011) present**[/COLOR]
bcmn43xx64 : driver installed
    **[COLOR="#0000CD"]device (0846:9011) present[/COLOR]**
mlpt@mlpt-HP-G72-Notebook-PC:~$ 
```

I did iwconfig like in post 10 on the thread I was following and got:

```
mlpt@mlpt-HP-G72-Notebook-PC:~$ iwconfig
wlan1     IEEE 802.11abg  ESSID:"Pri"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: B4:75:0E:57:04:38   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
....

??

Those outputs clearly show it was found, and iwconfig part suggests it was even used as wlan1. Or is "wlan1" something different?

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**EDIT:**
It maybe that the existance of both 32bit and 64bit drives could be causing troubles. I suggest purge the drivers and try again with the package that chili555 attached in his post #6 there (you may need to use "...amended" in the cd command then). Then install ONLY the one that you need, not 32 and 64 bit both.

---

### Post by Richard_Ford on 2014-08-15
I will check that link out in your signature.

I am not sure how to find it to use as the wireless. I tried running the program that came with it on a cd, but it prompts me to plug the adaptor in and after a minute or two it says it does not detect any adaptor so that is why I am thinking it does not recognize it?

---

### Post by varunendra on 2014-08-15
Program that came with it on a CD? Do you mean a program that is originally meant for Windows (so running over "wine" in Ubuntu)? That is neither required nor any helpful. Just forget it and use the Network Manager in Ubuntu to use the adapter.

I hope you also read my edit in the previous post.

---

### Post by Richard_Ford on 2014-08-16
I will try to remove the 32 bit drivers and not even bother with the cd anymore. 

I was also wondering, how can I switch wlan1? It is the card that the computer had installed originally. I thought I should have a wlan0?

---

### Post by varunendra on 2014-08-17
> **Richard_Ford said:**
> I was also wondering, how can I switch wlan1? It is the card that the computer had installed originally. I thought I should have a wlan0?
If it was the first wireless card the system detected, then yes, it should have been named "wlan0". New numbers (wlan1, wlan2 etc.) are added as new cards/adapters are detected and added to the system. Sometimes a driver also chooses to force a name on an interface, and sometimes it is the OS itself that assigns a different name to the same card if it starts using a different driver than the original one - that part is done for functional consistency of the system.

The logical names are stored/read from the udev rules file - "/etc/udev/rules.d/70-persistent-net.rules"

To see how the names are assigned, you can simply read that file -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

To reset all the names, deleting any interface names/configuration for cards that no longer exist in the system, simply delete the above file -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

It will be automatically regenerated as soon as required, containing only freshly assigned names (starting from wlan0, eth0 etc. again).

---

### Post by Trad_dog on 2014-08-30
Hi there, 

I have a pretty similar issue although I guess my set up is the cause for the wireless usb not working. 
I have an internal wifi card that chili55 manage to make work a long time ago. However, I realise
I cannot connect in most hot spots through the internal card. 
I thought I should try with a dual band wifi device. The shop where I went had hardly any choice
and it looked like the issue for the Netgear WNDA3100v2 had been solved. So I picked up that
one. 
I came back and proceeded to install ndiswrapper and the driver. At the begining, I had not realised
you could not have both cards activated. Then I switch off the internal card. But I still cannot connect
to the network. I tried a couple of other drivers to no avail. I probably missed a step somewhere and
further trials probably messed up the install. 
Here is what I can see currently:
```

Presario-C700-Notebook-PC:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present

```
```

Presario-C700-Notebook-PC:~$ iwconfig
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"virginmedia6249288"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 04:A1:51:2D:3C:C8   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```
```

Presario-C700-Notebook-PC:~$ dmesg | grep ndis
[   18.100337] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   18.101805] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   19.586069] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   19.848960] usbcore: registered new interface driver ndiswrapper
[  707.848750] ndiswrapper: device wlan1 removed
[  710.122205] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded

```
Well that almost the status, as I have to switch back to wlan0 -- the internal wifi card -- to be 
able to send this post. 
It looks to me as everything is fine but if I turn wlan0 off and wlan1 up, trying to connect to the wifi
router does not succeed. 
Any help would be appreciated. 

Best

Trad

---

### Post by varunendra on 2014-09-01
> **Trad_dog said:**
> ..The shop where I went had hardly any choice
and it looked like the issue for the Netgear WNDA3100v2 had been solved. So I picked up that
one.

Hi Trad,

Anything that requires ndiswrapper - I wouldn't consider it a 'solved' problem at all. I don't have any experience with ndiswrapper related issues, and I don't think there is much to try with it except loading different versions of windows drivers then crossing fingers, toes even.

I suggest you start a new thread instead of posting in existing ones, and post the [post=13024222]wireless_script[/post] report in it, along with other relevant background details and a description of the problem.

I hope someone more experienced with that card or ndiswrapper will pick it up and could possibly lead you to the solution. I may not be able to offer any good help with it.

---

### Post by Trad_dog on 2014-09-02
Hi Varun,

Hindsightful advice that I am going to follow. 

Thanks and best

---

