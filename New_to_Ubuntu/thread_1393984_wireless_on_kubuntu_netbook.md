---
title: "wireless on kubuntu netbook?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by j2the242 on 2010-01-30
I finally gave up on installing kubuntu netbook and upset myself by using wubi, but hey....I had to get away from windows.

So how come wireless internet doesnt work on kubuntu netbook??

If you are going to explain how to fix it please do so in layman's terms.....as I am not computer savvy, and FAR from Linux savvy. Thank you.


(running kubuntu netbook on an asus eeepc 1000hd, through wubi)

---

### Post by Ji Ruo on 2010-01-30
Since Kubuntu started using KDE 4 (from 9.04 onwards) you can't use wireless or mobile broadband with the new network manager they put in.

If you can use a wired connection, you could try installing WICD from the repositories. I've heard it works pretty well for wireless.

---

### Post by Ji Ruo on 2010-01-30
Um... perhaps that wasn't enough info for you...

I'm not sure if this program (WICD) will work because I haven't had to use wireless myself (I've had issues with mobile broadband on Kubuntu but that's a different story).

WICD is an alternative program that when you've installed it, should replace the network manager in Kubuntu which, as you can see, doesn't work. You can install it by using KPackageKit which you get to by clicking on the blue K button on the bottom left (from memory!) of the screen - so it's (K menu -> System -> KPackageKit Software Management).

Enter your password, and then you can search for: wicd

Install it, and then look for it in the menus and run it. Hopefully this will get your wireless working. If not, you can wait for someone else to help you here and you can also look for the kubuntu forums (unofficial but may be helpful).

---

### Post by Zorael on 2010-01-30
I haven't had any issues with the standard network manager (KNetworkManager) when connecting wirelessly or via a cable. I hear that for mobile broadband you need to manually edit a file or it won't work, though.

"It doesn't work" is very vague, so let's diagnose. It could be anything from the network manager being stupid (in which case Ji Ruo's suggestion of trying **wicd** would be appropriate) to there not being a proper driver available for the card. I'm assuming the wireless radio switch is on.

Enter the following in a terminal, and then find the file it creates in your home directory called **wlandebug.log**. It will ask for your password, but the command is harmless. Attach the output to a reply here - alternatively open it, copy its contents and paste it inbetween code tags.
```
sudo lshw -c network >> ~/wlandebug.log && sudo iwlist scan >> ~/wlandebug.log
```
After this we should know what wireless card you have, if it has a driver, and if it can see any networks.

---

### Post by kavoura on 2010-05-07
I tried booting my Asus Eeepc 901 with Kubuntu 10.04 in live mode, it does not recognise any wireless networking, although it does recognise bluetooth (although I did not test that).
In regards to WICD, can anyone confirm that it will work on a Kubuntu NR 10.04 installation?
Although so far, even though Kubuntu NR 10.04 looks great, its functioning is not that easy and I might choose something else to install on my netbook instead, e.g. in live mode I cannot find a way to change the system clock to 24-hour mode, although it is very easy to do that on my main PC running Ubuntu (perhaps this is a fault in KDE?).
Also, it would not recognise any webcams. Not the built-in one nor an external USB one. Nothing happens when I plug in the webcam. There does not seem to be any software installed for webcams. Is Kubuntu NR finished yet? The live CD/USB version seems to be lacking too much to be of any use.

---

### Post by Zorael on 2010-05-08
> **kavoura said:**
> I tried booting my Asus Eeepc 901 with Kubuntu 10.04 in live mode, it does not recognise any wireless networking, although it does recognise bluetooth (although I did not test that).
In regards to WICD, can anyone confirm that it will work on a Kubuntu NR 10.04 installation?
Although so far, even though Kubuntu NR 10.04 looks great, its functioning is not that easy and I might choose something else to install on my netbook instead, e.g. in live mode I cannot find a way to change the system clock to 24-hour mode, although it is very easy to do that on my main PC running Ubuntu (perhaps this is a fault in KDE?).
Also, it would not recognise any webcams. Not the built-in one nor an external USB one. Nothing happens when I plug in the webcam. There does not seem to be any software installed for webcams. Is Kubuntu NR finished yet? The live CD/USB version seems to be lacking too much to be of any use.

**Wireless**: Really depends on your machine. If you perform the commands I listed in my earlier post and attach the resulting logs here, we should be able to tell. WICD is just a different network manager than NetworkManager, so as long as there's driver support either should work.

**24-hour mode**: This is a locale setting global to KDE, so the first thing to do is to start up System Settings. Next into Regional & Language and not Time & Dates (which I'll concede can be a bit nonintuitive). Under the Country/Region & Language section you will find a Time & Dates tab, wherein you can set the time format.

**Webcams**: Like the wireless, it depends on your webcam models. Chances are they do work (meaning, there is driver support), but you're expecting something to automatically happen when you connect them. I'm not sure there are any "webcam applications" on the netbook live image, outside Kopete which only has some token webcam support. In the repostories there is **Kamoso**, which can take image snapshots, a series of images over time, and record videos. There is also Cheese but it's not a KDE application. I'm not going to vouch for either, but they're there.

**edit**: To see if the webcam has driver support at all, start up the **System Logs Viewer** after having connected the webcam. It should be in the netbook applications menu under System, else you can just hit Alt+F2 to get a run box to pop up and start typing 'system logs viewer' in there, or '**ksystemlog**'. Pick the Kernel view and see what it says at the bottom. If the window is too tall for your screen, Alt+click drag it to move it up a bit. Example cut and pasted from my netbook;
```
2010-05-08 11.02.03	usb 1-5		new high speed USB device using ehci_hcd and address 10
2010-05-08 11.02.03	uvcvideo	Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
2010-05-08 11.02.03	input		USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input13

```
If it lists it as an Unknown Device or something weird, obviously those are grounds for a bug report. Perhaps the camera isn't being configured correctly, or perhaps the drivers simply don't work with it yet.

Also if you run '**lsusb**' in a terminal it will list what USB devices are connected.
```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID **[COLOR="Green"]0c45:62c0[/color] Microdia Sonix USB 2.0 Camera**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

