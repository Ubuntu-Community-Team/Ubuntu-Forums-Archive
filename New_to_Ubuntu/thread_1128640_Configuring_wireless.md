---
title: "Configuring wireless?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-17
How do I configure wireless in Ubuntu? Or join networks?

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> How do I configure wireless in Ubuntu? Or join networks?

Well, assuming you have all your drivers working, you click the networking icon in the top right hand corner of the screen and when the menu appears you select 'manual configuration'. A new window will open, you then select 'unlock' and enter your password when prompted.

In this window should be an option for your wireless connection, you can change the properties of that wireless connection to configure your wireless settings.

If you can't see a wireless option in that window then you probably haven't sorted out the appropriate drivers yet, and Ubuntu probably doesn't come shipped with them, so you'll need to install them yourself (i.e. using the Ubuntu package managers). If you need help with any of that just ask, we are here to help.

---

### Post by Noise... on 2009-04-17
Yeah - I don't have that yet. What wireless manager would be best to get?

---

### Post by NullHead on 2009-04-17
Usually in a standard install of Ubuntu 8.04 (I'm guessing that's the one you installed?) there is a network manager pre-installed. 

To access it, it should be located in the top-right corner of your screen; next to the volume icon. 

You most likely need some drivers to get your wifi device working.

---

### Post by Noise... on 2009-04-17
> **NullHead said:**
> Usually in a standard install of Ubuntu 8.04 (I'm guessing that's the one you installed?) there is a network manager pre-installed. 

To access it, it should be located in the top-right corner of your screen; next to the volume icon. 

You most likely need some drivers to get your wifi device working.

I installed Ubuntu Studio 8.04. I don't have the volume icon either. All that's in my top right panel is the date, time, and trash icon.

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> Yeah - I don't have that yet. What wireless manager would be best to get?

