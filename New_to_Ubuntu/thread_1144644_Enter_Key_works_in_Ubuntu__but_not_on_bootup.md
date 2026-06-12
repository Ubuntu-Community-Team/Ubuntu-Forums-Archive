---
title: "Enter Key works in Ubuntu  but not on bootup"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by abrand888 on 2009-04-30
I have this problem in 8.10 and now 9.04. I have a interesting setup. I am using a KVM between two computers. On either my HP or Intel system, my mouse and keyboard work flawlessly. As soon as I switch from my HP to my Intel, everything is working fine. When I run a live session on my Intel or HP, when the screen comes up with the countdown from 30 sec to 0 sec, the enter key doesn't work at all but when Ubuntu boots up successfully, and I go in text editor or terminal, I can type without any problems, I can hit the enter button so I automatically go to the next line, the keyboard works normally. I think there is a bug in bootup.

---

### Post by jerrrys on 2009-05-03
is your KVM software wired or hardware wired...i have great luck with with no software and not so good with software...

---

### Post by blueridgedog on 2009-05-03
I suspect your KVM switch is not sending a signal when the Ubuntu box is not selected.  The cheaper ones do not and therefore the BIOS of the system thinks there is no keyboard present.  Just a guess.

---

### Post by abrand888 on 2009-05-04
My unit is a commercial unit made by Belkin. This kvm uses the power from the individual systems. It works on two Window systems that are connected to flawlessly but doesn't seem to be recognized in Ubuntu. I tried a separate usb keyboard and upon bootup worked well with Ubuntu and after Ubuntu booted up, I was able to use two keyboards. To me it sounds weird.

---

### Post by blueridgedog on 2009-05-04
Don't get hung up on "cheaper" in my post.  What I meant to imply was that not all KVM devices send a phantom keyboard and mouse to the non-selected device and this typically causes problem when you switch in and out of the bios which lack's the ability to detect a keyboard change event.

One way to test this would be to swith to a fully booted and logged in Ubuntu, and run dmesg, then swith out - waiting a while, then back and see if dmesg then reports that there has been a USB change.

---

### Post by abrand888 on 2009-05-04
Hi,
I connected a usb keyboard and usb mouse to my computer running the live session of Ubuntu. The keyboard worked as soon as Ubuntu started counting downward and went into loading Ubuntu. I had to leave the kvm connected otherwise I couldn't see anything on the monitor. After Ubuntu loaded, I was able to use two keyboards and two mouses. dmesg_ is the first time I ran it, dmesg_2 is the second time after I closed the the terminal.

---

### Post by blueridgedog on 2009-05-05
What I was hoping to get was for you to use the KVM, not another keyboard, then switch to the Ubuntu system and look in dmesg to see if it saw a USB event.  This would indicate that it was not getting the keyboard keepalive signal from the KVM when not selected and would explain the issue you see.  

I am not certain if that was the process you followed, but I do not see any USB activity in the two logs posted.

---

### Post by abrand888 on 2009-05-05
Please list the steps you would like me to try. I thought you meant another keyboard.

---

### Post by blueridgedog on 2009-05-05
The idea is to see if there is a USB event when you switch the KVM to the Ubuntu box.  To test this, you can look at dmesg, then switch out of the Ubuntu box then back and look at dmesg again.  If there is a USB event, then it may be that the KVM is not sending the keepalive keyboard/mouse signal when the Ubuntu box is not selected, hence the reason that the bios can't see the keyboard.

---

### Post by abrand888 on 2009-05-06
will try it tonight. At what line is a reference to usb event ? I also bought another keyboard to see if it might be the keyboard.

---

### Post by blueridgedog on 2009-05-06
It would be pretty easy to see, in fact you can plug and unplug the keyboard and see the result.  If you get that result when switching the KVM, then it may be the cause.

---

### Post by abrand888 on 2009-05-11
Hi,
I have been thinking about this problem and would like to try the following if it makes sense. The thing unique to the kvm is that the outputs are basically ps/2 4 pin connectors. In order to use it on the Intel system, I am using a y connector that has two ps/2 inputs going out thru a usb connector going to the motherboard. What if I directly connect the mouse and keyboards to this connector to my Intel system and see if the keyboard works like it should. If it does, then my problem is the kvm only for the switching not working properly. 

