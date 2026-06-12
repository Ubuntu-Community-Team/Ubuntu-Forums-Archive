---
title: "Realtek RTL8187 could not connect!"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by vandetta on 2007-09-27
I have a problem. I installed ubuntu in my machine and there's one problem. Wireless problem. The OS detect all the hardware perfectly and everything runs fine except for the wireless. The OS can detect wireless networks but could not connect to it. I attach together the screenshot and hopefully anyone can try to give me solution for this. Oh yes, the wireless was Realtek RTL8187. Thanks.

[IMG]http://i16.photobucket.com/albums/b34/lazrus/ubuntuerrorscreenshot.png[/IMG]

---

### Post by wieman01 on 2007-09-27
Have you enabled any kind of security on the router? If yes, what type (e.g. WEP, WPA)?

---

### Post by vandetta on 2007-09-27
Yes, there was security enabled. It was WPA-Pre Shared Key Mixed (TKIP+AES)
The router was Linksys WRT54G w/ DDWRT firmware.
Any idea mate?

---

### Post by wieman01 on 2007-09-27
Press "Connect to other wireless network" and enter your network name (SSID). Do you have a WPA and AES option further down? Or only WEP?

---

### Post by vandetta on 2007-09-27
> **wieman01 said:**
> Press "Connect to other wireless network" and enter your network name (SSID). Do you have a WPA and AES option further down? Or only WEP?

Let me give a screen shot, you might need this to help me :)

[IMG]http://i16.photobucket.com/albums/b34/lazrus/2.jpg[/IMG]

[IMG]http://i16.photobucket.com/albums/b34/lazrus/1.jpg[/IMG]

---

### Post by wieman01 on 2007-09-27
Excellent, no problem. WPA2 with TKIP + AES. 

Now try to do what I have described above using the Networking Applet (on your PC). Do you see a WPA option?

---

### Post by vandetta on 2007-09-27
I try "Connect to other wireless network" but could not find any WPA option. All listed was WEP options. Or maybe I need to change my router security to WEP instead of WPA?

[IMG]http://i16.photobucket.com/albums/b34/lazrus/Screenshot-1.png[/IMG]

---

### Post by wieman01 on 2007-09-27
> **vandetta said:**
> I try "Connect to other wireless network" but could not find any WPA option. All listed was WEP options. Or maybe I need to change my router security to WEP instead of WPA?

[IMG]http://i16.photobucket.com/albums/b34/lazrus/Screenshot-1.png[/IMG]
You can set the router to WEP if you want. That way you would be able to connect immediately I guess. But WPA is deeply flawed and insecure. If you need to use WPA, then you will have to replace the current Linus driver using a tool called "NDISwrapper" and the latest Windows driver for your card. If you can live with WEP, then you are ready to go.

---

### Post by vandetta on 2007-09-27
Well what is the different between WEP and WPA?

---

### Post by wieman01 on 2007-09-27
> **vandetta said:**
> Well what is the different between WEP and WPA?
Difference is that WEP is an old & outdated security standard which does not even deserve the name. It would take me about 30 minutes to break into your network. No more. WPA is secure, therefore I recommend it. But installing the appropriate driver that supports WPA will be a bit of hassle. WEP is a quick (and dirty) solution.

---

### Post by vandetta on 2007-09-27
Actually, the reason why I put security to my wireless network is to prevent my neighbor from getting free internet by just using my wireless network. If I share the connection the connetion will be slow. I don't care either use WEP or WPA as long as:
1. My network have security
2. My connection will not be slower

In this case, I think it is OK to use WEP, right? But since before this I don't have any problem with WPA in Mac and Windows environment, I guess in ubuntu should be workaround, right? Like you said before there's ndiswrapper. I've tried tu but still failed. Maybe I'm doing it in wrong way.

---

### Post by wieman01 on 2007-09-27
> **vandetta said:**
> Actually, the reason why I put security to my wireless network is to prevent my neighbor from getting free internet by just using my wireless network. If I share the connection the connetion will be slow. I don't care either use WEP or WPA as long as:
1. My network have security
2. My connection will not be slower

In this case, I think it is OK to use WEP, right? But since before this I don't have any problem with WPA in Mac and Windows environment, I guess in ubuntu should be workaround, right? Like you said before there's ndiswrapper. I've tried tu but still failed. Maybe I'm doing it in wrong way.
WEP will certainly ensure that your neighbors will get into your network. But that's no guarantee against serious crackers, but I guess that is a risk you can take. Your connection won't be affected in any way in that case.

As for "NDISwrapper", yes, it is tricky but not impossible. If you don't want to mess around with it, just use WEP. But be aware of the risks associated with it. You can try upgrading later on if you want to. "NDISwrapper" is always an option.

---

### Post by vandetta on 2007-09-27
Well, the reason I try linux is to learn, if I want something that just works, I guess I can just stick to my Mac, I think I'm going to try ndiswrapper again, and hopefully this time I success. Will update here later :)

---

### Post by wieman01 on 2007-09-27
Post here if you encounter problems. I'll try to help out as much as I can.

---

### Post by uputer on 2007-09-27
So, to use WPA, no matter the chipset/driver/adapter, you need to use ndiswrapper?

I have the same problem but with different hardware.   I cannot find settings to allow a WPA setup.  I did have knetwork manager allowing either wep or wpa but for some reason, when I select it now, it defaults to a manual configuration and only WEP is available.  

