---
title: "HowTo: Configuring multiple APs with wpa_supplicant"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by SugarDaddy on 2006-12-27
OK, while some of us may be happy to have only one SSID configured within our /etc/network/interfaces or wpa_supplicant.conf file, if you are like me, you probably find yourself on the move connecting to numerous access points (APs) and a single purpose solution just won't do. However, this can get complicated when we have to use wpa_supplicant.

Fortunately, it is easy to configure multiple APs in wpa_supplicant.conf: if you have already configured one network block, it is just a matter of adding another, and another, and another...until your are done. Just keep in mind the following:

- If you want to assign priorities to your network blocks (i.e. the order in which wpa_supplicant attempts to connect to the specified APs in the conf file), simply include the priority variable in your network blocks. This variable takes on integer values and the higher the integer the higher the priority. However, if you have to connect to APs with a hidden SSID, the ap_scan=2 global variable must be set in which case wpa_supplicant will simply move through the network blocks in the order they are included in the wpa_supplicant.conf file regardless of the priority variable.

- If you have configured your AP within the /etc/network/interfaces file, you will probably want to move those settings to your wpa_supplicant.conf file.

- Since you are on the move, you will probably be connecting to APs that use a variety of encryption methods (some won't have any encryption). The best reference I have found on how to properly set up each encryption is the following link:

[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain)

- Lastly this guide assumes you have a working AP that requires wpa_supplicant (i.e. already installed).

So with all that said let's go!

[B]Step 1: Get your existing AP set up within wpa_supplicant.conf
[/B] Open a terminal and type the following command:
```
sudo gedit /etc/wpa_supplicant.conf

```This will open a editor and hopefully you have something that looks similar to this. It doesn't have to be exact, in fact it will likely be different. The thingy we are looking for is a network block denoted by network={...}:
```
ctrl_interface=/var/run/wpa_supplicant 
#ap_scan=1 
 
network={ 
    ssid="your SSID name here" 
    scan_ssid=1 
    proto=WPA RSN
    key_mgmt=WPA-PSK 
    group=CCMP TKIP 
    pairwise=CCMP TKIP 
    psk="your super secret password"
}
``` If you have have an existing network block you can move to **Step 2**. If you only have the first two lines or the file is completely empty you probably have your AP settings in the /etc/network/interfaces file. Simply open up this file from a new terminal
```
sudo gedit /etc/network/interfaces

```and copy down the settings for each variable that starts with wpa-xxx and create a network block in your wpa_supplicant.conf file following the example above that includes the variables you have in your /etc/network/interfaces file. These should map nicely to the example above with the exception of wpa-driver and wpa-conf variables, but don't worry about these, we will replace all the wpa-xxx variables with something entirely different soon. Make sure that the first line ctrl_interface=/var/run/wpa_supplicant is in the wpa_supplicant.conf. Then save and close the file. You will probably want to skip to **Step 3** to make sure you got your single AP working before adding more APs.

[B]Step 2: Adding additional APs or network blocks
[/B] If you have a wpa_supplicant.conf that looks like the above, then it is a simple process of copying the existing network block and making the necessary changes for the new network(s). Below is an example where I have my home AP in the first network block, which is a hidden SSID (requiring ap_scan=2) and WPA2 with AES encryption. The second network block is shared WEP connection, and the third is an open SSID without any encryption. Since ap_scan=2, I have commented out the priority variables because wpa_supplicant will simply move through each network block in the order they are included in the conf file.
```
 ctrl_interface=/var/run/wpa_supplicant 
ap_scan=2 
 
network={ 
    ssid="my hidden SSID" 
    scan_ssid=1 
    proto=RSN 
    key_mgmt=WPA-PSK 
    group=CCMP
    pairwise=CCMP
    psk="my super secret password"
#    priority=10 
}[FONT=Verdana]
[/FONT]network={
    ssid="WEP SSID" [FONT=Verdana]
[/FONT]    key_mgmt=NONE[FONT=Verdana]
[/FONT]    wep_key0="abcde"[FONT=Verdana]
[/FONT]    wep_key1=0102030405[FONT=Verdana]
[/FONT]    wep_key2="1234567890123"[FONT=Verdana]
[/FONT]    wep_tx_keyidx=0[FONT=Verdana]
[/FONT]#    priority=5[FONT=Verdana]
}[/FONT]
network={
    ssid="Coffeehouse WiFi SSID"
    key_mgmt=NONE
#    priority=6 
 }
```[B]Step 3: Configure /etc/network/interfaces for dhcp
[/B]Now that your card is now on the move, you can't have a static configuration in your /etc/network/interfaces and you will need to make your eth1, wlan0, ath0, or whatever your wireless card is, dhcp. So open it up, and delete or comment out the static settings if they exist. If you skipped here from **Step 1** because you had a bunch of wpa-xxx settings, now is the time to delete or comment all of them out. When you are done, you should have something very similar to mine below. My wireless card is eth1. I have pre-up and post-down lines to start up wpa_supplicant and point it to the configuration file on boot up and shut wpa_supplicant down properly when closing up shop. The main things you need to watch out for are the -ieth1 flag e.g. if your wireless card is wlan0 then change this flag to -iwlan0. Also, the default driver -Dwext may need to be changed to -imadwifi for Atheros cards. To get help on the flags for wpa_supplicant type: wpa_supplicant -help, in a terminal.

Note that I have my eth0 active because I use my Broadcom wired card on occasion as well.
```
sudo gedit /etc/network/interfaces
``````
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf 
post-down killall -q wpa_supplicant
```[B]Step 4: Reboot and test
[/B]At this point it is probably just easier to reboot and watch what happens. But please bear in mind it could take a few minutes after reboot for your WiFi card to connect if the AP you are trying to connect to is the third or fourth network block in the list. Just be patient. If you get a little curious, it is always helpful to open a terminal and type
```
iwlist scan

```[B]Troubleshooting:
[/B]A good command sequence to use if you are having trouble getting your single purpose AP to work is to type the following commands in a terminal after making changes to any of the above files to avoid rebooting every time:
```
sudo killall -q wpa_supplicant
sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

```The debug flag -dd should allow you to troubleshoot any problems as well as confirm that the start up script in your /etc/network/interfaces files is correct.

---

### Post by dbbolton on 2006-12-28
there's a forum for howto's :)

---

### Post by molhki on 2006-12-28
Thanks SudarDaddy ! 

After searching numerous threads on the subject I finally managed to connect (and stay connected!) to my WPA protected AP, thanks to your instructions.
I'm using D-link DWL-G650 (H/W ver C2) with the madwifi drivers. Will try configuring multiple AP's later.

---

### Post by SugarDaddy on 2006-12-28
mohlki, glad this helped!

---

### Post by SugarDaddy on 2006-12-28
dbbolton, thanks for the tip!

---

