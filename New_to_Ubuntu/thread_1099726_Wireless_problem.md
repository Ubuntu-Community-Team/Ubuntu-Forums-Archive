---
title: "Wireless problem"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by crisson on 2009-03-18
Hi everyone. Name here is Jim and I am brand spankin' new to Linux and Ubuntu having just downloaded it last night. I am running it through windows for right now...committment issues. Anyway, I don't have any wireless access to my router...it doesn't even see my router or any other routers in the neighborhood. When I click on the Network Manager, I see "Wired Network" (grayed out) and below that "Auto eth0" (also grayed out). Then, below that is "VPN Connections" which allows me to open "Configure VPN". That gives me a dialog box and when I click on the "Wired" tab I see "Auto eth0" and the "Wireless" tab shows nothing.

As you can tell from my question, I am not the brightest bulb in the lamp and I am old to boot so, please try to keep it simple:)

Thanks...Jim

p.s. I did do a search of the forum first but didn't find         
     anything that helped me at my level.

---

### Post by Xero Xenith on 2009-03-18
Hey Jim, just to clarify - would running it "through Windows" mean you used the Wubi installer ([it looks like this]("http://www.harobed.org/images/wubi.png"))?

Also, do you know which version of Ubuntu you're running? You can usually find out by going to System (at the top), then About Ubuntu. The version will be under the big Ubuntu logo, in the context "Thank you for your interest in Ubuntu x.xx" where x.xx is the version number.

---

### Post by crisson on 2009-03-18
Hi Xero Xenith and thanks for getting back with me. Sorry for leaving out the info...yes, I am running version 8.10 through Wubi.
I am running an HP laptop with an Atheros AR5007 Wifi adapter.

Thanks

Jim

---

### Post by kaixi on 2009-03-18
First go to System -> Administration -> Hardwire drivers and see if there're restricted wireless drivers and enable them. After that, restart your computer and try clicking the network manager again to see if it works.

If there're no drivers to enable, then I suggest you grab your windows wireless drivers.
In order to find them follow these instructions:

> Under Windows, go to the Device Manager and find your wireless card under "Network adapters". Right-click on this and go to Properties->Driver->'Driver Details...'. Here you should find the path to a *.sys file, usually located in your C:\windows\system32\drivers\ directory. 

Now you will use the Windows "Search" functionality to find the corresponding *.inf file, which is nothing more than a simple text file (try opening one!) with a list of all the required driver's files. So a sample search query in Windows would be: 
Windows Search Query All of part of the file name:	*.inf 
A word or phrase in the file:	<the *.sys path found above> 
Look in:	Local Hard Drives (C:) 


This search may take a while! When you've found it, look inside the *.inf file with a text editor and see if you need to find any more files. If you're lucky, everything should be in a single directory (for example C:\Program Files\Atheros\Drivers\). Copy all these files to a single location (e.g. in /home/myuser sub-tree) or to an external USB drive which is accessible to your Linux system. 


**From the Driver Installation Software**

There are several places where you can try to find your drivers, listed here in order of preference: 
the installation CD that came with your hardware 
your PC or card manufacturer's support web site 
by searching for your *.sys file with Google 

If you're lucky, you will find the proper *.inf and associated files very easily. Sometimes, you will need to uncompress a *.cab file which contains your drivers. Tip: you can browse cab files with websites such as driveragent.com. You can try unpacking these *.cab files with any of the following: 
cabextract 
unshield 
i5comp 
i6comp 

Again, once you find all your files, copy them to a single location which is accessible to your Linux partition. 


[B]
Dealing with Multiple *.inf Files[/B]

If there's two or more .inf files don't panic, each one is for a different version of windows. My driver's disc has two: 
bcmwl5a.inf
and
bcmwl5.inf

The first is for win98 the second is for Win2K, Me, and XP. In my case, the win 98 driver works and the xp didn't.

The next step is to install **Ndiswrapper** (from Applications -> Add/remove). After you've done that, head for System -> Administration. You should be able to see a new entry called Windows Wireless Drivers (or Tools, i can't remember). Click on it to fire up the tool. Now choose Install Driver and select the .inf file we found above.

Once the driver is installed, restart and see if your wifi works. I hope this helps you :)

Kai

---

### Post by rendon on 2009-03-18
random notes:

1 laptops often have a button to turn on/off the wifi, make sure it's on

2 see if you can connect to the router through the web browser, I'm assuming you've done this before, it should be [http://192.168.1.1](http://192.168.1.1) or [http://192.168.1.11](http://192.168.1.11) or something like that.

3 I don't know about Wubi, but usually if you don't have a connection you should see a black box with a little red x in it on the topright near the clock.   right click that and make sure you have "networking enable" and "wireless enable".  if wireless is enabled then left click and see if any networks are available

4 still not working? with linux running try connecting directly to the router with a wire, then go ahead and reset all of the settings for the router as if you just bought it, making sure that dhcp is enabled.

5 check to see what hardware you have for your wireless card, you can usually google your computer manufacturer and model number.  then google to see if your particular card has driver issues with ubuntu.

good luck

---

### Post by crisson on 2009-03-18
Thanks to all for trying...still no luck however, Kaixi, the hardware drivers dialog box shows the Atheros driver as activated and in use but no connection.  
 
Rendon, I can connect directly to the cable modem (I am on the hardwire right now) but I don't know how to reset all the settings since it is my son's router and he set it up.

I did find out by google that there is a lot of trouble between these Atheros AR5007 cards and Intrepid. I wouldn't mind running 8.04 if I could find a download that would run through Wubi.

I guess I will just keep pluggin' away at it. Thanks again...Jim

---

### Post by kaixi on 2009-03-18
@crisson: Any luck with the 2nd solution (using Ndiswrapper)? Just remember to deactivate the drivers in 'Hardware Drivers' before proceeding.

---

