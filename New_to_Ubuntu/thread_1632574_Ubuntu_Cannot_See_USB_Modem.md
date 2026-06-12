---
title: "Ubuntu Cannot See USB Modem"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-28
Hi (again),

I'm really going round in circles on this one, partly because the USB dongle I've been given might not be supported by Ubuntu 10.10.

lsusb

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0af0:c031 Option 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

I was under the impression that this command should be telling me more than just 'Option', the make of the card. It is an Option Icon031 EDGE for Airtel (India).

I've been reading various threads like [Alexfish's guide]("http://ubuntuforums.org/showthread.php?t=1466490&highlight=connect+wireless+mobile+time") and contacting Pharscape who appears to know a thing or two about this but I haven't heard back from Paul (it is the weekend, after all) and I fall at the first hurdle of Alex's guide.

Really, though, I just don't know where to start. I'm at a complete loss as to how to get this thing up and running. It works fine in Windows 7. Could someone help me as of course I can't get online (using another computer at the moment).

Thanks.

---

### Post by QLee on 2010-11-28
[QUOTE=demonboy]...
lsusb

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0af0:c031 Option 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```I was under the impression that this command should be telling me more than just 'Option', the make of the card. It is an Option Icon031 EDGE for Airtel (India).[/QUOTE]
Well, actually it does Jamie, 0af0 is the manufacturer, c031 is the card ID.

[QUOTE=demonboy]I've been reading various threads like [Alexfish's guide]("http://ubuntuforums.org/showthread.php?t=1466490&highlight=connect+wireless+mobile+time") and contacting Pharscape who appears to know a thing or two about this but I haven't heard back from Paul (it is the weekend, after all) and I fall at the first hurdle of Alex's guide.[/QUOTE]

Well, since the guide doesn't have line numbers and it also doesn't have "hurdle" numbers, it isn't clear to me what you mean.

[QUOTE=demonboy]Really, though, I just don't know where to start. I'm at a complete loss as to how to get this thing up and running. It works fine in Windows 7. Could someone help me as of course I can't get online (using another computer at the moment).
[/QUOTE]

Probably using your father's computer again,eh? Or have you already gone back to India, if so, I envy you being in warm weather now.

One thing you might do would be to enter the command, lsmod, which would show you the installed modules (drivers). Since I don't have one of those broadband WiFi modems, my googling indicates the mod should be hso. As I have suggested to you previously, you should become more proficient with searching in order to be able to help yourself rather than waiting for others to tell you which keys to push, but that is your choice to make, not mine. Things I found suggested that it should already be in the kernel. If not the latest kernel (maybe there was a regression) try booting to the previous kernel.

If the correct mod is already loaded, you should be able to edit connections in Network Manager on the "Mobile Broadband" tab. It would find your card when you do an "add".

Unfortunately, I won't be around to help further, I had surgery on the 15th and have a limited amount of time that I am comfortable enough sitting up to be able to help and am at that limit.

As always, good luck!

---

### Post by zipteye on 2010-11-28
Go to /etc/modules
edit it so that it reads:
 
lp
ndiswrapper
 
You can comment out things that might be in there rather than delete them .
# This is a comment
 
Then reboot
 
Of course, make sure that you have ndiswrapper installed first.

---

### Post by demonboy on 2010-11-29
For the record I have attempted a [similar post]("http://ubuntuforums.org/showthread.php?t=1630941") on this subject. The website suggested does not list my dongle.

Zipteye, when you say 

> 
Go to /etc/modules
Do you mean create it? I don't have 'modules' in my /etc folder.

I've installed ndiswrapper but the driver is already installed. The problem is that the USB dongle, whilst being picked up in the Mobile Broadband Setup wizard, is not being initialised.

I've had this dongle for over a week now and spent all that time trying to get it up and running, to no avail. I think the easiest solution might be to just buy another dongle that has a recognised, working driver installed. I'm nipping in to town today so I'll keep you posted.

---

### Post by QLee on 2010-11-29
[QUOTE=demonboy]For the record I have attempted a [similar post]("http://ubuntuforums.org/showthread.php?t=1630941") on this subject. The website suggested does not list my dongle.[/QUOTE]

Sorry Jamie, when I searched I found this from the Linux Kernel Drive Database which seemed to indicate it could work:
[http://cateee.net/lkddb/web-lkddb/USB_HSO.html](http://cateee.net/lkddb/web-lkddb/USB_HSO.html)

Since I don't have the hardware to work with I can't do anything further, it appears you have posted at a forum which is specific and that is likely the best place to get help with the issue because it is totally concerned with those broadband WiFi modems. 

After you have the answer, it could be helpful to other Ubuntu users who have that modem for you to post a "how to" to the Ubuntu forum, if you have the time and inclination.

---

### Post by demonboy on 2010-11-29
Hi QLee, Zipteye and others who may be looking for a answer. Unfortunately I have not found a solution but I have solved the problem for myself by using another dongle altogether. I bought this off a friend this afternoon and 'had to make some changes to it'. Ahem. After my tweak it worked instantly and I am now online.

I went in to town today and must have visited about 15 different mobile stores. None could help and all said this particular dongle is not supported by Linux. I don't believe this and think that I should be able to solve the problem given more time. I contacted Option directly who said:

> 
The 3G modem device you have purchased is an OEM product. The product
has been commercialized by Capitel and is supported by your local
supplier. We are sorry that we are not able to assist you with your
support inquiries due to contractual reasons. Please contact your local
supplier support helpdesk.



Of course I have been to all the Airtel shops and they said they couldn't help. The Airtel website actually displays about six different types of dongles and I was hoping I could swap my one (you can see it [here]("http://www.airtel.in/wps/wcm/connect/Airtel.in/airtel.in/home/foryou/mobile/wireless+internet/devices/pg_fy_wi_device_capitel+2g")) for another one that might be Huawei or something. Unfortunately they claimed that my one was the only one that Airtel produces for its EDGE connection. I said this was rubbish so the bloke back-tracked and said the other dongles are not available in Kerala (the state I live in).

I'm sure a more experienced user of Linux could sort this out but I've been beating myself up and going round in circles on this for a week now, so I'm afraid there won't be a solution to the problem. I will be returning the dongle to the Airtel shop to get my money back and using the one I bought this afternoon. Sorry I couldn't be more helpful to others in the same position. I was so keen to change the status of this thread to [SOLVED] :(

---

### Post by alexfish on 2010-11-29
Hi

you have been posting on two thread

since the drivers are loading "HSO" as per your other thread

I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=[COLOR=Blue]hso[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=[COLOR=Blue]hso[/COLOR]
I: If#=  2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=[COLOR=Blue]hso[/COLOR]

can you post the results of

Code:

[COLOR=Blue]ls -al /dev/ttyHS*[/COLOR]

RE:

[http://www.pharscape.org/hso.html](http://www.pharscape.org/hso.html)

Don't down load anything from the site as yet (Airtel lists as connection with APN , check with Airtell or get details of connection in windows)
PS Stick two one thread

---

### Post by demonboy on 2010-11-29
Hi Alex,

Yeah, apologies for that. This one was just supposed to be a generic thread about Ubuntu not seeing the USB device at all. Still, as I explained in my previous thread I will be returning the device to the shop today or tomorrow, but whilst I still have it the result for [COLOR=Blue]

ls -al /dev/ttyHS*[/COLOR]

```


