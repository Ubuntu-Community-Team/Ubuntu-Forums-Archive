---
title: "Access Point: Not-Associated"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by tiachopvutru on 2007-04-23
I have a Netgear WG111T Wireless USB Adapter and Edgy Eft installed on the other computer. It's an old computer but I think it's capable of handling Ubuntu Linux.

I've installed ndiswrapper and have all the necessary drivers (I think). Anyway, I need help configuring the wireless, I'm not sure what I have done wrong since I can't connect.

Anyway, here's what my iwconfig turns out to be

```
chucuoi@Tran:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan2     IEEE 802.11g  ESSID:"nicholasnho"  
          
              Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          
              Bit Rate:108 Mb/s   
          
              Link Quality:0  Signal level:0  Noise level:0
          
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0



sit0      no wireless extensions.


```

The Access Point says "Not-Associated". I don't know what that is but I assume that it should say something different when connected.


Here's the result of my iwlist scan,

```
chucuoi@Tran:~$ iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan2     Scan completed :
          
Cell 01 - Address: 00:15:05:EE:34:A4
                    
               ESSID:"OM3V7"
                    
               Protocol:IEEE 802.11g
                    
               Mode:Managed
                    
               Frequency:2.437 GHz (Channel 6)
                    
              Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    
              Encryption key:on
                    
              Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              
                             9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              
                             48 Mb/s; 54 Mb/s
                    
              Extra:bcn_int=100
                    
             Extra:atim=0
          
Cell 02 - Address: 00:15:E9:65:47:38
                    
               ESSID:"nicholasnho"
                   
               Protocol:IEEE 802.11g
                    
               Mode:Managed
                    
              Frequency:2.462 GHz (Channel 11)
                   
              Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    
              Encryption key:on
                    
              Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              
                            12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              
                            48 Mb/s; 54 Mb/s
                    
                           Extra:bcn_int=100
                    
                           Extra:atim=0


sit0      Interface doesn't support scanning.


```

The one I want to connect to is the one with the essid nicholasnho


```
chucuoi@Tran:~$ ndiswrapper -l

athfmwdl : driver installed

WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied

netwg11t : driver installed
        
             device (1385:4250) present


```


And here's what's in my /etc/network/interfaces file

> auto wlan2

iface wlan2 inet dhcp

wireless-essid nicholasnho

wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

wireless-channel 11

wireless-mode managed



I have no idea why it's wlan2 (was wlan0 before then it changed to wlan1, now wlan2)

