---
title: "WUSB54Gv2 Problems"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by Robotra on 2006-12-25
I've been trying for ages to get this WUSB54G to work on my computer.  When I put in "ndiswrapper -l" I get:

wusb54gv2: driver installed

Regardless of if the adapter is connected to the computer or not.  I'm sure it's connecting; on XP the same adapter + cable are detected automatically and I can use the internet in seconds.  Not on here, however.

Is there anything I can do to get this to work?  On the ndiswrapper site I saw something about updated drivers, but even trying those didn't help.

NOTE: I know there's a sticky about this.  However, WUSB54Gv1/2 and WUSB54Gv4 have different chipsets.  Also, I'm using Edgy if it helps.

---

### Post by Floppyjoe on 2006-12-25
Does it ever say hardware present when the adapter is plugged in and you do the ndiswrapper -l command?

---

### Post by Robotra on 2006-12-25
No, it only says driver installed.  This bites :/

---

### Post by Floppyjoe on 2006-12-25
What version of ndiswrapper-utils are you using?
If you are not already, install ndiswrapper-utils 1.8 using synaptic package manager via System/Administration/Synaptic Package Manager.  Then list the installed driver using ndiswrapper -l. Then delete the driver listed using sudo ndiswrapper -e drivername where drivername is the listed installed driver. Then reinstall the driver using:

```
sudu ndiswrapper-1.8 -i drivername.inf
```
The drivername.inf is case sensitive.

Then try:
```
ndiswrapper -l
```
to see if it lists the driver with hardware present.

Hope this helps

---

### Post by Sleepy_Sentry on 2007-01-27
I am having the same exact problem. However, whenever I go to uninstall the driver, ndiswrapper tells me it isn't installed, even though it is! I am using the ndiswrapper 1.8 that is  on the Ubuntu CD.

---

### Post by JamieC on 2007-01-27
> **Sleepy_Sentry said:**
> I am having the same exact problem. However, whenever I go to uninstall the driver, ndiswrapper tells me it isn't installed, even though it is! I am using the ndiswrapper 1.8 that is  on the Ubuntu CD.

What's the output of ndiswrapper -l (in terminal)?

---

### Post by Sleepy_Sentry on 2007-01-27
It is:
```

Installed ndis drivers:
wusb54gv2     invalid driver!

```

The name of the .inf file is WUSB54Gv2.inf.

---

### Post by Sleepy_Sentry on 2007-01-27
Ok, it looks like I now have the device installed (hopefully)
```

Installed ndis drivers:
wusb54gv2    driver present, hardware present

```

However, iwconfig brings up "no wireless extensions" on lo, eth0, and sit0.

What should I do next?

---

### Post by JamieC on 2007-01-27
Open a terminal window and run the following commands:
```

sudo modprobe ndiswrapper

```

```

sudo ndiswrapper -m

```

Then edit /etc/modules using your preferred editor:
```

sudo <editor> /etc/modules

```

Add the following on a new line at the bottom of the file:
> 
ndiswrapper


Save the file and then run the following command (where <ssid> is the SSID of your router):
```

sudo iwconfig wlan0 essid <ssid> mode Managed

```

Now post the output of the following:
```

iwconfig

```

---

### Post by Sleepy_Sentry on 2007-01-27
> **JamieC said:**
> Open a terminal window and run the following commands:
```

sudo modprobe ndiswrapper

```

```

sudo ndiswrapper -m

```

Then edit /etc/modules using your preferred editor:
```

sudo <editor> /etc/modules

```

Add the following on a new line at the bottom of the file:


Save the file and then run the following command (where <ssid> is the SSID of your router):
```

sudo iwconfig wlan0 essid <ssid> mode Managed

```

Now post the output of the following:
```

iwconfig

```

sudo modprobe ndiswrapper returns:
```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

Is it possible ndiswrapper is corrupt and needs to be reinstalled?

---

### Post by JamieC on 2007-01-27
You did specify the correct password and or already have an active 'sudo session', right?

If so, skipping that step (for now) should not prohibit proceeding with the rest of the steps.

---

### Post by Sleepy_Sentry on 2007-01-27
I did specify the correct password and have a sudo session running.

sudo iwconfig wlan0 kcwingwalker(my SSID) mode Managed returns
```

Error: unrecognised wireless request "kcwingwalker"

```

iwconfig returns:
```

lo no wireless extensions

eth0 no wireless extensions

sit0 no wireless extensions 

```

Thanks for the help you've given me so far. I hope I can get this fixed soon.

---

### Post by JamieC on 2007-01-27
Try the following instead:
```

sudo iwconfig wlan0 essid kcwingwalker

```

Then:
```

iwconfig

```

---

### Post by Sleepy_Sentry on 2007-01-27
sudo iwconfig wlan0 essid kcwingwalker
```

Error for wireless request "Set ESSID" (8B1A) :
     SET failed on device wlan0 ; No such device.

```

Iwconfig returned the same information as stated in my previous post.

---

### Post by JamieC on 2007-01-27
Hm, it appears that the modprobe is required for the device to be detected. In terminal try the following:
```

sudo depmod -a

```

Then:
```

sudo modprobe ndiswrapper

```

If that fails, I suggest removing ndiswrapper, then installing it once again.

---

### Post by Sleepy_Sentry on 2007-01-27
No luck :(.

I will proceed with reinstalling ndiswrapper.

Thanks for the help.

---

### Post by JamieC on 2007-01-27
> **Sleepy_Sentry said:**
> No luck :(.

I will proceed with reinstalling ndiswrapper.

Thanks for the help.

Sorry, my wireless knowledge is pretty limited. After searching reinstalling seems to be a common suggestion throughout...

---

### Post by Sleepy_Sentry on 2007-01-27
Any help is better than no help.

How exactly do I uninstall ndiswrapper? I Googled but couldn't find the command.

---

### Post by JamieC on 2007-01-27
To remove ndiswrapper
```

sudo apt-get remove ndiswrapper

```

To install ndiswrapper:
```

sudo apt-get install ndiswrapper

```

---

