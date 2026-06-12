---
title: "Help with WICD"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-01
Currently downloaded and installed wicd 1.32 on Ubuntu Feisty 32bit.  Had previous successful configuration with network-manager with wpa2 encryption via ndiswrapper/wpasupplicant.  Have uninstalled network manager/network manager gnome prior to trying wicd.  WICD can not obtain dhcp address.  Is there something I have to change in the /etc/network/interfaces file, or some other config file to get this program to work?

---

### Post by ozooha on 2007-08-01
Dude I would suggest that you try all the different drivers like wext, broadcom etc under preferences.
I have ndiswrapper installed- the latest one 1.47 but WICD worked for me when I chose wext as my
driver. It would keep obtaining IP address when I had put ndiswrapper as my driver.
OZooHA

---

### Post by kevdog on 2007-08-01
OK I found a solution manually however I dont know how to fix this with WICD.

My router is set to WPA2 PSK with AES+TKIP ciphers.

By default WICD created a file within /opt/wicd/encryption/configurations named 0013108e94e9 for me (which is the MAC address of my router).  Here is what was in the file originally:

```
ap_scan=1

network={
       ssid="GoHilton.com"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=*Key Hidden Here but it was in hex format*
}
```

I tried the following at the command line with this file but it did not connect:
```

sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo wpa_supplicant -B -Dwext -iwlan0 -c/opt/wicd/encryption/configurations/0013108e94e9 -dd
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

It wouldnt receive a dhcp offer -- basically it would hang

I slightly modified the file to make it read:
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="GoHilton.com"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk=*PSK Hex Key Here*
}
```

Notice I added the ctrl_interface line and made some modification to the proto pairwise and group statement.  Please note that my router is set to use WPA2 with AES+TKIP cipher with PSK

Repeating the process above:

```

sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo wpa_supplicant -B -Dwext -iwlan0 -c/opt/wicd/encryption/configurations/0013108e94e9 -dd
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

I was able to obtain a IP address (in fact Im using it right now!)

The problem is that everytime I go to start WICD, this configurations file that I modified reverts back to the original.  HOW DO I STOP THIS FROM HAPPENING!!!

---

### Post by imdano on 2007-08-02
There are a couple of options.  
1) You could go into /opt/wicd/encryption/templates and edit the wpa template to look like the configuration that's working for you.  
2) You could also create a new template (so that normal wpa networks will still connect).  You can basically follow the pattern in the standard wpa template, just give it a different name, and make the changes you made to your configuration.  Then open /opt/wicd/encryption/templates/active and add the name of the template you made to the list.  When you open the gui you should see your new template in the list.  If you're able to get it working it'd be nice if you could post it here so we can add it to the next release.

Also it'd be helpful for myself and Adam if you could figure out exactly which of the changes you made were required to make wicd connect.  Just so to help us figure out exactly what was going on.

---

### Post by kevdog on 2007-08-02
Ill definitely pin it down as best as I can to let you know what changes were absolutely needed.  The problem for me is that I cant even get the wicd gui to start.  Im getting a lot of error messages in the terminal -- something about MII.  I manually start the daemon, but then when I go to the gui.py, nothing happens or I get something about MII.  

I'll work on the manual settings first to pin down the changes necessary, and then create a template to see if I can get wicd to work.  By the way, the wicd forum isnt really helpful since the last post was from April and you cant register.

---

### Post by fredj on 2007-08-02
Go to Sytem->Preferences->Sessions->Startup Programs->New and then enter
Wicd as the program name and /opt/wicd/tray-edgy.py as the command.

---

### Post by ugm6hr on 2007-08-02
> **kevdog said:**
> By the way, the wicd forum isnt really helpful since the last post was from April and you cant register.

I think you must be looking at the wrong forum:
[http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

You will see Adam and dano there pretty much any day you visit.  You will see that the "View active topics link" will give about 15 threads updated within the last week.

PS: Is there a reason you wanted to try Wicd, since NM was working for you?

---

### Post by kevdog on 2007-08-02
Thanks for the link.  As far as trying wcid, I just like messing aroung :)

---

### Post by imdano on 2007-08-02
> **kevdog said:**
> The problem for me is that I cant even get the wicd gui to start.  Im getting a lot of error messages in the terminal -- something about MII.  I manually start the daemon, but then when I go to the gui.py, nothing happens or I get something about MII.Mii-tool is used to determine if there's an ethernet cable plugged in to your computer.  Some computers don't support it, but I think that any errors it gives because of that should get handled by wicd.  You can test it by running ```
sudo mii-tool
``` from the console.  I sent you a pm a few minutes ago, try what I suggested in that and we'll go from there.

---

### Post by kevdog on 2007-08-02
Imdano

I just replied to your pm with my found solutions and some suggestions.  Thanks for your help.  I like WICD

---

