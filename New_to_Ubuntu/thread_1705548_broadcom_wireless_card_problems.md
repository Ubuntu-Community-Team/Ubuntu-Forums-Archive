---
title: "broadcom wireless card problems"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by sangsterthegangster on 2011-03-12
Hello, i just installed ubuntu x64 and my wireless card wasnt working. I found a solution using the *Windows Network Drivers* utility (or something like that) and my Windows 7 drivers and it worked amazingly..... ONCE. I shutdown my computer and when i booted it up again the drivers didnt work and wireless card doesnt show up at all in the Network Manager or ifconfig in the terminal. Im am running a HP Pavillion laptop with a Broadcom BCM4312 (rev 0) wireless card. Ive tried everything i could think of like reinstalling the drivers, ect.., but I'm still a noob in ubuntu. Can anyone Help me? thank you.

---

### Post by false truths on 2011-03-12
Did you open System->Additional Drivers and look for the Broadcom STA driver there? It's more stable on an Ubuntu system then a Windows driver will be.

I have a BCM4311 card and I had the same issue. Windows drivers wouldn't work, the B43 driver wouldn't cooperate for more then one run. The STA driver is a proprietary driver, but it works awesomely.

---

### Post by sangsterthegangster on 2011-03-12
Yes I just tried it, it I still have the same problem :(

---

### Post by wep940 on 2011-03-12
Chances are that when you used ndiswrapper that some of the modules ended up being blacklisted.
 
The best way of correcting this is to back out everything you did with ndiswrapper. Back out any edits you may have done to files. If you used ndisgtk, use it to remove your device. If you used just command line ndiswrapper, you must use it to remove the device you installed. Be sure any changes to the modules file have been reversed so that it isn't trying to load ndiswrapper.  Finally reboot before going on.
 

The recommended way of getting Broadcom and other cards working has changed, and as a result most of the old posts out there for Broadcom wireless no longer apply. The recommended way now is:
[LIST]
[*]if possible, temporarily hard-wire your PC to the router, then do the following:
[/LIST]sudo apt-get update
[LIST]
[*]in all cases, check under system/administration/additional drivers (some version may say Restricted Drivers) and see if a driver shows - if so, be sure it is enabled.
[*]if you had a hard-wire connection you can disconnect it now
[*]check in network manager and see if any networks show
[/LIST]***_ONLY_*** if you cannot try a temporary hard-wire -OR- nothing comes up in the additional/drivers should you consider ndiswrapper. It really is a last resort type of tool now, but there are still plenty of adapters for which it is needed. A couple of quick notes on ndiswrapper:
[LIST]
[*]after installing ndiswrapper, install ndisgtk. With no internet connection available, these can be loaded by booting Ubuntu, then inserting the LiveCD, using "Places" to navigate to the /pool/main/n folder on the LiveCD, then going to the ndiswrapper folder and installing each of the files there (double-click them), then the ndisgtk folder and installing the file there.
[*]ndisgtk can be accessed via system/administration/windows wireless drivers. Always use this instead of command line ndiswrapper. Ndisgtk is a GUI'd interface to ndiswrapper and takes care of all kinds of typing you would otherwise have to do.
[*]Unless things have changed, you can *ONLY* use Windows XP drivers with ndiswrapper.
[*]Your Windows XP drivers must match the architecture of your Ubuntu - 32-bit for 32-bit Ubuntu, 64-bit for 64-bit Ubuntu.
[/LIST]

---

### Post by sangsterthegangster on 2011-03-13
Ok I did everything u said, but it still doesnt work. I went into the additional drivers and it says that the Broadcom STA wireless driver is activated but not currently in use. How do I use it? Or is there another problem?

---

### Post by grahammechanical on 2011-03-13
May I mention a few things easy to forget, little things that can trip us up. When trying to solve a problem like this one we need to discount these things.

1) As it is a laptop, make sure that the wireless adapter is switched on at the keyboard.

2) If Windows allows you to switch off the wireless adapter then do not shutdown Windows with the wireless adapter switched off. It will need to be switched back on in Windows to work in Ubuntu.

3) Right click the network manager icon and make sure that there is a   tick mark against the two lines Enable Networking and Enable Wireless.

4) As you have already made a connection to the modem/router using wireless there should be a connection setting form in Network manager. Right click the icon and select Edit connections. Select the Wireless tab. Select your connection then select Edit and make sure that the two boxes Connect Automatically and Available to all users are checked (ticked).

5) Go to system>Preferences>Startup Applications and make sure that Network Manager is ticked as one of the startup applications.

Regards.

---

### Post by sangsterthegangster on 2011-03-13
Ok I got it to work useing the STA driver! I fixed the last problem using the solution in this link: [http://www.thetwaros.com/580](http://www.thetwaros.com/580) 

Thank you everyone who posted :)

---