crw-rw---- 1 root dialout 250, 0 2010-11-30 03:51 /dev/ttyHS0
crw-rw---- 1 root dialout 250, 1 2010-11-30 03:51 /dev/ttyHS1
crw-rw---- 1 root dialout 250, 2 2010-11-30 03:51 /dev/ttyHS2
crw-rw---- 1 root dialout 250, 3 2010-11-30 03:51 /dev/ttyHS3


```

---

### Post by zipteye on 2010-11-30
> **demonboy said:**
> For the record I have attempted a [similar post]("http://ubuntuforums.org/showthread.php?t=1630941") on this subject. The website suggested does not list my dongle.
 
Zipteye, when you say 
 
Do you mean create it? I don't have 'modules' in my /etc folder.
 
I've installed ndiswrapper but the driver is already installed. The problem is that the USB dongle, whilst being picked up in the Mobile Broadband Setup wizard, is not being initialised.
 
I've had this dongle for over a week now and spent all that time trying to get it up and running, to no avail. I think the easiest solution might be to just buy another dongle that has a recognised, working driver installed. I'm nipping in to town today so I'll keep you posted.
 
Sure you do.
cd /
cd /etc
ls
scroll up and down until you see modules.
Or... once you are in /etc
sudo gedit modules
 
You should list:
lp
ndiswrapper

---

### Post by demonboy on 2010-11-30
Hi zipteye,

I was using Nautilus. Even in sudo mode I was not able to see this folder. 

I have made the change you suggested and rebooted. Nothing has changed so far. What was supposed to happen?

---

### Post by alexfish on 2010-11-30
> **demonboy said:**
> Hi Alex,

Yeah, apologies for that. This one was just supposed to be a generic thread about Ubuntu not seeing the USB device at all. Still, as I explained in my previous thread I will be returning the device to the shop today or tomorrow, but whilst I still have it the result for [COLOR=Blue]

ls -al /dev/ttyHS*[/COLOR]

```


