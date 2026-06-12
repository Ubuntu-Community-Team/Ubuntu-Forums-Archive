---
title: "Wireless Drops After Reboot"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by louisd11 on 2007-03-13
Every time I reboot my computer my wireless drops and I have to type in the commands to connect back to my router a bunch of times until it work. I basically mess with my wireless settings in "Networking" menu and in Terminal till my wireless starts to work. Is their any good wireless tools out there that our good? I tried some that are in the "Add/Remove" menu and installed them, but there all flakey and cant search for wireless networks. Anything Amazing out there? I am running 6.10 Ubuntu. And my card is a Linksys WRT54GX (From what I remember cause i dont wanna take it out because thats another half hour."

---

### Post by atselby on 2007-03-13
Get wireless assistant and wi-fi radar from the add/remove dialogs or synaptic. I have both of those and usually one or the other will fix this.

---

### Post by louisd11 on 2007-03-13
Kind of didn't work, as I had to futs with things again.

---

### Post by atselby on 2007-03-13
How's your network setup?

---

### Post by louisd11 on 2007-03-14
I did have WEP encryption but turned it off because i thouhggt it was affecting how my wireless was working.

---

### Post by atselby on 2007-03-14
Using wi-fi radar that you can download through synaptic or the add/remove dialog you need to locate your network and with wep login to it. It should give you dialogs to guide you through it. Click edit on the network you want to connect to and do this.

Network Name: -Your networks name-
-Click WiFi Options-
Mode: auto
Channel: auto
Key: -Your WEP key-
Security: open

and make sure it says No WPA, Automatic network configuration (DHCP) and Connection Commands after that .Do not expand these unless your network doesnt use DHCP in which case I can't help further.

HOpe it works.

---

### Post by louisd11 on 2007-03-14
Well whenever I try to add a profile it says "Networkname" already exist. How do I make it so I can add a network.

---

### Post by atselby on 2007-03-14
Huhm.. .What's your SSID on your network?

---

### Post by louisd11 on 2007-03-14
The error says > A profile for Lenco already exists And the ssid is "Lenco"

---

### Post by atselby on 2007-03-14
Did you setup any profiles?

---

### Post by louisd11 on 2007-03-14
I think I tried this program out once and uninstalled it. But it wont let me edit this profile. anyway I can manually delete it?

---

### Post by SactoBob on 2007-03-14
If you are using the gnome network manager, it can be annoying in my experience.  If the profile you are using becomes bad, it will keep using it, and not let you add another profile under the same name.

I found a way around it like this:

When the applet asks for permission to the default keyring, deny permission.  Now click on the desired network and it will take you through the whole connection routine and save your new and hopefully accurate settings.

The problem seems to be that the network manager assumes everything is as it was when you previously connected, even though you may have changed security settings, for example.  It does not check that it's saved settings are accurate each time it tries to connect.

Bob

---

### Post by louisd11 on 2007-03-14
When does it ask for the default keyring? Are you talking about "Wifi-Radar"?

---

### Post by SactoBob on 2007-03-14
Sorry,
If you are not getting prompted for a password before you connect (with gnome network mgr) then you are not experiencing the problem I did.  I wasn't quite clear as to what you were experiencing.

How specifically are you able to reconnect after reboot?

I am assuming that this is not just a failure to load ndiswrapper at boot, which would be solved by sudo ndiswrapper -m.

---

