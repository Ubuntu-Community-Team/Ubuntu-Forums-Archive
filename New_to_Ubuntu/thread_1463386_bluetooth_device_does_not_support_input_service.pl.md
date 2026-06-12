---
title: "bluetooth device does not support input service.please help."
date: 2010-04-26
forum: New to Ubuntu
---

### Post by human75 on 2010-04-26
hi there.
 i am using Kubuntu 10.04 LTS x64.everything is working smoothly beside my Motorola s9-hd headset and my Sony Ericson X1 blutooth OBEX.
Bluetooth manager can find bluetooth devices but when i try to connect them i am getting always same error message."Sorry your bluetooth device does not support input service.is there anyway to fix this?please help.thanks a lot

---

### Post by human75 on 2010-04-27
is there no fix for this?should i report as a bug?i dont know i am really new with ubuntu.thanks

---

### Post by human75 on 2010-04-28
thanks for help to everybody:(

---

### Post by Cowboybebop79 on 2010-04-28
Sorry if no one has answered your call for help. A lot of them will be at the pub at the moment having a pre-release party and tomorrow..... etc.

Anyway some info to get hold of to find out what the problem might be is how do you get bluetooth: dongle/internal
Are you using the standard ubuntu bluetooth manager or blueman
and if you are using a dongle for bluetooth type lsusb in a terminal and paste the result in your next post.

And one question is the sony ericsson X1 an Xperia?

If any of this is confusing or not understandable then tell me and I will try to explain it better

---

### Post by human75 on 2010-04-28
> **Cowboybebop79 said:**
> Sorry if no one has answered your call for help. A lot of them will be at the pub at the moment having a pre-release party and tomorrow..... etc.
 
Anyway some info to get hold of to find out what the problem might be is how do you get bluetooth: dongle/internal
Are you using the standard ubuntu bluetooth manager or blueman
and if you are using a dongle for bluetooth type lsusb in a terminal and paste the result in your next post.
 
And one question is the sony ericsson X1 an Xperia?
 
If any of this is confusing or not understandable then tell me and I will try to explain it better
 eventully:)i lost  hope but i got someone i thank you.with  sony x1 i can pair device with my toshiba satellite A210 but i cant make it file transfer.everytime file transfer fails. with motorola s9 bluetooth headphone i can pair device but i am getting this error message "[bluetooth device does not support input service]("http://ubuntuforums.org/showthread.php?t=1463386")"of course it does not work.i googled a lot at the moment i am completly lost.i dont know what should i do?in windows it is easy.you going device manager you are uninstall device and re-install device or driver etc...but i dont know which way i must follow and what should i do?
 yes i am using KUBUNTU bluetooth manager.please help me thanks

---

### Post by Cowboybebop79 on 2010-04-28
got to go to bed now sorry :( but I have your thread tagged if you can open terminal which is similar to dos it will be in your accessories menu and type lsusb and hit enter and paste the results in a post and I will have a look at it tomorrow first thing and don't worry there is a solution to every problem some are harder than others but there is always a way.

:)

---

### Post by human75 on 2010-04-28
> **Cowboybebop79 said:**
> got to go to bed now sorry :( but I have your thread tagged if you can open terminal which is similar to dos it will be in your accessories menu and type lsusb and hit enter and paste the results in a post and I will have a look at it tomorrow first thing and don't worry there is a solution to every problem some are harder than others but there is always a way.
 
:)
 :) :) :) thanks a lot.you are very friendly:)i will do what you said and i will paste results.thanks a lot.goodnight

---

### Post by human75 on 2010-04-28
> **Cowboybebop79 said:**
> ....type lsusb and hit enter and paste the results in a post and I will have a look at it tomorrow first thing....
:)
here is the result
human@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
human@ubuntu:~$ 
btw i am using kbluetooth version 0.4 . this application gives me" bluetooth device does not support input service"...in other hand, i recently install blueman applet 1.21 which looks much better.looks like i can pair my device but still there is no sound on SMPlayer.BTW which application do you recommend to watch mkv,avi....in win7 when i pair my device smplayer automaticaly switch my bluetooth device.i dont know how does it work in kubuntu...first think is first lets sort sound problem first:)thanks a lot in advance

