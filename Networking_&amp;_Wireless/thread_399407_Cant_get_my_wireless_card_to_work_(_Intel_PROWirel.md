---
title: "Cant get my wireless card to work ( Intel PRO/Wireless 2200BG 802.11 b/g WLAN)"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by phiber102 on 2007-04-02
Hi just compiled a new kernel on my hp 510 pavilion notebook, after a guide ([http://hp500.xf.cz/us/Main.html](http://hp500.xf.cz/us/Main.html)) to get my touchpad and pentium M series support activated. 
But after i completed the kernel update i lost my wireless connection and ubuntu cant seem to find my Intel PRO/Wireless 2200BG 802.11 b/g WLAN, i have located it in my device manager so it seems to be installed on system, but how do i get it to work again??

appreciate all help i can get

---

### Post by Kobalt on 2007-04-02
You should only need to install Network-Manager to get your card working actually. Try to install it from Synaptic, then restart your computer and check you notification area to access Network-Manager...

---

### Post by phiber102 on 2007-04-02
i have installed network manager now from synaptics 
but what exactly do u mean by "check you notification area to access Network-Manager..." im a real newbie at this :)

---

### Post by Kobalt on 2007-04-02
After a restart, you should have a wifi signal icon in your notification area (if not start network-manager by hitting Alt+F2 and enter nm-applet, you can also add this to System > Pref. > Session : programs at boot so that it starts automatically). Then you just have to click on that signal icon and a list of available networks will pop up, pick yours and enter your wireless key, and you're done :)

---

### Post by phiber102 on 2007-04-02
ok i found it now :D sadly it says "no network connection" :(
and i dont have the "wireless network" option in network-admin.
isnt there any way that i can install the device manual, like ading a eth1 or so??
thanks for the help btw :D

---

### Post by Kobalt on 2007-04-02
Well then your card isn't recognized and installed... It's sad since it should be working out of the box with Edgy's kernels and Network-Manager. Which means the problem could come from the kernel you built...

---

### Post by phiber102 on 2007-04-02
ahh ok so i just have to live with a broken touch pad and reinstall i guess :D
well thanks for help

---

### Post by Kobalt on 2007-04-02
If you have an ethernet connection available, you can reinstall a "clean" kernel from Synaptic...

---

### Post by phiber102 on 2007-04-02
yes ofc i have cable connection :D how do i do that then ?? :D

---

### Post by Kobalt on 2007-04-02
You need to search for the following packages : linux-image, linux-headers and eventually linux-restricted-modules. Select the latest available and the ones corresponding to your architecture (x86, AMD64, etc.) then install it all. It will be added to your Grub kernel list : reboot and when Grub prompts you to press Esc to select option press Esc and chose the kernel you want to boot on... 

This works the other way around as well, you can remove kernels this way.
Isn't Aptitude wonderful :) ?

---

### Post by phiber102 on 2007-04-02
yes i love ubuntu, used fedora b4, i have the new kernel now and as i suspected my touch pad isnt working anymore :D
well thats life i supose. thx for all the help

---

### Post by Kobalt on 2007-04-02
Which touchpad are you using ?

---

### Post by phiber102 on 2007-04-02
The one on my hp 510 pavilion notebook :D

---

### Post by Kobalt on 2007-04-03
I meant : is it a synaptics touchpad, etc. You can find out with ```
lspci
```

---

### Post by mrund on 2007-04-03
Returning to the original question about wifi, you don't have to have a broken kernel for wifi to work poorly. I have the exact same problems. Same wifi card, same software, same situation where wsconfig is aware of the card and the surrounding access points, but network-manager sees nothing. :confused:

---

### Post by josephus on 2007-04-03
have you checked if the driver is being loaded up? use lsmod | grep ipw2200 to see if it's there.  i'm not sure what the correct driver is for your card, but someone else can chime in if it isn't.  if it's not listed then try loading it up using 'sudo modprobe ipw2200'

---

### Post by dca on 2007-04-03
Remove network-manager and install WiFi Radar is the only resolution I've found.  You boot the laptop and nm-applet says 'no network devices found' but when you go to 'system -> admin -> networking' and click on the IPW2200 it shows the avail access points in the drop-down...

---

### Post by phiber102 on 2007-04-03
Hello again

The thing thats weird is when i boot on other kernel (esc in grub) the card works perfectly, and wifiradar couldnt find network in the newly compiled kernel either :( 
But touchpad works fine, in the new complied kernel touchpad runs with synaptics.

---

### Post by phiber102 on 2007-04-03
and the driver is loaded i get the same values with the "lsmod | grep ipw2200" on the kernel where the wifi is working and the kernel where the touch pad is working but not wifi

---

### Post by mrund on 2007-04-03
With "lsmod | grep ipw2200" I got the following, which looks good to me.

ipw2200               115652  0 
ieee80211              35272  1 ipw2200

Wifi Radar sounds nice, but it's not available on Synaptic.

---

### Post by dca on 2007-04-03
I thought WiFi Radar was, you may have to add add'l repo for it...  Somebody might know off the top pf their head which one...

---

### Post by phiber102 on 2007-04-04
yepp also thought wifi-radar where synaptics, especially since i downloaded it with synaptics pakage handeler:)

---

### Post by dachin on 2007-04-04
There seem to be a few people here having trouble with this card.  I'm have the same issue as a few of you.  Ubuntu sees my wireless card fine, the driver is loaded, I can associate with my router (iwconfig), I can scan the wireless networks (iwlist), but for some reason NetworkManager sees no wireless networks and the built in network configuration only seems to allow for a 'network key', there is no way to specify if it is WEP or WPA, or other.

End result....my wireless connection never gets and IP address and manually configuring one does not work either.

Anyone get this working yet?  What is WiFi Radar?

---

### Post by josephus on 2007-04-04
dachin: once you've associated with the access point have you tried 
```
sudo dhclient
```
to request for a ip address?

---

### Post by digitalghost1 on 2007-04-08
> **Kobalt said:**
> You should only need to install Network-Manager to get your card working actually. Try to install it from Synaptic, then restart your computer and check you notification area to access Network-Manager...

OMG - I have an Intel PRO/Wireless 3945ABG, I always resigned to having the ndis wrapper (:roll:  or whatever) installed and some terminal code ](*,) to get the wireless going. But with the Network manager is all I had to install and after the reboot I was able to get on my WEP secured wireless network. Fantastic!:) :) =D>

