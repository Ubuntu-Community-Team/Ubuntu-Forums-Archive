---
title: "Problem with wireless connection"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by boilermaker on 2007-01-06
Hey,

I installed ndiswrapper and added the actual driver file from windows and here is what i got!



$ ndiswrapper -l

Installed drivers:
bcmwl5          driver installed, hardware present 



$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


When i tried to install Network Manager


./configure

....... (bunch of garbage!)
......
checking for wireless-tools >= 28pre9... no
configure: error: wireless-tools >= 28pre9 not installed or not functional

I am not sure if that was suppose to mean something (the last line)

When i tried double clicking network manager it says
" Failed to execute child process nm-applet"

ok also the i am able to load the network connection and signal meter at startup but it says not connected ](*,) 


I would be really happy if you someone can help me out.....


CAn you also tell me what this is suppose to mean

Blacklist native bcm43xx drivers

    * Type:
      Code:

      sudo gedit /etc/modprobe.d/blacklist

    * Add the line:
      Code:

      blacklist bcm43xx

    * After saving type at the terminal:
      Code:

      sudo rmmod bcm43xx



Sorry for such a long thread!

:)

---

### Post by aminoz on 2007-01-06
Can't help much with NM; I'ved only just started playing with it.  The "blacklisting" stuff is about disabling an existing broadcom driver that comes already installed with Ubuntu, but I don't think it works too well, at least it doesn't on my Dell 1300 

For  ndiswrapper to work, you have disable the default Ubuntu driver  using the blacklisting procedure, otherwise it will conflict with ndiswrapper.  I am using ndiswrapper and it works ok.  it was good to see my wireless light go on at last.

---

