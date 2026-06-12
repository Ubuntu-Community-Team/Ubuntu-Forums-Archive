---
title: "linksys usb300n wireless"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by antgul338 on 2009-09-05
ok i know there must be a lot of talk of wireless connections but im having trouble finding what i need can someone help or direct me to wherer i need to go???

i have a linksys usb300n and it isnt recognized 

i know i need ndis wrapper or something but i cant sonnect cuz the router is upstairs in the landlords apt. so i cannot connect with a wire.

so i need an offline installation of these programs and instructions on doing so.

thanks in advance people!

---

### Post by kiridude on 2009-09-05
I would begin with an upgrade to 9.04 first.

There has been much improvement in drivers and that alone may solve your problem.

---

### Post by antgul338 on 2009-09-05
ok got that i installed from a pressed 9.04 cd and the only difference between that install and the previous is that theres a wireless connection icon up top but there are no connections

---

### Post by coldReactive on 2009-09-05
1. NEVER install drivers with Wine, it simply WILL NOT work (Wine doesn't have a real Driver layer, ReactOS does though.

2. You may be getting no connections because your Adapter really can't detect any, or that this applies to even connections listed: "Downside of ndiswrapper is no network feedback/info from the Network Manager notification area icon on signal strength, etc."

---

### Post by bkratz on 2009-09-05
> **antgul338 said:**
> ok i know there must be a lot of talk of wireless connections but im having trouble finding what i need can someone help or direct me to wherer i need to go???

i have a linksys usb300n and it isnt recognized 

i know i need ndis wrapper or something but i cant sonnect cuz the router is upstairs in the landlords apt. so i cannot connect with a wire.

so i need an offline installation of these programs and instructions on doing so.

thanks in advance people!


I use ndiswrapper with my DWA130 dongle and mine shows signal strength by simply holding the cursors over it or left clicking on it for more details. If you wish to install ndiswrapper you would want to actually install ndiskgtk which is the user interface and actually installs all the files you need.  This can be done from the original installation disk by adding (checking) the correct box on the software sources listing in the menus.  I am not on my system right now and I can't remember the correct menu.  I will check the posting later and see if you find what you need, if not I will find it on my system and give you the full definition.

---

### Post by antgul338 on 2009-09-05
[B]uh yeah i didnt read ^^that^^ well, 
i will try that when i reboot and return 
thank you[/B]

[I]no this is not the case there is no adapters connected because i know there is connections wwith vista ( the way im talklin to you now) there is mine the free boston one and three or four secured ones.

the problem is is that my adapter is not there

how can i install it offline? well i can get on wirelessly with windows on the same machine[/I]

---

### Post by antgul338 on 2009-09-05
ok i tried to get it thru synapitc from the cd.....nothing in a search...........what am i doing wrong  any help?

---

### Post by bkratz on 2009-09-05
> **antgul338 said:**
> ok i tried to get it thru synapitc from the cd.....nothing in a search...........what am i doing wrong  any help?


If you are referring to my earlier post it is system--administration--software sources and tick cd rom at the bottom.  Then search for ndisgtk.

---

### Post by antgul338 on 2009-09-05
yes thats what i had done and i got nothing but ill will do one more time.....actually now that i think of it i open sources twice and the same boxes i checked where unchecked the second time around also



**did it again and still no search results**

---

### Post by bkratz on 2009-09-05
> **antgul338 said:**
> yes thats what i had done and i got nothing but ill will do one more time.....actually now that i think of it i open sources twice and the same boxes i checked where unchecked the second time around also



**did it again and still no search results**


I knew I wasn't crazy!  ( Just ignore the Dapper comment)

**Installing Packages (Without Internet access) **

 Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories. If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it. Put the CD into the drive, click **System** > **Administration** > **Synaptic Package Manager** and search for *ndis*. If you don't know how to install applications, [read this guide]("http://help.ubuntu.com/starterguide/C/ch02.html"). <<Anchor(configure)>> 







This was copied from the following location ( you might want to review), you can also download it with a Windows system, but that is difficult, :


[http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29](http://wiki.ubuntu.org.cn/UbuntuHelp:WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29)

---

### Post by antgul338 on 2009-09-06
ok first off im using the newest cd of ubuntu not dapper........second this guide is good but the first link doesnt work..........so i still cannot get or install ndiswrapper imma try with my 9.04 cd to search for just ndis unlike i did before and return...............

**ok i got it to work searching for ndis now i will try to install drivers using this guide........gees what a pain having to reboot in between talking and trying lol**

---

### Post by antgul338 on 2009-09-06
> Identifying Wireless Adapter 
/!\ Important: Be careful when using the drivers from the CD included with the wireless card. They may work and you can try them, but you could experience kernel crashes and other serious problems if the driver on your CD has not been tested with ndiswrapper. You should download a tested Windows XP driver which is suitable for your card from the ndiswrapper list. 

[&#32534;&#36753;] PCI Wireless Adapter 
1.Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key. 
2.Look through the output of the lspci command for an entry for your wireless card. 
3.Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0. 
4.Now, type lspci -n into the Terminal and press return. 
5.Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400.
[&#32534;&#36753;] USB Wireless Adapter 
1.Open a Terminal (Applications | Accessories | Terminal), type lsusb and press the return/enter key. 
2.Look through the output of the lsusb command for an entry for your wireless adapter. 
3.Once you have identified your adapter, note down the contents of the chipset ID, this will be in the form 104c:8400.



im stuck here.....


in windows my linksys usb300n does not power on until the device driver is installed so i cannot see the location when i type _lsusb_ so i have no idea what to do at this point.

there has got to be someone who has delt with this

please help im seriously about to cry im so sick of windows and since hardy i havent been able to use ubuntu because i moved and dont have my own wired connection

waaaah!!!

---

### Post by bkratz on 2009-09-06
Those comments above are referring to your Ubuntu installation, not your windows. Now that you have installed ndisgtk you should have a menu entry under one of the main headings (not on my system again, think it is called something like wireless devices or setup or something like). Place the .inf and .sys files somewhere you will remember (home?). Now start the ndisgtk program (remember this is in Ubuntu not windows). If I remember right it will ask for the location of those two files and do most of the work for you. Ignore it if it says (hardware not found, it always does for some reason). Once you do all this, you should be able to right click on the network icon and setup your system.

---

### Post by antgul338 on 2009-09-06
it doesnt say anything about it. also the lights are not on like theres no power

---

### Post by Old_Grey_Wolf on 2009-09-06
On my computer the program shows up in System > Administration > Windows Wireless Drivers.

---

### Post by antgul338 on 2009-09-06
are you serious? forget windows
when i type the lsusb it shows all my stuff but doesnt decribe everything it describes my usb hard drive and printer thats it the others all say usb hub but theres  a device in each usb . all six

---

### Post by Old_Grey_Wolf on 2009-09-06
> **antgul338 said:**
> are you serious? forget windows


If you installed ndisgtk on your Ubuntu partition, it added a menu item in System > Administration called Windows Wireless Drivers. Then do the rest posted by bkratz above. I got the Linksys wusb300n working on 9.04 using ndisgtk.

---

### Post by antgul338 on 2009-09-07
i did all that and i installed 2 vista drivers one of which was invalid and one xp driver and both say hardware is not present.....this shouldnt be this easy....actually sometimes i gotta unplug and replug the adapter in windows to get it to work ill go try that

---

### Post by antgul338 on 2009-09-07
ok tried that and it says it sees the device with the xp and 1 vista driver but the activity light is blinking like crazy and the icon at the top of my desktop moves but when i try to open firefox it crashes and soon after the whole system freezes up

i dont think its actually making a connection

---

### Post by Old_Grey_Wolf on 2009-09-07
Have you rebooted since you installed the drivers?

---

### Post by antgul338 on 2009-09-07
yezzir! ive tried everything and im no computer moron maybe a small ubuntu meathead but it aint workin for me

---

### Post by Old_Grey_Wolf on 2009-09-07
On my Linksys CD there were two drivers for XP. Did you try both of them?

---

### Post by antgul338 on 2009-09-07
vista had two and xp had 1 but it wasnt my cd its dl for website....but thanks imms go see for the most up to date and get it. brb.............

[COLOR="Purple"]what is the name of the driver your using???[/COLOR]

---

### Post by Old_Grey_Wolf on 2009-09-07
> **antgul338 said:**
> 
[COLOR="Purple"]what is the name of the driver you[COLOR="Red"]'[/COLOR]r[COLOR="Red"]e[/COLOR] using???[/COLOR]

netmw245.inf

The program "ndisgtk" said the the hardware could not be detected when I went to check which driver was being used  :). However, it works because that is what I'm using.

---

### Post by Old_Grey_Wolf on 2009-09-07
antgul338,

I hope you get the wusb300n to work. 

I find it is a nice adapter for me. Some people using Microsoft Windows have to unplug it in order to get their computers to boot. At least you only have to unplug it every once in a while to get your connection working with Windows. I have been fortunate that it has worked well for me. It picks up twice as many access points than any other adapter I have. I found a wireless router a few streets from my own that was unprotected. I logged into the router that had the default password. The userid for the ISP he connected to was his email address. I sent him an email telling him of the problem. I let him know that someone could have done a lot of mischief with his network. I was able to learn quite a few things about him by searching the Internet with the information I got from his router. For example, his address, phone number, his age (70), and so forth. 

For those that may stumble upon this thread, this is the adapter we are talking about [http://www.pacificgeek.com/productimages/xl/LICWUSB300N-RM-PB-R-2.jpg](http://www.pacificgeek.com/productimages/xl/LICWUSB300N-RM-PB-R-2.jpg).

---

### Post by antgul338 on 2009-09-09
Ok I got it to work with the free boston net but its still crashing ubuntu when I try my own secured network.

---

### Post by bkratz on 2009-09-09
> **antgul338 said:**
> Ok I got it to work with the free boston net but its still crashing ubuntu when I try my own secured network.

Could you expand on what is crashing?  Is it simply not connecting to your network or totally locking up your system or what? If it is simply not connecting can you try temporarily unsecuring your network and try again.  If you then can connect we can attack the security aspects.

---