---

### Post by Cowboybebop79 on 2010-04-29
Hi had a bit of a search around this morning and I found this forum post about toshiba laptop's

[http://ubuntuforums.org/showthread.php?t=316358&page=10]("http://ubuntuforums.org/showthread.php?t=316358&page=10")

Which talks about a special driver called omnibook as the toshiba laptops are based on HP omnibook laptops you can get the driver at sourceforge

[http://sourceforge.net/projects/omnibook/]("http://sourceforge.net/projects/omnibook/")

as far as watching avi/mkv is concerned open software center and install ubuntu restricted extras and vlc or if you prefer XBMC or have a look at boxee which is based on XBMC the later two are not in the software center as far as I know but they have instructions on there site on how to install take about 5 min

---

### Post by human75 on 2010-04-29
i think i am getting to solution :) i follow this 

[http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu](http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu)

 and i got my bluetooth device are make pair without error:)
   but still no sound with my motorolo s9 and i cant send file from sony x1 to laptop but weird enough i can send file to my sony x1 without problem:)
....for motorola s9:i dont know which output device must i choose?for example under vlc audio settings ALSA audio out put p&#305;lse audio output...etc...:)
....for x1:when i try to send file x1 to laptop ubuntu crashed and asking for a bug report?what should i do?....
i am stuck again now:)any advise..many thanks in advance

---

### Post by Cowboybebop79 on 2010-04-30
I was going to suggest the site you have linked to as the next step but you got there before me :) . After you have linked your X1 and head set open terminal and run this command

```
hcitool scan
```

this should give you a list of the bluetooth devices that are connected at the time this will give the bug team more information when dealing with your bug.

With the headset while it is connected open sound preferences and check under the input and output tabs to see if your headset is listed if so it may not be automatically switching between your sound card and the head set when it is linked.

As far as the X1 is concerned the next time it comes up with the bug submit the bug report to launchpad you will need to create a log in for this but it only takes a few minutes they will look in to the problem further and see if anyone else has had the same problem and if there is all ready a solution for this. I have heard However that there has been some problems with the bluetooth on sonyericsson x1 phones so it could be a problem with your phone in this instance but you will know better than me as I dont have an X1 K750I at the moment old but good :P

---

### Post by hellhound6 on 2010-05-03
I have this exact same problem.  I upgraded to 10.04 and today decided to pair my bluetooth BlueAnt Q1 headset to my computer.  I run through the Bluetooth Device Manager Wizard and it finds my headset, but alas I receive: "Sorry your Bluetooth Device does not support input Service." 

My bluetooth doogle is supported by Kubuntu and I was able to pair with Windows XP fine.

---

### Post by Cowboybebop79 on 2010-05-04
I have tried the bluetooth dongle/Headset combo I used previously on 9.10 for Skype calls with the standard 10.04 bluetooth set-up and it also failed. Originally when I was using 9.10 and was considering using bluetooth I did a bit of research before taking the plunge so I installed Blueman which is an alternative bluetooth manager. So this morning after the failed attempt with the standard set-up I removed my dongle (you can turn off bluetooth if it is integrated). Open Ubuntu software centre and search for bluetooth and remove the default bluetooth manager which will have a green tick next to it (if this sounds basic it is as I'm writing it for new users) after this has completed reset and log back in you might just have to log out and in but a restart will definitely give you a clean slate. Open up Ubuntu software centre and search for Blueman and install the program then restart your bluetooth or plug your dongle in double click the bluetooth symbol next to the clock on your desktop or in the system > preferences menu click bluetooth manager. Make your device discoverable and hit the search button in Blueman. You can then connect up your device and test. If this doesn't work then its probably a hardware compatibility issue remember that not all bluetooth is the same which is one of the reasons it hasn't replaced WIFI.

---

