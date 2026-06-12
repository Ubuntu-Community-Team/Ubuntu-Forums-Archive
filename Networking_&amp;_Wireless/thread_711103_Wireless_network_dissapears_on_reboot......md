---
title: "Wireless network dissapears on reboot....."
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Guitaraholic on 2008-02-29
Ive finally managed to get my wg111t working in ubuntu and it works GREAT

my problem is that if i turn off my pc and reboot its lost....

when i check ndiswrapper -l the drivers are loaded and device is present 

the way ive been fixing  this is by redoing 

depmod-a
modprobe ndiswrapper

and then rebooting
and it works but until i reboot again.....

I think the issue is with the driver bein loaded in the linux kernal on boot....is there any other settings i need to save to get the settings to stay everytime??

thanks

---

### Post by heyster on 2008-02-29
I think we can take the conclusion that Ubuntu and maybe Linux in general is not ready for Wifi yet.
We need to go back to the " wire"  or install Ubuntu Mobile :-)
I hope that the new main release will have bether Wifi support or just leave it out when it don't pass the quality check.

---

### Post by Guitaraholic on 2008-03-01
hmmm.....

what teminal command do i need to make this save into the kernal file so i can get it to load everytime i load ubuntu?

---

### Post by andrewabc on 2008-03-22
I have the same problem. I have trendnet 432brp wireless. I can get the internet to work.
I loaded the windows .inf file with ndiswrapper. When I do ndiswrapper -l  it lists the driver.
To get the internet to work on each boot I type in terminal
sudo modprobe ndiswrapper
Then it shows up in network config, and I can connect to the internet. But as soon as I reboot I lose the internet and have to type it in terminal again.

How do I make it so it remembers my internet connection?
Using hardy beta.
Is there something I need to startup each time? I tried to save my session with the internet working but that did not work.

At
[http://ubuntuforums.org/showthread.php?t=709447](http://ubuntuforums.org/showthread.php?t=709447)
someone says to 
> 10)DO NOT FORGET THIS STEP - go back to terminal and copy paste in the following command:

Code:

sudo gedit /etc/modules

a new window (text file) will open...at the bottom there is a list of names...add ndiswrapper to this list (do not misspell)
save file...reboot to ensure everything is working... TA DA your done

---

### Post by kevdog on 2008-03-22
Just type this and your ready to go:

echo ndiswrapper | sudo tee -a /etc/modules

Done!

---

### Post by andrewabc on 2008-03-22
Hi kevdog.
That added ndiswrapper to modules which is same thing as I put in end of my previous quote.
This works in the sense that it does start ndiswrapper when computer starts.

But I still have to go into network settings and change a setting for my wireless settings.
Upon boot it changes settings to password type: WPA personal, when I need it to be WEP key.
Currently the network is not password protected until I make sure internet works.

I will continue testing the settings.

---

### Post by kevdog on 2008-03-22
Whats in your /etc/network/interfaces file?

What does
iwlist scan 
show?

---

### Post by andrewabc on 2008-03-22
With internet working
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:47:32:F0
                    ESSID:"TRENDnet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Will post same scan after I reboot.

EDIT:
After reboot
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:47:32:F0
                    ESSID:"TRENDnet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


With security turned off on my router. When I start ubuntu it defaults to using WPA personal security (network password is blank). In order to get the internet to work I change it to ASCII and leave password blank.

Interfaces file has
> auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid TRENDnet

I tried enabling WPA ascii and hex security, but it didn't work. Network manager did remember the proper security setting and password after rebooting.

Hmm. Once I do get the internet working, I can change security to WPE, WPA, WPA2 (no password) and the internet keeps working.

EDIT:
Rebooted computer and it has WPA as default. I switched to WPA2 and it did the "changing interface configuration" progress bar like it normally does when changing network settings. Then my internet worked. So it seems my internet will work as long as I change the security type to anything so that it does the "changing interface configuration" progress bar.
So there must be a setting or something that is not being remembered when rebooting. Maybe it has to scan the network or something?

---

### Post by jonnywombat on 2008-03-22
hi..

I got a similar problem..
 
I have atheros 5006eg chipset.. I use ndiswrapper and the xp 64bit drivers (using 64bit hardy).

I set this up and restarted and all was good... I then shutdown and went off and did some other stuff. When I next booted the machine ndiswrapper and the drivers appeared to load ok, and I cn see my wireless network, but I cannot connect.. I do not get either green dot lit, and the blue whirly thing just goes around until it times out.

As I said It connect perfectly before.. and nothing else has changed (in fact no one has been in the house in the time in between). Any thought would be welcome

Ta 

Jonny

---

### Post by andrewabc on 2008-03-22
For me when I start the computer it just shows the normal network connection icon (2 black monitors, one behind the other). I don't see the wireless connecting icon.

---

### Post by unutbu on 2008-03-22
andrewabc, add 

```
auto wlan0
```

to /etc/network/interfaces.

Run 'man interfaces' and search for 'auto' for more info.

---

### Post by andrewabc on 2008-03-22
Thank you. My interfaces is now
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid TRENDnet
And it works! Takes about 20 seconds after booting up for the internet to work, but that is fine. Now to test the security features.

EDIT:
I could not get wep security working. On my router I tried 
WEP 128 bit hex open
WEP 128 bit hex auto
And neither worked. I am pretty sure I input the correct password, I typed it in a couple times, made sure all characters were correct. This isnt very important since I do not live in an urban area.

---

### Post by heyster on 2008-04-01
Thanks all. We can shake hands :-)
Once a while when I boot the laptop my Internet is also not there. But when I boot again it connects to the wireless lan. Do it like the Germans say "Reboot tut gut". A reboot is never bad.

---

### Post by lswest on 2008-04-01
You can try to install WICD to manage your network or try configuring it in the terminal with ```
sudo iwconfig [name of device] essid [name of network] key [wireless key] && sudo dhclient [name of device]
```  Don't know if you solved it already, but it might tell you if the key is being accepted or not.

---