---

### Post by GeneW on 2007-04-20
So what is the solution here?  I have the same card Intel PRO/Wireless 2200BG and the nm-applet refuses to see it.  I have functional wireless networking through the Network Settings but the nm-applet can't see the interface at all.  I need to be able to configure WPA and as far as I know, the only easy way to do that is through the nm-applet.  So how do I get it to see my card?  Am I using the wrong driver?  I looked at the "restricted drivers manager" but the card isn't listed there.

---

### Post by GeneW on 2007-04-21
Someone in[ this thread]("http://ubuntuforums.org/showthread.php?t=399101") gave me the solution, comment out all the entries in the file /etc/network/interfaces except the "lo" ones.  After a reboot, nm-applet could see my card and I could configure it.  Happy day.

---

### Post by xflbret on 2007-05-07
> **Kobalt said:**
> After a restart, you should have a wifi signal icon in your notification area (if not start network-manager by hitting Alt+F2 and enter nm-applet, you can also add this to System > Pref. > Session : programs at boot so that it starts automatically). Then you just have to click on that signal icon and a list of available networks will pop up, pick yours and enter your wireless key, and you're done :)

this is exacly what i'm trying to make happen in 6.10. i cant seem to find out how to make it happen, but i know for sure its possible because this feature is part of the ubuntu ultimate edition, which is based on 6.10. i posted for help in the beginners forum but was pretty much ignored. maybe i can do better here.

---

