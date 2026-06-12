---
title: "Walkthrough - Installing Ralink 2860 Based Wireless Adapters"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by flyguy97 on 2008-11-01
All,

I recently purchased a wireless PCI card that uses the Ralink 2860 chipset which I was having troubles installing with Ubuntu Intrepid Ibex. The following is a breakdown of what worked on my computer. My particular setup does not use NetworkManager, my ip addresses are dynamically assigned by dhcp, and my router uses WPA2 security. I post this in the hopes that it will help someone avoid similar pit-falls I encountered.

1. Remove network-manager and ensure Build Essentials package is installed
   ```
$ sudo apt-get remove network-manager
$ sudo apt-get install build-essential linux-headers-`uname -r`
```

2. Go to [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") and download the first option (WebUI is non-functioning from what I can tell).

3. Extract archive
   ```
$ tar xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```

4. Change directory into source folder
   ```
$ cd 2008_0918_RT2860_Linux_STA_v1.8.0.0
```

5. Edit os/linux/config.mk in source folder
   ```
$ vi os/linux/config.mk
```
And change the line HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y

6. Make
   ```
$ sudo make
```

7. Install ```
$ sudo make install
```

8. Install kernel module
   ```
$ sudo modprobe rt2860sta
```

9. Add line rt2860sta into /etc/modules
   ```
$ sudo vi /etc/modules
```
   Add rt2860sta to the end of the file.

10. Edit /etc/network/interfaces, mine looks like the following
   ```
auto lo
iface lo inet loopback

iface ra0 inet dhcp
broadcast 192.168.1.255
gateway 192.168.1.1
auto ra0
```

You may need to change the broadcast and gateway line depending on your configuration. Gateway will always take the form of XXX.XXX.X.255 (which is the broadcast address of your network). Gateway will usually be the address of you wireless router.

11. Edit /etc/Wireless/RT2860STA/RT2860STA.dat. The following are the lines I had to change
```
CountryCode=GB
SSID=My_Routers_SSID
WirelessMode=5
Channel=1
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=073d91b66565558a00ec7d1c9a034892928a2c44c490f400f86c9139506a203f
```

NOTE: Some people have had luck using WPA2PSK in AuthMode instead of WPAPSK, make sure to restart your computer after ANY change to the RT2860STA.dat file. Restarting networking is NOT enough to make the driver re-read the configuration file.

Q. How do I get my WPAPSK key?
A. Use the wpa_passphrase command. Example given with sample output:
```
$ wpa_passphrase My_Routers_SSID A_Strong_Password
network={
	ssid="My_Routers_SSID"
	#psk="A_Strong_Password"
	psk=073d91b66565558a00ec7d1c9a034892928a2c44c490f400f86c9139506a203f
}
```

NOTES: You will not need to be connected to any network to perform this step. The first argument to wpa_passphrase must exactly match your router's SSID, this is important and will muck up your key if you use a random value

A reasonably good explanation of appropriate values for CountryCode, WirelessMode, AuthMode, and EncrypType can be found at the bottom of the README_STA file that is included with the source files.

The appropriate value for channel can usually be found from your router's web admin console.

12. Restart computer and enjoy!

-flyguy97

---

### Post by J Caffrey on 2008-11-06
I only succeeded in removing network manager which has now left me without the cable connection too.When I try to extract aechive I get what seems to the stock answer for everything in ubuntu"Cannot open: No such file or directry"I have it downloaded to the desktop.Can I get my wired connection back? Can anyone help here please???? As usual with this os I'm getting nowhere fast.

---

### Post by flyguy97 on 2008-11-08
In order to get NetworkManager back you can do the following:
```
sudo apt-get install network-manager-gnome
```
or
```
sudo apt-get install network-manager-kde
```
depending on your window manager.

But before you go back to NetworkManager, I am willing to help you with the above install directions if you still want to give it a go. In a terminal windows path to your desktop and give it a try.

```
$ cd ~/Desktop
$ tar xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```

Then try the rest of the instructions.

---

### Post by J Caffrey on 2008-11-08
Many thanks for your reply.I'll leave network manager removed and try installing the driver. Will keep you posted:)

---

### Post by J Caffrey on 2008-11-09
I've got as far as trying to change has_wpa_supplicant=n to y.I can get the flashing black cursor over the "n" I even managed to remove it by pressing delete.I have it restored to "n" again but cannot change it to "y" As you've probably gathered my experience is very limited.If I manage to get past this stage do I open a new terminal window to type in "sudo make" or do I scroll down to the bottom of all the script?

---

### Post by flyguy97 on 2008-11-09
Before I get into the commands you need to use, you must understand just a little bit about vi to use it effectively. There are two modes in vi, edit mode and command mode. Command mode lets you perform things such as save, delete, exit abandoning changes, things like that. Edit mode is used to actually edit the text. I will go over the command mode commands first. Here is a table of the most often used commands. Keep in mind key strokes are denoted by the surrounding [] characters, so [Delete] means press the delete key and [:][q][!][Enter] means first press the colon key followed by the q key followed by the exclamation point key followed by the Enter key.

[Delete] - Delete highlighted character
[d][d] - Delete currently selected line
[:][w][q][Enter] - Exit vi saving file first
[:][w][Enter] - Save file but do not exit
[:][q][!][Enter] - Exit file without saving changes
[i] - Begin editing at the currently selected character
[a] - Begin editing one past the currently selected character

Editing mode is thankfully a lot less complicated. Once you enter editing mode by pressing either [i] or [a] then edit as you normally would, with one exception. Do not use the arrow keys to go to the text you want to edit. Instead go back to command mode by press the [Esc] key and then go to your desired location. If you do use the arrow keys in edit mode some funky characters will appear, delete these by going back to command mode, using the [Esc] key, and pressing [d][d] to delete the unwanted lines. When vi starts, it starts in command mode, if you are unsure what mode you are in pressing [esc] will guarantee you will be in command mode. If you have any more questions please don't hesitate to ask.

A note about my quick and simple vi tutorial, I am by no means a vi expert. The only keystrokes I use are the ones I laid out for you. vi can do a lot more than what I've shown you. If you want to learn more feel free to google vi to augment the information I've provided you.

---

### Post by flyguy97 on 2008-11-09
You also asked about where to put the```
$ sudo make
``` Once you are done editing the config file you should be in the root of the driver directory if you followed my directions. You can enter it after you use the [:][w][q][Enter] keys to save the file. So the short answer is no, you do not need to open another terminal window.

---

### Post by J Caffrey on 2008-11-10
I've got as far as step 9. When I type in sudo echo rt2860sta >> /etc/modules. I get bash: /etc/modules: Permission denied. What do I do now? Will I have to start all over again or am I missing something obvious? I don't know whether to continue to the next step now.I've just realised that I had reinstalled network manager to re-download the driver and forgot to remove it..... am I snookered??

---

### Post by flyguy97 on 2008-11-10
I apologise, this doesn't work for me either. It should have added the line rt2860sta to the end of the /etc/modules file. But we can always use our trusty vi editor to do the same. Edit /etc/modules with vi.
```
$ sudo vi /etc/modules
```
And add rt2860 to the end of the file. To do this go to the last character on the last line and press [a] and go to a new line by pressing [Enter]. Type rt2860sta and press [:][w][q][Enter]. This will satisfy step 9. Again, sorry for the confusion. And no, you will not need to start over. What you are doing in this step is telling the kernel to load the rt2860sta module each time it loads.

---

### Post by flyguy97 on 2008-11-10
As for your question about NetworkManager, you should remove it as soon as possible. Your wireless card was not configured to work with NetworkManager and NetworkManager will conflict with the above setup. No need to start over though, Linux can be very forgiving, at least sometimes.

---

### Post by J Caffrey on 2008-11-10
Got to the end worked out encrypytion for my ssid/passphrase combination.Double checked  everything restarted computer.........Nothing!!! No wireless light...no internet.I'm going to bed now very very dissapointed....All suggestions at this stage gratefully received.

---

### Post by flyguy97 on 2008-11-13
After a fresh reboot what is the output from 
```
$ sudo iwlist scan
```

---

### Post by YogiNL on 2008-11-13
For the people (like me) who are running a command line system: You need the headers installed also. I guess I mentioned it since I do not know if this is already installed when using gnome or something.

Well. I got mine working without authentication sofar. I followed the steps posted by the poster but I am having a question related to command line only install:

Accoring to the howto I have to set HAS_WPA_SUPPLICANT to yes in de config.mk file. Since there is no mention of wpa_supplicant in the rest of the howto I wonder if this is needed at all. I suspect that this driver has wpa build in already.

Am I correct? If so I should change the HAS_WPA_SUPPLICANT=y to no again and reinstall the driver?

Owww btw another tip: When doing the make && make install, make sure you are root. I got permission denied messages when using sudo. so do a sudo su.

---

### Post by flyguy97 on 2008-11-13
Unless you are trying to get this to work with network manager, follow exactly what I have in my walkthrough according to Ralink's instructions
```

3> In os/linux/config.mk
        define the GCC and LD of the target machine
        define the compiler flags CFLAGS
        modify to meet your need.
        ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
           => #>cd wpa_supplicant-x.x
           => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
        ** Build for being controlled by WpaSupplicant with Ralink Driver
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
           => #>cd wpa_supplicant-0.5.7
           => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

```

So from what I can gather from this exert, yes you do need to have HAS_WPA_SUPPLICANT=y if you want wpa support. It sounds like it is built into the driver but you need to enable it before the build to have compiled into the kernel module. When you setup your WPA key did you use your AP's SSID in the wpa_passphrase command as in step 11? When I initially set mine up I was lazy and just put some random characters as a placeholder but later it came to my attention the algorithm to get you WPA key is dependent on the SSID you supply, anything other than your SSID will not yield your WPA key. Also, make sure you restart your computer, just restarting networking has no affect.

It is curious why you got a permission denied error during the make process, the sudo command is supposed to give you root access to everything.

> **YogiNL said:**
> For the people (like me) who are running a command line system: You need the headers installed also. I guess I mentioned it since I do not know if this is already installed when using gnome or something.

Well. I got mine working without authentication sofar. I followed the steps posted by the poster but I am having a question related to command line only install:

Accoring to the howto I have to set HAS_WPA_SUPPLICANT to yes in de config.mk file. Since there is no mention of wpa_supplicant in the rest of the howto I wonder if this is needed at all. I suspect that this driver has wpa build in already.

Am I correct? If so I should change the HAS_WPA_SUPPLICANT=y to no again and reinstall the driver?

Owww btw another tip: When doing the make && make install, make sure you are root. I got permission denied messages when using sudo. so do a sudo su.

---

### Post by J Caffrey on 2008-11-13
I did the scan.It looks kike the card is "seeing" my network.There are 3 networks around me.I have my ssid named.Its called Cell 02 - Address 00:0F:CC:2D:97:88
                                                    ESSID:"Network name"
                                                    Mode:Managed
                                                    Channel:7 
                                                    Quality:100/100 Signal level:-42 dbm Noise level:-97dbm
Encryption key: on
Bit Rates:22 Mb/s
IE:WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
It also gives info for the other Two networks that are transmitting close by.
I'm very close now I think!!

---

### Post by flyguy97 on 2008-11-13
A few things to check, first does the channel entry from your iwlist scan match the channel entry you have in your RT2860STA.dat file? When you generated your WPAPSK key did you use the same entry that is found in your ESSID entry from your iwlist scan, and is your wireless mode set correctly, the following possibilities are below:

```

@> WirelessMode=value
        value
                0: legacy 11b/g mixed
                1: legacy 11B only
                2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
                3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
                4: legacy 11G only
                5: 11ABGN mixed
                6: 11N only
                7: 11GN mixed
                8: 11AN mixed
                9: 11BGN mixed
           10: 11AGN mixed

```
> **J Caffrey said:**
> I did the scan.It looks kike the card is "seeing" my network.There are 3 networks around me.I have my ssid named.Its called Cell 02 - Address 00:0F:CC:2D:97:88
                                                    ESSID:"Network name"
                                                    Mode:Managed
                                                    Channel:7 
                                                    Quality:100/100 Signal level:-42 dbm Noise level:-97dbm
Encryption key: on
Bit Rates:22 Mb/s
IE:WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
It also gives info for the other Two networks that are transmitting close by.
I'm very close now I think!!

---

### Post by flyguy97 on 2008-11-13
This is also just a general statement when it comes to changing anything in the RT2860STA.dat file. Reboot every time you make a change. You cannot simply restart networking, it does not work, you MUST restart. When I finally got my card to work it was only after I pretty much gave up and shut off my computer and when subsequently rebooted some time later that I found out my wireless was working.

---

### Post by Steve1961 on 2008-11-13
I know it's always preferable to use a native linux driver.  However, I have this wireless chipset in my eeepc 1000h and can confirm that the windows drivers work fine in ndiswrapper and let me connect to my wireless network with network-manager and wpa2 encryption without an issue.

---

### Post by flyguy97 on 2008-11-13
I've used ndiswrapper in the past (not with this chipset) but I was concerned it may cost me some performance as I would be using a windoze binary, what is your experience?

---

### Post by Steve1961 on 2008-11-13
> **flyguy97 said:**
> I used ndiswrapper in the past (not with this chipset) but I was concerned it may cost me some performance as I would be using a windoze binary, what is your experience?


can't tell the difference, it works fine, and certainly no noticeable drop in performance.

---

### Post by J Caffrey on 2008-11-13
I changed channel in dat file to 7 to match router channel 7.No joy.This is whats in the dat.file.
Country Region=1
Country RegionABand=7
Country Code=IE
ChannelGeography=1
SSID=name
NetworkType=Infra
WirelessMode=9
Channel=7
skip default values..
AuthMode=WPA2PSK
EncrypType=TKIP
WPAPSK=combination of ssid&pass phrase.
According to my router the encryption type is WPA-PSK not the other type of encryption which the Router calls WPA-802.1x.Should I change auth mode to WPAPSK?
I'm on line!!!!! JOY JOY JOY It was the AuthMode that made the difference!!!!
Get some sound now and I'm Laughing!!!

---

### Post by J Caffrey on 2008-11-13
I changed AuthMode to WPAPSK and it worked perfectly.Many many thanks to Flyguy97.......Do you know anything about sound??

---

### Post by MCBTunes on 2008-11-13
I need some help if you don't mind flyguy.

I tried the walk through but failed miserably and now I've lost my wired connection too :(.

Is there anyway I can undo my changes and start fresh? Initially I didnt delete my network manager initially because I wanted to hold on to my wired connection. 

I also kinda skimmed the last two steps because I only knew some of the information. 

Can I uninstall this thing and have all my files revert to default or something or what should I do?

thanks.

Edit: Ok I switched back what I could remember of the /etc/ changes and I have my wired connection back. I think I got everything except the /Wireless/ changes back to normal.

Now how do I uninstall the driver?

---

### Post by flyguy97 on 2008-11-14
If you want to disable the driver do the following commands.

1. Make sure the driver is not in use.

```
$ sudo ifconfig ra0 off
```
```
$ sudo modprobe -r rt2860sta
```

2. Edit the /etc/modules file to make sure it won't try to load next time you start up your computer.

```
$ sudo vi /etc/modules
``` and remove the line that reads rt2860sta.

This is all you will need to do to remove the file. Now you can re-compile and give it another go. Let me know who it works out for you.

As a side note: This setup will never work if NetworkManager is installed. Most applications, especially Firefox, look for a connection through NetworkManager, if it cannot find one it assumes the network is offline and will refuse to try to connect. If NetworkManager is removed than it will actually test for a network connection before insisting it is offline. It would be great if the package managers for Firefox and other offending packages could at least test for a network even if NetworkManager is not connected.

> **MCBTunes said:**
> I need some help if you don't mind flyguy.

I tried the walk through but failed miserably and now I've lost my wired connection too :(.

Is there anyway I can undo my changes and start fresh? Initially I didnt delete my network manager initially because I wanted to hold on to my wired connection. 

I also kinda skimmed the last two steps because I only knew some of the information. 

Can I uninstall this thing and have all my files revert to default or something or what should I do?

thanks.

Edit: Ok I switched back what I could remember of the /etc/ changes and I have my wired connection back. I think I got everything except the /Wireless/ changes back to normal.

Now how do I uninstall the driver?

---

### Post by flyguy97 on 2008-11-14
I am so glad you got it to work! I know it can be an agonising process. Please let me know which part of the instructions were difficult to understand, let's make this better for the next guy.

As for your question about sound, feel free to hit my up through either the private email/chat thing through my profile or start a thread and I will support you from there. 

> **J Caffrey said:**
> I changed AuthMode to WPAPSK and it worked perfectly.Many many thanks to Flyguy97.......Do you know anything about sound??

---

### Post by TBerk on 2008-11-14
1st off, many thanks for this thread it is very concise and specific to my hardware.

I have started another thread:

[http://ubuntuforums.org/showthread.php?t=981789](http://ubuntuforums.org/showthread.php?t=981789)

which asks "[HOWTO] Generate a WPA2 (HEX) passphrase from a wired, Windows connection?" .

Basically I get to step 11 and get hung up trying to convert the known passphrase in the WPA2-PSK (TKIP+AES) based wireless router to a hex version my Linux based system can understand.

The Ubuntu system is not conveniently located to connect via 100bT (wire) so I'm trying to configure it from scratch and once connected go about getting patches, etc.

Any help in converting a Windows (ascii) based passphrase to a Linux/Ubuntu/ndiswrapper/HEXadecimal based one would be great.

TBerk

---

### Post by flyguy97 on 2008-11-14
My instructions may not be as clear as they should be. The command you will run does not require you to connect to any network or access point in any way. Run wpa_passphrase and it will generate the WPAPSK for you. 

```
$ wpa_passphrase SSID_OF_AP CLEARTEXT_OF_PASSPHRASE
```
Where SSID_OF_AP is the broadcast name of your wireless access point (a.k.a. router) and CLEARTEXT_OF_PASSPHRASE is the human-readable version of your wireless key. Please let me know if this helps. Also, make sure NetworkManager is removed or it will not work.

As an alternative, if you are using an ASCII passphrase it may be used directly it looks like. Here is an exert from the readme file for the driver.

```
@> WPAPSK=value              	
	value
		8~63 ASCII  		or 
		64 HEX characters
```


> **TBerk said:**
> 1st off, many thanks for this thread it is very concise and specific to my hardware.

I have started another thread:

[http://ubuntuforums.org/showthread.php?t=981789](http://ubuntuforums.org/showthread.php?t=981789)

which asks "[HOWTO] Generate a WPA2 (HEX) passphrase from a wired, Windows connection?" .

Basically I get to step 11 and get hung up trying to convert the known passphrase in the WPA2-PSK (TKIP+AES) based wireless router to a hex version my Linux based system can understand.

The Ubuntu system is not conveniently located to connect via 100bT (wire) so I'm trying to configure it from scratch and once connected go about getting patches, etc.

Any help in converting a Windows (ascii) based passphrase to a Linux/Ubuntu/ndiswrapper/HEXadecimal based one would be great.

TBerk

---

### Post by YogiNL on 2008-11-15
> **flyguy97 said:**
> Unless you are trying to get this to work with network manager, follow exactly what I have in my walkthrough according to Ralink's instructions
```

3> In os/linux/config.mk
        define the GCC and LD of the target machine
        define the compiler flags CFLAGS
        modify to meet your need.
        ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
           => #>cd wpa_supplicant-x.x
           => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
        ** Build for being controlled by WpaSupplicant with Ralink Driver
           Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
           => #>cd wpa_supplicant-0.5.7
           => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

```

So from what I can gather from this exert, yes you do need to have HAS_WPA_SUPPLICANT=y if you want wpa support. It sounds like it is built into the driver but you need to enable it before the build to have compiled into the kernel module. When you setup your WPA key did you use your AP's SSID in the wpa_passphrase command as in step 11? When I initially set mine up I was lazy and just put some random characters as a placeholder but later it came to my attention the algorithm to get you WPA key is dependent on the SSID you supply, anything other than your SSID will not yield your WPA key. Also, make sure you restart your computer, just restarting networking has no affect.

It is curious why you got a permission denied error during the make process, the sudo command is supposed to give you root access to everything.

Thanks for the reply. I am currently not at home so I am not able to go on with my quest to get my wireless working using WPA. when I am home I will reinstall my command line install, also I will try to see if I get the permission denied message again when make && make install the driver and will post it here.

More from me on sunday..

---

### Post by flyguy97 on 2008-11-16
Instead of using sudo every time you need root privileges you can use: 
```
$ sudo su
```
This will log you in as root. Be sure to omit the sudo in front of the commands. It will no longer be necessary as you will be logged in as root.

> **YogiNL said:**
> Thanks for the reply. I am currently not at home so I am not able to go on with my quest to get my wireless working using WPA. when I am home I will reinstall my command line install, also I will try to see if I get the permission denied message again when make && make install the driver and will post it here.

More from me on sunday..

---

### Post by YogiNL on 2008-11-18
ok took a bit longer due to some funny circumstances which are too embarassing to mention here but here it is:

> **flyguy97 said:**
> Instead of using sudo every time you need root privileges you can use: 
```
$ sudo su
```
This will log you in as root. Be sure to omit the sudo in front of the commands. It will no longer be necessary as you will be logged in as root.

I did that to install it.. The funny part is this: If I do a make and make install seperate from eachother ( so first a make <enter> and after that is finished a make install) it works. If I do it in one go it fails:

```
rm -rf /etc/Wireless/RT2860STA
rm: cannot remove `/etc/Wireless/RT2860STA/RT2860STA.dat': Permission denied
make[1]: *** [install] Error 1

```

This could have happend because I forgot to change the config.mk file and did it a second time, but removing a directory using sudo should not give this error i believe. 
I got it working though. Now on to getting this WPA to work.

---

### Post by flyguy97 on 2008-11-18
You'll have to let me know how it goes. Also, this is for anyone, I would like to know if there is any interest in getting the 2860 chipsets to work with NetworkManager, if so I will give it a go and post my results.

> **YogiNL said:**
> ok took a bit longer due to some funny circumstances which are too embarassing to mention here but here it is:



I did that to install it.. The funny part is this: If I do a make and make install seperate from eachother ( so first a make <enter> and after that is finished a make install) it works. If I do it in one go it fails:

```
rm -rf /etc/Wireless/RT2860STA
rm: cannot remove `/etc/Wireless/RT2860STA/RT2860STA.dat': Permission denied
make[1]: *** [install] Error 1

```

This could have happend because I forgot to change the config.mk file and did it a second time, but removing a directory using sudo should not give this error i believe. 
I got it working though. Now on to getting this WPA to work.

---

### Post by YogiNL on 2008-11-20
I tried everything. only issue I might still have is the wireless router I use.. (Draytek 2600G) This router is my old router which I wanted to use to create a seperate network. I will try to get it to work with my new adsl2plus modem. Maybe the router just does not work well.

I will start all over and make a step by step desription of what I did. From install till the point it all should work. be back with you later.

---

### Post by YogiNL on 2008-11-20
Ok... I did a total reinstall and managed again to get an unencrypted connection. Below the steps I took:

**Step 1:**

I used the alternate install cd. I chose for a command-line install mode. (F4 at the screen where you have to choose what to install after the pc booted from the cd)

**Step 2:**

I am not going to discuss the installation itself in detail. Just did a basic install with default choices. after the installation I did a:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

**Step 3:**

I have this habbit of installing some basic apps on a clean system. 

```
 apt-get install ssh screen hellanzb irssi
```

Just added it cause it represents the situation.

**Step 4:**

I use putty to connect remotely to the system. Connecting remotely comes in very handy cause then you can copy/paste commands from howto's easier and you can lay back on the couch configuring everything watching tv if your system is somewhere else. call me lazy.

**Step 5:**

Here we start to go and install the software we need to install the wireless driver. For my command-line install I need the following extra software to be able to install the driver:

```
sudo apt-get instal build-essential linux-headers-`uname -r`
```
**Step 6:**

Download the driver from Ralink and put it somewhere you want. I put it in my home directory.
```
wget http://www.ralinktech.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```

and extract it

```
tar xvjf 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2
```
**step 7:**

Change the config.mk file. 

**Step 8:**

Time to install the driver.

just to be sure I am going for a sudo su before installing. (See why in previous posts)

Install the module:
```
make && make install
```

Install Kernel Module:

```
modprobe rt2860sta
```

Make sure that the driver starts at bootup:

```
echo rt2860sta >> /etc/modules
```

**Step 9:**

Configuring the interfaces file. Since I first want to make sure it works without encryption to make sure (and to show) that the wireless connection works I am not totaly going to follow the description at first.

my interfaces file at this point:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The wireless network interface
auto ra0
iface ra0 inet dhcp

```
before people are going to say that leaving the eth0 interface open might cause problems: The wireless network the eeebox is going to connect to is totaly seperate from my normal network and has a totally different ip-range. 10.0.0.0 instead of 192.168.1.0 my normal network has. it also makes it able to keep connecting to the eeebox if the wireless connection does not work.

**Step 10:**

Change the /etc/Wireless/RT2860STA/RT2860STA.dat file.

I change the following values:

```
CountryCode=NL
SSID=Badaboom
Channel=6  (checked this in my router)
```

I am not sure what to put in Wirelessmode in my case. It is set to 9 right now. But I do not know if this has any influence. If it does the connection should not work. If it doesn't.. well we will see.
**Step 11:**

Install wireless-tools to check if everything works. apt-get ```
install wireless-tools
```

**Step 12: **

```
reboot
```


**result:**

A working unencrypted connection:

ifconfig :

```
ra0       Link encap:Ethernet  HWaddr 00:15:af:e6:c0:d9
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fee6:c0d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:413513 (413.5 KB)  TX bytes:1084 (1.0 KB)
          Interrupt:17

```
iwconfig:

```
ra0       RT2860 Wireless  ESSID:"Badaboom"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0C:20:03:1D:2C
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-56 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sofar so good.. Any comments are welcome at this point.. Will post my wpa tryout later..

Well here is the rest:

**Step 13:**

I made a backup of my RT2860STA.dat file.
Installed wpasupplicant for the passphrase utility

(At the moment I am starting to wonder if I should have installed this before installing the wireless driver. Any comments are welcome on this)


**Step 14:**

create passphrase

Change RT2860STA.dat file

```
vi /etc/Wireless/RT2860STA/RT2860STA.dat
```

Changed the following values in the file:

```
AuthMode=WPA2PSK
EncrypType=TKIP
WPAPSK=67ea3c9ff4da7f209f73983ea5497b5038ffbfd615906fdb1c00a5c3d64fa103
```

**Step 15:**
I changed the settings of my router with the following settings:

I changed the Encryption type to WPA/PSK only
I set the possibility for encryption to WPA or WPA2 (so both are possible)
I added the HEX key. I had to add 0x in front of the key to make it work.

**Step 16:**

reboot the eeebox


The results are not satisfying. As expected the connection won't come up. Any info is welcome

---

### Post by scarf on 2008-11-21
i was able to get the wifi working with network-manager by following this post:

[http://ubuntuforums.org/showpost.php?p=5114684&postcount=41](http://ubuntuforums.org/showpost.php?p=5114684&postcount=41)

but, i am only connected at 54 Mb/s. :(

how to get connected at 300 Mb/s?

---

### Post by TJX09 on 2008-11-21
Ok i just installed Ubuntu Intrepid last week to try it out and purchase a rosewill wireless PCI wireless card because 56k modem doesn't work in ubuntu, Well the wireless PCI card have ralink chipset RT2561/RT61 the card seem to work great since I connected to my neighbors internet connection. The wireless pci card include a CD with a linux driver "2007_1003_RT61_Linux_STA_v1.1.1.0" or option to download the latest one "2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2" in website. What I wanted to know is how do i install the RALINK RT61 Wireless Card linux driver which is included on CD or the one i downloaded 2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2 ?? 


[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)
	07/23/2008	1.1.2.2

---

### Post by scarf on 2008-11-21
TJX09, i would recommend downloading the one from their website, to ensure you have the latest version.

just save the file to your desktop, then double-click it to open in the archive manager.  extract it too to your desktop.

go into that newly created directory and then into the Module directory and open the README file and have a look over it.  the instructions to build/install the driver are there, and pretty technical for a new user.  you will need to open up a terminal (applications > accessories > terminal), and then type "cd Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module" (that is step 1 in the "build instructions") and then follow the rest of the instructions in the README.

unfortunately, this thread is for the RT2860 chipset, which you do not have.  so, once you have gotten to the README and you still have questions, maybe it would be best to search for a RT2561/RT61 thread or start a new one.

best of luck

---

### Post by flyguy97 on 2008-11-21
The fact I couldn't get anything faster than 54Mb/s was the reason for the post. For some reason NetworkManager will not connect at anything faster than 54Mb/s. If you follow the instructions on these pages you should be able to at least triple your connect speeds. Of course 99% of users will not see a difference in their internet speeds since the fastest speeds I have heard of for residential only reach up to about 15Mb/s, if you have faster please let me know. However, if you transfer a lot of files or stream video (like me), the added bandwidth can really pay-off. 

> **scarf said:**
> i was able to get the wifi working with network-manager by following this post:

[http://ubuntuforums.org/showpost.php?p=5114684&postcount=41](http://ubuntuforums.org/showpost.php?p=5114684&postcount=41)

but, i am only connected at 54 Mb/s. :(

how to get connected at 300 Mb/s?

---

### Post by flyguy97 on 2008-11-21
Just for your knowledge, there is a package for your chipset in the Ubuntu repos called rt2500-source. I don't know what you would have to do with it after download but I think it's safe to assume the repo folks have already tested the source on Ubuntu before submitting.

> **TJX09 said:**
> Ok i just installed Ubuntu Intrepid last week to try it out and purchase a rosewill wireless PCI wireless card because 56k modem doesn't work in ubuntu, Well the wireless PCI card have ralink chipset RT2561/RT61 the card seem to work great since I connected to my neighbors internet connection. The wireless pci card include a CD with a linux driver "2007_1003_RT61_Linux_STA_v1.1.1.0" or option to download the latest one "2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2" in website. What I wanted to know is how do i install the RALINK RT61 Wireless Card linux driver which is included on CD or the one i downloaded 2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2 ?? 


[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)
	07/23/2008	1.1.2.2

---

### Post by flyguy97 on 2008-11-21
If you don't mind please post a copy of your RT2860STA.DAT file with all the necessary fields protected for your privacy.

> **YogiNL said:**
> 
**Step 13:**

I made a backup of my RT2860STA.dat file.
Installed wpasupplicant for the passphrase utility

(At the moment I am starting to wonder if I should have installed this before installing the wireless driver. Any comments are welcome on this)


**Step 14:**

create passphrase

Change RT2860STA.dat file

```
vi /etc/Wireless/RT2860STA/RT2860STA.dat
```

Changed the following values in the file:

```
AuthMode=WPA2PSK
EncrypType=TKIP
WPAPSK=67ea3c9ff4da7f209f73983ea5497b5038ffbfd615906fdb1c00a5c3d64fa103
```

**Step 15:**
I changed the settings of my router with the following settings:

I changed the Encryption type to WPA/PSK only
I set the possibility for encryption to WPA or WPA2 (so both are possible)
I added the HEX key. I had to add 0x in front of the key to make it work.

**Step 16:**

reboot the eeebox


The results are not satisfying. As expected the connection won't come up. Any info is welcome

---

### Post by YogiNL on 2008-11-22
> **flyguy97 said:**
> If you don't mind please post a copy of your RT2860STA.DAT file with all the necessary fields protected for your privacy.


WOW HALLELUJAH!!!! I thought well lets change it from WPA2PSK to WPAPSK and it worked.

I do think however that this was just luck I had. let me explain why it did not work in the past with (exactly) the same settings.

I have two routers one adsl2+ router which is connected to my dsl line. This router has ip-address 192.168.1.254. It gives out addresses through dhcp in the 192.168.1.0 range. This router sucks though it is a Zyxel...:-(

My other router is a great router (Draytek 2600G) but does not work with my adsl2+ dsl connection. This router is giving out ip-adresses in the range 10.0.0.0. These routers are not connected. This router is standalone and the only thing that is connecting to it is my eeebox through a wireless connection. The thing is, that this router supports 2 dhcp subnets. And one of those is ALSO 192.168.1.0. That is when I do a:

```
vi /etc/init.d/networking restart
```

it shows :

```
Listening on LPF/ra0/00:15:af:e6:c0:d9
Sending on   LPF/ra0/00:15:af:e6:c0:d9
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 10.0.0.1 from **[COLOR="Red"]192.168.1.1[/COLOR]**
DHCPREQUEST of 10.0.0.1 on ra0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.1 from 192.168.1.1
bound to 10.0.0.1 -- renewal in 112172 seconds.
```

I think in the cases that it did not work that the dhcp process was confused. Somehow I think it is sending a dhcp broadcast and since the same subnet is on the first router something went wrong. In the case that it worked the dhcp server on the second router responded faster. I can imagine the address in red above was the ip-address of the other router in the past.. 

Just a guess ofcourse... I am going to change the draytek to another subnet so it does not clash in the future..

Thank you very much for the help and support getting this to work. One more question:

Since I have to lend my draytek to someone else I want it to connect to my Zyxel which (I think) does not support the Hex values. Can I just change it to a plain password on the pc and the router?

---

### Post by sugrbear on 2008-11-23
The native Linux drivers for rt2860 based chipsets are available on the Ralink website, and all you have to do is build them. (ndiswrapper really should only be used for network hardware for which there are no native drivers.) 

Contrary to some posts I've seen, Network Manager works amazingly with these drivers. That has been my own experience anyway. The tarball includes simple instructions for building and installing the rt2860.ko and a couple of simple edits are required before building to ensure Network Manager compatibility.

---

### Post by flyguy97 on 2008-11-24
I agree with your note about network manager to a point. The ability to build and install the drivers was straight-forward. It even worked with network manager on the first go. My only problem was I couldn't get anything faster than g speeds. I purchased my n card to get n speeds. When I compile without network manager support I am able to connect at full n speeds, usually around 110 Mb/s.

> **sugrbear said:**
> The native Linux drivers for rt2860 based chipsets are available on the Ralink website, and all you have to do is build them. (ndiswrapper really should only be used for network hardware for which there are no native drivers.) 

Contrary to some posts I've seen, Network Manager works amazingly with these drivers. That has been my own experience anyway. The tarball includes simple instructions for building and installing the rt2860.ko and a couple of simple edits are required before building to ensure Network Manager compatibility.

---

### Post by scarf on 2008-11-24
i would appreciate more specificity.

> **sugrbear said:**
> Contrary to some posts I've seen, Network Manager works amazingly with these drivers. That has been my own experience anyway. The tarball includes simple instructions for building and installing the rt2860.ko and a couple of simple edits are required before building to ensure Network Manager compatibility.

are you getting connected at N speeds? or just 54 Mb/s?  if you are connecting at higher speeds, please explain more detail of how we might achieve this, since it seems most of us are only getting 54 Mb/s with the network manager app.

and what simple edits are you referring to to ensure network manager compatibility?

also, there are reports the network manager will not remember the password (maybe only for WPA2 connection).  i have experienced this.  so, if, for example, when you reboot ubuntu, will the network manager remember the password for you?  it didn't remember mine for a few reboots but i believe after this last reboot it connected automatically.... so there is definitely some strangeness still around.

thanks

---

### Post by scarf on 2008-11-29
it seems, the new kernel update, 2.6.24.22-generic, has totally wiped out the wifi connectivity.

```

$ lshw -C network
  *-network:1 UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by flyguy97 on 2008-11-29
With new kernels you may have to go through the whole process of installing from source. Be sure to back up your /etc/Wireless/RT2860STA/RT2860STA.dat file for convenience before starting. If kernel updates aren't that important to you it may be behove you to disable them through apt. Something like the following might be a solution that may apply. [http://ubuntuforums.org/showthread.php?t=636915]("http://ubuntuforums.org/showthread.php?t=636915")

> **scarf said:**
> it seems, the new kernel update, 2.6.24.22-generic, has totally wiped out the wifi connectivity.

```

$ lshw -C network
  *-network:1 UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by scarf on 2008-12-05
> **flyguy97 said:**
> With new kernels you may have to go through the whole process of installing from source. Be sure to back up your /etc/Wireless/RT2860STA/RT2860STA.dat file for convenience before starting. If kernel updates aren't that important to you it may be behove you to disable them through apt. Something like the following might be a solution that may apply. [http://ubuntuforums.org/showthread.php?t=636915]("http://ubuntuforums.org/showthread.php?t=636915")

thank you.  after recompiling and rebooting, the wifi is working again.

although, i am not using the RT2860STA.dat file.  as i understand, that is amongst the changes to the default instructions in order to make the wifi work with the network manager applet? or have i missed something?

i also did upgrade to ubuntu-8.10, currently running linux-2.6.27-9-generic, and the wifi is still working, and still reporting speeds of 54 Mb/s.  also i did notice some strange behavior regarding my load average.  the average continued to increase up to at least 20 and decreased as soon as i plugged in a cat-5 cable, thus switching network interfaces.  as i unplugged the cat-5 and switched back to wifi, the average started to increase again.  after about 20-30 minutes, the average went back down to 0-1.

---

### Post by autocrosser on 2008-12-07
Just so everyone knows---I have got the 2860 driver from this PPA to work with the 2.6.28 kernel series:

#Ralink wireless drivers
deb [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main

So we are about to include the 2860 driver in the DEFAULT kernel load---

Talking to Stéphane Graber--

<Quote>
[INDENT]> Greetings Stéphane--
>
> Well--I feel rather silly---I un-installed the DKMS build, booted
> into the .28 kernel & rebuilt/installed the module & the driver
> works very well---It took longer than I would like to admit to
> remember that moving from .27 to .28 would require a rebuild
> against the .28 kernel :)--So I can report that the PPA for
> Intrepid can & should be included in Jaunty sources as well.
>
> Cheers!!!! Dean Loros autocrosser@ubuntuforums
[/INDENT][FONT=monospace]
[/FONT]Hehe, ok :) It's good to know that it works with .28 and we have now have plenty of times to get it included in Ubuntu. I won't do it (I don't even have the hardware :)) but there is a lot of pressure on the kernel team to do so.

Stéphane


So, it looks like the driver will be included by Jaunty release.:popcorn:

---

### Post by flyguy97 on 2008-12-08
What speeds are you getting? Seems like if you try to use NetworkManager you can only get g speeds.

> **autocrosser said:**
> Just so everyone knows---I have got the 2860 driver from this PPA to work with the 2.6.28 kernel series:

#Ralink wireless drivers
deb [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main

So we are about to include the 2860 driver in the DEFAULT kernel load---

Talking to Stéphane Graber--

<Quote>
[INDENT]> Greetings Stéphane--
>
> Well--I feel rather silly---I un-installed the DKMS build, booted
> into the .28 kernel & rebuilt/installed the module & the driver
> works very well---It took longer than I would like to admit to
> remember that moving from .27 to .28 would require a rebuild
> against the .28 kernel :)--So I can report that the PPA for
> Intrepid can & should be included in Jaunty sources as well.
>
> Cheers!!!! Dean Loros autocrosser@ubuntuforums
[/INDENT][FONT=monospace]
[/FONT]Hehe, ok :) It's good to know that it works with .28 and we have now have plenty of times to get it included in Ubuntu. I won't do it (I don't even have the hardware :)) but there is a lot of pressure on the kernel team to do so.

Stéphane


So, it looks like the driver will be included by Jaunty release.:popcorn:

---

### Post by autocrosser on 2008-12-08
I made /etc/Wireless/RT2860STA & edited the RT2860STA.dat file like thus:

#The word of "Default" must not be removed
Default
WirelessMode=6

As I have a N router & set it to N transmit only--I get 130mb transmit with Network Manager.....

N speed will be available upon a reboot or restarting NM...I need to do more to see if it can be boosted to 300mb, but 130 is better than 54....

---

### Post by autocrosser on 2008-12-09
For more info about the RT2860STA.dat file--You can use either 6 (N only) or 9 (B,G & N) & get N speeds upon reboot (or logout/in)--I have tested both & they work---looks like the driver defaults to present G speeds for compatibility. You can insert as much or as little into the file--looks like "Default" is the only requirement.

There is a fairly good info file within the driver--I had to guess a bit to get to here....

---

### Post by scarf on 2008-12-10
thanks for the info!  i can confirm that i am now connected at a speed higher than 54 Mb/s (according to network manager app).

> **autocrosser said:**
> 
As I have a N router & set it to N transmit only--I get 130mb transmit with Network Manager.....

N speed will be available upon a reboot or restarting NM...I need to do more to see if it can be boosted to 300mb, but 130 is better than 54....

this may be simply because the network manager app is only reporting the speed of one of the channels (send or receive), so it is very likely that you are actually connected at 260 Mb/s.  i think you will only get 300 Mb/s if you are right next to the router.

is there any way to test this speed within our local network?  any better way than perhaps just copying a file over the network and timing it, etc.?

i would also like to report, that using the RT2860STA.dat file with just those two lines (Defualt and WirelessMode=6), the network manager app now seems to remember the password to my WPA2 network and connect automatically!

so, perhaps it is necessary to have that RT2860STA.dat file in place with at least the one line (Default), and the rest of the options not defined in the file will be handled by network manager applet.  so the two can work together essentially.

---

### Post by autocrosser on 2008-12-10
Agreed---I've not had any problems with password with the file edited as per my post above--also---good point about the transmit/receive idea--NM is a little "dumb" about things--that could be one of them (for another--run the Network Connection applet & NM at the same time--NM uses different metrics & reports a much lower signal strength--so miss-reading the total signal is well within the margin of error :)  ).

---

### Post by scarf on 2008-12-12
well, i take that back.  today, i woke up to my wifi disconnected and the network manager app waiting for me to click the "connect" button in the password dialog box.  it had the password saved and filled in already, but i still had to click connect.  after clicking connect, nothing happened.  then i clicked on the network manager icon and chose my wireless network from the list, to which it then automatically connected to.

maybe it is only after a fresh bootup (and/or login) that the connection is established automatically?

i right-clicked on the icon and chose "edit connections" and saw my wifi connection in the wireless tab.  it's the only wifi connection i have, so it's at the top of the list.  it's preceded by the word "Auto" and, if i click on edit button, the option "connect automatically" is checked.

perhaps there is some option i need in the RT2860STA.dat file that will assist in the network actually (re-)connecting automatically?  will research this more later....

---

### Post by littlefluffy on 2008-12-12
I would like to keep Network Manager or something similar, as I am using this adapter on my Eee PC and want something that will detect networks that I can connect to and generally make networking easy for me. Is there a way to get my wireless adapter working with Network Manager?

---

### Post by scarf on 2008-12-12
littlefluffy, i was able to get my wifi working together with the network manager by following this post,

[http://ubuntuforums.org/showpost.php?p=5114684](http://ubuntuforums.org/showpost.php?p=5114684)

(don't use the download link there, it is to an older version of the driver.  get the latest version here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html))

however, we have realized it might be best to not delete the /etc/Wireless/RT2680STA/RT2860STA.dat file.  instead, just empty out the file except for the following lines, for now:

```

#The word of "Default" must not be removed
Default
WirelessMode=5

```

the WirelessMode=5 will give you ABGN speeds, if you want just N, use 6.  for other options, see the README_STA file contained with the driver download.

and, i'm pretty sure you need to reboot after installing the driver.

---

### Post by autocrosser on 2008-12-12
And I'm working hard to get the driver in default for the Jaunty release, so we don't have to go thru this any more--I will keep everyone updated with info as it becomes available--I hope to be talking to the kernel devs within the next couple of weeks......

---

### Post by autocrosser on 2008-12-27
New information---been working with the RT2860STA.dat file & have found the combo for unlocking "N" speeds :)

1. you need to have your router run in "N" only.
2. create the /etc/Wireless/RT2860STA/RT2860STA.dat  & include only the file as I have edited it......

#The word of "Default" must not be removed
Default
WirelessMode=6
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0


Screenshot of result :)

---

### Post by scarf on 2009-01-11
while i definitely see higher speeds reported in the network manager app, my wifi connection has become sporadic and unstable.

i am using, however, a linksys wrt600n router with beta dd-wrt firmware.  might that have something to do with it?

here is a link to a discussion of that firmware, [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947)

however, before modifying the RT2860STA.dat to include all those extra options, my connection was very stable.  so i think it might have more to do with the modifications to th RT2860STA.dat file.

if anyone has any suggestions for other settings that might address this, great, please post away.  i'll look into it more.

in the mean time, i might like to undo those changes to the RT2860STA.dat file and commit them.  once i have modified the RT2860STA.dat, is there a way to commit them without logging out or rebooting the machine?  something like 'ifconfig ra0 down; ifconfig ra0 up' maybe?

---

### Post by kzm. on 2009-01-11
I have a very weird problem. I have a sitecom 300N wl-181 working with the ralink driver RT2860STA:

```
lshw -C network
 *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: a
       bus info: pci@05:0a.0
       logical name: ra0
       version: 00
       serial: 00:0c:f6:3e:e1:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 multicast=yes wireless=RT2860 Wireless
       resources: iomemory:fc510000-fc51ffff irq:201
```

I find my router running ```
iwlist ra0 scan
```.


But when i do ```
sudo iwconfig ra0 essid "whatever"
``` and look at the card again i see its not set!!?? I really do not under stand this... can anyody advise me on this??

```
sudo iwconfig ra0 
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.442 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-256 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by autocrosser on 2009-01-11
> **scarf said:**
> while i definitely see higher speeds reported in the network manager app, my wifi connection has become sporadic and unstable.

i am using, however, a linksys wrt600n router with beta dd-wrt firmware.  might that have something to do with it?

here is a link to a discussion of that firmware, [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947)

however, before modifying the RT2860STA.dat to include all those extra options, my connection was very stable.  so i think it might have more to do with the modifications to th RT2860STA.dat file.

if anyone has any suggestions for other settings that might address this, great, please post away.  i'll look into it more.

in the mean time, i might like to undo those changes to the RT2860STA.dat file and commit them.  once i have modified the RT2860STA.dat, is there a way to commit them without logging out or rebooting the machine?  something like 'ifconfig ra0 down; ifconfig ra0 up' maybe?

Hmmmm---I was modifying the file based on the readme included with the driver--you could experiment with the file to get it stable for you (mine has been like a rock ever after....). The main thing is a frequency multi that is default at 2x & needs to be set to 4x to get the speed up--sorry I can't be more help than that....most likely it is a mis-match between your router & the way the file is setup....Interesting that I am using the same router, but without the firmware you are using.

---

### Post by wmdiem on 2009-01-14
reply @
[http://ubuntuforums.org/showthread.php?t=1038984](http://ubuntuforums.org/showthread.php?t=1038984)

---

### Post by kzm. on 2009-01-14
*Post before this helped connecting to the unprotected router using AP instead of ESSID. But card has to be up.*

Now i have the wpa on and i am stuck again.. i start feeling a bit silly.. May be some wizard here can point me to my mistakes?

i tried all three approaches. the *.dat file:

```
sudo nano /etc/Wireless/RT2860STA/RT2860STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=NL
ChannelGeography=1
SSID=whatever
NetworkType=Infra
WirelessMode=9
Channel=7
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
#AuthMode=OPEN
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=***
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=                       
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
```

The interface file:

```
sudo nano /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Wifi
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up iwconfig ra0 ap 00:0C:F6:4B:D1:F2
pre-up iwconfig ra0 essid "whatever"
pre-up iwconfig ra0 mode Managed
pre-up iwconfig ra0 channel 7
pre-up iwpriv ra0 set Channel=7
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="***"
pre-up ifconfig ra0 up
auto ra0

```

And a daemon script:

```
sudo nano /etc/init.d/wifi
#!/bin/sh
# author me
# date 14/01/2009

modprobe rt2860sta
ifconfig ra0 down
dhclient -r ra0
ifconfig ra0 up
iwconfig ra0 ap 00:0C:F6:4B:D1:F2
iwconfig ra0 essid "whatever"
iwconfig ra0 mode Managed
iwconfig ra0 channel 7
iwpriv ra0 set Channel=7
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set WPAPSK="***"
iwpriv ra0 set TxRate=0
dhclient3 ra0
```

Not to say i also just tried the manual way typing the commands.. but nothing got me connected (dhclient fails and yes i also tried rebooting):

```
sudo iwlist ra0 scan
Cell 01 - Address: 00:0C:F6:4B:D1:F2
                    ESSID:"whatever"
                    Mode:Managed
                    Channel:7
                    Quality:100/100  Signal level:-13 dBm  Noise level:-71 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
```

```
sudo iwconfig ra0 
ra0       RT2860 Wireless  ESSID:"cocksucker"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:0C:F6:4B:D1:F2   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level:-13 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**Thank you so much!!**

---

### Post by scarf on 2009-01-14
kzm, i'm not sure how much help this will be, as i wanted to let network-manager app handle as much of the networking as possible.  i have achieved that, and my wireless is set as a system default and connecting automatically upon reboots, etc.  i am using WPA2-PSK/AES and it's working great.  however, you seem to want to do things a little more manually thru config files and CLI.

so, FWIW...

if you look previously in this thread to post #34, that is where i jumped in and you may read from there on to see what i have done.

i would recommend doing that, but, basically, i first followed this post,

[http://ubuntuforums.org/showpost.php?p=5114684&postcount=41](http://ubuntuforums.org/showpost.php?p=5114684&postcount=41)

of course i used the latest drivers, and that should read "ln -s ..." not "ln - s ..."

then, instead of deleting and completely not using the RT2860STA.dat file, i just used it with:
```

#The word of "Default" must not be removed
Default
WirelessMode=6

```
which brings the speed up but caps it to 130 Mb/s.  if you read further on, it seems that configuring more settings in the RT2860STA.dat file will unlock full N speeds.  i witnessed this but my connection was very unstable so i am back to just the two lines in the dat file and slower speeds for now...

additionally, if the mac address of your router has changed, that seems to cause problems.  have a look in /etc/NetworkManager/system-connections/ and/or maybe ~/.gconf/system/networking/.  i remember i had to edit the mac address for my connection or delete the connection's settings file altogether to get re-connected.

---

### Post by kzm. on 2009-01-15
hmm. I do not have the network manager installed because I have the wirelesscard on a headless machine. could you may be post the content of those files? may be I find something it I do different and thus wrong... thanks a lot!!

---

### Post by scarf on 2009-01-15
which files are you talking about?  the ones in /etc/NetworkManager/system-connections and ~/.gconf/system/networking/wireless are of no use if network manager is not installed.  so i would rather not just blindly post the contents, since there is sensitive info in there that i don't feel like meticulously censoring unless it's necessary. ;)

---

### Post by kzm. on 2009-01-15
:rolleyes:

well, i guess the network manager does not much different than i try to do here by hand... setting the one way or the other the wireless right. so i was wondering if it may be unveils some secrets I am not aware of yet, since i have no idea what the network manager file looks like.. so if you do not mind posting- at least the part concerning that card- you could "***" all sensual data, thats fine with me. of course only if you want to. thanks anyway.

---

### Post by GNUbee40 on 2009-01-20
Just like [COLOR="Blue"]scarf[/COLOR] I earlier had this card running with network manager using [COLOR="Blue"]LAW-Masterminds[/COLOR] approach. I could not use Draft-N, but roaming worked somewhat satisfying. After upgrading to Itrepid my Wifi connection has been lost for good. 
I tried various approaches including NDISwrapper and the debian driver package (ppa) but to no avail. The card seems to be claimed by the driver at times, but the Wireless LED of the computer is not blinking like in old days. Roaming does not work. If i try to connect manually through network manager I cannot connect. I am pretty clueless of what might be wrong here, and how to analyse the problem further. Especially because the wireless tools dont seem to give me any useful information. Thus i would be grateful for any helpful hints...:-k

---

### Post by scarf on 2009-01-21
GNUbee40, did you recompile and reinstall the driver after upgrading?  after such a process, or a kernel update, you will have to recompile and reinstall the driver.  i am using intrepid 8.10 just fine with the rt2860.  maybe try repeating the whole rt2860 installation process again.

kzm, haven't forgotten about you.  i will look into the file and see what i can post.

---

### Post by GNUbee40 on 2009-01-21
Hey Scarf!

Yes - i had recompiled numerous times, actually after almost each kernel update, so i have a script to do it. However, since the upgrade to intrepid the card remains unclaimed even after recompiling the driver. Inserting the module manually with insmod as stated in the readme seems to change that, but still the card is not fully activated, i.e. the LED is not blinking. 
I just repeated installing the latest driver from Ralink and are now following the README instructions in order to get the card activated at startup since LAW-Mastermind's method whith the softlinked Startup script doesn't seem to have any effect any more. :(

---

### Post by autocrosser on 2009-01-21
Just so everyone can cheer!!!!

This came in with todays updates in Jaunty----- and it seems to work well.....

Message: 5
Date: Wed, 21 Jan 2009 21:25:13 -0000
From: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Subject: [ubuntu/jaunty] linux-firmware 1.4 (Accepted)
To: [EMAIL="jaunty-changes@lists.ubuntu.com"]jaunty-changes@lists.ubuntu.com[/EMAIL]
Message-ID:
	[EMAIL="20090121212513.8720.77731.launchpad@cocoplum.canonical.com"]<20090121212513.8720.77731.launchpad@cocoplum.canonical.com>[/EMAIL]
Content-Type: text/plain; charset="utf-8"

linux-firmware (1.4) jaunty; urgency=low

  * Added firmware for RT 2860/2870
  * Copy license files.

Date: Wed, 21 Jan 2009 20:19:28 +0000
Changed-By: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Maintainer: Ubuntu Kernel Team [EMAIL="kernel-team@lists.ubuntu.com"]<kernel-team@lists.ubuntu.com>[/EMAIL]
[https://launchpad.net/ubuntu/jaunty/+source/linux-firmware/1.4](https://launchpad.net/ubuntu/jaunty/+source/linux-firmware/1.4)
-------------- next part --------------
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.8
Date: Wed, 21 Jan 2009 20:19:28 +0000
Source: linux-firmware
Binary: linux-firmware nic-firmware scsi-firmware
Architecture: source
Version: 1.4
Distribution: jaunty
Urgency: low
Maintainer: Ubuntu Kernel Team [EMAIL="kernel-team@lists.ubuntu.com"]<kernel-team@lists.ubuntu.com>[/EMAIL]
Changed-By: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Description: 
 linux-firmware - Firmware for Linux kernel drivers
 nic-firmware - Firmware for NICs (udeb)
 scsi-firmware - Firmware for SCSI controllers (udeb)
Changes: 
 linux-firmware (1.4) jaunty; urgency=low
 .
   * Added firmware for RT 2860/2870
   * Copy license files.
Checksums-Sha1: 
 3bb54c9796a2d045495274bd51f3c9689722b54d 774 linux-firmware_1.4.dsc
 1b8add1e886cf7289da873cd44871cf28bf812b1 3720037 linux-firmware_1.4.tar.gz
Checksums-Sha256: 
 4fe8ddf6e031c8c14156055f0db503357d37a59a52f04b09db2554b1c3172432 774 linux-firmware_1.4.dsc
 deba61d9d4d2aeb7e3e19f91ca30691ff6f0e1bc67903fc45b0006ec58e13751 3720037 linux-firmware_1.4.tar.gz
Files: 
 b8bf4673b6ac989da8ec5b079e1e19c9 774 misc optional linux-firmware_1.4.dsc
 be4680c49ab43bee013faa4ff412f2d2 3720037 misc optional linux-firmware_1.4.tar.gz

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEARECAAYFAkl3kh0ACgkQ/VwK2Iv57+YElwCfZb/4OKwfiOorrXs4h5ScvXFF
Uv8AoJTsU0BkqrgSZge4fNQEFjcwzvxm
=+XP2
-----END PGP SIGNATURE-----

------------------------------

---

### Post by GNUbee40 on 2009-01-22
Hey autocrosser!

Sounds promising. However I don't quite know what this means and how to act on it. :p
Are you indicating that the kernel needs to be updated before the card can work? Or that the driver will be implemented in forthcoming versions of Ubuntu?

I already installed the RT2860 drivers available as Debian packages (tried ver 17.x.x and 18.x.x). They also totally failed to claim the card...
If the problem  hadn't arisen at the same time as the upgrade, i would reckon the wifi interface is dead :evil:

---

### Post by autocrosser on 2009-01-22
Well---What this means:

As of this date, you no longer need to "roll your own" driver in the testing Jaunty--This will be the norm for all users as of the Jaunty release date (or RC1 if someone wants to jump in early). I worked with the devs prior to the last UDS to get rt2860/70 support in the 2.6.28 kernel cycle & can now report success.

So, from Jaunty on forwards there will be support for the rt2860/70 driver via the Firmware addon package :).

What this means to you:

1. If you wanted to try Jaunty (which I don't recommend right now), you would have support "out-of the-box" for the open-source driver from Ralink.

2. Wait until the release & do a normal upgrade.

In either case, to help move the source-package forward, bug reports will help us create a package that works for most users (there will always be corner cases)--right now I am one of very few working with testing this. I will keep on top of the reaction to the source-code & kernel upgrades....So at least we'll have the driver available in the future. 

Any bug reports will need to be filed against the "Firmware" & "Kernel" packages from this point forwards--This is NOT for Intrepid--This is Jaunty forwards---reason is that Intrepid won't have it due to the short time before Jaunty release & I don't think a dev wants to backport it for Intrepid for that same reason.

---

### Post by scarf on 2009-01-27
> **kzm. said:**
> :rolleyes:

well, i guess the network manager does not much different than i try to do here by hand... setting the one way or the other the wireless right. so i was wondering if it may be unveils some secrets I am not aware of yet, since i have no idea what the network manager file looks like.. so if you do not mind posting- at least the part concerning that card- you could "***" all sensual data, thats fine with me. of course only if you want to. thanks anyway.

here is what is in /etc/NetworkManager/system-connections/<connection name>:


```

[802-11-wireless-security]
key-mgmt=wpa-psk
wep-tx-keyidx=0
proto=wpa;rsn;
pairwise=tkip;ccmp;
group=wep40;wep104;tkip;ccmp;
psk=*****

[connection]
id=<connection name>
uuid=*****
type=802-11-wireless
autoconnect=true
timestamp=*****

[802-11-wireless]
ssid=<ssid in decimal format with a semicolon following each character. e.g. abc = 97;98;99;>
mode=infrastructure
channel=0
rate=0
tx-power=0
mtu=0
seen-bssids=*****
security=802-11-wireless-security

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false

```

---

### Post by scarf on 2009-01-30
> **scarf said:**
> while i definitely see higher speeds reported in the network manager app, my wifi connection has become sporadic and unstable.

i am using, however, a linksys wrt600n router with beta dd-wrt firmware.  might that have something to do with it?

here is a link to a discussion of that firmware, [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=24947)

however, before modifying the RT2860STA.dat to include all those extra options, my connection was very stable.  so i think it might have more to do with the modifications to th RT2860STA.dat file.

if anyone has any suggestions for other settings that might address this, great, please post away.  i'll look into it more.

in the mean time, i might like to undo those changes to the RT2860STA.dat file and commit them.  once i have modified the RT2860STA.dat, is there a way to commit them without logging out or rebooting the machine?  something like 'ifconfig ra0 down; ifconfig ra0 up' maybe?

i have been using autocrosser's version of the RT2860STA.dat file for a bit now, and it is stable also.  the stability issues just happen at such strange times that it is hard to figure out what is the problem.  until the dd-wrt firmware for wrt-600n is no longer beta, i will suppose the main problem affecting the wifi stability is this beta dd-wrt firmware.

i have found that restarting the rt2860 driver resolves a lot of the stability issues when i am experiencing them.  this is also the way to commit changes to the RT2860STA.dat file without restarting the computer:

0. make desired changes to /etc/Wireless/RT2860STA/RT2860STA.dat
1. right-click on the network-manager icon and uncheck "enable wireless" (or, if you are not using network-manager, issue "ifconfig ra0 down") to stop the use of the driver.
2. issue "rmmod rt2860sta" in the terminal
3. issue "insmod /lib/modules/<kernel version>/kernel/drivers/net/wireless/rt2860sta.ko" (2.6 kernel) (or use rt2860sta.o for 2.4 kernel) in the terminal
4. right-click on network-manager icon and check "enable wireless" (or, if you are not using network-manager, issue "ifconfig ra0 up") to start the use of the driver.

---

### Post by simon_says on 2009-02-01
Just wanted to say a big thanks to flyguy97 - I'd been having a real problem getting my Edimax 7728 card to play ball in Ubuntu 8.10 (and subsequently Linux Mint 6 which I have now switched to), but following the manual approach seems to have sorted things nicely and I am now connecting at almost top speed.  Incidentally I ended up using WPA2PSK and AES in my .dat file.

---

### Post by orchid.se on 2009-02-03
Hey, just wanted to drop in and say thanks for making my 'oh-so-portable laptop' portable once again!

Thanks!

---

### Post by TBerk on 2009-02-28
Many Thanks to flyguy97, 

I just today (27Feb09) got this working using (primarily) this thread's instructions.

My main trouble was having to use the computer's 10/100BaseT built in Ethernet to 1st update via Synaptic Package Manager and then to gain access to the Internet for things like a vi editor cheat sheet, etc. (Been many Moons since I was using any form of a Unix based OS.)

Once I got the OS patched I seemed to breeze past my earlier troubles w/ error running the 'make' command & switching over from Network Manager to using wicd.

So, 1st thing after checking for function and adding somethings to my web browser was to post here as a way of providing feedback.


TBerk

[follow up]

March 22 2009

For the last day or two I have lost full connectivity in Ubuntu via wireless. I can see the local networks (and I can connect in WinXP, hence this post) but I can not validate in Ubuntu 8.10 using the same wicd setup (wpa2 and 80211.g) I had just days before.

Only change I had made was to run Update Manager and/or Synaptic Package, etc etc and get an Open Office update (and perhaps something else unnoticed?)

Temporarily I switched away from the default wext driver to ralink legacy and I was able to reconnect. But that failed again and I have noticed using the wext driver I have IPv6 support but not IPv4.

All for now, root-canal-ing continues.

TBerk

---

### Post by scarf on 2009-03-06
i am unable to connect to an Apple Airport Extreme access point.  it is configured to use WPA/WPA2.  the NetworkManager asks for the WPA/WPA2 password, but it doesn't connect.  i see the thing swirling around and only one of the dots is green.  after a while the NetworkManager asks for the password again.  hmm.... this seems like the problems we were having early on when first trying to get rt2860 working.....

i have tried to reset the RT2860STA.dat file so it just has the word "Default" in it, but still can't connect.

i have access to the Airport Extreme. so, if there are any suggested settings i can change on there, i am able to try that.

i read somewhere else to try changing the channel to 11.  tried that, but still no connection.

bonus points if we can figure out how i can access the hard drive attached to the Airport Extreme. ;)

---

### Post by andre_orwell on 2009-04-18
Quick summary of my experience with ralink 2860 wireless:

1. recent kernels (>= 2.6.28 perhaps .27? not sure) integrate the rt2860sta driver "out of the box".  This driver is close to a direct copy of the driver provided by ralink on their linux support page.  Importantly is is maintained - so it still builds for the 2.6.29 kernel whereas the code distributed by ralink doesn't.  In other words you will not have to rebuild any drivers.

2. The kernel driver looks for firmware in /lib/firmware.  I have noticed that this is not always installed.  If your system appears to recognise your card but it doesn't work then check this.  You can download the firmware from the realink linux support page and just drop it in /lib/firmware.  This was all I needed to get wireless working in ubuntu 8.10.

3. The latest ralink driver (with kernel >= 2.6.28 ) apparently has some autonegotiation issues that at least effect WPA (a regression it would seem).  If your router gives a choice of cypher, chances are you will have problems connecting.  Your options here are to limit the router to use a single cypher (e.g. TKIP).  I have not tried this but you may also get it to work by specifying a single cypher in the wpa_supplicant configuration.

My connection for sending this post is a Ralink 2860 :-)

---

### Post by GNUbee40 on 2009-04-20
Well well - verrrry interesting news!

After updating from 8.04 to 8.10 i could not get my Ralink2860 based wireless to work. Eventually I had to reinstall the good old 8.04. Interestingly after a complete update of 8.04 the wireless would not work either. So currently I am running happily wireless on an entirely unupdated 8.04 (I just don't dare to update anymore - things stop working more often than they improve #-o)

According to your post, my trouble comes from the kernel updates as the later kernel versions are not supported by Ralinks own drivers. Also according to You placing a [COLOR="Blue"][8 kb little bin-file]("http://www.ralinktech.com.tw/data/drivers/RT2860_Firmware_V11.zip")[/COLOR] in /lib/firmware would solve aaall the trouble with the latest linux kernel - namely having the wireless card listed as claimed by its driver when using lshw, but unaccessible by both network manager og iwpriv.

Looking forward to try this out as soon 9.04 gets released.

Thanks man

---

### Post by TBerk on 2009-04-21
re: GNUbee40

One work around, esp w/ the RT2860 family was to ditch Network manager in favor of **wicd**.  In fact when you go to install wicd (via say Synaptic) it will remove Network manager by default.

When I was running 8.10 this was part of my 'fix'.


TBerk

---

### Post by GNUbee40 on 2009-04-22
@Tberk

Thank you for the tip, my man.
Trouble is - in my darkest hours I also tried replacing Network Mangager with WICD without any success.
My experience is, that if the card is properly installed, it will work under Network-Manager. If it doesn't work under Network Manager, it won't work with WICD or manual configuration either.
According to numerous posts on this thread RT2860 based NICs can run satisfying under Network Manager even at N speed.
I am currently running at G speed only, but hopefully can improve that later on.

Cheers

---

### Post by GNUbee40 on 2009-04-23
Ok - the 9.04 finally released.:popcorn:
Boot from the Live Cd to test if my RT2860 wifi is supported out of the box as promised.
Nada.:confused:
ra0 is listed when I run lshw, iwconfig. But no wireless networks in Network Manager. I did not trie to configure the card using iwconfig and iwpriv, while using the live CD. In the past it did not work out for me, so I don't bother to try now. :(

BTW: I checked on the live system if the RT2860 firmware was missing in /lib/firmware. But no - there it was. So all in all - I am just mystified. Maybe it is the new version of Network Manager, which no longer will cooperate with my card. 

Always the same with the new linux kernels. Looks like I am stuck with 8.04. Not a big deal, but would like to be able to receive security updates, Firefox updates, and Wine updates.

---

### Post by scarf on 2009-04-24
after upgrading to 9.04, the wifi is still working, but it seems to be very unstable.

it appears that rt2860 is supported, but i'm not sure.

```

$ modprobe -l -a rt2860*
kernel/drivers/staging/rt2860/rt2860sta.ko

```

so, i thought the module we were using was kernel/drivers/net/wireless/rt2860sta.ko, so why is that other rt2860sta.ko showing up with modprobe? (i have much to learn)

even after re-compiling, re-installing (make;make install), rmmod and insmod, the kernel/drivers/staging/rt2860/rt2860sta.ko is still showing up:

```

$ sudo rmmod rt2860sta
$ sudo insmod /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko
$ modprobe -l -a rt2860*
kernel/drivers/staging/rt2860/rt2860sta.ko
$ ls -l /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
-rw-r--r-- 1 root root 620088 2009-04-16 20:42 /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
$ ls -l /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko 
-rw-r--r-- 1 root root 621255 2009-04-24 09:44 /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko

```

the two modules appear different (different file sizes).

i tried to move /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko into /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/ and the wifi is still unstable.

i notice ralink has just released a new version of the driver today, v2.1.1.0.  i am still using v1.8.0.0.  i will try compiling the new driver and see how that goes.

would be nice to understand more about modules and why insmod doesn't appear to be working...

---

### Post by InkyGB on 2009-04-24
I've got this working with WPA/WPA2 after changing my router to broadcast SSID after seeing in the log that Ubuntu was identifying my SSID as blank rather than the one I'd supplied.

---

### Post by mauro24 on 2009-04-26
> **scarf said:**
> after upgrading to 9.04, the wifi is still working, but it seems to be very unstable.

it appears that rt2860 is supported, but i'm not sure.

```

$ modprobe -l -a rt2860*
kernel/drivers/staging/rt2860/rt2860sta.ko

```

so, i thought the module we were using was kernel/drivers/net/wireless/rt2860sta.ko, so why is that other rt2860sta.ko showing up with modprobe? (i have much to learn)

even after re-compiling, re-installing (make;make install), rmmod and insmod, the kernel/drivers/staging/rt2860/rt2860sta.ko is still showing up:

```

$ sudo rmmod rt2860sta
$ sudo insmod /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko
$ modprobe -l -a rt2860*
kernel/drivers/staging/rt2860/rt2860sta.ko
$ ls -l /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
-rw-r--r-- 1 root root 620088 2009-04-16 20:42 /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
$ ls -l /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko 
-rw-r--r-- 1 root root 621255 2009-04-24 09:44 /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko

```

the two modules appear different (different file sizes).

i tried to move /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rt2860sta.ko into /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/ and the wifi is still unstable.

i notice ralink has just released a new version of the driver today, v2.1.1.0.  i am still using v1.8.0.0.  i will try compiling the new driver and see how that goes.

would be nice to understand more about modules and why insmod doesn't appear to be working...

I'm a newbie to Ubuntu, some got my wireless card working with Ubuntu 8.10 but after upgrading to 9.10, my card doesn't work anymore.  My card uses the same driver rt2860, I try to install it, but I could not help it.  I need some help trying to reinstall the driver. I would like to install that new driver from the ralink website, the one you mentioned.  thank you.

---

### Post by GNUbee40 on 2009-04-27
Hey Guys!

*As autocrosser wrote earlier in this thread, with Ubuntu 9.04 RT2860 chip based wifi should "work out of the box", which means no installing drivers, or fiddling around with config files.*
However in order to unleash the full power of N-based Wireless, the RT2860.dat configuration file has to be modified it seems (see earlier pages of this thread). Haven't tried to play with this file yet. So can only connect using G.

I wrote earlier after trying the latest live CD that my card would not work. Well, I was wrong (the wifi switch on my laptop was set to off - duh!) ](*,)
I was surprised how well it worked actually, quite reasonable performance without any hassles :biggrin:

In earlier versions of Ubuntu I used an approach where RT2860.dat was deleted after inserting the driver module. [COLOR="Blue"][(See here)]("http://ubuntuforums.org/showthread.php?t=683085&page=5")[/COLOR] The theory was at that time, that the RT2860.dat file could not be used with Network-manager. That might have been true then. But if you have look on the latest pages of this thread, it seems not to be true any more.

Now after upgrade to 9.04 I only rely on the driver integrated in the kernel. Haven't rebuilt or reinstalled anything :guitar: Works good for me. :popcorn:
The only serious flaw right now is also written about earlier in this thread: Autonegotiation does not work. We have 3 APs in our flat. 1 uses WPA, 1 WPA2, and 1 is in mixed mode (WPA/WPA2). I have no trouble connecting to the first 2 APs, but the 3d doesnt work for me. Seems my card cannot decide which WPA version to use. Maybe this could be fixed by adding a line to the RT2860.dat restricting the Wifi to one WPA version only.

The question is off course why with Ubuntu 9.04 Wireless is unstable now for some of you.
Maybe because you earlier modified etc/network/interfaces, and these settings now interfere with the new driver? 
Also I do not know what happens, if you (scarf) insert a driver module for the wireless, while the system already has claimed the wireless with its own driver. Could be messy...
What kind of unstableness are we talking here, btw...?


**For those new to Ubuntu**: in order to get the drivers from Ralink to work with your card, you need to read this thread and the one I linked too earlier in this post. You need to read them carefully and know, that there are several methods to this. 
Some *do not *want the Network manager *(NM)* to handle the network connections. Instead they either install WICD to handle the connections or just plainly remove NM and configure everything manually. This is daunting for new user, who do not know much about Wireless, network connections, and how they are handled and configured in Linux (there are several ways for doing this as well :???:). You'll find yourself reading a lot of man pages to gain some understanding (Well, knowledge never hurts :roll:) It is recommended to do this research, look up the man or info pages for interfaces, ifconfig, iwconfig, iwpriv, wireless, iwscan, insmod, depmod and maybe others. Read a tutorial about Linux basics also. I really like *Introduction to Linux*, which can be found here [COLOR="Blue"][http://tldp.org/guides.html]("http://tldp.org/guides.html")[/COLOR]
Be especially aware, that NM also handles your wired connection! Before you remove it, you'll have to know how to configure /etc/network/interfaces, so you still will have a connection! (See first two pages of this thread)

Personally I prefer having the comfort of having NM handling things, even though there might be some performance trouble here and there... That's why I used the approach linked to earlier in this post.

@mauro: Don't know how your card was configured under 8.10 - and you do not seem to know either. :confused: Fiddling around with drivers is timeconsuming.
First try running Ubuntu 9.04 from CD (live system) and see if the Wifi starts working. (remember to turn the wifi switch on though :)) If the card works fine when running the system from CD, reinstalling a fresh 9.04 system might be the simplest solution. Remember to back-up your data though.

All others who are struggling might do the same - test 9.04 with the live-cd first. If wireless works with the live-CD but not after upgrading, there might be some old settings which needs to be removed.

Regards

---

### Post by mauro24 on 2009-04-27
> **GNUbee40 said:**
> Hey Guys!

*As autocrosser wrote earlier in this thread, with Ubuntu 9.04 RT2860 chip based wifi should "work out of the box", which means no installing drivers, or fiddling around with config files.*
However in order to unleash the full power of N-based Wireless, the RT2860.dat configuration file has to be modified it seems (see earlier pages of this thread). Haven't tried to play with this file yet. So can only connect using G.

I wrote earlier after trying the latest live CD that my card would not work. Well, I was wrong (the wifi switch on my laptop was set to off - duh!) ](*,)
I was surprised how well it worked actually, quite reasonable performance without any hassles :biggrin:

In earlier versions of Ubuntu I used an approach where RT2860.dat was deleted after inserting the driver module. [COLOR="Blue"][(See here)]("http://ubuntuforums.org/showthread.php?t=683085&page=5")[/COLOR] The theory was at that time, that the RT2860.dat file could not be used with Network-manager. That might have been true then. But if you have look on the latest pages of this thread, it seems not to be true any more.

Now after upgrade to 9.04 I only rely on the driver integrated in the kernel. Haven't rebuilt or reinstalled anything :guitar: Works good for me. :popcorn:
The only serious flaw right now is also written about earlier in this thread: Autonegotiation does not work. We have 3 APs in our flat. 1 uses WPA, 1 WPA2, and 1 is in mixed mode (WPA/WPA2). I have no trouble connecting to the first 2 APs, but the 3d doesnt work for me. Seems my card cannot decide which WPA version to use. Maybe this could be fixed by adding a line to the RT2860.dat restricting the Wifi to one WPA version only.

The question is off course why with Ubuntu 9.04 Wireless is unstable now for some of you.
Maybe because you earlier modified etc/network/interfaces, and these settings now interfere with the new driver? 
Also I do not know what happens, if you (scarf) insert a driver module for the wireless, while the system already has claimed the wireless with its own driver. Could be messy...
What kind of unstableness are we talking here, btw...?


**For those new to Ubuntu**: in order to get the drivers from Ralink to work with your card, you need to read this thread and the one I linked too earlier in this post. You need to read them carefully and know, that there are several methods to this. 
Some *do not *want the Network manager *(NM)* to handle the network connections. Instead they either install WICD to handle the connections or just plainly remove NM and configure everything manually. This is daunting for new user, who do not know much about Wireless, network connections, and how they are handled and configured in Linux (there are several ways for doing this as well :???:). You'll find yourself reading a lot of man pages to gain some understanding (Well, knowledge never hurts :roll:) It is recommended to do this research, look up the man or info pages for interfaces, ifconfig, iwconfig, iwpriv, wireless, iwscan, insmod, depmod and maybe others. Read a tutorial about Linux basics also. I really like *Introduction to Linux*, which can be found here [COLOR="Blue"][http://tldp.org/guides.html]("http://tldp.org/guides.html")[/COLOR]
Be especially aware, that NM also handles your wired connection! Before you remove it, you'll have to know how to configure /etc/network/interfaces, so you still will have a connection! (See first two pages of this thread)

Personally I prefer having the comfort of having NM handling things, even though there might be some performance trouble here and there... That's why I used the approach linked to earlier in this post.

@mauro: Don't know how your card was configured under 8.10 - and you do not seem to know either. :confused: Fiddling around with drivers is timeconsuming.
First try running Ubuntu 9.04 from CD (live system) and see if the Wifi starts working. (remember to turn the wifi switch on though :)) If the card works fine when running the system from CD, reinstalling a fresh 9.04 system might be the simplest solution. Remember to back-up your data though.

All others who are struggling might do the same - test 9.04 with the live-cd first. If wireless works with the live-CD but not after upgrading, there might be some old settings which needs to be removed.

Regards
Well, a friend of mine configured ubuntu to run my wireless card for my eee box b202 pc. But after upgrading from the update manager to ubuntu 9.04, the card stopped working and I cannot connect to the internet, except through wire.
 I'm just looking for an easy step by step procedure to fix my card. But i'm not sure if I should use procedures for the older version of ubuntu.  Also, I've tried to do the walkthrough, I get to the point where I need to tar the driver, but I don't know how to write the folder location. Thanks for your attention.

---

### Post by GNUbee40 on 2009-04-28
Hey Mauro!

The driver your friend installed usually has to be rebuilt every time your Linux kernel gets updated (which has happened now with the upgrade). That means you more ore less repeat the procedure from last time. 
However - using the latest driver makes sense as the latest driver probably supports the latest linux kernel better.
You might want your friend to help you again...

If you wanna try to give it a go on your own:

I suppose you already downloaded the latest driver from Ralink. You can unpack it by doubleclickin it (in the GNOME desktop). Has the same effect as if you use tar in the shell. 

Never the less you need to know how to find the folder it gets extracted to. So here's how can find your way:

Where did you download the driver to? Most commonly things will get downloaded to the Desktop folder.
When you start the Terminal you are in your home folder. You can change to your Desktop folder by writing
```
cd Desktop
```
Remember: This is Case sensitive! cd desktop wont work!

If you downloaded the tarball to this folder, you might run the tar command and procede.
If you already unpacked it, there will be another folder containing the unpacked files from Ralink. U will have to change to that folder.
Another possibility is to type the first letters of a folder or filename and hit the "TAB" button. The bash shell (command line) will try to autocomplete. F.eks. Type cd Desk, hit Tab once and the Shell will autocomplete. Very handy for long folder names, like the one where the drivers are.

These things U need to know here are the basics of Linux: Where are usually things located and how do I get there, etc. Not knowing them make things hard, when trying to fiddle with the system. So I recommend U set aside a little time reading the aforementioned Linux guide and practice a little :) 

It would be really nice to know, if a fresh 9.04 system still fails to get the wifi working. But i guess the EEpc has no CD-drive. So U would have to boot from USB. Go to [http://www.ubuntu.com/getubuntu/download-netbook]("http://www.ubuntu.com/getubuntu/download-netbook") to learn more.

Regards

Edit: Just checked. Your Eebox has not been tested yet with the netbook version of Ubuntu. So maybe you should stick with the Standard Desktop version.

---

### Post by mauro24 on 2009-04-29
Ok, now I have reinstalled ubuntu 9.04 brand new, now the network manager detects the wireless networks, it detects mine but when I try to connect, it doesn't work, it asks for my password again.  I don't know what to do I'm going to try to install the new driver from the ralink website, if someone has done it, could you give me a hand?.  thanks.

---

### Post by GNUbee40 on 2009-04-30
Hey Mauro!

Congrats for getting the card to work. Now you only need make it talk to your wireless router :P
As stated before in this thread (told you to read it!) there are some issues with the driver included in Ubuntu Jaunty (ver.1.8.0.0). This means, you have to set the Cypher of your Router to either AES or TKIP encryption, because the automatic switching between WPA/WPA2 doesn't work with the driver included in 9.04. That is most likely your problem. I could not connect to my fairly new D-link DIR635 after upgrading, because WPA mode was set to "Auto" and Cypher to both AES and TKIP. 
So - get the manual to your router, connect to it with wired connection, and set it to EITHER WPA (with TKIP cypher) OR WPA2 (with AES cypher).
Maybe the latest driver release from Ralink (ver.2.1.1.0) has fixed the above issue, but you seem a little lost, so I wouldn't recommend messing with building your own drivers, until you gather some more knowledge.
Regards

---

### Post by richinnewzealand on 2009-05-01
Hi,

I'm running the Ralink 2860 on an Acer laptop. I am just at a friends place and wanted to use his wireless which he has set up on channel 14 I think. I discovered that my ralink adapter only pics up channels from 0 - 12. Has this to do with the fact that some countries block channels 13 - 14? Can I change that somehow myself?  

Would love to get advice from you guys.

Ah, just booted into XP and used the Ralink config tool there on my 2860 adapter. Ha, the AP is set up on channels 13 - 14. Any idea of how I can work this around on my 9.04? 
Everything else works perfect. Any help will be appreciated.

Thanks,

Rich

---

### Post by richinnewzealand on 2009-05-01
Fixed the problem with a patch from:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891)

Rich

---

### Post by HankB on 2009-05-01
Thanks to both flyguy97 and GNUbee40 for helping out with this.

> **GNUbee40 said:**
> ... 
So - get the manual to your router, connect to it with wired connection, and set it to EITHER WPA (with TKIP cypher) OR WPA2 (with AES cypher).

I can confirm the same with myt Eee PC 901 and WRT150N running DD-WRT. Since I figured that out, I have been a happy camper on 9.04 UNR using the driver that came installed. (Almost - still need to get wireless broadband working via my cell phone, but that's a different issue. ;) )

But that's not quite good enough for me. :p I have an lpia install running on SD card and seem to get about double video performance (according to gtkperf anyway) Unfortunately the lpia flavor of 9.04 dowes not include the rt2860sta module. I have followed the directions on the first post and downloaded and installed the driver (v2.1.1.0) both with and without WPA supplicant support. I have left nm-applet installed and managing my networks since it works with vanilla 9.04. I have not touched the .dat file.

This is the result of trying to connect (from daemon.log)
```

May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) starting connection 'Auto Barad-dur' 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): device state change: 3 -> 4 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): device state change: 4 -> 5 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0/wireless): access point 'Auto Barad-dur' has security, but secrets are required. 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): device state change: 5 -> 6 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): device state change: 6 -> 4 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): device state change: 4 -> 5 
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto Barad-dur' has security, and secrets exist.  No new secrets needed. 
May  1 11:19:07 bonsai NetworkManager: <info>  Config: added 'ssid' value 'Barad-dur' 
May  1 11:19:07 bonsai NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May  1 11:19:07 bonsai NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
May  1 11:19:07 bonsai NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
May  1 11:19:07 bonsai NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 11:19:07 bonsai NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 11:19:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
May  1 11:19:07 bonsai NetworkManager: <info>  Config: set interface ap_scan to 1 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected 
May  1 11:19:07 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May  1 11:19:09 bonsai dhclient: DHCPREQUEST of 192.168.100.103 on eth0 to 192.168.100.1 port 67
May  1 11:19:09 bonsai dhclient: DHCPACK of 192.168.100.103 from 192.168.100.1
May  1 11:19:09 bonsai dhclient: bound to 192.168.100.103 -- renewal in 44 seconds.
May  1 11:19:12 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May  1 11:19:22 bonsai NetworkManager: <info>  ra0: link timed out. 
May  1 11:19:22 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
May  1 11:19:22 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May  1 11:19:27 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May  1 11:19:37 bonsai NetworkManager: <info>  ra0: link timed out. 
May  1 11:19:37 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
May  1 11:19:37 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May  1 11:19:42 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May  1 11:19:52 bonsai NetworkManager: <info>  ra0: link timed out. 
May  1 11:19:52 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
May  1 11:19:52 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May  1 11:19:53 bonsai dhclient: DHCPREQUEST of 192.168.100.103 on eth0 to 192.168.100.1 port 67
May  1 11:19:53 bonsai dhclient: DHCPACK of 192.168.100.103 from 192.168.100.1
May  1 11:19:53 bonsai dhclient: bound to 192.168.100.103 -- renewal in 50 seconds.
May  1 11:19:57 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0/wireless): association took too long. 
May  1 11:20:07 bonsai NetworkManager: <info>  (ra0): device state change: 5 -> 6 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0/wireless): asking for new secrets 
May  1 11:20:07 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
May  1 11:20:07 bonsai NetworkManager: <info>  (ra0): device state change: 6 -> 4 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
May  1 11:20:07 bonsai NetworkManager: <info>  (ra0): device state change: 4 -> 5 
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto Barad-dur' has security, and secrets exist.  No new secrets needed. 
May  1 11:20:07 bonsai NetworkManager: <info>  Config: added 'ssid' value 'Barad-dur' 
May  1 11:20:07 bonsai NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May  1 11:20:07 bonsai NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
May  1 11:20:07 bonsai NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
May  1 11:20:07 bonsai NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 11:20:07 bonsai NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 11:20:07 bonsai NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
May  1 11:20:07 bonsai NetworkManager: <info>  Config: set interface ap_scan to 1 
May  1 11:20:07 bonsai NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 

```

dhclient messages mingled with the above are for the wired connection. This is with HAS_WPA_SUPPLICANT=n.

I see assertion in the log. Perhaps I should try with HAS_WPA_SUPPLICANT=y again.

Edit - with my AP set for WPA2 personal and AES encryption and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y, I have WiFi working on my Eee PC 901 using the lpia install :guitar:

---

### Post by docklc on 2009-05-04
I recently installed Ubuntu 9.04 on my secondary desktop system which is an AMD Athlon 64x2 with 2.5GB RAM and 500GB HD, with 416GB free after Ubuntu install, and NetGear PCI wireless card--as a dual boot with WinXP/SP2.

I am communicating with you on the XP side of this system, with no problems.  However, Ubuntu will not connect via this wireless connection, even though I have tried various different setups.

Ping will not work to ping my wireless router, either.  I have WPA/PSK enabled on my router.  I really do not want to screw up my XP side on this system until I believe that Ubuntu will work with my peripherals.  Other than the wireless connection, Ubuntu seems to be working properly.  Can you help me with setup?  Thanks, Kent.

---

### Post by HankB on 2009-05-04
> **docklc said:**
> I am communicating with you on the XP side of this system, with no problems.  However, Ubuntu will not connect via this wireless connection, even though I have tried various different setups.

I have WPA/PSK enabled on my router.

No sense to disturb the XP side until you are sure that Ubuntu does everything you need.

I did not try WPA/PSK so I cannot comment on that. I do know that WPA2/AES works for me and for others. Can you configure your router like that? (XP should work with that too.)

-hank

---

### Post by scarf on 2009-05-09
the problem that seems to be recurring with me is that i cannot connect to the router if it is using WPA security.  as soon as i configure the router to use WEP i can connect fine.

i don't really understand, because i have had my router using WPA and everything was fine, but the firmware on the router was very old and needed to be upgraded.  after upgrading, i can no longer connect when using WPA, but WEP works ok.

there must have been a solution to this since i just had it working before upgrading the router's firmware.

maybe someone can refresh my memory?  does it have to do with wpa_supplicant?

---

### Post by scarf on 2009-05-10
also, does anyone else get this annoying message in dmesg every two minutes?
```

===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 510

```
the "6(6)" and "510" values vary from message to message.  i notice the code for this message appears in os/linux/sta_ioctl.c, on line 1468:
```

DBGPRINT(RT_DEBUG_ERROR ,("===>rt_ioctl_giwscan. %d(%d) BSS returned, data->length = %d\n",i , pAdapter->ScanTab.BssNr, data->length));

```
it appears to be an error message?  what is the problem?  how can i stop it?

---

### Post by GNUbee40 on 2009-05-11
Hey scarf!

this line you are talking about 
```
May 11 19:23:04 nino-laptop kernel: [16588.372114] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 577
``` appears in my logs, too. Both syslog, messages and kernel. Around every 2 minutes.
I do not see any connection to faulty behaviour though. I guess it is just a part of maintaining connection with the router or keeping the system up to date with wireless APs around.
With 9.04 my system now connects to both WPA2 and WPA most of the time. I do have some trouble from time. Few times my card would not connect. And few times I was connected, but Firefox could not resolve addresses (maybe a problem with my ISP).
But all in all I am satisfied. Fiddling with the RT2860.dat also unleashed N power with much larger throughput even when I am 3 walls from the router.
I think we should look out for appropiate logs to sort this thing out. Will look into this and post them for you to compare.

Regards

---

### Post by mauro24 on 2009-05-12
> **GNUbee40 said:**
> Hey Mauro!

Congrats for getting the card to work. Now you only need make it talk to your wireless router :P
As stated before in this thread (told you to read it!) there are some issues with the driver included in Ubuntu Jaunty (ver.1.8.0.0). This means, you have to set the Cypher of your Router to either AES or TKIP encryption, because the automatic switching between WPA/WPA2 doesn't work with the driver included in 9.04. That is most likely your problem. I could not connect to my fairly new D-link DIR635 after upgrading, because WPA mode was set to "Auto" and Cypher to both AES and TKIP. 
So - get the manual to your router, connect to it with wired connection, and set it to EITHER WPA (with TKIP cypher) OR WPA2 (with AES cypher).
Maybe the latest driver release from Ralink (ver.2.1.1.0) has fixed the above issue, but you seem a little lost, so I wouldn't recommend messing with building your own drivers, until you gather some more knowledge.
Regards
Sorry for the lateness. Yes I was lost, but after reading a lot of walkthroughs, I figured out how to compile the new driver, using procedures for the prior driver. thanks a lot anyways, everything works fine now.:)

---

### Post by Sportsjd on 2009-05-12
I have a Belkin Pre-N router and I installed Ubuntu 9.04 on a desktop with no XP.  It is only Unbuntu 9.04.  I seem to be having the same problem with it continually asking me for the password and it not connecting.  Is it a Pre-N router issue?  Do I need a new router?  I can't seen to be able to set it to only a WPA1 or WPA2 only as GNUbee40 suggests. The router only allows the combined setting of WPA1/WPA2.  Do I need a new router?  I am a very very green student of Ubuntu and most computer operations, but I need to get the wireless working on it.  Thanks for any help.

---

### Post by GNUbee40 on 2009-05-13
Hey Dudes!

Thumbs up to Mauro - you learn fast! I needed 1 year to get this card  towork properly ):P

 
@Sports: Sounds strange with a router, which cannot be set to using 1 cipher only - only combined WPA/WPA2. You should check the router manual to be sure, that there is no way to change that. Often you can access router settings by entering the router's networks address (typically 192.168.1.1 or 192.168.0.1) in your webbrowser.
However - the error in the driver has been identified and actually there is a patch out there on launchpad, which should correct this issue, thus RT2860 wifi cards can connect in Mixed Mode again (the error seemingly was introduced after driver Ver. 1.7.1.0). On page 10 of this thread is a link to this patch. However it involves several steps, and I have not tried it myself yet. 
I can post the steps for you though. Here it goes...
> 
[LIST=1] Download [latest drivers from Ralink]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz") and unzip it in a directory of your choice = driver directory 
[*] Download the [Patch from Launchpad]("http://launchpadlibrarian.net/26192677/Patch%20for%20rt2860sta%20driver%20for%20WPA1-2%20connection%20v1.8.0.0%2B.patch") and place it in /common subdirectory of the driver directory
[*]Open the Makefile and make sure at the top two lines are as follows:- (this is always the case from driver to driver so I normally skip this...)
RT28xx_MODE = STA
TARGET = LINUX
save the file.
[*] then go to the directory os/linux and open the file called config.mk. If you want to use Network Manager (which i consider most practical) make sure that HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT are set to y

[*] Open terminal window

[*]Take the wifi down and remove the drivers that come with Jaunty
```
$ sudo ifconfig ra0 down
$ sudo rmmod rt2860sta
$ sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt2860/rt2860sta.ko /tmp # just in case it's still there
```

Then change to the driver directory, build the driver and insert driver module. Then run wifi card up again:
```


$ sudo make && sudo make install
$ sudo modprobe rt2860sta
$ sudo ifconfig ra0 up
```

Shorter form (Terminal only):
```
wget http://launchpadlibrarian.net/26192677/Patch%20for%20rt2860sta%20driver%20for%20WPA1-2%20connection%20v1.8.0.0%2B.patch
wget http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz:
tar xzf 2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz
cd 2009_0424_RT2860_Linux_STA_V2.1.1.0/
patch -p1 < ../"Patch for rt2860sta driver for WPA1-2 connection v1.8.0.0+.patch"
sed -i 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/;s/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' os/linux/config.mk
sudo make
sudo make install
sudo ifconfig ra0 down
sudo rmmod rt2860sta
sudo modprobe rt2860sta
sudo ifconfig ra0 up
```

[/list]

Hopefully no typos in this :D 
Respect to the guys from Launchpad for figuring this out. Hopefully the patch will soon be included in future releases of the driver.

Cheers
GNUbee40

---

### Post by scarf on 2009-05-14
@GNUbee40:

i'm sorry to say that the above method didn't help. in fact, it made things worse.  the only difference was i hadn't used the patch.  after installing the patch, recompiling, and reinstalling the driver, i could not only not connect to my WEP-protected network, i could also not connect to the neighbor's open network.  i could also not connect to my network after trying WPA2.  it tries to connect for about a minute and then asks me for the password again, and that continues until i hit cancel.

i have tried deleting the connection settings in NetworkManager and re-creating the network, etc.

fortunately, i didn't move the old rt2860sta.ko to /tmp, as that would have deleted it after a reboot.  after moving back the old rt2860sta.ko, which i think is the one that shipped with jaunty (620088 bytes, 2009-04-16 20:42), i can connect again to my WEP-protected network and the neighbor's open network, but still no WPA.

i have always been using the RT2860STA.dat file explained in [post 57](http://ubuntuforums.org/showpost.php?p=6443042&postcount=57).

also, my router running dd-wrt can be set to 8 different ciphers: WEP, Radius, WPA Personal, WPA Enterprise, WPA2 Personal, WPA2 Enterprise, WPA2 Personal Mixed, and WPA2 Enterprise Mixed.  i would say that the mixed ones use WPA/WPA2 while the others are just the single cipher.  i think i have tried all of the personal ciphers, with TKIP+AES (i could also choose just AES or just TKIP).

that is a lot of settings, so maybe i didn't try all of them.

what would you recommend in order that i can connect to my network with WPA2, and also be able to use other networks which may use WPA, WPA2, WEP, or no encryption?

---

### Post by GNUbee40 on 2009-05-14
Hey scarf!

Sounds dissapointing with the patch and all. Had hoped for better. The guys at Launchpad reported full success. Well...

If  you want to use WPA2 I'd say you try to set your Router to WPA2 Personal and the Cypher to AES only. Don't understand the WPA with mixed cypher settings anyway. As far as i know WPA cannot use AES encryption. Anyways. WPA and TKIP only - or WPA2 and AES only. That what works for me here.

Regards

---

### Post by scarf on 2009-05-14
> **GNUbee40 said:**
> Hey scarf!

Sounds dissapointing with the patch and all. Had hoped for better. The guys at Launchpad reported full success. Well...

If  you want to use WPA2 I'd say you try to set your Router to WPA2 Personal and the Cypher to AES only. Don't understand the WPA with mixed cypher settings anyway. As far as i know WPA cannot use AES encryption. Anyways. WPA and TKIP only - or WPA2 and AES only. That what works for me here.

Regards

great!  thanks!!  that was it!  setting to WPA2 and AES in my router's settings did the trick.  

BTW, where is that launchpad bug?  i'll read up on it and post my experience with the patch, etc.

---

### Post by GNUbee40 on 2009-05-15
Nice Dude!

The link is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891")

Cheers

---

### Post by flyguy97 on 2009-05-19
All,

I think I finally have a permanent solution to my issues. The stock rt2860sta that shipped with Jaunty worked perfectly. The only thing I needed to do to get connected with Network Manager was to change my routers type of wireless encryption from "WPA & WPA2 encryption" to "WPA2 only encryption". This setting was found under Wireless->Advanced->Security in my routers web conf. No other configuration was needed. For those of you who have compiled and recompiled like myself, be sure to issue "sudo modprobe -r rt2860sta" to remove the custom module. The biggest advantage to using the stock module is that it will be automatically updated when a new kernel is released, no more needing to recompile everytime a new kernel is released. Thank you to all of those who tirelessly worked on resolving this issue.

Cheers,
Jason

---

### Post by scarf on 2009-05-19
flyguy, i think you're right.  my wifi was working after upgrading to jaunty, it was just unstable, but i really think that is my router's fault, running a development version of dd-wrt.  after a day or so, the wifi becomes stable.

i had done so much moving around the stock rt2680sta module, and compiling the old ralink version, and the newest version, etc. that i don't know if i still have the stock module lying around.

is there anyway to get that stock module back?

---

### Post by GNUbee40 on 2009-05-20
Hola!

Yeah - Router set to fixed Cypher - my speach since 1948 :)
Scarf - unstableness means your connections is lost temporarily?

I have a D-link DIR 635 with standard Firmware. I noticed when i lie in bed streaming videos wirelessly from a NAS in our LAN, that occasionally the datastream will diminish to near zero. Even browsing the web gets unacceptable slow. Pinging the router yields response time around 5-6 seconds - thousand times higher than normal. This might last for a minute or two - then throughput goes up again. This phenomenon does not correlate well to signal strength which might be as high as 80 %. 
However my bedroom is three walls away from the router - so maybe interference problems.
However - if this sounds familiar to some of you - it migth be a problem associated with RT2860.

Cheers

---

### Post by scarf on 2009-05-20
gnubee: yeah, that's what i mean by unstableness.  sometimes it will take about 1 minute to reconnect but none of my ssh sessions ever get dropped.  occasionally, it won't be able to reconnect and i have to manually select my ssid from the list to initiate a reconnection.  sometimes i don't experience any unstableness for several days (maybe it is happening when i'm sleeping or something), other times the connection will drop in and out several times in a row.

i stream videos also and i can't remember if i've experienced a disconnect during that time, i think i have rarely.  most of the time, it just happens when i'm not really doing much, like typing this response, or reading an e-mail, or some light web surfing.  so, in my case, i don't think it has to do with throughput.

i have a ceiling and a tile floor between my laptop and the router, and the distance is maybe about 15 feet.  with dd-wrt, i have the xmit power in the router boosted to 150 mW.  the default of 70 mW is definitely not enough, as the stability problems increase and i can't really do much of anything... maybe i need more xmit power.  it can go up to 251 mW but that seems like a lot for this short distance.... but maybe the tile floor is really hard to get thru.

now, i did have windows xp on this laptop when i bought the rt2860 wifi card, and, at that time, i used the laptop in the same room as the router, not more than 10 feet from the router, and i still think there were stability problems, but maybe not.  so, you might be right that the rt2860 chipset might be the problem :\

---

### Post by GNUbee40 on 2009-05-21
> **scarf said:**
> gnubee: yeah, that's what i mean by unstableness.  sometimes it will take about 1 minute to reconnect but none of my ssh sessions ever get dropped.  occasionally, it won't be able to reconnect and i have to manually select my ssid from the list to initiate a reconnection.  sometimes i don't experience any unstableness for several days (maybe it is happening when i'm sleeping or something), other times the connection will drop in and out several times in a row.


This means your connection is temporarily lost? Because mine doesn't seem to loose the connection. It doesn't have to re-authenticate and such. I am always connected, but suddenly the data stream just ceases. Need to find a log for this to see what's going on.

---

### Post by scarf on 2009-05-21
> **GNUbee40 said:**
> This means your connection is temporarily lost? Because mine doesn't seem to loose the connection. It doesn't have to re-authenticate and such. I am always connected, but suddenly the data stream just ceases. Need to find a log for this to see what's going on.

yeah.  the icon for network manager changes from the bars to the two dots with the blue swirly, and about a minute later the connection is re-established.

other times, i experience what you are describing: slow performance, sometimes no performance with dns errors, etc., without the connection being lost.

for a log, i have checked /var/log/wap_supplicant.log.

right now, i am experiencing some instability and disconnects, and these lines keep repeating every few seconds in that log file (i have edited out the ssid and mac address for privacy ;)):

