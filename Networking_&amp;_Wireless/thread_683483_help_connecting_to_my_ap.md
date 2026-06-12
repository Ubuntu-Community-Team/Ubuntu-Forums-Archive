---
title: "help connecting to my ap"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by cakemaster on 2008-01-31
I have been trying to get my wireless working for a few days now.  This is the first thing I have tried to do in linux (probably not good to send a noob to do the work of someone who knows what theyre doing).  I got through using ndiswrapper for my zonet zew1602a through many guides and finally ended up with [http://ubuntuforums.org/showthread.php?t=403139&highlight=zonet+ZEW1602](http://ubuntuforums.org/showthread.php?t=403139&highlight=zonet+ZEW1602) getting the best results.  The drivers that were listed somewhere else were not working correctly (when I tried to give it the ESSID it would return that the device did not support ip) but with the drivers off the cd that came with it I can associate with the router but not connect to the network.  oddly, I cannot do this if I change the router settings to be unprotected, only if I leave set the way it was when I started this (with wpa).  I followed a wpa_supplicant tutorial to try to get that working and I don't know how to tell if that is correct or not, though when I enter the line sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd from the tutorial [http://ubuntuforums.org/showthread.php?t=571188&highlight=wpa_supplicant](http://ubuntuforums.org/showthread.php?t=571188&highlight=wpa_supplicant) it gives me responses that lead me to believe something is wrong there.  I have obviusly changed what needs to be changed to the right things.  I am running the server edition of gutsy gibbon (only command line).  when I try to connect to the network I get multiple dhcpdiscover tries (the way I was told it should be) but at the end it tells me that there were no dhcpoffers.  ideas?  if more info is needed I can get it.  If anyone is tempted to tell me I should just use ethernet for a server there are two things to that 1)it is not available as a permanent solution 2)wireless is not a problem because this server is only for my own use, or if I were to share it with someone I know (in which case it would only be used briefly)  thanks in advance.  I hope someone can help me, this has gotten overly frustrating.  Ive also been through other guides than the two I listed here, and I think (not sure) I have overwritten or erased all residue of past attempts, though possibly not.  if there is something I need to check to make sure it is off/on that may have been set by another method let me know.  thanks again.

---

### Post by Rome.konig on 2008-01-31
alright i may not be the best help for this but i do have some experience with wireless. im pretty sure that you are able to access your wireless settings and know how to play around with wpa or wep keys.  i have tried doing wpa and wep keys for Ubuntu to set up my wireless computers and they don't work. i also have tried to read forums and help guides like you and didn't get any where. 
I didn't understand what you were saying about "not being able to connect even its unprotected"
have your checked your IP network pool?  The way i was able to get my wireless working was to use the unprotected setting.  I disabled the SSID boardcast, but made sure i knew what my SSID wireless net work name. then i changed the wireless MAC filter to permit only the PC's listed in my wireless network.

i don't know what type of router or hub you are using, but check your MAC address for your PC and changed the permission settings to allow only that PC, then when you have more PC's that want to connect to that SSID, just manually type in the SSID, and add the MAC of the PC you want to add into the address pool. 

i hope this will work for you, i know wireless can be a pain when they don't work the way you want it to. t

---

### Post by cakemaster on 2008-01-31
what I meant by not beaing able to connect in unprotected mode was that I went in on the machine im using now (with windows) and changed the setting to be unprotected in every way.  Now when it is set as wpa and I tell my other comp that cant connect fully to connect to the ap with my ssid and then look at iwconfig output it will tell me I am associated with it and give me the info on noise, strength etc.  when I do the same without wep/wpa it tells me that everything is zero and, despite having *just* set it the ssid remains off/any and access point is unassociated.  if I could fix this and do a mac filter I would be fine with that.

---

### Post by cakemaster on 2008-01-31
sooo, i dont know what happened.  couldnt tell you.  whenever I tried to dhcp I would get no offers.  Now, using this windows maching i went to go and check to see if I was able to use a mac filter and see if it was worth trying to get that to work.  on a hunch i look at the associated devices and, lo and behold, listed is this machine and my server box...didnt touch it for about an hour there, and it wasnt connected then, as far as I know.  tried to sudo apt-get update to see if it was connected.  certainly looked like a download to me when a bunch of get:n popped up and it had % counting up many times.  solved, I guess?

---

### Post by Rome.konig on 2008-01-31
Nice, so i guess everything works fine then. So we can close this thread.

---

