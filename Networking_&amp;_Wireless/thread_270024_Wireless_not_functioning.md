---
title: "Wireless not functioning"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by mayben on 2006-10-02
I am using a custom build laptop with a linksys wireless G pcmcia adapter (model # WPC54G). I cant connect to any wireless network. I went to the getting started forums first and read all the docs on how to connect to wireless networks and howto troubleshoot wifi. None of which helped.

I checked device manager and lshw and the device and driver showed up fine.

Under network settings I deactivated my ethernet and made the only default gateway my wireless connection.

Under properties of my card I enabled the connection put in my ssid and chose DHCP for configuration.

Yet after activating  I still cant connect to the web and when I go back under network settings my wireless card is set BACK to not active status.

In terminal under iwconfig it lists everything correctly except my frequency is off and my AP is "invalid".

When I attempt to change the channel or frequency I get this error.

"SET failed on device eth1 ; Operation not permitted."

My wireless device worked last night right before I installed Ubuntu. 
I am new to linux so I am now out of idea's on how to fix this. Any ideas anyone?

---

### Post by darth_vader_ca on 2006-10-02
I have the same wireless card for my notebook. what you require is the ndiswrapper as well as the wifi tools, you can install them in ubuntuu. after you have them installed you need the windows drivers via download or cd. copy them to your desktop in linux. then in the terminal run ndiswrapper -i "i think its the bcm one in the folder you have to type. after it installs you can type ndiswrapper -l it should say that the hardware is present. reboot your laptop and you can configure it in the networking area.


cheers.

---

### Post by darth_vader_ca on 2006-10-02
I could forward you detailed instructions if requested.

cheers.

---

### Post by gem1849 on 2006-10-02
Can you help me too? I have an HP with an internal 802.6b wireless card. It normally auto detects the web. I tried installing the drivers but it won't let me.

---

### Post by darth_vader_ca on 2006-10-02
gem1849 what is your wireless card brand and model do you know.?

cheers

---

### Post by darth_vader_ca on 2006-10-02
Hi Gem

since your wireless card is a Broadcom chipset you can use ndiswrapper, do you have the windows drivers on your cd? all you have to do is copy the drivers in a folder on your desktop 
then install ndiswrapper and wireless tools using synaps. after its installed go to your terminal and type sudo ndiswrapper "input what the driver is" after it goes through the install type ndiswrapper -l and see if the hardware is present, once it is reboot the notebook and you should see your adapter present. if not, reply and I will get the detailed instructions when i got home tonight after work.

cheers.

---

### Post by mayben on 2006-10-02
Yes please that would be extremely helpful my email address is [email]nicklydick@gmail.com[/email].

---

### Post by darth_vader_ca on 2006-10-02
mayben,

install ndiswrapper from synaptic package manager
then

you have to have the correct windows drivers for your card. be it v2 - v5 it should show the version on the bottom of the pcmcia card.

if you have the cd copy the files from it into a directory on your desktop. if you dont have the cd download the drivers from linksys them extract them in a directory on your desktop.

*when performing the next step you have to be in the directory of the drivers

sudo ndiswrapper -i lsbcmnds.inf or its the other .inf one (cant remember its name) * if you install the wrong driver just do ndiswrapper -e then the driver name. then repeat the step above

then do 

ndiswrapper -l

it should list the hardware as present


then once the hardware is detected and driver is present

type 

modprobe ndiswrapper
echo ndiswrapper >> /etc/modules 

* this will reload it at startup

then reboot

after reboot go to networking and put your settings

hope this helps. if you still have issues do not hesitate to reply.
cheers

---

### Post by mayben on 2006-10-04
So I tried ndiswrapper. Still no go. It still gets deactivated in networking.  So I tried a different version of the card (I currently have v1 I I used a brand new v3) it still didn't work. I then tried a USB wireless adapter (netgear w111 g v2 I think) and still same problem....Any idea's anyone?

---

