---
title: "Wifi not working after hibernation/suspend"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by cool2121 on 2007-06-01
So my laptop works out of the box with Ubuntu 7.04. 

The Gnome network manager automatically pick the card, Intel Pro Wireless2200.

My wireless network use WPA, and the manager let me pick WPA fine. Everything works great. 

However, about 7/10 times after my laptop wakes up from suspend or hibernation, the wireless refuses to connect. 

The card seems to be still there , the network manager seems to see the card fine. It can still list the site survey . However when i choose to connect to my AP. It just flashes for few second like its trying to get IP then its back to "No connect" status. 

Reboot the laptop would make it works fine again. In fact, it works fine for as long as i dont put it into hibernation. 

Can someone shine a light on this?  

Is it a common bug? any how to or help to solve it?

---

### Post by golfing22 on 2007-06-01
On my laptop sometimes the wifi doesn't work and when I toogle the wifi radio on/off it will connect agian.  Maybe that will help you also.

---

### Post by harty83 on 2007-06-01
I had the same problem . I found that unloading and reloading the module fixed it.  So I made a little script that ran when I resumed.

I named it 99-fixwifi.sh and added it to /etc/acpi/resume.d. 

The file contains the following:

```

#!/bin/sh

#stop everything using the ipw3945 module
/etc/init.d/networking stop
/etc/acpi/suspend.d/07-network-manager.sh

#remove the module
modprobe -r -f ipw3945

#add it back
modprobe ipw3945

#start everything back up
/etc/init.d/networking start
/etc/acpi/resume.d/99-network-manager.sh
```

Make sure you make the file executable 

```
sudo chmod +x /etc/acpi/resume.d/99-fixwifi.sh
```

I have a pro/wireless 3945ABG so you may have to change what module is unloaded/reloaded.

Alan

---

### Post by cool2121 on 2007-06-02
where can i check what module it use?

---

### Post by harty83 on 2007-06-02
> **cool2121 said:**
> where can i check what module it use?

It is probably ipw2200.  While your wireless is working, type this into a terminal

```
lsmod | grep 'ipw'
```

and see what it returns.

Let me know if that doesn't get you anywhere.

---

### Post by cool2121 on 2007-06-02
Yes its ipw2200 
> 
ipw2200               148040  0 
ieee80211              34760  1 ipw2200



I'm copying your script now. I will let you know as i'm done. 

Thanks

---

### Post by cool2121 on 2007-06-02
OK so i got the script done just like yours except i put ipw2200 instead. 

I test it twice with suspends and hibernation. The wireless works fine now. 

However, there is another issue. This is the second time it happens. After the suspends, the mousepad no longer works. The power button also does not respond. During the wake up, when the screen quickly shows the text, its so quick i can only see someting "USB"

Thanks alot everyone.

---

### Post by rkent on 2007-06-05
> **harty83 said:**
> I had the same problem . I found that unloading and reloading the module fixed it.  So I made a little script that ran when I resumed.

I named it 99-fixwifi.sh and added it to /etc/acpi/resume.d. 

The file contains the following:

```

#!/bin/sh

#stop everything using the ipw3945 module
/etc/init.d/networking stop
/etc/acpi/suspend.d/07-network-manager.sh

#remove the module
modprobe -r -f ipw3945

#add it back
modprobe ipw3945

#start everything back up
/etc/init.d/networking start
/etc/acpi/resume.d/99-network-manager.sh
```

Make sure you make the file executable 

```
sudo chmod +x /etc/acpi/resume.d/99-fixwifi.sh
```

I have a pro/wireless 3945ABG so you may have to change what module is unloaded/reloaded.

Alan

Question: did you also write those *-network-manager.sh files yourself?  I don't have those (kubuntu 7.0.4) and I'm having the same problem (network down after suspend/resume cycle) and I wonder if that's the problem...

---

### Post by Atomic Dog on 2007-06-06
I remarked out the 99-network_manager line and it still resumes from suspend just fine.  Wireless now works!  Three suspends and starts in a row without issues.

Glad I found this thread!
One strange thing is the LED for the wireless stays on during suspend.  Is this normal?  I'm concerned the wireless card is being fed precious power from the battery unnecessarily.

---

