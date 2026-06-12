---
title: "New to ubuntu, several questions"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by thenetminder33 on 2010-09-14
I am essentially brand new to linux and ubuntu, and have several problems that i would like resolved. 
I am running ubuntu 10.04.1 in dual boot with Win7, each time i boot ubuntu i have to log in at the command prompt and use the "startx" command to get to the desktop. I have inquired about this before and not worked out a solution. Any ideas would be nice, however i can live with it(for now) and really would like to fix these.

1. Wireless, i have skimmed through many threads and not much has helped, as i do not have a LAN port in the room with my computer WiFi is my only internet. My adapter is a brand new AZIO AWU354. I tried installing the driver, assuming it was not in the kernel. However, disc does not auto run and i cannot find it or the drive under Computer folder.
Using one of the commands provided in ubuntu help, i found the adapter listed as Disabled.

2. Ubuntu does not let me shut down, i tried the power button in upper right, but no drop down menu appears. I tried ctrl alt del but the shut down and restart options are faded and "unclickable" so i have to power down using case buttons.

Thanks for any help

---

### Post by Lateralis on 2010-09-14
Problem 0: having to **startx**

When you get to the grub screen (press shift immediately after the BIOS has stopped posting output if you are operating only Ubuntu) highlight the kernel you wish to boot and press 'e'.  This will enable you to edit the kernel boot options.  On the next page, highlight the kernel line and hit 'e' again.  Scroll to the end of the line and place a '5'.  Did you start up in a graphical environment, or did you still end up at the command line?  Or did nothing happen and it all went to put?!  

Problem 1: Wireless.  

It sounds like you were trying to install the Windows driver; is that correct?  If so (your post made it seem you were), well it won't work.  Windows and Linux work in different ways and drivers for one cannot be used in the other.  Specifically, drivers in Linux are loaded directly into the kernel as modules.  Kernel modules can also be loaded into and removed from the kernel in real time.  

Anyway, I've had so few networking problems that my knowledge of networking issues is somewhat limited.  A few things that might help diagnose the problem.  

On the top bar do you see a little network applet?  If you do not, right click the panel and select "Add to panel".  Scroll down and select the "Network Monitor" applet.  Then left click on that; what do you see?  

The other thing to do is to open up a terminal and type in the following: 

```

sudo ifconfig eth1 up

```
 
to start up the wireless connection.  It might work, it might not.  

If it doesn't, then lets look in more detail at the hardware.  Type

```

sudo lshw

```

into the command line and find the entry which corresponds to your wireless network card (you will have two **-network* entries, one corresponding to your wired, the other your wireless cards).  Paste the results into your reply.  If you want, you can just past the whole thing, but ensure to enclose the result in code tags.  

Problem 2: This is quite peculiar.  Right click on the panel -> Add to Panel -> scroll down and select *Shut Down...*.  Can you shut down/restart your computer using this applet?  
If not, a temporary fix is to use the command line to shut down and restart:

```

sudo shutdown -h now
sudo restart now

```

as opposed to a hard shut down/reboot.

---

### Post by fly-by-night on 2010-09-14
2. Try this in terminal (Accessories/Terminal):```
sudo shutdown -P -time 13:50
``` Where 13:50 is time based on a 24h clock and the password is your admin/root password. Choose a time that's close to your current time. If it work, then you created an account with limited rights. That's just a guess and the command will either work or not, no harm done.

