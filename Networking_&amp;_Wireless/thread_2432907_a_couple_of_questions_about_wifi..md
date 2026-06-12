---
title: "a couple of questions about wifi."
date: 2019-12-10
forum: Networking &amp; Wireless
---

### Post by wolftrax on 2019-12-10
hi.
I been using ubuntu lst releases  for  several years and just recently installed the new version of ubuntu  and find a sertting in wifi that I dont underrstand the meaning of.  I cant find anything on google or the danish ubuntu foirum  userguides but its titled flytilstand which directly translated is airplane settings on/off and since I live nearby a airport I would really like to know what that setting does ?

the uname -output for that question is 

Linux unix 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

I live in a area where lots of planes or helicopters come by often.  its both medical and military and regular airports that happens to be at a close range to where I live in so I see and hear planes everyday and often a helicopter .
hope someone can explain me exactly what it is and what it does. 

thanks for your time.

---

### Post by TheFu on 2019-12-10
airplane mode disabled all RF devices on a computer. This is the same as tablets and smartphones.  
It disables wifi and bluetooth.  Basically, using either is/was forbidden during take-off and landing on commercial airlines.

However, since all RF is a 1/r**2 law, the idea that wifi radio in any portable computing device can impact copper wires outside the passenger cabin isn't scientifically sound.  Whatever.  Soccer mommies rule the airport security world.

---

### Post by wolftrax on 2019-12-11
thanks. 
that helped me a lot.  

where can I find the man pages on this ? 

thank you .

---

### Post by TheFu on 2019-12-11
Have you searched all the local manpages with **apropos** for  the programs?  Getting useful results from apropos for tertiary functions is nearly impossible.  The manpage for the program with the settings should have something.

---

### Post by chili555 on 2019-12-11
> **TheFu said:**
> airplane mode disabled all RF devices on a computer. This is the same as tablets and smartphones.  
It disables wifi and bluetooth.  Basically, using either is/was forbidden during take-off and landing on commercial airlines.

However, since all RF is a 1/r**2 law, the idea that wifi radio in any portable computing device can impact copper wires outside the passenger cabin isn't scientifically sound.  Whatever.  Soccer mommies rule the airport security world.Correct.

Its only use, as far as I know, is when you are actually on board the airplane and you are instructed to turn off all wireless devices. After you set your wifi to Airplane Mode, you can still use your laptop, tablet or phone to watch a movie that you previously downloaded, continue working on you next novel on a word processor, or, everyones favorite, play solitaire. 

Living near the airport and necessarily using wireless should be no danger at all.

---

### Post by wolftrax on 2019-12-13
I did not know that command  apropos . thanks.

---

### Post by TheFu on 2019-12-13
I use airplane mode all-the-time with phones and tablets.  It is a quick way to avoid city RF tracking poles claiming to be used as "Smart Cities" without having to use a Faraday pouch. [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5134626/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5134626/)  They call it **Internet of People**.

I prefer not to be tracked and will accept a little inconvenience to make that just a little harder.  I used to work in telecom and for the federal govt. Nobody is really out to track me specifically, except data brokers trying to sell my location data so others can sell us stuff. Once the data is captured, it has been used by govts world-wide in phishing for criminals without using warrants.  

Being paranoid only makes sense when there are proven reasons.

---

### Post by wolftrax on 2019-12-15
sorry but I could not find the manpages on the progrram.  what I need to know is how to configure internet and wireless from commandline if need be.

---

### Post by TheFu on 2019-12-15
> **wolftrax said:**
> sorry but I could not find the manpages on the progrram.  what I need to know is how to configure internet and wireless from commandline if need be.

Here's a start:

```
$ apropos wifi
wifi (1)             - enable/disable internal wifi (wireless lan) device

$ apropos bluetooth
blueman-applet (1)   - a tray applet for managing bluetooth
blueman-assistant (1) - application for configuring and pairing bluetooth devices
blueman-manager (1)  - bluetooth device manager
blueman-sendto (1)   - application for sending files to bluetooth devices
blueman-services (1) - Configure local bluetooth services
bluetooth (1)        - enable/disable internal bluetooth device
bluetoothctl (1)     - bluetooth control tool
bluetoothd (8)       - Bluetooth daemon
btmon (1)            - Bluetooth monitor
ciptool (1)          - Bluetooth Common ISDN Access Profile (CIP)
gatttool (1)         - tool for Bluetooth Low Energy device
hciconfig (1)        - configure Bluetooth devices
hcitool (1)          - configure Bluetooth connections
hid2hci (1)          - Bluetooth HID to HCI mode switching utility
mpris-proxy (1)      - Bluetooth mpris-proxy

```

Your system is most definitely different from mine, so the manpages available will be different.  I use wicd-curses for wifi setup.  Most Ubuntu-flavored desktops would use network manager ... network-manager{tab} and nm-{tab} should show those programs, if they are in the PATH.

Network configuration has changed drastically the last few years. The exact ubuntu release you are running will have different answers then others.

---

### Post by wolftrax on 2019-12-15
thanks.  I run ubuntu and but running apropos gives me no man pages. 

uname -a
Linux unix 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

apropos wifi 
wifi: ingenting egnet.

I am Danish so perhaps its why there is no manual entries for it or its not installed. 

the output of man man will give me man pages on the man program in Danish so I figure its because there is no translated man pages for wifi yet or its simply not installed. 

the reason I ask is because I got a old computer I want to use as commandline system only and it ran freeDOS and minimal freeBSD install and it can run solaris 10 as well but I need to buy a wireless adapter because its so old that it has no build in wireless and I want to be able to configure it in a console only environment. 

its a old HP pavilion ze5600 that I been trying to get to run something useful with a desktop but the only thing that is not so slow is solaris 10 and desktop BSD 8.2  other than that I cant find a linux distribution that is not too slow.  some distributions cant find the hardware either , its the graphics card that usually is the problem but on opensolaris it wont find the drivers for the soundcard.   Debian buster wont find the graphics card either. 

I just want to see if I can find something useful to do with it its not a matter of life or death but it would be nice to get it to work with wireless internet as well.   the power supply must always be plugged in because there is no battery capacity anymore so if I could get wireless on it that would be much easier to find a place where it can stand in a other room without having to use cabled connection.

---

### Post by chili555 on 2019-12-15
Possibly helpful: [https://askubuntu.com/questions/1164074/how-to-connect-to-wifi-using-just-the-terminal/1164095#1164095](https://askubuntu.com/questions/1164074/how-to-connect-to-wifi-using-just-the-terminal/1164095#1164095)

---

### Post by TheFu on 2019-12-15
Exactly how will you add wifi to the machine, physically?

---

### Post by wolftrax on 2019-12-15
you can buy a USB wireless adapter that you plug into the USB port and it should be working as a wireless card . at least that is what the sales person told me but I never seen it before so I don't know if it works.

---

### Post by TheFu on 2019-12-15
> **wolftrax said:**
> you can buy a USB wireless adapter that you plug into the USB port and it should be working as a wireless card . at least that is what the sales person told me but I never seen it before so I don't know if it works.

Yes, that is true.  I didn't want to assume USB or PCI or PCIe or PCMCIA.  If you pick the USB adapter well, it will be plug-n-play.  Automatic.  If you pick poorly, it may never work. Look at the specific wifi chip uses.

---

### Post by wolftrax on 2019-12-16
thanks.  I will have to do some research on it before I buy it then.

---

### Post by chili555 on 2019-12-16
> **wolftrax said:**
> thanks.  I will have to do some research on it before I buy it then.Please check here: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

