---
title: "Wifi inconsistant - but always shows connected (Intel Wireless 3165 Rev 79)"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by lxr200 on 2016-10-28
Hello everyone! First time Linux user - got interested after watching some A+ lectures and figured I'd give it a shot. SO my issue is that my wifi seems to be very sporadic, my wifi icon shows it is always connected but it will randomly not have Internet access and I need to disconnected and reconnect for it to resume internet connectivity (even though it shows always connected). My current set up is a Dell Inspiron 13-7353 and installed Ubuntu 16.04 on a separate partition on my SSD

here is my wireless-info text [http://pastebin.ubuntu.com/23391524/](http://pastebin.ubuntu.com/23391524/) to get that out of the way.

I've found similar posts here: [http://askubuntu.com/questions/657774/how-to-get-my-intel-wireless-3165-to-work](http://askubuntu.com/questions/657774/how-to-get-my-intel-wireless-3165-to-work) and here [https://ubuntuforums.org/showthread.php?t=2219917](https://ubuntuforums.org/showthread.php?t=2219917) and I have tried everything I could within those posts to try to fix my network issue but have not had any luck. I will say, the only thing that I could not get to work, is the command for setting my country for my wireless settings.. "sudo iw reg set US" no matter whenever I check it shows "Country 00: DFS-UNSET" I'm not sure if that has anything to do with it, but I have no idea what else to do or where else to check. I've also verified my Power Save option on my wireless settings is off.

Thanks in advance for your help, and I really hope I didn't stupidly miss something.

-Luke

EDIT: I've noticed whenever I restart my wireless power management automatically turns itself back on.

---

### Post by Hadaka on 2016-10-28
Hi, from your wireless report.
```
wlp1s0    IEEE 802.11abgn  [COLOR=#ff0000]ESSID[/COLOR]:"Pretty Fly For A Wi-Fi"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: <MAC 'Pretty Fly For A Wi-Fi' [AC1]>   
          Bit Rate=433.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          [COLOR=#ff0000]Power Management[/COLOR]:on
```
[COLOR=#ff0000]ESSID[/COLOR]
Please access your router configuration and remove the spaces in the ESSID name. change to 
example ->    Pretty_Fly_For_A_Wi-Fi 
While in the router configuration settings please also remove the [COLOR=#ff0000]TKIP [/COLOR][COLOR=#000000]change to [I]WPA2 AES 
[/I]you may also want to try a different channel other than 157 or try the 2.4Ghz setting 
[/COLOR]
 [COLOR=#ff0000]Power Management[/COLOR][COLOR=#000000]
```
gksudo gedit /etc/network/if-up.d/off-power-manager
```
Enter these 2 lines into the editor..
```
#!/bin/sh
/sbin/iwconfig wlp1s0 power off

```
*Save and close gedit
*Back to Terminal...ctrl/alt/t
```
sudo chmod +x /etc/network/if-up.d/off-power-manager
```
[/COLOR][COLOR=#ff0000]Country Code[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#000000]```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/& US/' /etc/default/crda
```
then do..
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo iw reg set US\nexit 0" | sudo tee -a /etc/rc.local
```

[/COLOR]

---

### Post by lxr200 on 2016-10-29
Thanks for the reply!

So first off when doing the power off code It opens up that txt file and I enter the code, save and exit. but it pops up with the following

```
** (gedit:2283): WARNING **: Set document metadata failed: setting attribute metadata::gedit-spell-enabled not supported.
** (gedit:2283): WARNING **: Set document metadata failed: setting attribute metadata::gedit-spell-enabled not supported.
** (gedit:2283): WARNING **: Set document metadata failed: setting attribute metadata::gedit-spell-enabled not supported.
```

I still do the chmod code and recheck and my power management is still "on"

for the country code I enter all the strings of code, and on the "echo sudo sed....." command it brings a white ">" in terminal, I entered the other 2 strings, and then it just stays at a white ">". I closed it and checked and my country code is still "Country 00: DFS-UNSET"

EDIT: sorry if this is stupid, but as far as the remove the TKIP I have no idea what you mean, and WPA2 AES I'm not too sure what that is. I have the ability to change WPA2 Personal, WPA2 Enterprise, and then WPA2/WPA Mixed personal or Mixed enterprise. - sorry if this is making anyone cringe at me not knowing.

EDIT 2: Googling around, found its a type of WPA2 security but I'm not finding the ability to change it on my routher (Linksys AC2600 / EA8500) but I'm still searching.

---

### Post by Hadaka on 2016-10-29
Hi my error on the command, I apologize, it should be..

```
gksudo gedit /etc/network/if-up.d/off-power-manager
#!/bin/sh
/sbin/iwconfig wlp1s0 power off
```
*Save and close gedit

open a terminal and do..
```
sudo chmod +x /etc/network/if-up.d/off-power-manager
```
boot and see if it is now off.

on the country code...please Copy and paste the 4 commands
thanks.

---

### Post by lxr200 on 2016-10-29
I tried the country command codes again and still didn't seem to work.

[http://imgur.com/lHePVjU](http://imgur.com/lHePVjU)

The power command seems to have worked, I installed the gksudo program and ran the codes, got errors shown below (is this normal?), but it seems my power manager is off now. 

```
luke@Luke:~$ gksudo gedit /etc/network/if-up.d/off-power-manager

(gksudo:3136): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

** (gedit:3150): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:3150): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported


```

---

### Post by Hadaka on 2016-10-30
Hi please boot your computer then do..
```
iw reg get
```
is it still 00 ??
also please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
thanks.

---

### Post by lxr200 on 2016-11-02
Hello! Sorry for the late replay, I was dealing with a lot of crap about my car and freaking out a little. Anyways, Yes my country is still 00. Also my wireless still seems to "lose Internet" while still being connected to my router, this is the only device that it happens to, and only while on ubuntu, when running windows, it never happens fyi - could be country code related but I have no idea.

When it happens I don't get any notification of being disconnected, I just don't have internet even though it shows full signal on my network indicator. I have to click on my wi-fi icon, and click on my connected network, it will disconnect then automatically reconnect and I'll have internet again. It seems to be random but Usually happens after 5 - 10 minutes.

Here is the link for my wireless-info that I just created.

[https://paste.ubuntu.com/23418928/](https://paste.ubuntu.com/23418928/)

---