crw-rw---- 1 root dialout 250, 0 2010-11-30 03:51 /dev/ttyHS0
crw-rw---- 1 root dialout 250, 1 2010-11-30 03:51 /dev/ttyHS1
crw-rw---- 1 root dialout 250, 2 2010-11-30 03:51 /dev/ttyHS2
crw-rw---- 1 root dialout 250, 3 2010-11-30 03:51 /dev/ttyHS3


```

Hi

the device is Definitely seen , if you can't connect with NM

try the connection with wvdial or ppp

have a look in the how to , if you connect via APN , could also try Sakis3g

as you can see there are 4 tty's to choose from

some Managers need to see the end points of the device eps 03 = modem

but need to match this to the ttyHS*

can post details of

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/*[/COLOR]

alexfish

---

### Post by demonboy on 2010-12-01
Hi Alex,

Sorry, been offline for a day. I was supposed to have returned the dongle today but couldn't get in to town so I will be doing this tomorrow. However I did pop it back in to the machine and tried [COLOR=Blue]ls -al /dev/serial/by-id/* [COLOR=Black]and received:

```

ls: cannot access /dev/serial/by-id/*: No such file or directory

```

Would this be because the device was not recognised? I frequently have take out my USB modem and plug it back in again for it to get managed. 
[/COLOR][/COLOR]

---

### Post by zipteye on 2010-12-01
> **demonboy said:**
> Hi zipteye,

I was using Nautilus. Even in sudo mode I was not able to see this folder. 

I have made the change you suggested and rebooted. Nothing has changed so far. What was supposed to happen?

I'm sorry. Is this only linux on the hard drive, or is it linux and windows?

I'f only linux, then ndiswraper is of no use.

If you use only the terminal to navigate directories and files, you should have been able to see /etc modules.
But, maybe I do not know enough about nautilus.

---

### Post by alexfish on 2010-12-01
> **demonboy said:**
> Hi Alex,

Sorry, been offline for a day. I was supposed to have returned the dongle today but couldn't get in to town so I will be doing this tomorrow. However I did pop it back in to the machine and tried [COLOR=Blue]ls -al /dev/serial/by-id/* [COLOR=Black]and received:

```

ls: cannot access /dev/serial/by-id/*: No such file or directory

```Would this be because the device was not recognised? I frequently have take out my USB modem and plug it back in again for it to get managed. 
[/COLOR][/COLOR]

Hi

when you get the below the it is one the system

Code:
[COLOR=Blue]ls -al /dev/ttyHS*[/COLOR]

crw-rw---- 1 root dialout 250, 0 2010-11-30 03:51 /dev/ttyHS0
crw-rw---- 1 root dialout 250, 1 2010-11-30 03:51 /dev/ttyHS1
crw-rw---- 1 root dialout 250, 2 2010-11-30 03:51 /dev/ttyHS2
crw-rw---- 1 root dialout 250, 3 2010-11-30 03:51 /dev/ttyHS3
not sure where else it is seen on the system as this " [COLOR=Blue]ls -al /dev/serial/by-id/*" [COLOR=Black]does not register there[/COLOR][/COLOR],

but a suggested , if you get like the above then use

Either ppp or wvdial (think WVDIAL may be the better of the TWO with this Device as you can send init codes  Or even gnomeppp ,{ as requested  does it connect via APN }
 Unless you get info from Pharescape
 ADDED :Have TRACKED DOWN your thread ... at Pharescape Have you look at the [COLOR=Blue]GO[/COLOR] [COLOR=Black]options at bottom right of the page![/COLOR]

maybe you can get the info for the connection using Network Manager



if you have been through the HOW TO as listed earlier in the thread

then set the port to use from one of these :I suggest first using the /dev/ttyHS[COLOR=Blue]0[/COLOR] the [COLOR=Blue]0[/COLOR] is numerical

/dev/ttyHS0
/dev/ttyHS1
/dev/ttyHS2
/dev/ttyHS3

Have been requesting you do things and your not doing: Please read what  is suggested

If the device is not listing all the time then the Plug/Socket  or the Device could be Suspect 
Can try with the Device connect upon Boot  or Connect After Boot / see what happens

alexfish

---

### Post by demonboy on 2010-12-02
```

then set the port to use from one of these :I suggest first using the /dev/ttyHS[COLOR=Blue]0[/COLOR] the [COLOR=Blue]0[/COLOR] is numerical

/dev/ttyHS0
/dev/ttyHS1
/dev/ttyHS2
/dev/ttyHS3
Have been requesting you do things and your not doing: Please read what  is suggested

```

Alex, I have already been accused of being impatient and not reading the necessary documentation, which is rubbish and precisely why I am back here posting more questions. I still need to understand more though so its back to guide books for me. Also I had to return the dongle this morning, as I said I would, so I can't test this any furt[COLOR=Black]her.[/COLOR][COLOR=Blue][COLOR=Black] Your input has been invaluable and I have at least learned a bit about this subject already.[/COLOR][/COLOR] I appreciate your time and patience and have bookmarked this thread, as well as your other guides, for future reference.[COLOR=Blue]

[COLOR=Black]@zipteye - I have both running and I did manage to find modules in the end, thanks. [/COLOR]
[/COLOR]

---

### Post by demonboy on 2010-12-02
```

then set the port to use from one of these :I suggest first using the /dev/ttyHS[COLOR=Blue]0[/COLOR] the [COLOR=Blue]0[/COLOR] is numerical

/dev/ttyHS0
/dev/ttyHS1
/dev/ttyHS2
/dev/ttyHS3
Have been requesting you do things and your not doing: Please read what  is suggested

```

Alex, I have already been accused of being impatient and not reading the necessary documentation, which is rubbish and precisely why I am back here posting more questions. I still need to understand more though so its back to guide books for me. Also I had to return the dongle this morning, as I said I would, so I can't test this any furt[COLOR=Black]her.[/COLOR][COLOR=Blue][COLOR=Black] Your input has been invaluable and I have at least learned a bit about this subject already.[/COLOR][/COLOR] I appreciate your time and patience and have bookmarked this thread, as well as your other guides, for future reference.[COLOR=Blue]

[COLOR=Black]@zipteye - I have both running and I did manage to find modules in the end, thanks. [/COLOR]
[/COLOR]

---

### Post by alexfish on 2010-12-04
Hi all
 

 as a reminder  
 

 If you have devices which list as &#8220;option or option icon&#8221; it is advisable to visit the Pharscape Site
 

 If you visit the site , read through the intro and follow the instructions
 

 It is the only site I know of if there are problems getting connected with these devices
 

 These devices fall into two categories , some which will connect via apn , same as gsm
 

 and some which connect to dedicated servers (dns) this requires accessing the device to get
 

 the information , the AT commands are totally different for getting the info , and also for getting the device to connect, as to the standard gsm  
 

 Pharscape have the specialised drivers/software for these devices and may also need a resolver programme , like resolvconf

It is only possible to define the options to take by visiting
 

 [http://www.pharscape.org/](http://www.pharscape.org/)
 

 alexfish

---