startx - [http://ubuntuforums.org/showthread.php?t=598463](http://ubuntuforums.org/showthread.php?t=598463) It's a bit old, but the same problem that might work for you.

---

### Post by thenetminder33 on 2010-09-14
thanks for the help, cant try these things out right now, but when i do ill let you know how they worked

---

### Post by thenetminder33 on 2010-09-15
Neither the Network Monitor or Shutdown applets appear in the in the add to panel list,

However the terminal commands do allow me to shutdown.

This code does not work (returns an error)
```

sudo if config eth1 up

```

```
sudo lshw
```
returns an extremely long list, i could not copy it all but i assume you are looking for this:
```

*-network DISABLED
     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: c8:3a:35:e4:68:64
     capabilities: ethernet physical wireless
     configuration: broadcast=yes multicast=yes wireless= IEEE 802.11bgn


```

---

### Post by thenetminder33 on 2010-09-15
> **fly-by-night said:**
> startx - [http://ubuntuforums.org/showthread.php?t=598463](http://ubuntuforums.org/showthread.php?t=598463) It's a bit old, but the same problem that might work for you.

The commands in this forum provided some interesting results for me:
```
sudo apt-get update
```
produced lots of files listed out:
```
Failed to fetch http://...
Failed to fetch http://...
...
...
Some index files failed to download, they have been ignored, or old ones have been use instead
```
however, could this be because i dont have internet access??

Command number 2
```
sudo apt-get install ubuntu-desktop
```
all up to date

Command number 3
```
sudo /etc/init.d/gdm restart
```
sent ubuntu into low graphics mode with following error:
```
(EE) RADEON(0): Acceleration initialization failed
```
My graphics card is RADEON HD 5770 and is new and may not be in the kernel

Any thoughts??

---

### Post by nothingspecial on 2010-09-15
The first thing I would do is get a wired connection somehow and do all your updates

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Then, still with the wired connection, in your menu go system > administration > hardware drivers and see if anything shows up there.

---

### Post by thenetminder33 on 2010-09-15
I would like to do that however i do not currently have a LAN port available near me. But i will get to it ASAP

---

### Post by thenetminder33 on 2010-09-17
Wired LAN connection, still cannot download updates.
Wired LAN listed as DISABLED in lshw

What now?

---

### Post by thenetminder33 on 2010-09-17
wireless works :D i think

my wireless card's name was wlan0 not eth1

so i entered this```
sudo ifconfig wlan0 up
```
and the wireless device is no longer listed as DISABLED, actually does not have any "status" (CLAIMED, UNCLAIMED, ENABLED, or DISABLED)

However Firefox does not work: Returns can not find server error.

Any thoughts as to why?

---

### Post by sandyd on 2010-09-17
> **thenetminder33 said:**
> wireless works :D i think

my wireless card's name was wlan0 not eth1

so i entered this```
sudo ifconfig wlan0 up
```and the wireless device is no longer listed as DISABLED, actually does not have any "status" (CLAIMED, UNCLAIMED, ENABLED, or DISABLED)

However Firefox does not work: Returns can not find server error.

Any thoughts as to why?
you have to connect to a wireless network before browsing.
enabling your wireless network will not automatically connect you to a wireless network.

---

### Post by thenetminder33 on 2010-09-17
My computer wont open
System>Preferences>Network Connections

Nothing happens when i click on it

This is the way to connect to a network right?

---

### Post by Lateralis on 2010-09-18
Ah, of course its wlan0, not eth1.  That was careless of me. :P  

Anyway, there's a network applet on the Gnome panel at the top right.  If you click on that, do you see any wireless networks listed? 

If you can't see the network applet on the Gnome panel, you can try scanning for wireless networks manually. 

```

iwist wlan0 scan

```

The question: does your wireless card see broadcasting wireless networks?

---

### Post by 29732 on 2010-09-18
hey for your #2 problem...
idk how to fix it, but you can manually shut it down with sudo halt
thats all i can do :/

---

### Post by thenetminder33 on 2010-09-18
Scan for networks

```
wlan0    no scan results
```

However, my win7 sees two or three networks on same wireless card

---

### Post by thenetminder33 on 2010-09-18
running of ubuntu live cd in "try mode"
I can get a wired connection,  downloaded all updates, not sure if that affects regular boot though.

Still no wireless, though i can open the Network Connections but no networks are listed

I am really beginning to lean towards reinstalling because it feels like something probably got messed up.

---

### Post by sandyd on 2010-09-18
> **thenetminder33 said:**
> running of ubuntu live cd in "try mode"
I can get a wired connection,  downloaded all updates, not sure if that affects regular boot though.

Still no wireless, though i can open the Network Connections but no networks are listed

I am really beginning to lean towards reinstalling because it feels like something probably got messed up.
I don't think something got messed up. 
I instead think were overlooking something very simple here....

maybe ->
```

sudo ifconfig wlan0 txpower on
sudo iwlist scan

```?

---

### Post by thenetminder33 on 2010-09-18
```
sudo ifconfig wlan0 txpower on
```
returns
```
txpower: Unknown host
```

still no scan results

the reason i think that something probably got messed up is not just because of my wireless,
Wired does not work either
Many menu apps under System and Applications do not work
ubuntu boots to terminal

---

### Post by thenetminder33 on 2010-09-18
Good News!

Reinstall with new Live CD fixed all of my problems, ubuntu running like a charm:)

---

### Post by 29732 on 2010-09-19
good good :D

---

