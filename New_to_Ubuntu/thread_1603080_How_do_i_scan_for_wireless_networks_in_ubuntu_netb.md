---
title: "How do i scan for wireless networks in ubuntu netbook 10.10?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by KristinaK on 2010-10-22
How do i scan for wireless networks in ubuntu netbook 10.10?

---

### Post by silbak04 on 2010-10-22
You could try installing wireshark. I think this is what you're looking for.

```

$ sudo aptitude install wireshark

```

If you're not looking for wireshark...and just want to scan (look for wireless network around you) I'm sure you can just right click network manager at the bottom right corner, and it should show up all the scanned networks.

I hope this helps.

---

### Post by KristinaK on 2010-10-22
I can not see this in ubuntu 10.10 netbook, can you attach screenshot?

---

### Post by KristinaK on 2010-10-22
yes just want to look for wireless network around me

---

### Post by Hippytaff on 2010-10-22
networks should appear in network manager (ones in range that is)

---

### Post by KristinaK on 2010-10-22
please attach screenshot, cause it doesn't, and in Windows 7 I can see plenty of them

---

### Post by Hippytaff on 2010-10-22
> **KristinaK said:**
> please attach screenshot, cause it doesn't, and in Windows 7 I can see plenty of them
 
Sorry...not at home so not on my ubuntu box, it should be as easy as clicking on the icon that looks like a radar thing (bad description, but it should be fairly obvious that it is a wireless icon) on the right hand side of the top panel and a list should appear. If it doesn't click on show hidden networks. If your getting nothing you might need to enable wireless...if still no joy then we'll have to do a bit more digging :-)

---

### Post by gandaran on 2010-10-22
> **KristinaK said:**
> I can not see this in ubuntu 10.10 netbook, can you attach screenshot?
which ubuntu 10.10 do you have the desktop or the netbook version?
have you checked if wireless card is working or does it need to install the wireless card driver

---

### Post by Hippytaff on 2010-10-22
I can feel an
 
```

lspci

```
 
coming on :-)
 
If you need to troubleshoot, type the following commands into a terminal and post the results
 
```

lspci | grep wireless

```
 
```

iwconfig

```
 
```

lshw -c network

```

---

### Post by KristinaK on 2010-10-22
> **gandaran said:**
> which ubuntu 10.10 do you have the desktop or the netbook version?
have you checked if wireless card is working or does it need to install the wireless card driver

I use 10.10 netbook version

how to check if wireless card is working? I do not know how to use terminal

---

### Post by Hippytaff on 2010-10-22
open the terminal with CTRL+ALT+T and report the results of the commands above :-)

---

### Post by KristinaK on 2010-10-23
is there a way to see if it is working without going to terminal?

---

### Post by yetiman64 on 2010-10-23
Please note that I don't actually use netbook myself. However having googled for some images for you the 2 attached pictures may help you out.

Depending on how you are connected (wired or wireless) will determine which of the 2 pics below apply to you. 

In either case, left or right clicking on the icon used will bring up different menus. One of the 2 menus (I think it is left click though not 100 % certain) will show the local networks available around you. Hope this helps you and let us know if you find them :).

Edit: if they are not showing in here then it will be necessary to follow the instructions given in a terminal (Applications > Accessories > Terminal) as has been mentioned already. Using copy and paste is the most accurate way for you, as gandarin mentions below in post15.

---

### Post by Perfect Storm on 2010-10-23
Thread moved to beginner's forum.

---

### Post by gandaran on 2010-10-23
> **KristinaK said:**
> is there a way to see if it is working without going to terminal?
whats so difficult typing or copy/paste in terminal this command and hit enter?
```
lspci
```
and post all the results, so we can see what brand of wireless card you have.
I dont know if theres a system » administration » hardware drivers in the netbook edition but check it if theres a driver you can install.

---

### Post by KristinaK on 2010-11-05
> **Hippytaff said:**
> I can feel an
 
```

lspci

```
 
coming on :-)
 
If you need to troubleshoot, type the following commands into a terminal and post the results
 
```

lspci | grep wireless

```
 
```

iwconfig

```
 
```

lshw -c network

```

What these commands will do?

How to exit terminal?

---

### Post by Hippytaff on 2010-11-05
ok...so - lspci will list all pci devices and some information about them.

lspci | grep wireless will print the word 'wireless' in if it appears in any result of the lspci command.

iwconfig will show wireless information, much like ip config in windows, but for wireless troubleshooting instead.

lshw -C network will show detalais about what your network specific hardware is doing (in a way)

so there is nothing sinister in these commands...we're not hackers in the negative sense of the word, if that is what your worried about :-)

exit the terminal with
```

exit

```or click the 'x' in the top left of the window

---

### Post by KristinaK on 2010-11-06
what is this "-C" ?

---

### Post by KristinaK on 2010-11-06
lspci | grep wireless gives no results, maybe bad command?

---

### Post by KristinaK on 2010-11-06
iwconfig

lo no wireless extensions

eth0 no wireless extensions

---

### Post by QLee on 2010-11-06
> **KristinaK said:**
> what is this "-C" ?

This is not going to help with your question but it may be helpful information for the future. Whenever someone suggests running a command you can read the manual page for the command to see what it will do. If you still don't understand after that, and it sometimes happens because manual pages aren't always easy to understand, you can ask specific questions on the forum until you do understand. As Hippytaff states, most of us trying to help here are not crackers and don't want to give you malicious commands. Because of peer review (lots of eyes looking at the posts even if not replying) someone will warn you if you wait until you understand what a command will do. A lot of times people just watch because too many "helpers" firing questions and suggestions at a poster at the same time can be counter productive. I think you acted correctly by asking about the -C switch.

For example:
If you entered the command, man lshw, it would show you the manual page for lshw and you could see the -C refers to "class", which in this case is network because that is the type of hardware you are interested in. 


I'd make the guess that your wireless interface isn't "up", might even need a restricted driver but that is what the posters are trying to get you to do. Identify your hardware so they can help you get it working. That's the way most of us would proceed.

---

### Post by KristinaK on 2010-11-06
broadcom bcm43225 802.11b/g/n (rev1)

---

### Post by QLee on 2010-11-06
> **KristinaK said:**
> broadcom bcm43225 802.11b/g/n (rev1)
OK then. you'll want to have a look at this.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by KristinaK on 2010-11-06
Í have red but still don't know how to proceed... I am on live usb

---

### Post by Hippytaff on 2010-11-06
You either need to install the Broadcom Driver, or if it is installed  you may need to use usb_modeswitch so ubuntu recognises the usb dongle  as a wireless thing, rather than a usb storage device.

```

lsusb

```
will help identify the problem :-)

---

### Post by QLee on 2010-11-06
> **KristinaK said:**
> Í have red but still don't know how to proceed... I am on live usb
If you have read the step-by-step procedure on the site for your network interface chipset, then detail for us what part you don't understand so we can help. It is a step-by-step, telling you how to proceed.

---

### Post by arhant01 on 2013-01-01
This thread has not been able to give a solution to original question in my view. I face the same question - How to scan for new wireless connections. I see a network connections box through the control center but this is very manual approach. I'm sure there is a software/app with GUI where new connections can be searched for... Thanks

---

### Post by uRock on 2013-01-01
This thread is two years old. Please start a new thread with your issues. This will gain better results.

Thread Closed

---