```

CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with SSID '<ssid>'
Associated with <router mac address>
WPA: Key negotiation completed with <router mac address> [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to <router mac address> completed (reauth) [id=0 id_str=]

```

this is going in daemon.log:

```

May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake 
May 21 12:32:53 kovu NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed 
May 21 12:32:58 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:33:03 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:33:03 kovu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May 21 12:33:03 kovu NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May 21 12:33:06 kovu NetworkManager: <debug> [1242934386.003674] periodic_update(): Roamed from BSSID <router mac address> (<ssid>) to (none) ((none)) 
May 21 12:33:08 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated 
May 21 12:33:08 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake 
May 21 12:33:08 kovu NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake 
May 21 12:33:08 kovu NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed 
May 21 12:33:12 kovu NetworkManager: <debug> [1242934392.002610] periodic_update(): Roamed from BSSID (none) ((none)) to <router mac address> (<ssid>) 
May 21 12:33:13 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:33:13 kovu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> associated 
May 21 12:33:13 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake 
May 21 12:33:13 kovu NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake 
May 21 12:33:13 kovu NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed 
May 21 12:33:18 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:33:18 kovu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
May 21 12:33:18 kovu NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
May 21 12:33:20 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated 
May 21 12:33:20 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake 
May 21 12:33:20 kovu NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake 
May 21 12:33:20 kovu NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed 
May 21 12:33:26 kovu NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected 
May 21 12:33:26 kovu NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> associated 
May 21 12:33:26 kovu NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake 
May 21 12:33:26 kovu NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake 
May 21 12:33:26 kovu NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed 

```

