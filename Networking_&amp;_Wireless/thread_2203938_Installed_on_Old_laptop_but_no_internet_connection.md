---
title: "Installed on Old laptop but no internet connection"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by Gillette on 2014-02-06
I just installed Lubuntu 13.10 on an old Compaq Presario 2100 but there is no internet connection. I had Xubuntu 8.04 installed prior to that and I had internet connection with no problems. What do I need to do to get this connected to the Internet. I have DSL.

---

### Post by sudodus on 2014-02-06
I think you might have better luck with a flavour, re-spin or distro based on Ubuntu 12.04 LTS. Not standard Ubuntu, it needs too much horsepower, but Xubuntu, LXLE, Bento, Bodhi or Precise Gnome Classic Tweaks. See this link (The first post and the last few posts). [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by mastablasta on 2014-02-06
@sudodus - they instaled Lubuntu

@gillette - how are you connecting ? wired, wireless? 3G?

---

### Post by sudodus on 2014-02-06
@*mastablasta* - I like Lubuntu and use it myself, but since Lubuntu 13.10 has no driver for *gilllette*'s network chip, and there is no other Lubuntu version with [security] updates, I suggested something based on Ubuntu 12.04 LTS, which might work out of the box.

But it is definitely worth exploring the route you are suggesting, to identify the chip or card and maybe find and install a driver for it.

---

### Post by varunendra on 2014-02-06
Drivers are part of the kernel which is same for all flavours, so I'd assume either the problem lies somewhere else, or would be same for all flavours.

@Gillette,
Please open a terminal (Ctrl-Alt-T) and run the following command in it (you may copy-paste it) :
```
sudo lshw -numeric -C network
```
Post back its entire output here in your next post. Do not forget to wrap the output within 'Code' tags (see the "Using Code Tags" link in my signature below).

I am assuming, by your mention of "DSL", that you are using a cable connection (a cable plugged in your computer's Ethernet port). If not, please answer mastablasta's question first.

---

### Post by Gillette on 2014-02-06
Wired connection.

---

### Post by Gillette on 2014-02-06
Here are the results:

```

lance@lance-Presario-2100-DK578A:~$ sudo lshw -numeric -C network
[sudo] password for lance: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller [14E4:4320]
       vendor: Broadcom Corporation [14E4]
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:10 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller [100B:20]
       vendor: National Semiconductor Corporation [100B]
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:e8:f5:fe
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:11 ioport:8c00(size=256) memory:d0005000-d0005fff memory:24000000-2400ffff
lance@lance-Presario-2100-DK578A:~$ sudo lshw -numeric -C network

```

---

### Post by varunendra on 2014-02-06
> **Gillette said:**
> ```

       configuration: **autonegotiation=[COLOR="#FF0000"]off[/COLOR]** broadcast=yes **driver=[COLOR="#006400"]natsemi[/COLOR]** driverversion=2.1 **duplex=[COLOR="#FF0000"]half[/COLOR]** latency=90 **[COLOR="#006400"]link=yes[/COLOR]** maxlatency=52 mingnt=11 multicast=yes port=twisted pair **speed=10Mbit/s**

```
The driver is found and loaded, since the link is detected. But other than that, the configuration doesn't look good. Have you tried any tweaks with 'ethtool' or 'mii-tool' commands?

Please try -
```
sudo mii-tool -r eth0
```

Or,
```
sudo mii-tool -F 100baseTx-FD eth0
```

If the interface is not compatible with mii protocols, you will receive an error saying so. In that case, try this alternative -
```
sudo modprobe -rv natsemi
sudo modprobe -v natsemi full_duplex=1
```
Or, if this doesn't help, try -
```
sudo modprobe -rv natsemi
sudo modprobe -v natsemi options=17
```
..this is rather a guess, not sure if it can even be accepted by the driver, so in case of errors, just reload the driver normally again -
```
sudo modprobe -v natsemi
```

Another thing you may try is to manually assign an IP to the interface, although the Half Duplex mode may still be a problem -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 **192.168.1.40**
```
..where ***192.168.1.40*** is just for example, replace it with a valid available IP as per your local network.

If none of these could help, we may have to install "nictools-pci" package to diagnose your card's problems.

---

### Post by Gillette on 2014-02-06
Success! I'm connected to the internet now and using the elderly laptop to type this reply. I ran both of the first two commands and they clicked on the internet icon and then on something I think said autoeth or something. Got immediate access. Thanks for the great help. Now that the laptop is working maybe I'll investigate getting a replacement battery for it.

---

### Post by varunendra on 2014-02-06
Awesome! :)

The "Autoeth.." message, I guess, indicates that you got a DHCP assigned address, which is more good news. Hope it stays this way now. :)

---

### Post by Gillette on 2014-02-06
Bad news. I shut it off and restarted it and no automatic internet connection. I did the first command and it then connected. Anyway to get the fix permanent? Or do I just memorize that command?

---

### Post by varunendra on 2014-02-07
I am still not confident about whether the changes made by mii-tool or ethtool are permanent or temporary. In your case it is obviously temporary, and I don't know a decent way to make it permanent.

There is a driver parameter that looks like it may work, but I haven't yet found a source that explains the meaning of the values it can accept. So try values 1-3 and 17 with it and check everytime with just "sudo mii-tool" command (with no parameters) to see if the driver parameters made any difference. If they did, report back and we can make THAT permanent more decently.

The parameters test -
```
sudo modprobe -rv natsemi
sudo modprobe -v natsemi options=1
```
Then check -
```
sudo mii-tool
```
Does it show "100 Mbit, full duplex" ? If not, try value "2" this time -
```
sudo modprobe -rv natsemi
sudo modprobe -v natsemi options=2
```
..and check "mii-tool" command again. No difference --> try again with values "3" and "0". If still no difference, try the same values (at least 1-3) in combination with another parameter "full_duplex" as in the example below -
```
sudo modprobe -rv natsemi
sudo modprobe -v natsemi options=1 full_duplex=1
```

Sorry for giving you quite an assignment, but I don't yet have much knowledge about this driver and don't know how its parameters work (if at all).

If all this results in an epic fail, time to try some crude workarounds, starting with /etc/rc.local.

ONLY if the above tests fail, then try this -
```
sudo sed -i 's:^exit 0:mii-tool -r eth0\n&:' /etc/rc.local
```

What we are doing is adding the command "mii-tool -r eth0" to your /etc/rc.local file just before its last line that must end with "exit 0". This is assuming that this command always succeeds for you. If so, the only chance of its failure is the timing of its execution. So if it fails (despite working everytime when run manually), we can use other ways to make it permanent.

---

### Post by Gillette on 2014-02-07
I ran this command:

```

sudo modprobe -rv natsemi

```
And I was immediately disconnected from internet.
So then I ran 
```

sudo mii-tool -r eth0

```
and the response was: 
```

SIOCMIIPHY on 'eth0' failed: No such device

```
So then I did:

```

sudo mii-tool -F 100baseTx-FD eth0

```
and got the same failed response.

So then I did:

```

lance@lance-Presario-2100-DK578A:~$ sudo mii-tool
eth0: 100 Mbit, full duplex, link ok
lance@lance-Presario-2100-DK578A:~$ 

```
Now I have internet again. Hope it is a permanent fix. What do you think?

---

### Post by varunendra on 2014-02-07
> **Gillette said:**
> I ran this command:

```

sudo modprobe -rv natsemi

```
And I was immediately disconnected from internet.
So then I ran....

Sorry, I should have explained clearly, the first command Unloads the driver (due to the -r or --remove option), hence will obviously disable the interface. We unload it because that's the only way to load it with parameters. The second command (without the -r option) will reload it, with our supplied additional parameter (options or full_duplex=...). This will make the connection active again.

So it is important to run both of first two commands to see the effect.

About this -
> Now I have internet again. Hope it is a permanent fix. What do you think?
No, I don't think it is permanent. If the previous effect of 'mii-tool' command was lost after a reboot, it will be lost again.

But check the output of just "sudo mii-tool" after next boot, whether the connection is failed or not. It is possible that its effect was permanent, only the DHCP request failed, thus not getting you a valid IP address last time. If so, and if that becomes a problem, we may use an Static IP that does not rely on DHCP.

---

### Post by Gillette on 2014-02-08
I still have to run this command everytime I boot up to get internet:

```

sudo mii-tool -r eth0

```

So how do we use a Static IP so this is a permanent fix?

---

### Post by varunendra on 2014-02-09
> **Gillette said:**
> I still have to run this command everytime I boot up to get internet:

```

sudo mii-tool -r eth0

```

So how do we use a Static IP so this is a permanent fix?

As a sanity check, please make sure that "Connect Automatically" in Network Manager settings for your connection is enabled. And if possible, also try replacing the current cable with a rather fresh/shorter one (don't bother if is too much trouble and the workaround/fix works).

Whether a Static IP is going to work or not depends on whether it is just a DHCP failure or a failure on the correct detection on the media type (speed/duplex). (by the way, and extra long or poor quality cable/contact may be cause for both of these, forgot to mention that earlier).

As I mentioned in my previous post, check the output of -
```
sudo mii-tool
```
..and see whether it shows "10 Mbit, half duplex" or "100 Mbit, full duplex" in the output. If it shows 10M/Half-duplex, try the "sudo mii-tool -r eth0" command as you have been trying, then check with the above command again to see which mode it defaulted to.

If the mode (speed, duplex) is different than what is detected initially, it is a media detection failure (changing cable with a shorter and/or good quality one *may* solve the problem automatically). If it remains the same, then a manual IP assignment should solve it.

**For manual IP assignment**, you may also need to change current DHCP configuration in your router (to limit the DHCP range so that it doesn't assign the same IP to another machine on the network, thus causing an IP conflict). Then,
 in **Network Manager menu > Edit Connections... > "Wired" tab > double-click your connection > "IPv4 Settings" > set 'Method' to "Manual" > enter "Address, Netmask, Gateway" > press 'Enter' > set 'DNS servers' (e.g. 8.8.8.8, 8.8.4.4) > "Save..." > Close**

You can see the current values of all these settings in the output of command -
```
nm-tool
```

However, if the failure is because of correct media detection (seems more probable to me), then please try again what I suggested in post #12 earlier, and report back if any of the driver parameters work (values 0,1,2,3 and 17 for parameter "options=", and the same with parameter "full_duplex=1").

But...... If you are already tired of the experiments, and are sure it is the "sudo mii-tool -r eth0" command that works without fail, then try the last command (that edits the "/etc/rc.local" file) in post #12. It is our ultimate 'Workaround' (not a fix). It may require some tweaking, but will work if the command manually works.

---

### Post by Gillette on 2014-03-11
I never got around to attempting a permanent fix to this problem. I had the sudo mii-tool -r eth0 memorized and it only took a few seconds to get connected that way. But last week there were some new updates for Lubuntu and after that the laptop connects to the internet automatically when I boot it up.

---

### Post by varunendra on 2014-03-12
Thank God updates finally seem to get it right. 

[s]The lord giveth, the lord taketh away..[/s]
Updates breaketh, updates giveth again.. :p

---