As far as running dmesg, I am confused because you stated you didn't see any usb activity in either txt files. Would running dmesg withh the connectors directlyt show any usb activity ?

Is there any way to change the default bootup time from 30 sec to 5 sec ?

---

### Post by blueridgedog on 2009-05-11
The second post in this thread talks about reducing the timeout:

[http://ubuntuforums.org/showthread.php?t=1155383&highlight=grub+30+seconds](http://ubuntuforums.org/showthread.php?t=1155383&highlight=grub+30+seconds)

Your plan sounds great to test.

---

### Post by abrand888 on 2009-05-11
Blueridgedog,

You won't believe this but the kvm isn't the culprit because when I disconnected the mouse and keyboard from the kvm input and connected to the ps2-usb converter, I had no video. It must make a complete circuit of graphics, mouse and keyboard to work. So I connected the monitor directly to my Intel system, with the keyboard and mouse to the adapter and the keyboard would not work. I connected a second keyboard and it still didn't work. It only worked when I used the usb keyboard. So the ps2-usb converter cable is the culprit. As far as speeding up boot times, I think the link you gave me is for a complete install. I am using the live session and I can't change anything on a cd yet. I think I did good detective work.

---

### Post by blueridgedog on 2009-05-12
Yes...great detective work.  I am sorry that I missed the fact that you are on the LiveCD.  The CD run time is so slow, I am surprised you can stand it.  If you want to run Ubuntu w/out installing it, I have had luck and satisfaction with a USB thumb drive (flash drive).  You can get a live install working or an updatable one.

---

### Post by abrand888 on 2009-05-12
How can I make a usb install on a thumb drive ? It is amazing how cheap they are today. If I install it on a usb flash drive then I could modify it to boot instantly.

---

### Post by abrand888 on 2009-05-12
the converter cable is made by Inland products so I sent them a email to tell them of my problem. Lets see what they have to say.

---

### Post by blueridgedog on 2009-05-12
> **abrand888 said:**
> How can I make a usb install on a thumb drive ? It is amazing how cheap they are today. If I install it on a usb flash drive then I could modify it to boot instantly.

This site is a good starter:

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by abrand888 on 2009-05-12
Hi,

I see that Ubuntu 9.04 has a USB startup disc creator in administration. Is the link you gave better than the 9.04 Ubuntu
cd ?

---

### Post by blueridgedog on 2009-05-13
I do not know if the one that Jaunty makes is persistent...which is what you want so you can make changes and customize it.  It would not hurt to try them and decide which works for you.

---

### Post by abrand888 on 2009-05-13
what do you mean by persistent ? I will buy a few 2 gb flash drives and play around with them. The reason I was using the Live version is because no one can write to a cd. In my house I go on line with a Live version of Jaunty and save my downloads to a external usb flash drive. After I downloaded some downloads, I reboot into Windows and run Kapersky Anti-virus to make certain these files do not have unwelcomed guests. If I can boot from a flash drive and save downloads to a download partition on the usb flash drive, I imagine that after I close down Ubuntu, pull out the flash drive, boot back into windows, run anti-virus and see that the files are clean would work the same way.

---

### Post by blueridgedog on 2009-05-13
Persistent means that you can make changes and they will survive a reboot. This includes customizing a shell, your desktop, installing new applications or running updates for example.

It appears that you do not need a persistent install based on your usage.

---

### Post by abrand888 on 2009-05-19
blueridgedog,
I finally got a reply from inlandproducts.

Hello,
The way how our adapter works:
It has an integrated USB hub that has two "USB HID" (Human Interface Device)converters which does the translating between USB and PS/2.  The problem is that Ubuntu only loads the "USB HID" drivers during that menu; it doesn't load the "USB HUB" drivers until it boots.
You can modify your Ubutnu live CD to load the "USB HUB" drivers before that menu, but you would have to hunt on their forums on how to do that. 

HINT:
modify the ISO file before you burn it.

I  guess I should leave it alone and wait 30 seconds. I look forward to your thoughts

---