this is repeating in debug.log:

```

May 21 12:35:30 kovu NetworkManager: <debug> [1242934530.000791] periodic_update(): Roamed from BSSID <router mac address> (<ssid>) to (none) ((none)) 
May 21 12:35:36 kovu NetworkManager: <debug> [1242934536.002838] periodic_update(): Roamed from BSSID (none) ((none)) to <router mac address> (<ssid>) 

```

this is going in kern.log:

```

May 21 12:34:29 kovu kernel: [252841.268264] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 528
May 21 12:34:34 kovu kernel: [252846.256099] Rcv Wcid(1) AddBAReq
May 21 12:34:34 kovu kernel: [252846.256106] Start Seq = 00000000
May 21 12:34:39 kovu kernel: [252851.254794] Rcv Wcid(1) AddBAReq
May 21 12:34:39 kovu kernel: [252851.254803] Start Seq = 00000000
May 21 12:34:50 kovu kernel: [252862.254840] Rcv Wcid(1) AddBAReq
May 21 12:34:50 kovu kernel: [252862.254848] Start Seq = 00000000
May 21 12:34:55 kovu kernel: [252866.983085] Rcv Wcid(1) AddBAReq
May 21 12:34:55 kovu kernel: [252866.983085] Start Seq = 00000000
May 21 12:35:02 kovu kernel: [252873.976631] Rcv Wcid(1) AddBAReq
May 21 12:35:02 kovu kernel: [252873.976638] Start Seq = 00000000
May 21 12:35:07 kovu kernel: [252879.000526] Rcv Wcid(1) AddBAReq
May 21 12:35:07 kovu kernel: [252879.000536] Start Seq = 00000000
May 21 12:35:14 kovu kernel: [252886.255039] Rcv Wcid(1) AddBAReq
May 21 12:35:14 kovu kernel: [252886.255049] Start Seq = 00000000
May 21 12:35:19 kovu kernel: [252891.255179] Rcv Wcid(1) AddBAReq
May 21 12:35:19 kovu kernel: [252891.255189] Start Seq = 00000000
May 21 12:35:24 kovu kernel: [252896.255203] Rcv Wcid(1) AddBAReq
May 21 12:35:24 kovu kernel: [252896.255213] Start Seq = 00000000
May 21 12:35:33 kovu kernel: [252905.255054] Rcv Wcid(1) AddBAReq
May 21 12:35:33 kovu kernel: [252905.255063] Start Seq = 00000000
May 21 12:35:38 kovu kernel: [252910.215274] Rcv Wcid(1) AddBAReq
May 21 12:35:38 kovu kernel: [252910.215274] Start Seq = 00000000
May 21 12:35:46 kovu kernel: [252918.255138] Rcv Wcid(1) AddBAReq
May 21 12:35:46 kovu kernel: [252918.255147] Start Seq = 00000000
May 21 12:35:51 kovu kernel: [252923.255170] Rcv Wcid(1) AddBAReq
May 21 12:35:51 kovu kernel: [252923.255180] Start Seq = 00000000
May 21 12:35:57 kovu kernel: [252929.255225] Rcv Wcid(1) AddBAReq
May 21 12:35:57 kovu kernel: [252929.255236] Start Seq = 00000000
May 21 12:36:03 kovu kernel: [252935.157801] Rcv Wcid(1) AddBAReq
May 21 12:36:03 kovu kernel: [252935.157811] Start Seq = 00000000
May 21 12:36:09 kovu kernel: [252941.255459] Rcv Wcid(1) AddBAReq
May 21 12:36:09 kovu kernel: [252941.255469] Start Seq = 00000000
May 21 12:36:17 kovu kernel: [252949.255634] Rcv Wcid(1) AddBAReq
May 21 12:36:17 kovu kernel: [252949.255644] Start Seq = 00000000
May 21 12:36:28 kovu kernel: [252960.256491] Rcv Wcid(1) AddBAReq
May 21 12:36:28 kovu kernel: [252960.256501] Start Seq = 00000000
May 21 12:36:28 kovu kernel: [252960.274811] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 623
May 21 12:36:35 kovu kernel: [252967.255504] Rcv Wcid(1) AddBAReq
May 21 12:36:35 kovu kernel: [252967.255514] Start Seq = 00000000
May 21 12:36:43 kovu kernel: [252975.255658] Rcv Wcid(1) AddBAReq
May 21 12:36:43 kovu kernel: [252975.255668] Start Seq = 00000000
May 21 12:36:49 kovu kernel: [252981.255619] Rcv Wcid(1) AddBAReq
May 21 12:36:49 kovu kernel: [252981.255629] Start Seq = 00000000
May 21 12:36:54 kovu kernel: [252986.255722] Rcv Wcid(1) AddBAReq
May 21 12:36:54 kovu kernel: [252986.255732] Start Seq = 00000000
May 21 12:37:03 kovu kernel: [252995.255779] Rcv Wcid(1) AddBAReq
May 21 12:37:03 kovu kernel: [252995.255790] Start Seq = 00000000
May 21 12:37:08 kovu kernel: [253000.255957] Rcv Wcid(1) AddBAReq
May 21 12:37:08 kovu kernel: [253000.255966] Start Seq = 00000000
May 21 12:37:14 kovu kernel: [253006.255967] Rcv Wcid(1) AddBAReq
May 21 12:37:14 kovu kernel: [253006.255977] Start Seq = 00000000
May 21 12:37:19 kovu kernel: [253011.255994] Rcv Wcid(1) AddBAReq
May 21 12:37:19 kovu kernel: [253011.256005] Start Seq = 00000000
May 21 12:37:24 kovu kernel: [253016.256061] Rcv Wcid(1) AddBAReq
May 21 12:37:24 kovu kernel: [253016.256071] Start Seq = 00000000
May 21 12:37:29 kovu kernel: [253020.692627] Rcv Wcid(1) AddBAReq
May 21 12:37:29 kovu kernel: [253020.692627] Start Seq = 00000000
May 21 12:37:36 kovu kernel: [253028.255895] Rcv Wcid(1) AddBAReq
May 21 12:37:36 kovu kernel: [253028.255905] Start Seq = 00000000
May 21 12:37:41 kovu kernel: [253033.256612] Rcv Wcid(1) AddBAReq
May 21 12:37:41 kovu kernel: [253033.256622] Start Seq = 00000000
May 21 12:37:46 kovu kernel: [253038.256827] Rcv Wcid(1) AddBAReq
May 21 12:38:15 kovu kernel: [253067.257419] Rcv Wcid(1) AddBAReq
May 21 12:38:15 kovu kernel: [253067.257428] Start Seq = 00000000
May 21 12:38:26 kovu kernel: [253078.256362] Rcv Wcid(1) AddBAReq
May 21 12:38:26 kovu kernel: [253078.256372] Start Seq = 00000000
May 21 12:38:26 kovu kernel: [253078.269970] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 528
May 21 12:38:31 kovu kernel: [253082.658314] Rcv Wcid(1) AddBAReq
May 21 12:38:31 kovu kernel: [253082.658323] Start Seq = 00000000
May 21 12:38:36 kovu kernel: [253087.773660] Rcv Wcid(1) AddBAReq
May 21 12:38:36 kovu kernel: [253087.773660] Start Seq = 00000000

```