If you are running a normal Ubuntu Hardy Heron installation then you have Network Manager. It is default. You should be able to open it (if you can't see an icon in the top right corner next to the date...which is strange because if you have an ethernet card that is functioning you should be able to see that icon) by going to System --> Administration --> Network.

While Network Manager does work, it isn't exactly awesome as far as wireless networking goes. A networking GUI that is more wireless-focussed is 'wicd'.

you can check out the details about it (as well as a guide on installing it) at the wicd website [http://www.wicd.net/download.php](http://www.wicd.net/download.php)

I would try and get it running through Network Manager first though, because more people on this forum can help you with Network Manager than can with wicd. Once you have the network connection up and running, then mess with wicd.

EDIT:
> **Noise... said:**
> I installed Ubuntu Studio 8.04. I don't have the volume icon either. All that's in my top right panel is the date, time, and trash icon.

Sorry only just read that.

You can check whether or not the network manager is installed using this command in the console:

```
apt-cache policy network-manager-gnome
```

If the package is not installed you can download it [here]("http://packages.ubuntu.com/hardy/network-manager-gnome")

---

### Post by Noise... on 2009-04-17
> **porchrat said:**
> If you are running a normal Ubuntu Hardy Heron installation then you have Network Manager. It is default. You should be able to open it (if you can't see an icon in the top right corner next to the date...which is strange because if you have an ethernet card that is functioning you should be able to see that icon) by going to System --> Administration --> Network.

While Network Manager does work, it isn't exactly awesome as far as wireless networking goes. A networking GUI that is more wireless-focussed is 'wicd'.

you can check out the details about it (as well as a guide on installing it) at the wicd website [http://www.wicd.net/download.php](http://www.wicd.net/download.php)

I would try and get it running through Network Manager first though, because more people on this forum can help you with Network Manager than can with wicd. Once you have the network connection up and running, then mess with wicd.

EDIT:


Sorry only just read that.

You can check whether or not the network manager is installed using this command in the console:

```
apt-cache policy network-manager-gnome
```

Network Manager IS installed - just no icon. 

I just opened it, and since I installed Windows drivers, Wireless is no longer configurable. I have two options; Wired Connection and Point to Point connection. Both of which say under them "This Network Interface is not configured."

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> Network Manager IS installed - just no icon. 

I just opened it, and since I installed Windows drivers, Wireless is no longer configurable. I have two options; Wired Connection and Point to Point connection. Both of which say under them "This Network Interface is not configured."

Windows driver? So you used ndiswrapper?

If not then please explain to us what you have done so far to attempt to get it all running. Also could you post the output of this command so that we can determine whether or not ubuntu sees a functional wireless device:

```
iwconfig
```

---

### Post by Noise... on 2009-04-17
> **porchrat said:**
> Windows driver? So you used ndiswrapper?

If not then please explain to us what you have done so far to attempt to get it all running. Also could you post the output of this command so that we can determine whether or not ubuntu sees a functional wireless device:

```
iwconfig
```

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.
```

In a thread I made the other day regarding the wireless, I was recommended to install ndiswrapper and the XP drivers for the wireless device. 

According to the driver install, the driver sees the wireless adapter, Ubuntu doesn't. However, prior to this, Ubuntu DID recognize it, but wouldn't activate it. 

Thinking back now, it probably just wasn't configured and I've botched it trying to fix it. :(

---

### Post by NullHead on 2009-04-17
Also, what is the Manufacturer and model of the wifi card?

---

### Post by izizzle on 2009-04-17
Personally, I hate the network manager implemented in 8.10. It's very buggy and (IMHO) a downgrade from the previous Network Manager. Try using [WICD]("http://wicd.sourceforge.net/") and see if you have better luck.

---

### Post by Noise... on 2009-04-17
The wireless adapter is;

Intel Corporation PRO/Wireless 4965 AG

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> ```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.
```

In a thread I made the other day regarding the wireless, I was recommended to install ndiswrapper and the XP drivers for the wireless device. 

According to the driver install, the driver sees the wireless adapter, Ubuntu doesn't. However, prior to this, Ubuntu DID recognize it, but wouldn't activate it. 

Thinking back now, it probably just wasn't configured and I've botched it trying to fix it. :(

No need to worry, it definitely looks like ubuntu doesn't recognise your wireless module at the moment, therefore running network manager isn't going to help.

I've taken a read through that other thread you started and I see you are running an Intel Corporation PRO/Wireless 4965 AG. Just to be sure please post the output of this command:

```
lshw -C network
```

Keep in mind that Linux is case sensitive so use a capital 'C'.

I have had a little experience with intel PRO/wireless modules and in the end I settled on ndiswrapper as well, but as was mentioned in that previous thread, Ubuntu has drivers for that module. You may find it was working.

Luckily it is easy to undo the ndiswrapper install and get the original driver running again, however first we need to confirm that that is the module you have, so please post that output. (I realise we are asking you to repeat things, but it is best to be certain)

Also note that just because the wireless light doesn't come on and the wireless switch on the notebook case does not respond, this does not mean your wireless module is not functioning. For example, my wireless switch does not respond, but my light works.

---

### Post by Noise... on 2009-04-17
Here's the output;

```
 lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:f4:b2:c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

---

### Post by porchrat on 2009-04-17
```
product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation

```

OK so that is indeed what you are running.

It is probably a good idea right now to try and see what the original driver was like. In order to do that we need to remove the ndiswrapper driver and install the original one again.

The ndiswrapper driver can be removed using that same program (ndisgtk) that you used to install it in the first place.

Go to System --> Administration --> Windows Drivers and select 'remove driver'.

You should then be able to reinstall the old driver through the 'restricted drivers' window.

If memory serves (not in front of Ubuntu at the moment), you can get there through System --> Administration --> Hardware Drivers. Under 'Hardware Drivers' there should be a wireless driver, enable it, restart the machine and hey presto it is running again.

You can then run 'iwconfig' (or open network manager) again to see if the device is recognised.

---

### Post by Noise... on 2009-04-17
Ok - I uninstalled the Windows driver, but under hardware drivers there aren't any listed drivers.

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> Ok - I uninstalled the Windows driver, but under hardware drivers there aren't any listed drivers.

It should load the driver on a restart.

Another alternative (often works on intrepid installations, perhaps it would help in a hardy install) is to install the linux-backports-modules-hardy package:

```
sudo apt-get install linux-backports-modules-hardy
```

Again you would need to restart.

---

### Post by Noise... on 2009-04-17
> **porchrat said:**
> It should load the driver on a restart.

Another alternative (often works on intrepid installations, perhaps it would help in a hardy install) is to install the linux-backports-modules-hardy package:

```
sudo apt-get install linux-backports-modules-hardy
```

Ok. I'll restart and post back.

---

### Post by Noise... on 2009-04-17
No change with the restart. :(

---

### Post by porchrat on 2009-04-17
> **Noise... said:**
> No change with the restart. :(

Did you install the linux-backports-modules-hardy package?

That should've contained the driver you need.

What is listed under the 'Hardware Drivers' window?

EDIT: Another thing to be aware of is that if you are dual booting you need to make sure that the switch on the case is 'on' under XP/Vista. If that switch is 'off' under XP/Vista, then the module sometimes remains off under Linux (depends on make and model of notebook). Unfortunately because Linux can't use that switch there is no way to turn the module on under Linux.

---

### Post by Noise... on 2009-04-17
> **porchrat said:**
> Did you install the linux-backports-modules-hardy package?

That should've contained the driver you need.

What is listed under the 'Hardware Drivers' window?

They're downloading now. 

There's nothing listed in the Hardware Drivers window. It just says "No proprietary drivers are in use on this system."

---

### Post by Noise... on 2009-04-17
Ok - drivers are downloaded (along with a kernel?) and installed.

In my standard kernel, nothing showed up.

In the new generic kernel (same number as my usual kernel) the new driver showed up in the hardware drivers window.

It says that it's enabled, but not in use. The network doesn't show the wireless adapter though.

---

### Post by Noise... on 2009-04-17
Bump. What should I do now?

---

### Post by Noise... on 2009-04-17
Bump. I need to get this fixed by tomorrow. :(

---

### Post by aldrinmirambel on 2009-04-17
I don't get what your problem really is?
What kind of wireless you're going to install?

_________________________
**[Art Framed, Posters, Art Prints](http://www.ichatart.com/)**

---

### Post by Noise... on 2009-04-17
> **aldrinmirambel said:**
> I don't get what your problem really is?
What kind of wireless you're going to install?

_________________________
**[Art Framed, Posters, Art Prints](http://www.ichatart.com/)**

Basic wireless so that I can connect to wi-fi networks.

---

### Post by Noise... on 2009-04-18
Bump. :(

---

### Post by porchrat on 2009-04-18
> **Noise... said:**
> Ok - drivers are downloaded (along with a kernel?) and installed.

In my standard kernel, nothing showed up.

In the new generic kernel (same number as my usual kernel) the new driver showed up in the hardware drivers window.

It says that it's enabled, but not in use. The network doesn't show the wireless adapter though.

Sorry I had to go to sleep.

Yes it would've installed kernel headers along with the linux-backports-module-hardy package. That is normal.

What says "enabled but not in use"? The Hardware Drivers window? If so that is a good sign.

One of the easiest ways to check whether or not you have a functional wireless device is to type "iwconfig" into the console.

It should have a device called "wlan0", this is your wireless device.

It may help to install wicd as well, I find it easier to use than the gnome Network Manager.

---

### Post by Noise... on 2009-04-18
No worries. I'm thankful for your help so far!

Ok, iwconfig still has the same output as before. No wlan0 entry.

The kernel that downloaded has quite a few issues - there's no sound, and boot up is slow and glitchy. My usual kernel works fine, but doesn't show the new driver. 

Would it be easier to just reinstall Ubuntu? I can confirm 100% that the wireless device was showing up before messing with the windows drivers. I really wish someone would have just told me that it probably wouldn't have the light on the switch, and that it just needed to be configured. :(

---

### Post by Noise... on 2009-04-18
bump.

---

### Post by Noise... on 2009-04-18
Final bump before I just reinstall Ubuntu. :(

---

### Post by hesjnet on 2009-04-18
The thing I'm not understanding here is why your intel card isn't configured automaticly. It is, as far as I know, a quite common wifi card and should work out of the box.

Have you tried to run a live-disk to see if it has something to do with  your install?

Boot from the install-cd and choose "Try without any changes to the computer"

---

### Post by Noise... on 2009-04-18
> **hesjnet said:**
> The thing I'm not understanding here is why your intel card isn't configured automaticly. It is, as far as I know, a quite common wifi card and should work out of the box.

Have you tried to run a live-disk to see if it has something to do with  your install?

Boot from the install-cd and choose "Try without any changes to the computer"

The issue is that I got bad advice when I didn't realize that the card was working. I thought that it had to have the light on the switch to be working, when that just wasn't the case. The bad advice was that I needed windows drivers and a large update to Ubuntu.

Installing the Windows driver erased the Ubuntu driver that was actually working. 

Now that I've learned more about wireless in Ubuntu, it basically just needed a signal to connect to and I would have been set. Instead of just being told that, I was given bad advice, and now I'm stuck.

---

### Post by hesjnet on 2009-04-18
The easiest way then, is to reinstall ubuntu. Sorry if someone gave you bad advise. It was probably not intentional;). 

There is always a way to fix the problem, but for you the fastest and easiest would probably to do a clean install. Remember to back-up your files on another drive/partition.

---

### Post by Noise... on 2009-04-18
> **hesjnet said:**
> The easiest way then, is to reinstall ubuntu. Sorry if someone gave you bad advise. It was probably not intentional;). 

There is always a way to fix the problem, but for you the fastest and easiest would probably to do a clean install. Remember to back-up your files on another drive/partition.

I don't really have anything that needs backed up, as the install is still pretty clean aside from the wireless drivers and Wine. 

Is there any way that I can back up downloaded updates so that I didn't just waste 250MB of my 5GB monthly bandwidth?

---

### Post by hesjnet on 2009-04-18
In the thread [Back up downloaded updates]("http://ubuntuforums.org/showthread.php?t=149489") Sutekh suggest this:

[quote="Sutekh"]Easiest ways

[Ubuntu Wiki - Apt Move Howto]("https://wiki.ubuntu.com/AptMoveHowto")

and

[Ubuntu Wiki - Apt Move Howto (Simple)]("https://wiki.ubuntu.com/AptMoveHowto/simple")


[Ubuntu Starter Guide - Backup and Restore apt-get cache]("http://www.ubuntuguide.org/#backuprestoredownloadedrepositoriescache")


You could also create a local repository, on say another partition that won't be formatted when you re-install Ubuntu. You can add that to your sources.list and "download" your packages from there.[/quote]

I suggest you try the middle one: Ubuntu Wiki - Apt Move Howto (Simple)

Hope this helps.

---

### Post by Noise... on 2009-04-18
Will Aptmove also add in the Windows driver thing that messed everything up in the first place?

---

### Post by porchrat on 2009-04-19
I'm sorry, it seems we have been unable to help you very much with this particular problem. At least we have isolated the problem.

I have just recently tried installing my windows xp drivers again using ndiswrapper, just to see if I could find a way to make them work that might be helpful to you.

I found that when I installed wicd, somehow my ndiswrapper drivers worked straight away. I'm still not 100% sure how this is even possible, because wicd shouldn't have effected the drivers at all. However I tried the exact same drivers using gnome Network Manager a week ago and I couldn't get them to run.

I doubt it will help you, but I can tell you that I have found that running drivers under ndiswrapper (if you can get them running) seems to be better than running the default Ubuntu drivers (at least with regards to Broadcom modules and Intel PRO/Wireless modules). With atheros cards there are so many easier alternatives that are equally as effective (if not more so) than windows drivers running through ndiswrapper.

---

### Post by XubuRoxMySox on 2009-04-19
I found that **ndiswrapper** would not work in my 8.10 without *also* using **ndisgtk**. So to get Windows drivers for your wifi to work:

**[COLOR="Purple"]1.[/COLOR]** Have the Windows drivers copied to your desktop. These should be the .inf and .sys files, not .aip or .exe

**[COLOR="Purple"]2.[/COLOR]** Using the Ubuntu Installation CD (just have it in the drive) and Synaptic Manager, get and install ndisgtk, and ndiswrapper and it's utilities from the CD.

**[COLOR="Purple"]3.[/COLOR]** Open a Terminal window and type
```
cd ~/desktop <enter>
sudo ndiswrapper -ixxxxx.inf (where xxxxx id the the name of the .inf file) <enter>
sudo ndiswrapper -l <enter>
```

That's how I got mine to work. I'm a newbie too, so before you try this, let's see if one of the veterans will confirm my advice before you take it. But it worked for me.

-Robin

---

### Post by porchrat on 2009-04-20
> **dixiedancer said:**
> I found that **ndiswrapper** would not work in my 8.10 without *also* using **ndisgtk**. So to get Windows drivers for your wifi to work:

**[COLOR="Purple"]1.[/COLOR]** Have the Windows drivers copied to your desktop. These should be the .inf and .sys files, not .aip or .exe

**[COLOR="Purple"]2.[/COLOR]** Using the Ubuntu Installation CD (just have it in the drive) and Synaptic Manager, get and install ndisgtk, and ndiswrapper and it's utilities from the CD.

**[COLOR="Purple"]3.[/COLOR]** Open a Terminal window and type
```
cd ~/desktop <enter>
sudo ndiswrapper -ixxxxx.inf (where xxxxx id the the name of the .inf file) <enter>
sudo ndiswrapper -l <enter>
```

That's how I got mine to work. I'm a newbie too, so before you try this, let's see if one of the veterans will confirm my advice before you take it. But it worked for me.

-Robin

You don't NEED ndisgtk, but it does make it much, much easier. Also there is a utilities package that you can install too. The utilities package has scripts that run the ndiswrapper'ed drivers on startup, before that you often ended up having to start them manually.

What you have done there is essentially run ndiswrapper _without_ using ndisgtk. ndisgtk is a GUI system for ndiswrapper. It creates an option under System --> Administration --> Windows Drivers. You can click that and then navigate to your .inf file using a window system. It makes it easy for those who are uncomfortable with using the command line to use ndiswrapper.

---

### Post by Noise... on 2009-04-20
There's no need for ndiswrapper now.

I reinstalled Ubuntu to get the original driver back. Once the reinstall was done, the wireless and the switch worked. I got Wicd for a wireless manager, and I finished it just in time to be able to use Ubuntu when I was out in town yesterday. 

My only issue since then is being unable to connect to a created ad-hoc network. It hangs at the "obtaining IP Address" part and won't connect.

---

### Post by porchrat on 2009-04-20
> **Noise... said:**
> There's no need for ndiswrapper now.

I reinstalled Ubuntu to get the original driver back. Once the reinstall was done, the wireless and the switch worked. I got Wicd for a wireless manager, and I finished it just in time to be able to use Ubuntu when I was out in town yesterday. 

My only issue since then is being unable to connect to a created ad-hoc network. It hangs at the "obtaining IP Address" part and won't connect.

Congratulations, I'm glad you managed to sort it out.

That was probably the best course of action all things considered. I'm sorry ndiswrapper didn't work out for you.

Keep in mind that you can change the settings of the wireless device through the command line by using the "iwconfig" command. You need to use "sudo" with it though. To check out the various things you can do with iwconfig look at the man page through the command line:

```
man iwconfig
```

"ifconfig" can also be helpful.

May help you when connecting as you could bypass the GUI.

---

