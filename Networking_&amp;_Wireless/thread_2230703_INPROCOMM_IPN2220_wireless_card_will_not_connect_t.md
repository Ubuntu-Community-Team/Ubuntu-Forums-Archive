---
title: "INPROCOMM IPN2220 wireless card will not connect to encrypted network, Lubuntu 14.10"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by leonard032 on 2014-06-20
Hello,
I am new to linux and am having problems connecting to my home wireless network. I have a Acer Aspire 1410 (only 512 mb of RAM, that is why I am moving away from Windows XP which was super slow. The network worked on it though) with an INPROCOMM IPN2220 wireless network card. I have searched for help on the net like crazy and have spent approximately 10 hours on this already with no luck (not kidding). The card has no linux drivers so I must use ndiswrapper. I have downloaded this and successfully installed a Windows XP driver. The card is now recognized and seems to be in working order. If i run the nm-applet I can see a list of the networks around but that is where my problem is; most (including mine) are grayed out and cannot be clicked. I have come to the conclusion that it has something to do with the WPA2 encryption as I was able to connect to an unsecured network from a different router. As well as that I have been trying in Puppy Linux and when trying to connect to the same encrypted network it gives back an error that either the password is incorrect (it is not) or the card has compatibility problems with the wpa_supplicant. I do not know if this has anything to do with it but i am running off of a live CD. I have also done sudo apt-get update but could not do sudo apt-get dist-upgrade for lack of room. Also the laptop just died on me so I will upload the results of the wireless script in a few minutes. (The wired connection works fine)
Thanks for any help you can give me cause I am at the end of my rope and am going to snap the Lubuntu CD over my knee in a little bit.

Here is the result of the wireless script, it is different from before the computer died. Specifically I had scan results before. I do not know what i did differently. Also the light that indicates wireless activity is not longer blinking, I have not turned it off.

If anyone could help me with this it would be greatly appreciated. I am also wondering if it would make any difference if I did an install.
Thanks!

---

### Post by chili555 on 2014-06-23
This is a somewhat older (ahem, just like Chili!) device and I'm not at all sure it actually is capable of WPA[COLOR="#FF0000"]2[/COLOR]. Check:```
sudo iwlist wlan0 auth
```Do you see:```
wlan0     Authentication capabilities :
		WPA
		[COLOR="#FF0000"]WPA2[/COLOR]
		CIPHER-TKIP
		CIPHER-CCMP