similar lines appearing in syslog and messages.

---

### Post by Sportsjd on 2009-05-22
Well, I switched to a new router - Netgear WNR2000 - set it to WPA2 AES and everything works fine.  I didn't have to mess with anything with the drivers.  Worked fine.  Thanks everyone for your thoughts/help!  ):P

---

### Post by GNUbee40 on 2009-05-24
Hey scarf

I know about the wpa-supplicant log. But it annoys me that it doesn't write the date and time. This would make it possible to compare it to the other logs to get the whole picture.

It strikes me that you have a lot of these lines:

```
May 21 12:37:29 kovu kernel: [253020.692627] Rcv Wcid(1) AddBAReq
May 21 12:37:29 kovu kernel: [253020.692627] Start Seq = 00000000

```

I only see these rarely and mostly when my connection is buggy. Maybe this could be a clue...

---

### Post by del_diablo on 2009-06-01
So what version on ralinks site acutally works? Last time i attempted to use the latest it failed.

---

### Post by scarf on 2009-06-02
> **del_diablo said:**
> So what version on ralinks site acutally works? Last time i attempted to use the latest it failed.

yeah i cannot seem to get the new versions to work either.  maybe 1.8.0.0 was the last that worked for me.

[http://www.ralink.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2](http://www.ralink.com.tw/data/drivers/2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2)

---

### Post by del_diablo on 2009-06-04
Well................. Status:
*1.8.0.0, does not work. Not detecting any networks and cannot connect
*2.1.0.0, same as above.......... :(
*9.04 kernel included: Not working :(

From what i read in this tread also: the driver can only see WPA networks, but thats a option to change the one over here because the way i use my laptop.........

---

### Post by scarf on 2009-06-07
dear all,

i think we are finally getting towards the bottom of this.

please check out this [latest post](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891/comments/98) to the [wireless rt2860 not connecting to WPA bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891)

i also recommend subscribing to that bug so you can keep following the progress.

---

### Post by null_pointer_us on 2009-07-03
Software:
 - Ubuntu 9.04 x86_64
 - updated kernel 2.6.28.13 (?)
 - RT2860 driver included with kernel, no driver patches
 - wireless card installed after OS installation

Hardware:
 - Linksys WRT54G (G router)
 - Encore ENWHI-N (N router)
 - Encore ENLWI-N (RT2860 adapter)

The adapter could not connect to either router. I did some reading and concluded that the driver has problems deciding which security settings to use when several are available. However, limiting the routers to WPA2PSK TKIP security did not fix the problem.

The fix was simple: create a [RT2860STA.dat file]("http://ubuntuforums.org/showpost.php?p=6079224&postcount=1") with the appropriate CountryCode, SSID, WirelessMode, Channel, AuthMode, and EncrypType.

After that, I could configure NetworkManager to connect although the connection status shows a lower speed rating and has less stability than in Windows. But it's much better than nothing!

This sounds easy, but figuring this out took hours. I wonder why the RT2860STA.dat file was not present on my computer. It had to be created manually. Something needs to be fixed.

(Maybe this will help someone else.)

---

### Post by physeetcosmo on 2009-08-16
> **GNUbee40 said:**
> 
Hopefully no typos in this :D 
Respect to the guys from Launchpad for figuring this out. Hopefully the patch will soon be included in future releases of the driver.

Cheers
GNUbee40

GNUbee40,

This seems to work great on my eeePC 1000h. When i downloaded the patch, it had some "awfullongfilename.patch", and i renamed it to "patch.patch" which didn't have any issues during compilation. i can now connect to my WPA secured network!!! Thanks alot!

=D>

---

