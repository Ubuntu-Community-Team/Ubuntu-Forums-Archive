---
title: "NDIS wrapper"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by cowtippinlinux on 2008-05-31
i need step by step instructions on how to install a NDIS wrapper so i can get my wireless internet working

---

### Post by issih on 2008-05-31
Easiest way is to install the package ndisgtk, which is a gui front end to ndiswrapper.

The new program will be located at System->Administration->Windows Wireless Drivers

Open that and point it at the *.inf file from your windows drivers. N.B. you may have to extract this file from the windows installation file somehow, either by unzipping the .exe or by running the .exe under wine.

If you are lucky that will be all you need to do. If you are unlucky, you will have to blacklist some kernel modules, so that the none working default drivers aren't loaded erroneously, but to know if that is required we need to know more about your setup....what exactly is your wireless card, more importantly what chipset does it use...without that info no one can really help you..

---

### Post by cowtippinlinux on 2008-06-01
ok ... here goes ... i dont know what you are talking about a kernal  
 
heres my setup .

120 GB hd -Ubuntu (gutsy gibbon)
80GB hd - windows XP 
512 ddr ram 
AMD sempron processor (3000+)

wireless card - netgear WG111 v2 but i dont know the chipset ... i think its atheros

---

### Post by issih on 2008-06-01
Search is your friend :)

