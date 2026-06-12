---
title: "WG511T will not WEP"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by infernon on 2007-10-03
I recently purchased a Netgear WG511T wireless PCMCIA card for use with my T61 Thinkpad because I read that it worked 'out of the box' on the supported cards page.

Ubuntu sees the card without a problem, but will not connect to my 64-bit WEP network at home.  It will, however, connect to the WPA network at work, but the signal is pretty weak considering that I'm sitting roughly ten feet away from the AP (36%).  Connection with WEP networks is crucial for me, however.

I wanted to pull the latest version of the madwifi drivers off of the madwifi web site, but I wasn't sure that it would correct the problem and I wanted to post here first to see if anyone could offer any advice.  I'm willing to do what it takes to work through this one.

---

### Post by kast on 2007-10-03
indulge me for a minute here and walk me threw what you are doing when setting your card to 64bit WEP.

---

### Post by tgalati4 on 2007-10-03
Try in a terminal:

>sudo iwconfig wlan0 key open essid "Your Network Name" key AB:BC:CD:01:02

---

### Post by infernon on 2007-10-03
Sure.

My home network does not broadcast the ESSID so I click on Network Manager, select the option to 'Connect to another network' and enter the name of my network, choose the option for '64/128 bit WEP Hex' (don't remember exact wording), enter the key and click 'Connect'.

It 'swirls' for a couple of seconds, but fails to connect.  On a WPA network, I find that it easily connects without any trouble at all.

If you need more information, just let me know.

ALSO, I am using Feisty.  I apologize as that is obviously an important piece of information.

---

### Post by kevdog on 2007-10-03
For testing purposes can you turn on essid broadcast.  Im not certain but I think that it its current state many of the drivers/network manager do not work well with hidden essid broadcast.

---

### Post by Lambert on 2007-10-03
One more suggestion to research.

> Why won't my wireless NIC associate properly when I use enable restricted mode WEP on my AP?

This question and answer were supplied by Aaron Turner. 

If your AP is configured to have WEP enabled and is in restricted mode (rather then open mode) the madwifi driver won't properly associate. Symptoms of this include iwconfig showing the NIC associating and unassociating on a regular basis and not being able to send any traffic. 

The solution is to force the authentication to restricted mode using iwpriv in addition to iwconfig. 

The following commands should do the trick: 
```

iwconfig ath0 key restricted
iwpriv ath0 authmode 2

```


---

### Post by infernon on 2007-10-03
Just a quick note.  I ran home at lunch and had a chance to quickly test the connection with the ESSID broadcasting ON.  Unfortunately, my attempt to connect was still unsuccessful.  I will be trying the other proposed solutions when I get home later today.

---

### Post by kevdog on 2007-10-03
sudo ifconfig <interface name> down
sudo ifconfig <interface name> up
sudo iwconfig <interface name> essid "ESSID_iN_QUOTES"
sudo iwconfig <interface name> mode Managed
sudo iwconfig <interface name> key 10_digit_hex_key (no quotes or colons)
sudo dhclient <interface name>

---

### Post by infernon on 2007-10-03
kevdog, 

Your solution worked as far as getting me to connect.  I still have other questions, of course:)

Network manager did not recognize that I was connected to a network after I performed the sequence of commands that you suggested.  Is there a way to correct this or another tool to use that would recognize the connection?

My wife would like to use the laptop and I would need her to be able to easily connect to the wireless network without running the commands.  Short of writing a script to do so, are there any other options for simplifying the process?  In other words, does the fact that this worked tell you anything else about the problem that I'm having?

I also noticed that the interface will not reconnect after it has been disconnected unless the machine is rebooted.  In addition, I'm showing both an ath0 interface and a wifi0 interface on my machine.  ath0 is what works as far as the commands that you gave me go.

Any more information would be greatly appreciated!

---

### Post by kevdog on 2007-10-03
Your using the madwifi drivers that create virtual interfaces for wifi0.  So having ath0 (the virtual interface) is normal for the madwifi drivers (but not other drivers).   I dont know why network manager doesnt work for you, since it works from the command line doing a "manual" connect.  What I would probably recommend is installing WICD and uninstalling network manager.  WICD does a lot of things, however I know that at its core it simply issues the manual commands that you typed (among others) to make the connection, so I understand how this program works.  Im not certain how network manager works (but I dont think it could be that different).  The author of WICD frequently peruses these forums so if you ever had any problems or requests he would make the change for you.  Make you when you install WICD to go for the unstable or testing version -- it works a heck of a lot better than the stable version.

---

### Post by tgalati4 on 2007-10-04
I use WiFi Radar for managing connections.  Others have experienced problems with Network Manager in Feisty.  A forum search will quickly reveal Network Manager's strengths.

Or lack thereof.

---

### Post by infernon on 2007-10-04
I'm reading sarcasm in there, but not sure if I'm on the right track:)

---

### Post by infernon on 2007-10-04
On a whim, I decided to see if another distro had the same issues.  FC7 was the only one that I had on hand.

Network manager works perfectly with FC7 and my home wireless network.  I'm sure that there are a number of things that work into this that I'm not aware of (madwifi and kernel versions, etc.), but I figured that it would be food for though for anyone who cared.

---

