---
title: "Sharing bluetooth mouse between Windows and Ubuntu"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by axos88 on 2008-04-24
Hello!

I have a Mac mighty mouse which I have been using under Windows. 

I want to switch to Ubuntu, but because games don't really work under Ubuntu, I have to stick with windows for a while for gaming. 

I would really like to be able to share the mouse between Ubuntu and Windows so that I don't have to pair up every time I boot into the other operating system. Actually not being able to do this slows down my switch considerably, because I keep booting into Windows out of convinience. There should be a way to extract the link key from windows and register it under linux... I suppose that is a kind of a hack, but maybe there are better ways?

HW:
  Asus F3SV
  Mighty mouse

SW: 
  Windows XP: Toshiba Bluetooth manager

(I don't think anything else is of interest)



Thanks for your help,
    axos88

---

### Post by steveneo on 2008-08-15
My mighty mouse does not works for 8.04. Ubuntu can find bluetooth device and show mighty mouse on device list as well. But mouse never works. 


I have same problem to switch back to window.

---

### Post by tarvtarv on 2008-08-28
Hey there Im New to the Whole Linux System Im Impressed So far Just that i Have the same problem as You Aswell 

"I have a Mac mighty mouse which I have been using under Windows."

I really want to get on with my work so if anybody knows the solution Please share

---

### Post by roy430 on 2008-11-03
bump for a similar issue. 
(want to share a bluetooth mouse between my macboook and linux box)

---

### Post by jbiggs12 on 2009-01-28
bump again.
I want my trackpad to appear as a mouse on bluetooth (penryn macbook pro)

---

### Post by Platypus222 on 2009-05-03
OK, I think I figured it out. In Windows (I'm using XP), go to Control Panel > Bluetooth Devices> Hardware> Properties > Advanced. Here, it shows you the radio's name and address. Copy these down or remember them or whatever.

Now, in Ubuntu (I'm using 9.04), open the terminal and type```
hciconfig
```The BD Address given should match the radio address in Windows, seeing as how it's the same physical machine. Now, type ```
hciconfig hciX name "name"
``` where "name" is the name of your Bluetooth radio in Windows. Alternately, you can go to Ubuntu's Bluetooth preferences and change the "Friendly Name" to this name.

Or, you could do the reverse of this and change the one in Windows to match that in Ubuntu. Either one should work just fine.

Next, you'll need to connect your mouse in both OSes, making sure to use the same passkey/PIN (or to not use one).

Both OSes should recognize the mouse immediately upon activation. Depending on the mouse, you may need to turn it off and back on upon changing OSes.

This is what worked with me, but your mileage may vary. Good luck!

Oh, and as an unrelated note, having just started with Ubuntu recently, I'd like to thank the entirety of ubuntuforums.org for being so damn helpful!

---

### Post by Platypus222 on 2010-02-17
I just got this reply as a PM from dgttm ([http://ubuntuforums.org/member.php?u=1019330](http://ubuntuforums.org/member.php?u=1019330)). I thought it might be of some help to someone in the future.

hi,

could you please help me a little more with your explanation how to get a  bluetooth mouse working with a dual boot windows + linux laptop..

(this is the thread: [http://ubuntuforums.org/showthread.php?t=764756](http://ubuntuforums.org/showthread.php?t=764756))


could you please tell me, which values exactly got be replaced with  hciconfig and where to find them in windows (i have windows 7). 

I just changed the name to the same name in windows and linux but it is  still not recognized and requests a password/key.


thank you very much

Nicolas

---

### Post by Platypus222 on 2010-02-17
> **dgttm said:**
>  
hi, 
 
could you please help me a little more with your explanation how to get a bluetooth mouse working with a dual boot windows + linux laptop.. 
 
(this is the thread: [http://ubuntuforums.org/showthread.php?t=764756](http://ubuntuforums.org/showthread.php?t=764756)) 
 
 
could you please tell me, which values exactly got be replaced with hciconfig and where to find them in windows (i have windows 7). 
 
I just changed the name to the same name in windows and linux but it is still not recognized and requests a password/key. 
 
 
thank you very much 
 
Nicolas 
 
OK, so since the original post, I've upgraded to Windows 7 and Ubuntu 9.10, so let's see what's different. 
 
In Windows, go to Bluetooth Settings (in the Start Menu, type in "bluetooth" and choose "Change Bluetooth settings"). There, go to the Hardware tab and select your primary Bluetooth radio (for me, one had a physical location and the other had the first one as its location, so I picked the first one). Hit the "Properties" button and go to the "Advanced" tab. Here, you'll want to copy down the Name and Address. 

OK, now, on Ubuntu, go to the terminal and type the same command as before, although a sudo would probably help:
```
sudo hciconfig hciX name "name"
```where "name" refers to the Name as stated in Windows (including the quotes). As I said before, you could also go into the Bluetooth Settings in Ubuntu (System > Preferences > Bluetooth) and change the "Friendly name" to match that in Windows.

I would assume you could change it the other way around (match Windows to match Ubuntu), but I think this is probably the easier route to take.

Now, I'm not sure if you got this far or not, but I had to cover my bases. If it's still not working at this point, you just have to make sure that the mouse is using the same PIN on each OS. When connecting the mouse, it should ask you for a PIN. You can have no PIN (not a big deal for a mouse), but you have to have no PIN on both. If it doesn't ask for a PIN, then I would assume it's using the default PIN for the mouse, which can probably be found on the underside of the mouse or in the documentation that came with it. If you still can't find it, Googling the specific model of mouse may help. You then need to try putting in the default PIN on the other OS for the PIN.

At this point, it should work, but if it's not, let me know (as a reply here, not another PM) with specifics.

Good luck!

---

### Post by dgttm on 2010-02-17
Thank you very much for your explanation. I followed this and now i got it working... I had to set it up (ms laser bluetooth mouse 5000) first in ubuntu lucid beta, and afterwards in win 7. Windows required a password, but I could use "no password" after a previous try with default pin 0000. But now I have no problem connecting it without entering any pin.

Now almost everything is working on my tm2 1090. Touch screen with pen, even with pressure recognition.. Way better working as with ps cs4 in win 7. 

Did you get your touchpad buttons working already?

My biggest issue is setting the display brightness. Popups and hotkeys are working but there is no impact on the brightness.. Already found bug id for that one, but no solution so far.

---

### Post by Platypus222 on 2010-02-17
> **dgttm said:**
> Thank you very much for your explanation. I followed this and now i got it working... I had to set it up (ms laser bluetooth mouse 5000) first in ubuntu lucid beta, and afterwards in win 7. Windows required a password, but I could use "no password" after a previous try with default pin 0000. But now I have no problem connecting it without entering any pin.

Now almost everything is working on my tm2 1090. Touch screen with pen, even with pressure recognition.. Way better working as with ps cs4 in win 7. 

Did you get your touchpad buttons working already?

My biggest issue is setting the display brightness. Popups and hotkeys are working but there is no impact on the brightness.. Already found bug id for that one, but no solution so far.

Glad to hear it's working!

The touchpad issue was not mine. I came here, I assume, as you did, hoping to find a solution to a problem that other people asked about. I fixed my problem and hopefully some of their problems as well. My touchpad never had any issues, but maybe that issue will be solved/has been solved.

Good luck with the brightness buttons. Mine work fine, but part of Linux is hoping that all the different hardware configurations can work together well under one OS.

---

### Post by randomslices on 2010-10-27
This issue has been bothering me for the past few days and the solution presented here just worked. I just wanted to thank you all.

---

### Post by ericyan3000 on 2011-01-13
> **Platypus222 said:**
> OK, so since the original post, I've upgraded to Windows 7 and Ubuntu 9.10, so let's see what's different. 
 
In Windows, go to Bluetooth Settings (in the Start Menu, type in "bluetooth" and choose "Change Bluetooth settings"). There, go to the Hardware tab and select your primary Bluetooth radio (for me, one had a physical location and the other had the first one as its location, so I picked the first one). Hit the "Properties" button and go to the "Advanced" tab. Here, you'll want to copy down the Name and Address. 

OK, now, on Ubuntu, go to the terminal and type the same command as before, although a sudo would probably help:
```
sudo hciconfig hciX name "name"
```where "name" refers to the Name as stated in Windows (including the quotes). As I said before, you could also go into the Bluetooth Settings in Ubuntu (System > Preferences > Bluetooth) and change the "Friendly name" to match that in Windows.

I would assume you could change it the other way around (match Windows to match Ubuntu), but I think this is probably the easier route to take.

Now, I'm not sure if you got this far or not, but I had to cover my bases. If it's still not working at this point, you just have to make sure that the mouse is using the same PIN on each OS. When connecting the mouse, it should ask you for a PIN. You can have no PIN (not a big deal for a mouse), but you have to have no PIN on both. If it doesn't ask for a PIN, then I would assume it's using the default PIN for the mouse, which can probably be found on the underside of the mouse or in the documentation that came with it. If you still can't find it, Googling the specific model of mouse may help. You then need to try putting in the default PIN on the other OS for the PIN.

At this point, it should work, but if it's not, let me know (as a reply here, not another PM) with specifics.

Good luck!

Thank you for your instructions, but unfortunately for me, the problem is not solved.

I did every step as you stated, 1) found the name and address of the bluetooth radio under windows, 2) restart to ubuntu, make sure the bluetooth radio has the same address, and change it tot the same name. 3) connect the mouse in ubuntu 4) restart into windows, the mouse is still NOT connected automatically.

I've tried to switch off the mouse while restarting into different system, but no help. 

I also tried to configured under ubuntu first, without connecting to the mouse, restart into windows, connect the mouse, then restart into ubuntu, the mouse is not connected either.

So now everytime I boot into a system different than last time, I've to remove the bluetooth mice first (the one remembered by the system, but couldn't be connected), and the run a setup as adding a new device. I need to do this regardless booting into ubuntu or windows.

I'm using the Apple might mouse, do you think this could be the cause of the problem? Or I'm doing something else wrong?

Thanks for your help in advance.

---

### Post by gregdavisfromnj on 2011-07-03
Have this same problem.  Vista SP2, and actually using openSUSE 11.4.  Hey, at least its Linux.  I think that the GUIs for the "pairing" process in each OS are hiding from the user the fact that it is using a default passcode for the mouse, or no passcode.  So, you end up with a mismatch between the OSes, and the mouse won't join the piconet of the penultimately paired OS.  I haven't found out how to peer into the inner workings of Vista to figure out what it is using for a passcode for my mouse (or none) which is a MS Bluetooth Laser 5000.  I think with the bluez stack in Linux, the passcode should be found in a file under /etc.

I'm going to try this sequence: find the local device's name (the BT adapter or dongle) in Windows, set the BT adapter's name to that in Linux, pair the mouse to Linux, find the passcode for the mouse in Linux, start Windows, let Windows complain that a mouse is requesting a passcode, enter the passcode from Linux, go on with life.

I'll update on whether or not that works the next time I have 45 minutes to spare while I reboot a few times.

---

### Post by gregdavisfromnj on 2011-07-04
> **gregdavisfromnj said:**
> 

I'm going to try this sequence: find the local device's name (the BT adapter or dongle) in Windows, set the BT adapter's name to that in Linux, pair the mouse to Linux, find the passcode for the mouse in Linux, start Windows, let Windows complain that a mouse is requesting a passcode, enter the passcode from Linux, go on with life.



Tried this sequence.  When Windows asks for the passcode for the device that is requesting access (my mouse), I give it 0000, which is what I told the KDE bluetooth pairing wizard.  But, Windows doesn't like that response and throws a device not connected error (device doesn't connect).  Tried turning off the mouse, and back on, as some people have had to do that.  I suspect now that Windows authenticates to the mouse correctly, but the mouse appears foreign to Windows, and it throws the error.  I'll try forcing a passcode in Windows first, then starting Linux second.

---

### Post by a.frings on 2011-11-05
Hi,
first thanks for that instruction. However it did not work but I found out what else is necessary to get it working. My setup is:

- Windows Vista
- Debian Linux with KDE
- Microsoft Bluetooth Notebook Mouse 5000

First start Linux and bind the mouse in the usual way. Open the list of bluetooth devices and mark the mouse as "trusted" so it can connect to the computer when switched on. Otherwise you would need to initiate the connection always manually from PC side. You possibly know that already. Maybe the bluetooth Manager of Ubuntu sets that flag automatically. I dont know, because I always worked with KDE on different Linux distributions.

Then start Windows and remove the mouse from the list of registered bluetooth network devices (if it exists). Still in that window, click on the button to add a new device. Press the bind button on the mouse and wait until the mouse gets detected by the computer.

Now comes the important part that was missing: 

Right-click on the mouse to open the list of available services that the mouse offers. There is normally only one entry, which is the HID device (mouse and keyboard). Check this entry. Windows will install a driver immediately, before you clicked on any confirm or save button. The mouse starts working. Then click on cancel - not on Ok! (If you click on Ok, then Windows activates encryption and then the mouse will notwork with Linux anymore).

If you connect the mouse the "normal" way, you connect it with encryption and then it cannot be shared to multiple operating systems. Just to be sure, mark the mouse in the list of connected devices and take a look at the status bar. It should say "Encryption: no" and "Connected: yes".

Open the hardware detail window to get the name of the bluetooth sender. In my case, the name was the same as the computer name in windows networking (stefanspc).

Then boot Linux. In a terminal window, enter 

sudo su -    (in debian only: su -)
hciconfig

In my case, only one device with name hci0 appeared, which is the bluetooth interface. 

hciconfig hci0 name stefanspc

Power off the mouse and power it on again. It should immediate connect and work now in both operating systems.

---

### Post by wmor06705 on 2011-11-17
Hi, I have a pc with Ubuntu, Windows 7 and OS X Lion, and a  Magic mouse, but I don't get use my magic mouse in the three S.O. whitin  to install each time.

Can you to explain a bit in detail how to connect whitin encryption? I can't get.

Thanks in advance!

---

### Post by a.frings on 2011-11-18
If you enable encryption (which is the default behaviour on WIndows), you cannot share the mouse to other operating systems because they will use a different key. The key is well protected, so there is no way to read it out of the registry and copy it to the other operating systems.

You must connect the mouse to Windows without encryption.
Then you can also connect it to Linux without encryption.

I dont know whether Mac OS support non-encrypted connection.

---

### Post by rykel on 2012-12-09
> **a.frings said:**
> Hi,
first thanks for that instruction. However it did not work but I found out what else is necessary to get it working. My setup is:


Hi, I am trying to disconnect my BT mouse from Ubuntu and then reconnect it easily to Windows 7, but Windows is the OS that is giving me a major problem. Unlike Ubuntu, Windows does NOT give me a button to "connect" the BT device.

Using your note, I noticed that Windows 7 installed the BT Mouse driver correctly but the mouse does NOT appear in the BT Devices list. Of course, I still CANNOT connect the BT Mouse under Windows easily...   

p/s1. My disconnected BT Mouse can be simply reconnected to Ubuntu by either using the "Connect" button or turning it off and on again. I wish Windows would just give me that dang "Connect" button!

Ubuntu 12.10
Windows 7
Prolink BT Mouse

p/s2. Now the "unencrypted" BT Mouse DOES show up in the Windows 7 BT Devices List, but once I disconnect it from Windows, there is NO easy way to reconnect it back. No button, right-clicks or turning on/off any switches works. By the way, how do I see whether the BT Mouse is "connected to Windows but not encrypted"?

Thanks for your help!

---