[http://ubuntuforums.org/showthread.php?t=590942](http://ubuntuforums.org/showthread.php?t=590942)

Follow the steps of your forerunners, that guide is for gutsy, which I see you are running

Good luck with it

---

### Post by cowtippinlinux on 2008-06-01
im computer illiterate .....i need serious help ... i dont know about half the stuff they are talking about

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> im computer illiterate .....i need serious help ... i dont know about half the stuff they are talking about

One thing.... Make sure your wired network card is unplugged before you scan for the wireless.

---

### Post by issih on 2008-06-01
So what level do you understand? do you know how to install a package? do you know how to enter commands in terminal...

how illiterate is illiterate?

Oh, and do you have internet connection to the computer you are trying to fix at all? e.g. by a wired conection.

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> wireless card - netgear WG111 v2 but i dont know the chipset ... i think its atheros


These are a little harder to config, but they work.

---

### Post by cowtippinlinux on 2008-06-01
ok ... i think i was wrong about the chipset to my wireless adapter ... its a realtek chipset

---

### Post by cowtippinlinux on 2008-06-01
ok .... and i dont know nothing about linux .... but im learning i want to get my wireless working ...but im a complete idiot at this stuff ...so ..

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> ok ... i think i was wrong about the chipset to my wireless adapter ... its a realtek chipset

And how do you know that?

Type the following and tell me what you see.

```
iwconfig
```

---

### Post by cowtippinlinux on 2008-06-01
rt8187

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> rt8187

Is that all  the xterm states, or is there more?

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> rt8187

Link for drivers for Realtek ==>[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false")

---

### Post by Unix_Slayer on 2008-06-01
If it was the Netgear, this link would have been perfect for you. ==>[http://ubuntuforums.org/showthread.php?t=202254]("http://ubuntuforums.org/showthread.php?t=202254")

---

### Post by cowtippinlinux on 2008-06-01
ok ... i dont have a wired internet connection ... or my install disk for netgear . i had to download the drivers from the netgear site ...im haveing to go from operating system to operating system cause my laptop crashed .

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> ok ... i dont have a wired internet connection ... or my install disk for netgear . i had to download the drivers from the netgear site ...im haveing to go from operating system to operating system cause my laptop crashed .

Follow Oputres guide in the link I gave you below.

---

### Post by cowtippinlinux on 2008-06-01
what link ?

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> what link ?

This one. ==>[http://ubuntuforums.org/showthread.php?t=202254]("http://ubuntuforums.org/showthread.php?t=202254")

---

### Post by cowtippinlinux on 2008-06-01
i guess that you missed the part where i dont have a wired internet connection or my netgear driver disk  that i can use

---

### Post by issih on 2008-06-01
Ok, this is still going to be doable, just trickier.

If you have the driver downloaded from the netgear site. In windows grab the exe file, rename it to .zip and extract it.

If that works (it might not sadly) look at the files you get and see if you can find one called <something.inf>, if you can then we have achieved step 1. Copy all these extracted files onto a cd or a usb key so you can easily get at them from ubuntu later.

Now go to the ubuntu install, stick the ubuntu cd you used to do the installation in the drive then go to System->Administration->Software Sources and tick the check box to look for software on the cd rom.

Now open a terminal window and type:

```
sudo apt-get install ndisgtk
```
enter your login password when prompted and wait for the install to finish.

Now type:
```
sudo gedit /etc/modprobe.d/blacklist
```

and in the text editor that opens copy and paste the following lines onto the end of the file:

```
#Netgear conflicting drivers
blacklist islsm
blacklist islsm_pci
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
```

save the file and exit.

Remove the install cd and reboot the pc.

log back in and now insert the media with the files you extracted earlier. Open System->Administration->Windows Wireless Drivers
and then hit install and locate the *.inf file from earlier.

You can drag and drop it over if that is easier.

If all has gone well, a driver will appear in the list, which says hardware present next to it. If that happens then hardware wise you should be set.

Just activate the wireless from the network applet in the top right.

Can't really make it any simpler than that, sorry, if you don't understand any of that let me know 

good luck :)

---

### Post by cowtippinlinux on 2008-06-01
ok ... i found the INF file ....does this sound right ?
Windows .INF file for NDIS driver...

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> ok ... i found the INF file ....does this sound right ?
Windows .INF file for NDIS driver...

Your looking for the .inf for the Netgear driver. It's on the CD, or on Netgears website.

---

### Post by issih on 2008-06-01
Where did you find the file, that is the question, did you find it in the unzipped exe file? If so then its probably right, if you found it by just doing search for a *.inf in windows its probably not.

I'd have expected something more related to the wireless chipset or the manufacturer than just "windows.inf", but in the end theres no way I can tell you if that is the right file. If you found it in a sensible manner, in a place related to the wireless driver, then it probably is, if not, then its probably something else.

in the end, give it a whirl, just don't delete it from windows, copy it and nothing can break.

You will need the *.inf from within the wireless driver setup file, not just any random one.

---

### Post by cowtippinlinux on 2008-06-01
> **issih said:**
> Where did you find the file, that is the question, did you find it in the unzipped exe file? If so then its probably right, if you found it by just doing search for a *.inf in windows its probably not.

I'd have expected something more related to the wireless chipset or the manufacturer than just "windows.inf", but in the end theres no way I can tell you if that is the right file. If you found it in a sensible manner, in a place related to the wireless driver, then it probably is, if not, then its probably something else.

in the end, give it a whirl, just don't delete it from windows, copy it and nothing can break.

You will need the *.inf from within the wireless driver setup file, not just any random one.

i went through my windows program files and i found the netgear program and i extracted all the files and that was the only <inf.> file that was there

---

### Post by issih on 2008-06-01
I doubt that is the right file, you need to go and download the driver setup file for Windows from netgear. Then take that setup file and treat it like a zip file (e.g. rename it to setup.zip and extract it). Then find the *.inf file from within there. The inf file you want will be available somewhere in the windows install, but its probably buried deep within the windows folder, more than likely in a hidden folder.

Go download the driver file and get it the way we have suggested..it will save you time and effort, honestly.

If you want try the file you've found first, if it works then excellent, all is well. As I said as long as you don't delete it from windows you can't do any harm. just don't be surprised if it doesn't work.

---

### Post by Unix_Slayer on 2008-06-01
> **issih said:**
> I doubt that is the right file, you need to go and download the driver setup file for Windows from netgear. Then take that setup file and treat it like a zip file (e.g. rename it to setup.zip and extract it). Then find the *.inf file from within there. The inf file you want will be available somewhere in the windows install, but its probably buried deep within the windows folder, more than likely in a hidden folder.


C:\Windows\System32\Inf or C:\Windows\System32\Drivers It would be easier just to download it from the Netgear site.

---

### Post by cowtippinlinux on 2008-06-01
> **Unix_Slayer said:**
> C:\Windows\System32\Inf or C:\Windows\System32\Drivers It would be easier just to download it from the Netgear site.

ok ... i redownloaded the netgear driver and saved it to a usb key .
i took out the INF file and now im about to switch over to ubuntu


will this same proceedure work for PClinuxOS

---

### Post by Unix_Slayer on 2008-06-01
> **cowtippinlinux said:**
> ok ... i redownloaded the netgear driver and saved it to a usb key .
i took out the INF file and now im about to switch over to ubuntu


will this same proceedure work for PClinuxOS

Depends..... Ubuntu is more friendly in my opinion, but that would be your choice.

---

### Post by cowtippinlinux on 2008-06-02
Ok .... i tried doing what Issih told me to do and when i went to type in the code < sudo apt-get install ndisgtk> it said something about tree not found ... anyways it wouldnt work ...so now im back on square one

---

### Post by Unix_Slayer on 2008-06-02
> **cowtippinlinux said:**
> Ok .... i tried doing what Issih told me to do and when i went to type in the code < sudo apt-get install ndisgtk> it said something about tree not found ... anyways it wouldnt work ...so now im back on square one

You need to be connected wired first before you can apt-get. Tree not found means your not connected.

---

### Post by cowtippinlinux on 2008-06-02
oh ... thanks ... let me try again ....

---

### Post by Unix_Slayer on 2008-06-02
> **cowtippinlinux said:**
> oh ... thanks ... let me try again ....


After you apt-get and install. Reboot, but remember to unplug your wired card. Otherwise you'll be banging your head on the wall.

---