### Post by harty83 on 2007-06-06
Oops.  I did write those files.  I forgot about that. I'm not on the computer with them, but I'll check them and post what they are.  It had to do with network manager not working after suspend/resume back on Dapper I think.  The problem has probably been fixed.  All they do is shut down the network manager dispatcher on suspend and then start it again on resume.  

I"ll get them to you ASAP.

Alan

---

### Post by DavidFourer on 2007-06-06
> I had the same problem . I found that unloading and reloading the module fixed it. So I made a little script that ran when I resumed.
I named it 99-fixwifi.sh and added it to /etc/acpi/resume.d.
I have this problem with my wired connection about once per day on resume.  I want to write a re-set script and put an icon on my tool bar.  Can you tell me what to write? (Explain what it does would be nice, so I can learn some thing new).  Thanks

---

### Post by harty83 on 2007-06-06
For the suspend script I had 

```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```

and then for the resume I had 
```

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start
```

>  I have this problem with my wired connection about once per day on resume. I want to write a re-set script and put an icon on my tool bar. Can you tell me what to write? (Explain what it does would be nice, so I can learn some thing new). Thanks


DavidFourer,

What network card do you have?  Do ```
lspci 
``` from the command line and find what network card it is.  Then find the module that loads the card.  (Unless you use something like ndiswrapper, that would change things.)   Do you use network manager to control your card?

Here is an example of what you can do after you know the module (replace ipw3945 with your module name:

Create and open the file by 
```
sudo -b gedit /usr/sbin/fixnetwork.sh
```

Copy and paste this into it (remember to change ipw3945 with your module)
```

#!/bin/sh

/etc/init.d/networking stop
/etc/dbus-1/event.d/25NetworkManager stop

modprobe -r -f ipw3945
modprobe ipw3945

/etc/init.d/networking start
/etc/dbus-1/event.d/25NetworkManager start

```

The make it executable by 
```
sudo +x /usr/sbin/fixnetwork.sh
```

Then right click on your toolbar and click on Add to Panel.  Click on Custom Application Launcher.  Give it whatever name you want.  For the command type "gksu /usr/sbin/fixnetwork.sh"  Click on "No Icon" and select an icon of your choice.  Then click OK.  You should be all set.

Let me know if you get stuck along the way or can't find the module your card uses.

---

### Post by ewinslow on 2007-11-11
Nice to get a fix for this. Thanks. It's a very troublesome issue.

Do you know if a bug has been submitted for this problem? I haven't searched yet myself.

---

### Post by svguy on 2007-11-28
I've had this problem on my dell d600 laptop.  I added this script and did quite a few tests where i quickly put it to sleep or hibernate and opened it back up again and it works, but if the computer goes to sleep for any significant period of time (like 30 minutes) then when i come back it won't work.
A couple times now it's also failed to work on boot.

In fact, the boot just before my current one it said no network devices could be detected.
I did ifconfig and it only showed "lo."
I tried doing ifconfig eth1 up and it said the device was missing.
I tried modpro ipw2200 and it didn't change anything.

Does anyone know what's cause this or where i can look?

Thank you

---

### Post by svguy on 2007-11-29
It did it again today.  It was in suspend for about an hour and when i brought it back the GUI said there was no network connection.
I checked in a terminal and did iwlist scan and it showed my wireless network, but I just couldn't get it to work.
Can someone please help me?

---

### Post by inverseroom on 2008-01-27
ALAN!!!!  YOU'RE MY HERO!!!!

I just discovered your script and it absolutely works on my Pavilion dv1000.  This was my last remaining serious issue with Gutsy...THANK YOU.

---

### Post by kevdog on 2008-01-27
That's a great script -- Im going to have to make a link to this post!

---

### Post by Arthur Archnix on 2008-02-26
```
sudo +x /usr/sbin/fixnetwork.sh
```

Let me know if you get stuck along the way or can't find the module your card uses.[/QUOTE]

That returned an error. Perhaps sudo chomod +x?

---

### Post by Wikzo on 2008-03-14
Can I use the same script with Wicd Manager? Or what should I do, because my Wifi doesn't work after hibernating my laptop (Intel PRO/Wireless 4965 and driver=iwl4965).

I am using Wicd on Ubuntu 7.10, because I can't get the default NetworkManager to work with my schools WEP encrypting.

---