Is Ubuntu going to use a program that makes it easier to install a WPA setup?  

Sorry, I find it rather annoying.  The router (Linksys WRT54G) allows either WEP or WPA but I can only choose WEP at the moment and to even consider WPA, seems to require elaborate procedures (i.e. installing and using ndiswrapper)?).   I'd like to confirm what options there are.   Thanks to anyone who tries to answer these questions.

---

### Post by wieman01 on 2007-09-27
> **uputer said:**
> So, to use WPA, no matter the chipset/driver/adapter, you need to use ndiswrapper?

I have the same problem but with different hardware.   I cannot find settings to allow a WPA setup.  I did have knetwork manager allowing either wep or wpa but for some reason, when I select it now, it defaults to a manual configuration and only WEP is available.  

Is Ubuntu going to use a program that makes it easier to install a WPA setup?  

Sorry, I find it rather annoying.  The router (Linksys WRT54G) allows either WEP or WPA but I can only choose WEP at the moment and to even consider WPA, seems to require elaborate procedures (i.e. installing and using ndiswrapper)?).   I'd like to confirm what options there are.   Thanks to anyone who tries to answer these questions.
Many Linux drivers do support WPA, however, some don't. It really depends on what hardware you happen to have...

---

### Post by vandetta on 2007-09-27
This was my new PC. The board was Asus M2N DH, comes together with Asus WIFI. Last time I use Aztech  WL230USB dongle to connect to internet in kubuntu. Need to use kubuntu "Windows Wireless Driver" - I think that also ndiswrapper right? But in interfaced way :)

---

### Post by wieman01 on 2007-09-27
> **vandetta said:**
> This was my new PC. The board was Asus M2N DH, comes together with Asus WIFI. Last time I use Aztech  WL230USB dongle to connect to internet in kubuntu. Need to use kubuntu "Windows Wireless Driver" - I think that also ndiswrapper right? But in interfaced way :)
Exactly! :-) Let us know if you need a hand.

---

### Post by vandetta on 2007-10-01
I installed the wireless driver using "Windows Wireless Driver" but it cant detect my hardware and also no WPA when I try to connect manually, only WEP.. same as before..

---

### Post by wieman01 on 2007-10-02
What does this command yield:
> ndsiwrapper -l
And this one:
> sudo iwlist scan
From command line please.

---

### Post by vandetta on 2007-10-02
vandetta@vandetta-linux:~$ ndiswrapper -l
netrtuw_x64 : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
vandetta@vandetta-linux:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:FF:31:94
                    ESSID:"MMURocks"
                    Mode:Master
                    Frequency:2.412 GHz
                    Quality=12/64  Signal level=22/65  
                    Encryption key:off
                    Extra:tsf=0000000034546ec6

vandetta@vandetta-linux:~$ 


**That is what I got after type in what you asked to. Now I have to turn OFF my wifi security so that ubuntu can connect to it :(**

---

### Post by wieman01 on 2007-10-02
This line here looks suspicious:
> wmaster0 Interface doesn't support scanning : Operation not supported
Have you blacklisted the Linux driver? It appears you have not.

---

### Post by vandetta on 2007-10-02
The way to blacklist the driver is by adding it to */etc/modprobe.d/blacklist* right? And I do *gedit /etc/modprobe.d/blacklist* and I found this at the end of line:

[I]# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187[/I]

---

### Post by vandetta on 2007-10-02
Oh yes, this one might helps:

vandetta@vandetta-linux:~$ lsusb
Bus 002 Device 005: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 002 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 003: ID 1130:cc00 Tenx Technology, Inc. 
Bus 002 Device 002: ID 03eb:0902 Atmel Corp. 
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. **
Bus 001 Device 001: ID 0000:0000  
vandetta@vandetta-linux:~$

---

### Post by vandetta on 2007-10-02
**Update:** I add blacklist rtl8187 to the blacklist and after restart it freeze my ubuntu. I have to take out the wifi adapter to make it ok. After delete back the blacklist rtl8187 ubuntu goes normal :confused:

---

### Post by wieman01 on 2007-10-04
> **vandetta said:**
> **Update:** I add blacklist rtl8187 to the blacklist and after restart it freeze my ubuntu. I have to take out the wifi adapter to make it ok. After delete back the blacklist rtl8187 ubuntu goes normal :confused:
Here is what I suspect: Blacklisting is necessary in order for "ndiswrapper" to work. Otherwise your system will simply ignore "ndiswrapper" and continue to use the native driver ("RTL8187"). However, whan you blacklist your driver, "ndiswrapper" causes a system freeze. That could have 2 reasons:

1. The current "ndiswrapper" package is faulty. In that case you need to update to the latest one, but you need to compile it yourself (happened to me before as well).

2. The driver you are using has an issue. Try to get hold of the latest version and deploy it as explained in my tutorial (see signature). Don't use the graphical tool.

---

### Post by wieman01 on 2007-10-04
There are instructions posted here:

[http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html]("http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html")

---

### Post by panurge77 on 2007-12-08
Problem might be with networkmanager starting. It does not work here with ndiswrapper and rtl8187.
Other possible problem is ndiswrapper is not loading and network manager stays waiting for it? Did you add ndiswrapper to /etc/modules? And did you use ndiswrapper -m or added manually an alias?

Try turning off network manager and using ndiswrapper -m

More here: [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

---