The router is not mine. (it's my household's and she let me use it so I can't tell whether I can connect without the WEP key, but turning the key off is impossible). I have the key and it works on this computer. (I installed Edgy on the other comp). The PC that I installed Edgy on used to have Windows and the wireless used to work on it, too.

I have just started using Linux for the first time 2 days ago (in other word, noob). So please give easy instruction or explain it. Also, I'm not quite sure what informations to put here...

---

### Post by spd106 on 2007-04-25
Could you please link the guide you used to get the driver installed?

If you haven't already you might have better luck building a newer version of ndiswrapper from source. This means you will have to download the tar.gz from sourceforge.net and compile it yourself.

---

### Post by Jouke74 on 2007-04-25
Clean out your aliasses file from all Wlan's, I guess you attempted the install a few times? Make also sure all old ndiswrapper stuff is removed before you compile a new one (see ndiswrapper site). I had also the access point not associated problem, and it was solved by compiling 1.42. Finally, check if the wireless card is not supported already.

---

### Post by tiachopvutru on 2007-04-26
I did download the latest version of ndiswrapper but it didn't work. I think I didn't delete the old ndiswrapper version when I compiled the new one though. And I'm not sure how to "clean out all aliasses file from all Wlan"

As for the guide I used, it's right here: [http://ubuntuforums.org/showthread.php?t=407377](http://ubuntuforums.org/showthread.php?t=407377)

Scroll down to the 5th post and you will see it. However, as stated, the router is my household's so I can't turn the WEP encryption off like how the tutorial told to.

---

### Post by spd106 on 2007-04-26
The part in the guide about editing the /etc/iftab file tells you so substitute the all 0s address for your own, so it should look something like this.
```
:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:0x:xx:xx:xx:xx 

```
This line isn't neccessary and if wrong will prevent your card from getting the wlan0 name, so it will be forced to wlan1, then wlan2 etc. The idea is persistent naming of interfaces so that each card you use will get (and keep) a unique name on your PC.

This wiki page is a better formatted and more thorough version of that guide [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

---

### Post by Sensei_V on 2007-04-26
I had similar problems, but I lived to [tell about it]("http://ubuntuforums.org/showthread.php?t=424262").  I'm no expert, but after I got to the point where I could see wireless networks with "iwlist scan", I think the drivers were properly installed for my wireless card and the main problem left was the encryption.  I had no luck with modifying /etc/network/interfaces , so I switched my wireless interface to roaming mode and was able to configure the NetworkManager applet to access my default keyring in order to associate with the network.  See the thread I linked to for details.

---

### Post by tiachopvutru on 2007-04-27
@spd106: Still doesn't work. I don't understand where I did wrong. 

@Sensei_V: I quite don't understand the instruction. Do I go to Keyring Manager and adds key name "default"? And then open System > Administration > Networking? I didn't see any pop up that prompt to input any wireless information though.

---

### Post by Sensei_V on 2007-04-27
> **tiachopvutru said:**
> @Sensei_V: I quite don't understand the instruction. Do I go to Keyring Manager and adds key name "default"? And then open System > Administration > Networking? I didn't see any pop up that prompt to input any wireless information though.

After creating the default keyring (not key, I can't add individual keys, just keyrings), I used the nm-applet to select my wireless router.  You can only do this if you have roaming mode set in Networking.  If you don't see a list of wireless networks in the nm-applet, you're not ready to connect.  I'm attaching some screenshots so that you can get the idea of what the nm-applet is.  They are roughly in the order you should see them during setup.  If you don't have this menu, just type "nm-applet" into terminal.  In my Feisty installation, this was automatically part of my startup programs located in System > Preferences > Sessions with the command "nm-applet --sm-disable", but I will be changing that shortly to try the pam-keyring automatic keyring access on login technique.

Do you have the nm-applet working in roaming mode?  You set up roaming mode in System > Administration > Networking under the properties for your Wireless connection.  Once the nm-applet is ready to use as a network selection tool (rather than hard coding things into the network settings) and you select a network, it should prompt you for a password.  For me, it even tells me what kind of security the router is running.

The tricky part is somewhat random, when you get prompted to either create or access the default keyring after entering the network password, and I'm wrestling with that now since I decided to switch between WPA and WPA2 ...  I always seem to break things right after I get them working.

Update: while writing this I was able to reconnect by actually following my own advice ... go figure.  This time, after deleting and recreating the default keyring, I wasn't even prompted for keyring access, perhaps because I had accessed it so recently (sometimes commands like sudo make root access stick for a short time).

Does this clear things up?

Edit: @tiachopvutru:  If you don't have the driver installed, with ndiswrapper or otherwise, what I've just told you is irrelevant.  On the other hand, I think that if you can see networks with "iwlist scan" you already have the driver installed, but I could be wrong.  There is the possibility that the driver you have installed doesn't support the encryption you need, but I can't help you there.

---

### Post by tiachopvutru on 2007-04-28
Sorry for being nab but I'm still having trouble XD.

I have added the keyring "default". About the Network Manager, or nm-applet thing, you are referring to the program name "Networking" in System > Administration? If so, when I configured the "Wireless" in there, all I had was the option for inputting the Essid and the Key. (Also the IP Address, Subnet Mark and Gateway). Also, in terminal, it says "Command not found" when I typed "nm-applet."

I don't have that little nm-applet on the menu like you do, nor do I know how to get it... 

Sorry, but I need further help =P ... Thanks in advance.

Also, I do have ndiswrapper and the drivers for it install.

EDIT: the WEP encryption has 26 letters + numbers in it (not 26 letters and 26 numbers but altogether), so it's 128-bit hexadecimal WEP encryption btw

---

### Post by spd106 on 2007-04-28
Edgy doesn't have network manager installed by default so you will have to install it yourself.
See [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by tiachopvutru on 2007-04-29
When I tried to click the box to the left to install it, it gives me the message: 
"Network Manager cannot be installed on your computer type (i386)  
Either the application requires special hardware features or your vendor decided not to support your computer type"

I feel the day I have to quit using Linux on a PC is coming near...

---

### Post by spd106 on 2007-04-29
Let's try installing through Synaptic instead.

Open System -> Admin -> Synaptic Package Manager, then select Settings -> Repositories... and ensure that universe is ticked.
Close, then click Reload.
Search for network-manager and select it by double-clicking, check that network-manager-gnome is also going to be installed.
Click Apply and follow through until it's installed.

You will then have to logout or restart as directed in the wiki page I linked earlier.

---

### Post by tiachopvutru on 2007-04-29
When I checked the universe packages and click reload, it gave me an error that it wasn't able to index the packages due to internet problem. (the PC I'm running Linux doesn't have Internet connection)

Are there anyway for me to download it somewhere? I can transfer it to my USB storage device then install it on my Linux machine

---

### Post by spd106 on 2007-04-29
Yes, but there are a few dependencies.

You will need to download:
dhcdbd
libnl1-pre6
libnm-util0
network-manager
network-manager-gnome

I have previously posted direct links to the edgy versions in [this]("http://ubuntuforums.org/showthread.php?t=403479&p=2415484") thread.

These are on the alternate cd, but not the desktop cd.

---

### Post by Sensei_V on 2007-05-01
I recently upgraded to Feisty, so I have NetworkManager installed already.  I hope you have better luck getting it installed on Edgy.

If you want to try doing what worked for me, you'll have to get NM.  I also needed to check the box for "Roaming Mode" in my wireless properties for the menu to show other networks.  For some reason, the Wireless properties window shows WEP settings, but has nothing about WPA.  But even with my router set to use WEP, I couldn't connect.

The NetworkManager supports WPA, but it needs access to the keyring in order to connect.  I've found that NM is more likely (but not guaranteed, I had to try it multiple times) to ask for access to your default keyring if you already have a default keyring set up.

---

### Post by tiachopvutru on 2007-05-01
Network Manager saves the day :)  ... Thank you very much for your help.

Before I'm done with this thread, may I ask one more question? Where do the installed program from .deb usually go? This time I have the nm-applet but it would be troublesome in the future if I install something

---

### Post by spd106 on 2007-05-01
There are a variety of places that files are copied to, /usr being the normal place. If you install a gui based app from the repositories it will usually place a shortcut in the Applications menu. However if you install a none gui or none official package there likely won't be an obvious shortcut. You shouldn't have to worry too much, most of the time the documentation is clear.

---

### Post by tiachopvutru on 2007-05-02
Alright, thanks a lot for the help.

For some strange reason the device doesn't flash anymore today but I'll see about it.

Thanks for the helps again.

EDIT: Sorry, one more question :P ... Where do I find Safety Remove Hardware equivalent on Linux? Since just unplug a device can be unsafe

---

### Post by spd106 on 2007-05-03
For most devices it's not neccessary to stop it before it's removed. The only time you really should is when you have a filesystem mounted, such as an external hard drive. In that case just unmount the filesystem nautilus. This is usually done by right-clicking the symbol and then clicking unmount.

---

### Post by josephus on 2007-05-03
tiachopvutru:  even if you get everything working i think you will have a hard time getting it to connect that network.  the signal strength is *very* low.  move your computer closer to the access point if you can.

---

### Post by tiachopvutru on 2007-05-03
Look like I need some help again. The wireless USB device didn't flash yesterday so I reinstalled the OS, redid everything and was able to get it working once again. When I was done with everything, I shut the computer off. Today, however, when I turn the computer back on, the wireless device doesn't flash ... 

Anyone has any ideas what it is? I did ndiswrapper -l in terminal and it says device present. However, the device doesn't flash and Network Manager can't detect it either...

@spd106: So I don't need Safety Remove Hardware equivalent for my wireless USB device? Also, about the installing stuff in Linux issue... I have installed BitDefender AV for Linux but now I don't know where to execute the program...

@josephus: This is as far as I can move it. My household keeps the router upstair... I been connecting fine with wireless on this computer with windows on so I guess the one I installed ubuntu to should be fine to


EDIT: I had to reinstall ndiswapper and now it works. But, I don't know what gonna happen in the future... I can't manage to keep reinstalling ndiswrapper everytime if it keeps occuring like that

---

### Post by spd106 on 2007-05-04
Next time you reboot, check that ndiswrapper has been loaded by running this command.
```
lsmod | grep ndis
```
If it shows nothing then try inserting the driver with this command
```
sudo modprobe ndiswrapper
```


It might also be worth checking that you have ndiswrapper listed in the /etc/modules file.

---

### Post by tiachopvutru on 2007-05-04
Nevermind, it seems that the problem is solved as long as I unplug the device when shutting down the computer and plug it back only *after* the comp is turned back on.

I'm still having trouble of finding whereabout in the system the Bitdefender AV I installed. I know where the plugins are but the actual program... I have no idea

---

