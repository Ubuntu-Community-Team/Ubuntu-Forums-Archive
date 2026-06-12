---
title: "Bluetooth killed the new guy"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by avalanche-870 on 2009-12-17
I am not sure how to start, or even is this the right place to post my problem.
Here is the case: I am totally new to ubuntu, this forum and to every thing that has to do with linux, when i switched to ubuntu i had a few troubles that i managed(thanks to this forum) but i cant get my bluetooth up and running(its a built in bluetooth on a fujitsu simens v6545), i guess its not detected in the first place (but how can i know, i am a.....newbie) so i was looking for some help with it in a plain non technical english. And i would like to apologize in advance if there is any thing wrong about this post or its place but as i said before: this is my first post and i am new to all this.
Thanks in advance.

---

### Post by LowSky on 2009-12-17
Hi Welcome to the forum...

Do you have a bluetooth icon on the top right part of the panel? 
What are you trying to connect?

Also Please use the normal normal size font, Its more respectful.
thanks!

---

### Post by avalanche-870 on 2009-12-17
First of all thanks for the welcome, second, sorry for the font (a new guy doesn't know the rules,does he?), third no i dont have an icon and i have 3 devices i want to connect to: a nokia 6670 and a nokia 5610 and a Lenovo s10e netbook runnig windows xp

---

### Post by tom.swartz07 on 2009-12-17
lets see if its detected by your system. 
we're going to have to do some detective work to figure out whats wrong.

open the terminal application, and type in this command

```
lspci
```

then copy and paste the output here. This command tells you what items are detected by the os, and how they are connected to the computer. It will give us a better idea of whats going on.

---

### Post by avalanche-870 on 2009-12-18
avalanche@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller



Thats what the terminal says, is it bad??? :D

---

### Post by Doogle_42 on 2009-12-18
Hi ppl
I know this is off the topic but i dont know how to start my own thread.
I am also new to Ubuntu
I am running Ubuntu 9.10 and i have a Darwin Streaming server set up.
My plan in the end is to create a bluetooth server that is automated to bond to blutooth devices like cell-phones and allow the cell-phone to browse the computers files and download videos and ultimately for security reasons just allow the cell-phones to stream the videos through the Darwin Sreaming Server.:confused:
If any one could help with anything. Even just to help with allowing the cell-phone to just download. (The automation can be done at a later stage)
I am also wondering how to set up my own Proxy Website for testing purposes.
Thanx Dave

---

### Post by tom.swartz07 on 2009-12-19
Alrighty,

Looking at your output, it seems that your bluetooth isnt recognized by your system. Perhaps try going into the Software Center, and installing the bluetooth manager application from there. 

That might install the required support for the system to recognize the device.

Post back and let me know how it works!



Dave, Im not too sure that you will get the help you need posting here, so I would suggest making your own thread. The new thread buttons are on the top left hand side of the thread list. Try this: [http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331)

---

### Post by avalanche-870 on 2009-12-19
I tried installing bletooth manager as you said, and when i started it, it gives me this message"Connection to bluez failed: Bluez daemon is not running, blueman-manager cannot continue."and gives me only a close option.
I tried adding other applications "i looked for any apps that has the word bluetooth in it" so i added bluetooth analyzer and bluetooth and still no luck, the manager still gives me the same message.
So till now its not working, but i think that by your help i'll be able to get it running sooner or later.....

Thanks again

---

### Post by gradinaruvasile on 2009-12-19
Install blueman - this is another bluetooth manager, better than the default one. I connected phones, transferred files with it and i connected and used a bluetooth handsfree with Skype.

Also, make sure that bluetooth is activated in BIOS and if you have killswitch, make sure its off.

And, if you have ubuntu 9.10, open a terminal and type:

rfkill list

What is the output?

---

### Post by avalanche-870 on 2009-12-19
avalanche@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

this is the output.
About the blueman, i cant find it in the software centre,
any particular place to download it from???

---

### Post by avalanche-870 on 2009-12-19
ok, here is what happened
i don't know why i did it but i logged on the windows(still keeping it till i get fully adapted to ubuntu), i turned on the bluetooth and wifi, restarted, logged into uubuntu and......Bang, it was there, the bluetooth icon in the top panel looking more beautiful and gorgeous than ever before.
So there is no more problem, everthing is settled, smiles everywhere.
thank you all guys: Lowsky, Tom swartz and Gradinaruvasile, its great to know that I got people like you that got my back and I hope that one day i would be able to help people here like you all helped me...
one more thing to end this, how can i turn bluetooth and wifi on and off in Ubuntu

thanks all

---

### Post by tom.swartz07 on 2009-12-19
> **avalanche-870 said:**
> ok, here is what happened
i don't know why i did it but i logged on the windows(still keeping it till i get fully adapted to ubuntu), i turned on the bluetooth and wifi, restarted, logged into uubuntu and......Bang, it was there, the bluetooth icon in the top panel looking more beautiful and gorgeous than ever before.
So there is no more problem, everthing is settled, smiles everywhere.
thank you all guys: Lowsky, Tom swartz and Gradinaruvasile, its great to know that I got people like you that got my back and I hope that one day i would be able to help people here like you all helped me...
one more thing to end this, how can i turn bluetooth and wifi on and off in Ubuntu

thanks all

HEY! glad it worked!
thats strange- ive never heard of it being locked into being disabled from one OS to the next! Ill keep that in mind for the future.

I might be pointing out the obvious, but do you have a bluetooth switch on your laptop? I have a WiFi switch here on mine, and it controls it in both OS's.

If not, you could go up to your top bar:
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Srr5pse4FkI/AAAAAAAAAHQ/O9t4Ml72yTc/s800/Screenshot-1.png[/IMG]
The bluetooth icon top left, next to the clock, right click and select "turn off bluetooth". that should fix it.

Also, just to be sure that everything is a-okay, lets check for some hidden drivers and update your system really quickly.

go to System, Administration, and Hardware Drivers. See if there's anything listed there. you 'MIGHT' have something related to your bluetooth there.
Next, System, Administration, and Update Manager. You should run this at least once a week; I run it almost daily. check and see if you have updates, and install them. that will keep you up to date with all of your software!


Hope this helps!

---

### Post by avalanche-870 on 2009-12-20
OK, i checked for driver updates and system updates and found nothing.

I figured out how to turn bluetooth and Wifi on/off through the desktop panel

but I have a switch on my laptop that used to control both bluetooth and wifi, and its not functioning in ubuntu, Can you help me to get this switch functioning

---

### Post by sgosnell on 2009-12-20
That should be a direct hardware switch, which shouldn't depend on the OS.  Hard to say for sure, though, laptops are very quirky and non-standard.  I don't have a clue about a Fujitsu-Siemens product.  You might check their website for Linux drivers, but good luck with that.

---

### Post by avalanche-870 on 2009-12-21
I tried Fujitsu siemens site but there is no drivers for ubuntu (only for windows)
Anybody knows how to get such drivers?????????

---

### Post by tom.swartz07 on 2009-12-21
> **avalanche-870 said:**
> OK, i checked for driver updates and system updates and found nothing.

I figured out how to turn bluetooth and Wifi on/off through the desktop panel

but I have a switch on my laptop that used to control both bluetooth and wifi, and its not functioning in ubuntu, Can you help me to get this switch functioning

Hey,

Just like sgosnell said, for the most part the switch is what controls your hardware's power, not usually the OS. You might be in the same situation as me with my WiFi card. My Broadcomm wifi chip has a switch on the side of my Dell, it doesnt work until I send an update to the chip from the OS, such as disable wifi from the OS or attempt to reconnect to another hotspot. If you were to need a driver to control it, that would mean that you turn the device on/off from the OS (which you said you can do)

Just because the OS doesnt update to the status, it doesnt mean that it isnt off.

Lets try this, just to see if its the same with you. Flip the switch and see if you could connect to (or send files to your bluetooth device). That should update that the power state has changed.

If not, then we could go about digging up some kind of support for the power.

---

### Post by avalanche-870 on 2009-12-21
ummmmmmmmm, I didn't get what you said fully but i'll try to explain to you based on what I understood
the switch is not really an on/off switch(like the light switch that i hit when i go into my room), its rather a spring assisted button that returns to its position after you push it to the right
so in windows I push it to the right, its goes back to original position and gives me a windows that give me the option to turn on/off the wifi and bluetooth(so i think that its not really an electricity switch)
In ubuntu I push it and nothing Happens
I hope that you understand what i am trying to say

---

### Post by tom.swartz07 on 2009-12-21
> **avalanche-870 said:**
> ummmmmmmmm, I didn't get what you said fully but i'll try to explain to you based on what I understood
the switch is not really an on/off switch(like the light switch that i hit when i go into my room), its rather a spring assisted button that returns to its position after you push it to the right
so in windows I push it to the right, its goes back to original position and gives me a windows that give me the option to turn on/off the wifi and bluetooth(so i think that its not really an electricity switch)
In ubuntu I push it and nothing Happens
I hope that you understand what i am trying to say

I seeeeee...
I was thinking it was an on/off switch. That means it is a driver based thing. Ill look and see what I can dig up, but for the mean time I guess you'll just have to turn it on/off from the top bar area.

---

### Post by avalanche-870 on 2009-12-21
No problem, it's not killing me but it would be nice to use the full functionality of my laptop( i paid a great deal of money for it :D ) one thing else i forgot to mention, remember when i told you how i logged into windows and switched on the wifi and bluetooth, well a small lamp (indicator for bluetooth and wifi) turned on, this lamp remains turned on in ubuntu even when i disable both wifi and bluetooth (i thought saying that might be useful),

by the way i like the way your desktop looks
Thanks

---

### Post by tom.swartz07 on 2009-12-21
> **avalanche-870 said:**
> No problem, it's not killing me but it would be nice to use the full functionality of my laptop( i paid a great deal of money for it :D ) one thing else i forgot to mention, remember when i told you how i logged into windows and switched on the wifi and bluetooth, well a small lamp (indicator for bluetooth and wifi) turned on, this lamp remains turned on in ubuntu even when i disable both wifi and bluetooth (i thought saying that might be useful),

by the way i like the way your desktop looks
Thanks

Alrighty, I did some google-fu and I found that the terminal command to interface with your bluetooth should be ```
hciconfig hci0 up
``` or to turn it off is ```
hciconfig hci0 down
```

To be completely truthful, I have no idea how to set it so that your hardware switch will issue that command, but as soon as I figure it out I'll let you know!

Try that command in the terminal, see if it turns your bluetooth on and off, and post the output of the command 
```
ifconfig
```

That will give us all a better idea of the types of hardware interfaces you have; and we could fine tune the commands for that.

**EDIT:** I've Figured out how to do it- you add the command in 'keyboard shortcuts' and use the switch as the shortcut key.


OH! and Thanks! That's my older desktop from 9.04, my new one is a little bit cooler :)

---

### Post by avalanche-870 on 2009-12-22
[FONT=monospace]avalanche@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:01:dd:40  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe01:dd40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10148940 (10.1 MB)  TX bytes:1900355 (1.9 MB)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:12:1e:05  
          inet6 addr: fe80::222:5fff:fe12:1e05/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1469 (1.4 KB)  TX bytes:2503 (2.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-12-1E-05-31-32-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


This is the output of "ifconfig"

About the other 2 codes they both give "Can't init device hci0: Permission denied (13)" and "Can't down device hci0: Permission denied (13)"

However this is not the problem right now

When i installed Blueman bluetooth manager, its bluetooth icon in the panel wass on, and when i turned it off it would never turn on no matter what i did,
so i removed it and installed BLUETOOTH which install BLUETOOTH ANALYZER with it and it works but the is no turn off bluetooth order,

so (if its not too much to ask) can you help me with Blueman issue before i can go into that switch issue
[/FONT]

---

### Post by tom.swartz07 on 2009-12-24
Okay, I don't think I quite understand your problem....

You said that Blueman was able to properly connect your bluetooth devices, but when you disabled bluetooth from this program, it would no longer work.

After this, the "Bluetooth" application was able to re-enable your bluetooth card, and connect?

If bluetooth works, then just use that?

Im not sure what the problem is.


Additionally, the last two commands from the terminal, referring to the bluetooth up and down, add sudo before them and see what they return.

---

### Post by avalanche-870 on 2009-12-25
I am sorry for troubling you,
and there is no further need for commands and this kind of stuff

Here is what happened: I was trying to get a new theme, after I installed it, it took my ubuntu system down.
so i went into windows and wubied my ubuntu once again (making sure this time that bluetooth and wifi are turned on) and every thing is working perfectly right now (except for the switch that i told you about but i'll stick right now to the panel control).

so for now i'll spend my time trying to get this ubuntu a bit more and may be in the future i'll post a thread about that switch thing (when i am more knowledgeable about linux)

so Thanks for all who helped especially for you Tomswartz

---

### Post by tom.swartz07 on 2009-12-25
> **avalanche-870 said:**
> I am sorry for troubling you,
and there is no further need for commands and this kind of stuff

Here is what happened: I was trying to get a new theme, after I installed it, it took my ubuntu system down.
so i went into windows and wubied my ubuntu once again (making sure this time that bluetooth and wifi are turned on) and every thing is working perfectly right now (except for the switch that i told you about but i'll stick right now to the panel control).

so for now i'll spend my time trying to get this ubuntu a bit more and may be in the future i'll post a thread about that switch thing (when i am more knowledgeable about linux)

so Thanks for all who helped especially for you Tomswartz

Im glad I was able to help you for the most part!

I would suggest looking at this free guide available on Google Books. Its tuned for a slightly older version of ubuntu, but it is still very very good! I even learned some things from this guide!

[http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q=&f=false)

Give it a quick read-through, it covers pretty much everything you need to know as you switch from windows to linux!

Happy Ubuntu-ing!

Feel free to let me know if you ever need help!

---

### Post by gradinaruvasile on 2009-12-26
> **avalanche-870 said:**
> [FONT=monospace]avalanche@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:01:dd:40  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe01:dd40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10148940 (10.1 MB)  TX bytes:1900355 (1.9 MB)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:12:1e:05  
          inet6 addr: fe80::222:5fff:fe12:1e05/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1469 (1.4 KB)  TX bytes:2503 (2.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-12-1E-05-31-32-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


This is the output of "ifconfig"

About the other 2 codes they both give "Can't init device hci0: Permission denied (13)" and "Can't down device hci0: Permission denied (13)"

However this is not the problem right now

When i installed Blueman bluetooth manager, its bluetooth icon in the panel wass on, and when i turned it off it would never turn on no matter what i did,
so i removed it and installed BLUETOOTH which install BLUETOOTH ANALYZER with it and it works but the is no turn off bluetooth order,

so (if its not too much to ask) can you help me with Blueman issue before i can go into that switch issue
[/FONT]

You can control the bluetooth (and wireless too) device with rfkill - you can switch it on/off with it (i am not at the laptop and i have Jaunty on this comp that doesnt have rfkill so i cant tell the exact syntax now).
 The blueman icon dissapears when you turn off the device, but when you switch the bluetooth on with rfkill, the icon will appear - in my Dell laptop i have to click on it and asks me to enable bluetooth (that is supposed to be on), i click enable and the device is working.

---

### Post by jsundin on 2010-01-19
I have had similiar issues that the newguy had with Bluetooth - he may not be out of the woods yet.... 
Mine works then Not so much - ;^{ 
The windows thing seems to fix it but not consistantly. I believe there may be a conflict with the pairing of the MAC address with either the name or the Passcode as it seems to crop up when I have tried to pair with other Master devices such as a different computer or phone. It seems that a new pairing is required but the Ubuntu is not clearing the old association.
Anyone who can help me prove my crackpot theory?:)

---

### Post by helotbc on 2013-04-09
I installed Blueman.  After some clicking around, I was able to pair my device.  I checked the default bt manager and it was then enabled.  Thanks for the help.  -Brendan

---

### Post by wildmanne39 on 2013-04-09
Thread closed. Please do not post in old threads.

---

