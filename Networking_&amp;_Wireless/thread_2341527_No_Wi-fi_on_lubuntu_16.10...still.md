---
title: "No Wi-fi on lubuntu 16.10...still"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by roarinflames on 2016-10-28
I decided to install Lubuntu 16.10 on an Acer AOD250, since W10 wrecked my hard drive a couple weeks ago (and was sluggish anyway). This IS my first rodeo with any linux distro, so I am very wet behind the ears when it comes to using the terminal.
I was initially plagued with no internet connection whatsoever. After a night of struggles, I managed to get the LAN connection to finally work, expecting it would also enable the wireless connection. It did not.:(

Things I've tried:
Additional Drivers->selected 'Broadcom STA' , rebooted
sudo apt-get update
install/reinstall bcmwl-kernel-source
install/reinstall firmware-b43-lpphy-installer; would not install, apparently obsolete
ndiswrapper with windows driver (i very likely did this wrong)

No wifi on a netbook really sucks, but after hours of googling and trying different methods, I figured I either suck at the search bar or suck at following instructions.

I should also add that I'm pretty certain it's a Broadcom unit, unless the following command only gives info based on the installed driver.
```
lspci -nn -d 14e4:
```
^^This says I have a Broadcom Limited BCM4312 802.11b/g LP-PHY unit

Any suggestions on what to try next/again?

[Edit]:forgot to mention, 'rfkill list all' shows 'soft block:no' and 'hard block:no'
[Edit2]: added info to 'tried' list and added possible wireless card info

---

### Post by howefield on 2016-10-29
Hello and welcome to the forums, I have moved your thread to the "*Networking & Wireless*" forum as a better place for you to get help.

In the meantime I'd suggest that you read the sticky thread [here]("https://ubuntuforums.org/showthread.php?t=370108") and supply the wireless info script as described.

---

### Post by roarinflames on 2016-10-29
I appreciate the move, and the link to the sticky. I've attached the wireless-info.tar.gz file as instructed.
Also, reading through the sticky, I didn't find my wireless card (BCM4312) in the list of supported cards, but I'm still hoping there's some way to get this card to work.
[ATTACH]271847[/ATTACH]

---

### Post by wildmanne39 on 2016-10-29
Please do:
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
Then:
```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by roarinflames on 2016-10-29
Ok, rebooted and I still got nothing.

---

### Post by wildmanne39 on 2016-10-29
Please run the wireless script again and post the new results here.
Thanks

---

### Post by roarinflames on 2016-10-29
Here you go, thanks for the help thus far.
[ATTACH]271849[/ATTACH]

---

### Post by wildmanne39 on 2016-10-29
Did you run the commands I gave you in my first post? because nothing has changed, ndiswrapper is still installed and the correct driver is not being used.

You just copy and paste the commands into the terminal and watch for errors, after you enter the command you will have to enter your password but it will not be displayed on the screen so when you have finished entering it just hit enter key

---

### Post by roarinflames on 2016-10-29
I must have posted the same file by mistake. When I run the commands you provided again, it states ndiswrapper is not even installed and thus can't be removed.

I deleted the file instead of overwriting it like last time, so this is absolutely the new file.
[ATTACH]271851[/ATTACH]
If this shows the same thing as last time, then I have no idea why.

[Edit]: I'm currently viewing the forum from my main pc, so I can't just copy/paste. That said, I double checked each time I ran the provided commands to be sure there were no errors.

---

### Post by wildmanne39 on 2016-10-29
First every time you run the script it overwrites the old one so you do not have to and you always have the newest file.

The commands other then the purge command you need an internet connection, where you connected by wire or tethered to a cell phone?

Please run the commands again and post all the output here using code tags.
Thanks

---

### Post by roarinflames on 2016-10-29
I am running these with a direct ethernet connection. I've also switched over to strictly using the netbook, so this time I copy/pasted.

```
zain@nTop:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
[sudo] password for zain: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper' instead of 'ndiswrapper-common'
Package 'ndisgtk' is not installed, so not removed
Package 'ndiswrapper-utils-1.9' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ndiswrapper ndiswrapper-dkms
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
zain@nTop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version (1:019-3).
The following packages were automatically installed and are no longer required:
  ndiswrapper ndiswrapper-dkms
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by wildmanne39 on 2016-10-29
Lets do:
```
sudo apt autoremove
```
to remove ndiswrapper ndiswrapper-dkms.
Then try:
```
sudo modprobe b43
```
does wireless come on?

---

### Post by roarinflames on 2016-10-29
My god, you're a wizard.
I can't thank you enough.

[Edit]: Is this temporary? or should I reboot to be sure?
[Edit2]: I've noticed a slight bug when i go to select anything in the connections taskbar menu. It basically gives me about a second to select something before it closes. Is this because I have 'autohide' enabled?

---

### Post by wildmanne39 on 2016-10-29
> Is this temporary? or should I reboot to be sure?
Please do the following to make the driver load at boot every time.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
About the other issue please start a thread in the appropriate section with a descriptive title because I do not know the the answer to that.

---

### Post by roarinflames on 2016-10-29
> **Wild Man said:**
> Please do the following to make the driver load at boot every time.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
About the other issue please start a thread in the appropriate section with a descriptive title because I do not know the the answer to that.

Fantastic, thank you again!

Also, disabling the auto-hide panel fixed my other issue.

I appreciate all the help, I was definitely lost without it.:D:D

---

### Post by wildmanne39 on 2016-10-29
Your welcome!
Enjoy!

---

