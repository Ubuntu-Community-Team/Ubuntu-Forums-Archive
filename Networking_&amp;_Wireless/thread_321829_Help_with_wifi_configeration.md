---
title: "Help with wifi configeration"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by computerwiz3491 on 2006-12-19
I have a Intel Prowireless 2200BG in a Compaq Presario v2000. I am able to connect to non-secured wireless networks as long as I already know they exist. I have two questions:
1)How do I connect to a WPA secured wireless network. (Step-By-Step)
2)How do I scan for avalible networks. (I can use wifi-radar, but that doesn't actually allow me to connect to any networks, just view them (unless I'm doing something wrong there too)

THANx

---

### Post by floke on 2006-12-19
You'll need to know the SSID of the network you're trying to connect to, and of course the encryption.
Go to (Gnome instructions) 'System', 'Administration', then 'Networking'. Make sure the wireless connection is enabled. Click on 'Properties'. Then you'll need to enter the SSID name, follied underneath by the encryption (depending on whether Ascii or Hex will apply - select the appropriate one - if not sure then try one and then the other). Enter the code underneath. Either set the 'Configuration; to Automatic (DHCP) or Static IP Address (if the latter then you'll have to enter the details below this too) - If you're unsure then select Automatic (DHCP) first and leave all the other entries below this blank.

You shnould then be able to use the encrypted wireless network.

For troubleshooting: (a) change the Ascii/Hex around; (b) chnage Automatic config. to Static IP, and enter the details - the first time I connected wireless on Ubuntu I thought I'd have to enter all the nonsense numbers like I did in Windows - it never occured to me that Ubuntu could sort all that out automatically - so the first time I would just set at Automatic and leave entries below blank.

I know this works for WEP - not sure about how different it would be for WPA - but try it and see!

Good luck,

---

### Post by computerwiz3491 on 2006-12-19
I tried the above, and it didn't work. Still no wireless.

---

### Post by floke on 2006-12-19
What's your iwconfig reading?

---

### Post by computerwiz3491 on 2006-12-19
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by floke on 2006-12-19
Looks like its picking it up (good news!)
I think you should try to turn the encryption off and see if you can connect to it.
So - go to the router homepage (from where you set up encryption) and disable it altogether.
Then follow the above instructions - ie Make sure wireless is enabled, set the SSID to 'linksys', leave Ascii/Hex and code lines empty. Select Automatic (DHCP) and leave the rest blank.
Hopefully that will work.

You'll then need to go back and set up the encryption again from the homepage.
I don't know how to do WAP in Ubuntu, but I have WEP and it works fine (you can always add MAC filtering from the homepage for extra security if that concerns you - or you can run with WEP until you figure the rest out).

So set up WEP from homepage - enter the Ascii/Hex + code in wireless and away you go (of course this assumes that it worked after disabling the security in the first place!)

As for wireless scanning and connecting - I don;t know about this in Gnome  - but there's one in KDE KWifiManager that I think lets you try to connect - you could always pull that from the repos.

But anyway - since the wireless is being detected you should be able to connect to it by disabling everything first.

---

### Post by computerwiz3491 on 2006-12-19
I already know that I could connect to the network. I had two original problems:
1) I need to be able to connect to a WPA network, and I am unable to. I can connect to unsecured networks
2)I was wondering if there were a way for me to find and connect to networks without already knowing they exist


THANK YOU

---

### Post by floke on 2006-12-19
I assumed that the WPA network was your home network - and that (since I don't know how to access it if it can't be done via the Ascii/Hex etc. stuff) it might be a good idea (until you sussed the WPA etc. out properly) if you switched it to WEP (I know this works since its what I have) - this would give you wireless functionality until you got things set up as you wanted.

If this is not the case (eg if you can't change the WPA to WEP etc.) then I don;t know how to do it - in fact from a quick scout on the web it seems like this is not set up as default in Edgy.

This seems like a good link: [http://www.tuxmachines.org/node/11938](http://www.tuxmachines.org/node/11938)

From a Google of 'Connect to WPA in Ubuntu' it seems that there's a few more such links to examine for clues.

As for the second point - KWifiManager seems to work (if I remember rightly) - though you could also search the repos - I think there's a few packages in there. 

Knoppix does a good job (though not much use form Ubuntu!):rolleyes:

---

### Post by chronusdark on 2006-12-19
have you tried using networkmanager, it does all those neat features you need.

```
sudo apt-get install network-manager-gnome
```

it lets you see networks and supports all the cool encryptions

---

### Post by little dave on 2006-12-19
> **chronusdark said:**
> have you tried using networkmanager, it does all those neat features you need.

```
sudo apt-get install network-manager-gnome
```

it lets you see networks and supports all the cool encryptions



 I'm using it now, it was easy:mrgreen:

---

### Post by computerwiz3491 on 2006-12-21
I installed network-manager, but it doesn't allow me to select the wireless interface. In fact, it prevents me from connecting to wireless through the standard utility. Is there any way I can let it know I have a wireless card installed? Also, is there a user manual anywhere?

Thank you

---

