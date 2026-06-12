---
title: "Wireless Won't Turn On PLEASE HELP!"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by halomasta on 2007-03-05
My card is on this page

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

Ubuntu 6.10 .. Compaq Presario 2200 .. Works well after installing fwcutter, wpasupplicant, and network-manager-gnome. 

I have the newest version of ubuntu and I have a Compaq Presario 2200. But it's not working so well....

I need ALOT of help. Step by Step instructions would be best.

Thanks!

---

### Post by srhegde on 2007-03-05
This is what I did to get my dlink working:
This is very fresh in my memory, so I am just putting it down here

[LIST=1]
[*]Download the win-xp driver from the dlink website and unzip it to a directory
[*]Install the ndiswrapper - [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) gives you a very neat explanation, even the README/INSTALL/man of ndiswrapper is very easy to follow.
[*]Go to the directory where the win-xp driver is copied.
[*]Execute the following commands
[*]sudo ndiswrapper -i <filename> (replace filename with the .inf file in the directory)
[*]sudo modprobe ndiswrapper
[*]Next you open the wireless assistant (wlassistant) and select the network, use the WEP key if required.
[*]You should all be set
[/LIST]

I am yet to get the wireless working on bootup, if and when I get it working, I will post the procedure!

Hope this helps

---

### Post by halomasta on 2007-03-05
How do you execute commands? Also how do i install it?

Also I'm on Windows XP. How am I suppose dot get the files to linux?

---

### Post by benfindlay on 2007-03-05
By execute commands, I believe srhegde means type 5 and 6 into a terminal and hit ENTER between each one

Hope this helps!

---

### Post by srhegde on 2007-03-05
Okay, here is what you do

Copy my post on a piece of paper. 
If you cannot connect to internet with wire (not wireless), then copy the driver files to a USB drive or floppy.
Boot with ubuntu
Execute the commands in a gnome-terminal or konsole

---

### Post by halomasta on 2007-03-06
My network card is listed and supported. I have the driver on linux but the problem is the card will not turn on. When I press the button it won't turn on which means Linux does not recognize this.

If you can answer this question also it would be nice:

My laptop doesn't sleep, hibernate, or anything. No matter what option I choose my Laptop goes to a dark screen. It's still on but whatever button I press the screen will still be black. 

Thanks for your help

---

### Post by StereoHeathen on 2007-03-06
Same problem here, I would think from what you're (kind of) describing

---

### Post by halomasta on 2007-03-06
Yeah my network card won't turn on at startup. I installed the driver correctly I just need the stupid thing to turn on.....

Also why do all the tutorials say you need to do a whole bunch of code? I installed the driver graphically.

---

### Post by StereoHeathen on 2007-03-06
I installed mine via terminal, but yeah, same thing. Won't turn on, even after messing with the BIOS settings for it.

Edit: Well, I made it work somehow. I'm not quite sure how, but I configured all the settings and it works just as well as it should now.

---

### Post by halomasta on 2007-03-06
Do you have any intructions? Is yours set-up like mine? Where you have to press a button to turn it on?

---

### Post by halomasta on 2007-03-06
I have a light on my laptop to tell if it's on. I have the driver installed and it reconizes my hardware. But the light still won't come on. I am using fiesty...can anyone help?ware. But the light still won't come on. I am using fiesty...can anyone help?

I am using a broadcom if that helps.

Thanks for all your help...Ubuntu rules

---

### Post by halomasta on 2007-03-06
I am using Compaq Presario 2200 if that helps also

---

### Post by teaker1s on 2007-03-06
if your using ndiswrapper you need
ndiswrapper-utils-1.8
install with synaptic

---

### Post by halomasta on 2007-03-07
I used ndiswrapper trust me i've done every tutorial. The light won't turn on. I know it works because it works in windows. Is there ayhting I can do?

---

### Post by halomasta on 2007-03-07
Is there something else I can show you to help? I am using 7.04 fistey fawn

---

### Post by halomasta on 2007-03-07
I have everything installed. The firmware, the driver, everything. Ubuntu reconizes I have the card. Problem is the blue light won't turn on when i press it.

Using Fiesty
Compaq Presario 2200
Broadcom

Please help I feel I am SO CLOSE:mad: 

Tell me what else I should post I can get you screenshots. Please I'll do anything.....HELP ME!!!:KS :KS :KS

---

### Post by conjur3r on 2007-03-07
What have you done?  What wireless settings is your network in?  Dont' give specifics, just like infrastructure, wpa, hidden ssid, etc...

You are using ndiswrapper right?

---

### Post by chili555 on 2007-03-07
Just because the light won't turn on doesn't necessarily mean the radio is off. I have read a number of posts on this forum where posters go to extraordinary lengths to get the light to turn on as the button is pushed. Other posters say it works fine.

The true tests are if iwconfig shows something like:```
eth1 radio off ESSID:off/any
``` then the radio is off. If sudo iwlist eth1 scan produces scan results, then, regardless of the light, the radio is on.

If these tests seem to indicate the radio is on, go ahead and configure your interface and connect. Obviously, substitute your interface, wlan0, ra0, etc. in the above examples.

Post back if we can help.

---

### Post by halomasta on 2007-03-07
kristhagreat@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by halomasta on 2007-03-07
kristhagreat@ubuntu:~$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.

kristhagreat@ubuntu:~$ sudo iwlist lo scan
lo        Interface doesn't support scanning.

Yeah I have the hardware and everything installed. It just refuses to turn on. I have no idea why. I do use ndiswrapper.

---

### Post by halomasta on 2007-03-08
Any other suggestions....?

---

### Post by benfindlay on 2007-03-08
if you open a console and type ```
sudo ndiswrapper -l
``` does your card come up as both hardware and driver present?

---

### Post by halomasta on 2007-03-09
Yes

---

### Post by FreeJersey2007 on 2008-02-08
Resurrecting this one.  I just got the same problem, though it had been working before.

For full disclosure, this just started after I tried to add additional memory, which was faulty.  I went back to the original memory and everything works fine aside from the inability to turn on the card.  I even did a fresh install of 7.10 to clear out any variables.  Driver is installed, hardware is present, you can see the device in iwconfig as Power Off.  I have a Toshiba L15.  Just wondering if there's any utility (command line or otherwise) to force the thing on.  iwconfig has a Power parameter, but that's not helping.

---

