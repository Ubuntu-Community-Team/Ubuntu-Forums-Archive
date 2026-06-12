---
title: "Installing Wireless USB adapter"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by Boat on 2005-10-04
I have a Linksys Wireless USB adapter that I'd like to use with Ubuntu. I looked for a linux driver on the Linksys site but could not find one. I'm a real newbie to Linux so any help would be appreciated.

---

### Post by Dr. Nick on 2005-10-04
Need a few more specidics,look on the bottom of the card and post the model and version number. If its like mine its real small in the top corner under the Linksys logo. You need to know the chipset used to determine what drivers needed. I can bet its either a prism based and in that case google "wlan-ng" or its atmel (sp?) which needs other drivers, If its prism I may be of help as I am setting my linksys up as we speak. Linksys doesnt have official linux drivers for these cards unfortunately.

Post this info and it will be easier to help.

---

### Post by Boat on 2005-10-05
Model number WUSB54G
FCC ID: Q87 WUSB54G
Serial number MEQ104215741
IC: 3839A WUSB54G

I just contacted Linksys and they say  it is a version 1 as versions 2 and 4 would be listed as such.

---

### Post by Dr. Nick on 2005-10-06
well it seems that is a PrismGT chipset if it is indeed a version 1. Have you used the card in windows? If you want type lsusb in a terminal while the card is plugged in and look for it in the list to make sure its detected at all
You can try this page [here]("http://prism54.org/") for drivers but it looks like you would have to build them from source which can be a pain.
Your best bet and probably the easiest would be to use ndiswrapper which can be installed from synaptic. Then go to this [Wiki]("https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29") article and follow it from the Installing the Windows Drivers section making sure to subsitute the correct file names for the location of your windows drivers which you can copy from the cd or download off the internet. Or this [link]("http://www.ubuntuforums.org/showthread.php?t=25683") both are for different cards but should still give you a general idea of how its going to work. Just remember to subsitute the correct names for your situation.
I havent used ndiswrapper much but im sure others who see this have and may be able to help if you hit a wall ](*,) 
Try this and if you have any questions post back and I can try to answer or others may be able to help.
Good Luck

---

### Post by majkmil on 2005-10-10
Iha****ve a linksys usb adapter also (80.21.b) ver. I downloaded the driver from linksys but is is an EXE file not a inf. file. I follwed the WIKI post to compile ndiswrapper and everything is fine although I had a newer ver. Can I convert the exe to inf or do I need another driver?
Adapter is WUSB11 ver. 2.6                        Thanks

---

### Post by Dr. Nick on 2005-10-11
Do you have the Linksys Cd it came with, the inf is in it. The exe is the windows format as you probably guessed. I had this same problem today as I couldnt extract the exe file to get to the inf. If you have windows I think you can use it to extract the exe, see if maybe winzip will open it

---

### Post by jdgiotta on 2005-11-01
I have Linksys Wireless-B USB Adapter (model: WUSB11 ver: 2.8)
I just installed Breezy Badger 5.10 last night and I'm following [these instructions]("http://www.fuw.edu.pl/~pliszka/hints/prism2.html") to configure the device.

However, when I'm asked for the linux source directory it fails. So I thought I was pointing to the wrong directory.

Can someone provide me some tips?

---

### Post by Dr. Nick on 2005-11-01
It doenst look like your card has a prism chipset but instead an Atmel AT76C503A according to this page [http://www.linuxquestions.org/hcl/showproduct.php?product=1791](http://www.linuxquestions.org/hcl/showproduct.php?product=1791)
Linksys often switches up chipsets and doesnt rename models so its confusing, therefore I could be wrong, is it a ver "2 . 8 " (I assums thats what the smiley is messing up)?

try this link [http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11](http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11) someone says they got it but I dont have that revision so I cant try it, I have the wusb11 v3 which looks to be a different chipset than th 2 . 8 and have mine working.

If you want to try that and fix the source error make sure linux-source and linux-tree are installed in synaptic and are the correct platform (eg i386 etc.) and same version as your current running kernel and try again

---

### Post by az on 2005-11-01
[QUOTE=majkmil]Iha****ve a linksys usb adapter also (80.21.b) ver. I downloaded the driver from linksys but is is an EXE file not a inf. file. I follwed the WIKI post to compile ndiswrapper and everything is fine although I had a newer ver. Can I convert the exe to inf or do I need another driver?
Adapter is WUSB11 ver. 2.6                        Thanks[/QUOTE]


That EXE should open up like a zip file.  Use file-roller (just open it in nautilus and chose file-roller) or try the command line 

unzip file.exe

---

### Post by jdgiotta on 2005-11-01
Cool, that worked.
I got the adapter recognized, but now I need to connect to the network.

---

### Post by Dr. Nick on 2005-11-01
Since you have your card working the one thing I might reccomend is disabling any wireless security in your router, only if you are the owner of the network and understand all of the potential risk involved with having your router unsecure for 30 mins :p . 
Get your card working like that then re-enable your desired security. Its up to you wether you do this or not , but I had a easier time troubleshooting with WEP off, Ideally you wouldn't have to trouble shot though :KS 

Glad you got it working so far

---

### Post by jdgiotta on 2005-11-01
Hmm... interesting development.
I can now choose wlan0 as an network option, but I get 0% signal strength.

---

### Post by Dr. Nick on 2005-11-01
[QUOTE=jdgiotta]Hmm... interesting development.
I can now choose wlan0 as an network option, but I get 0% signal strength.[/QUOTE]


Any encryption? Also does it list your access point under the networking menu, also you can try to open a terminal and run ifconfig and see what adapters are up and their IP addreses, do you have a wired card also, if so try to disable it in the networking control panel before trying wireless, not sure if you can have wired and wireless on at the same time.

---

### Post by jdgiotta on 2005-11-01
WEP encryption, I do see my wireless network in the menu, and all other cards are deactived.

DHCP returns nothing, but static IPs are more promising.

---

### Post by jdgiotta on 2005-11-01
Whoo hoo!
I got it. This reply comes to you from Ubuntu :smile:

I had WEP type set to Plain Text, duh!

---

### Post by az on 2005-11-01
[QUOTE=jdgiotta]Whoo hoo!
I got it. This reply comes to you from Ubuntu :smile:

I had WEP type set to Plain Text, duh![/QUOTE]

That is not a dumb thing.  It is a useability problem.  Too many people make that mistake.

---

