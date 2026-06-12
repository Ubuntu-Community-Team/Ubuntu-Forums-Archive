---
title: "Mobile broadband"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by Okami on 2008-10-05
How do I configure mobile broadband in network manager 0.7? It is a MC8775 PCI Express Mini Card from Sierra Wireless and Ubuntu finds it when I try to configure. The only information I have from my ISP is a PIN-code, PUK-code, APN and a profile name, no username or password.

---

### Post by Okami on 2008-10-06
No one? I forgot to say I am sorry for my bad English, hope my question is understandable.

Thanks anyway.

---

### Post by Plumtreed on 2008-10-06
Sorry, I don't use NM 0.7 yet but the following Wiki might help.[HTML]https://wiki.ubuntu.com/NetworkManager/Hardware/3G[/HTML]

---

### Post by Okami on 2008-10-07
Thank you. I actually use Ubuntu 8.10 and when I updated today wired network also stopped working. So I will just wait and see if the problem with mobile broadband solve itself when 8.10 really is out.

---

### Post by Okami on 2008-10-30
I still cant get it to work. I reinstalled Ubuntu 8.10 today and it recognizes the modem and opens the wizard for mobile broadband. But then it says "network disconnected".

Any help would be appreciated.

Thanks in advance and sorry for my bad English, hope it is understandable. =)

---

### Post by Plumtreed on 2008-10-30
Good to see you have installed 8.10 along with NetworkManager! I stuck with Hardy 8.04 but did install NetworkManager 0.7 and found that it works well. At the present time I access the internet via the 3UK network's mobile broadband and a WIFI connection. The only trouble I have seems to do with the 'drop-down' menu from NetworkManager which fumbles with the selection and this means I have to reinstall the dongle. It usually gets to the right selection after a few tries and works from there.

I previously pointed you to a page that has a table of devices and the correct terms used to configure these devices. Check it out right to the bottom to see if it refers to your dongle. You can 'cut & paste' the thread. It does include dongles and things used in Sweden.

Tell us how you go!

By the way did you know you can edit the connection by right clicking the 'icon'?

---

### Post by Okami on 2008-10-31
Thanks again
I looked at the link you posted and found the modem from sierra, but I could not get it to work.

I also tried with the linux guide on sierra wireless homepage, and found out that the drivers are already installed when writing modinfo sierra in a terminal.

I do not have a dongle, the modem is build in.

---

### Post by CbrPad on 2008-11-04
I'm having that 'network disconnected' issue as well.  What seems to be happening with me is that Network Manager is not passing the Pin code to the modem.  I run a wdial script which passes it over, then I disconnect from the script, run Network Manager and it works fine then.  Hopefully this might help some?

---

### Post by Okami on 2008-11-04
Thank you for your answer. Can you tell exactly what I have to do? I dont know what script you mean.

Thanks.

By the way, is there another program than Network Manager to use which can pass the PIN code to the modem?

---

### Post by CbrPad on 2008-11-04
I did the following in a terminal...  

sudo gedit /etc/wvdial.conf  

and changed mine as below - it still doesn't connect but at least gets the Pin across (you'll probably want to make a backup of yours first,e.g. sudo cp /etc/wvdial.donf /etc/wvdial.old )

You'll probably have to change Modem to wherever your device is and also change the last four settings to whatever your providers should be (these should also be in your Network Manager settings).

Save that and then just type wvdial in the terminal. Once it comes up with waiting for connect or whatever press Ctrl and C to disconnect, then try to connect with Network Manager.  This works for me so if it's a Pin problem you also have fingers crossed it'll also work.




[Dialer cellular]
[Dialer Defaults]

# Your modem device. Usually /dev/ttyUSB0 or /dev/ttyACM0
# Bluetooth devices use an rfcomm device (/dev/rfcomm0, etc) that must be set
# up first.
#
Modem = /dev/ttyUSB0

# Port speeds that're worth testing:
# 921600
# 460800
# 115200
#  57600
Baud = 460800

# If your SIM card has a PIN, comment this line, uncomment the next one, 
# change the PIN shown to your PIN.
#Init = ATZ
 Init = ATZ+CPIN="6666"

Init2 = AT+CGDCONT=1,"IP","open.internet"
Phone = *99#
Username = gprs
Password = gprs

---

### Post by Okami on 2008-11-04
Thanks again.

It didnt work =( It said "modem not responding"

---

### Post by CbrPad on 2008-11-05
Ok, here's maybe another alternative to using Network Manager.  I've since been googling about on my own pin problem and found a tool called Umtsmon.  A bit more googling led me to a forum post here !   

[http://ubuntuforums.org/showthread.php?p=5449081](http://ubuntuforums.org/showthread.php?p=5449081)

I followed step one and got it installed with no problems.  I was then able to run a command to disable my pin, woohoo, but even better, I've found that I'm able to put in my usage allowance and it tracks it and warns me.  

Anyways, getting sidelined, maybe try it out and see if it picks up your card.  There's a list of some of the supported cards and other info at [http://www.umtsmon.org/](http://www.umtsmon.org/)

---

### Post by blackcoatman on 2008-11-05
Same for me here for my 3G stick modem, i am also prompted to enter the PIN when I insert the modem but then I will just not connect. Network Manager 0.7 used to work fine when installed over the Alpha and Beta version of Ubuntu 8.10.

In order to use UMTSMON, you must have QT. I can only download it from Windows due to this 3G problem, unfortunately. Where can one find the depndencies for manual download for it?

---

### Post by CbrPad on 2008-11-05
Same problem alright, it used to work fine and request the pin in Hardy but no longer.

I'm not sure I understand you about QT, I'm running Gnome and it works great, though I do have some Kde stuff installed as I run Amarok etc.

A look at Synaptic tells me the dependencies are..

libc6 >=2.4
libgcc1 >=1:4.1.1
libqt3-mt >=3:3.3.8-b
libstdc++6 >=4.1.1
libusb-0.1-4 >=2:0.1.12
libx11-6
libxext6

I'm also attaching the .deb I generated with Alien.  Hope this helps.

---

### Post by geyids on 2008-11-06
What if who want to share the connection?

---

### Post by blackcoatman on 2008-11-08
libqt3-mt is a library for QT... Since you have some kde apps installed (and QT is a kde standard), you probably have this too.

I manually installed the .deb files i needed for umtsmon and now I can use it instead of network manager... 

Unfortunately, it only works ok for me when I disable speed/traffic monitoring, so I have to estimate it and add it to my Usage statistics in Windows to know if I am out of pre-paid traffic limits, lol

But at least I could finally install the apps I wanted!
(which brought me new problems, nevertheless, as you can see in the Video section of the forum :P)

---