```You might also try changing the router to WPA only, if it's available, as an experiment.

EDIT: Please check here: [http://superuser.com/questions/188089/how-can-i-get-my-router-and-inprocomm-ipn2220-wireless-network-card-connected](http://superuser.com/questions/188089/how-can-i-get-my-router-and-inprocomm-ipn2220-wireless-network-card-connected)> Success! What I did first was to first take Sathya's advise to change my router's encryption mode to WPA2 Mixed Mode which would allow WPA2-PSK AES & WPA-PSK TKIP encryption methods. I needed this because the *InProComm Wireless Card only accepts WPA-PSK*.

---

### Post by leonard032 on 2014-06-23
There's the problem, WPA2 is not listed. I don't understand this though as I could connect to the WPA2 network on Windows XP. Is it the driver I'm using? I'm not actually using the one that is on the computer as I can't find the .inf file in XP.

---

### Post by chili555 on 2014-06-23
Generally, the encryption is a function of the hardware. Some, but not all, drivers offer the option to use either hardware or software (wpa_supplicant) to manage encryption. Here is an example from *ath9k*:```
parm:           nohwcrypt:Disable hardware encryption (int)
```ndiswrapper is not such a driver.

Even then, if the silicon was encoded, for example, in the days before WPA was conceived, we can't, as far as I've ever seen, trick the card to do WPA. I went through this with an old Intel 2100 that refused any encryption except WEP! I drove it to the dump!

Where did you get the inf file, if not your XP install?

Did you try the mixed mode WPA and WPA2 mode in the router?

---

### Post by leonard032 on 2014-06-23
But on XP the hardware could connect to the WPA2 network. So wouldn't that mean the hardware was capable?
The driver I got online. On the windows side the driver location it gives is a .sys file and I can't find a .inf file of the same or similar name in the /WINDOWS/inf folder.
I just tried to connect to an extra router lying around with a WPA encyption and it won't work. In nm-applet it is not grayed out but it does not show a locked symbol either. If I try clicking it it does nothing. If I try to pretend it is a hidden network it just asks me for the password about every minute but will not connect. The light for wireless activity is flashing but it isn't connected to anything.
Also I can't delete old network connections.

---

### Post by chili555 on 2014-06-24
> On the windows side the driver location it gives is a .sys file and I can't find a .inf file of the same or similar name in the /WINDOWS/inf folder.Did you search the entire install for 'neti2220? It may not be where you expect to find it. Where, on line, did you get the .inf and .sys files? I wonder if they are the latest version.> But on XP the hardware could connect to the WPA2 network. I suspect that, with the right driver, the hardware is capable. Now we need to find the *right *driver files.

---

### Post by rafiqcombrinck on 2014-06-24
The good news is, even with NDISwrapper your wifi card will be able to connect to WPA2 (just did it a few minutes ago), the bad news is, even after you get it working, it will be temperamental as hell. It will work fine for half an hour and then, without actually disconnecting, will just stop doing anything.  I know you are not going to want to hear my final solution, I would not have :P Get a cheap usb wifi dongle. I actually just scratched out an ancient one I had given all hope up on (don't even know why I still had it), but thought I would stick it in for the heck of it and see what happens ... 5 seconds later I was connected to my  AP.  As for your other question, I don't think you will get it to work via a liveCD session, you will have to install. I struggled at first to get NDIS to work, but then later on realised it was my Ubuntu installation that was a botch up (somehow ended up with something between a live session and an install, Unetbootin hard drive install experiment gone bad).  Good luck.

---

### Post by leonard032 on 2014-06-25
I just did a full system search for neti2220.inf and got six results. Two were form different drivers i had tried to download. The others I can't get to. Two are in A802/Win2k and A802/Winxp. I tried entering this in the address bar of My Computer but it just brought up Chrome and tried (unsuccessfully) to load it as a webpage. The same thing happened with the other two files in Wireless(A802)_Ambit_2.10.3.2014_XPx86/Win2k and/Winxp. Neither seem to be actual address as they don't begin with C:\ and the slashes are the wrong way.

The drivers I am using I got from [here]("http://forums.laptopvideo2go.com/topic/7172-inprocomm-latest-driver/"). One funny thing i noticed about them is that they are not made by INPROCOMM they are made by LANExpress or something. I only found one driver online that was actually made by INPROCOMM and it was 64 bit.

I also tried searching for the file with the name of the .sys (i2220ntx.sys) file the device manager says it is using but that does not result in any .inf files.

@rafiqcombrinck I was hoping I would not have to install until I was certain I could get the wireless working as I do not have a the CD to re-install windows if it doesn't work. Also if your system is 32 bit it would be great if you could post the drivers you are using. I don't think the computer is worth buying a dongle for but I might have to go that way if all else fails.

---

### Post by rafiqcombrinck on 2014-07-10
Hi Leonard

My system is 32-bit, but it is Ubuntu 12.04 LTS. This driver is from a windows xp update I ran a month back or so, but it shows it was made back in 2004, but windows was happy about it being more up to date than the driver on my recovery disk.

As mentioned before, I don't think ndiswrapper functions properly on a live session though.

Give it a try and let us know.

Peace,
R

---

### Post by leonard032 on 2014-07-10
Success! Yahoo! Card now connects to a WPA2 encrypted network. WPA2 now shows up in the results of ```
sudo iwlist wlan0 auth
```
For those who come to this later download the drivers rafiqcombrinck very kindly provided and use them with ndiswrapper. If you're system is 32-bit you should be good to go! Also I managed to get this to work on a live session if you want to verify it before making a full install.

---

### Post by rafiqcombrinck on 2014-07-10
Great stuff, enjoy ;)

---

