---
title: "[Solved] Howto install Buffalo WLI2-USB2-G54"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by bluefightingcat on 2007-08-17
Hi,

I recently managed to get my Buffalo WLI2-USB2-G54 usb wireless adapter working. It too me a couple of weeks of research and reading but I finally managed to make it work. So I thought I would save everyone else lots of hassle by posting the instructions here. This has been tested on Feisty. I use Kubuntu but that shouldn't make any difference.

You can see this thread for more information about the discussion that led to the solution. But this post should provide you with all you need. 

[http://ubuntuforums.org/showthread.php?t=524826](http://ubuntuforums.org/showthread.php?t=524826)

Please not that this is how I managed to get my usb adapter to work. There is no guarantee that this will work for you. But I don't see a reason why it shouldn't.

First off this is the information about my wireless adapter:

> Card: Buffalo Tech WLI2-USB2-G54 (USB2 device), 54mbps

*
Chipset: Prism54
*
usbid: 0411:0050

I found this information from the ndiswrapper website. Go to the website and find the information about your device.  I assume that this method will work for all Prism54 usb/dongle wireless devices. 

To get things to work you need the latest version of ndiswrapper (I used 1.47) and the drivers for the linksys website for the device WUSB54G. There are 3 versions of the driver. I managed to get my device working with version 1 of the driver but I have heard version 2 should work also. Version 4 will not work (it's designed for a different chipset). 

The first thing you need to do is make sure your usb device is connected. Then type: 

> lsusb 

From there you should be able to find the id of your device. In my case it is 0411:0050. If you are using the same device as mine then it should be the same for you. The id is model specific. So all people with a Buffalo WLI2-USB2-G54 device should have the same id. Ok write down your device ID and lets move on.

The next step is to install ndiswrapper: 

First we want to make sure that there aren't any previous versions of ndiswrapper on your device. Type in the following in a console:

> sudo modprobe -r ndiswrapper 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

Then download the latest version of ndiswrapper from their website and do the following:

> tar xvfz ndiswrapper-1.47.tar.gz 
cd ndiswrapper-1.47
sudo make uninstall
sudo make
sudo make install

Then open this file /etc/modprobe.d/blacklist and add the following lines to the file. Make sure you have root privileges. 

> blacklist islsm_usb
blacklist bcm43xx
blacklist rt2500
blacklist rt2561
blacklist rt25xx
blacklist rt2570
blacklist r8187
blacklist r818x
blacklist NET2280
blacklist ISL3886
blacklist islsm
blacklist p54u
blacklist prism54
blacklist prism54usb
blacklist prism54_usb
blacklist prism54common

Great. Now you have ndiswrapper installed. You should reboot at this point to make sure the updated blacklist file becomes effective. 

Now we want to install the device drives into ndiswrapper. I assume you have already downloaded the drivers from the linksys website. You only 2 files. One is the .sys file and the other is the .inf file. 
If you are using a Linksys WUSB54G then you don't have to make any changes. However if you are using the Buffalo WLI2-USB2-G54 device you are going to hack the .inf file. It is really quite easy and I have included a ready hacked file here.

The reason we have to hack the file is because the .inf file looks for the id of the WUSB54G device. Our WLI2-USB2-G54 device has a different id so the .inf file won't look for our device. So essentially what you need to do to hack the .inf file is to change the WUSB54G id to the WLI2-USB2-G54 id. If you are interested you can just compare the original .inf file to the hacked .inf file that I have included here. 

Great now that we have our driver files we have to load them into ndiswrapper. This should be quite simple. Type the following into the console:

> sudo ndiswrapper -i WUSB54G_hacked.inf

Then type:

> sudo ndiswrapper -l

You should get an output that looks something like this:

> wusb54g_hacked : driver installed
device (0411:0050) present

Great! Now we just have to load ndiswrapper as a module. Type the following:

> sudo modprobe ndiswrapper

If everything goes well your usb device should now be recognised. Type "iwconfig" in the console and you should be able to see your usb device. In my case it is called wlan0. 

There now your usb device should be installed. 

I use WEP encryption and it works fine. I am not sure about WPA encryption. I will let you know when I try it out. 

Let me know if you need any more help. 

BFC

P.S. The forum doesn't allow .inf files to be attached. So I've renamed it into a .txt file. Just download the file and then change the extension back to .inf
You will also need the WUSB20XP.sys that comes with the driver. Make sure that the .sys file is in the same directory as the .inf file.

---

### Post by funsport on 2007-09-16
Now that I have gotten a dialup modem to work, I am trying out a wireless connection.

Did you uninstall the KNETWORKMANAGER? I have been going in circles trying to figure wireless out. I am a TOTAL NEWBIE when it comes to wireless. From what I have been reading, most were uninstalling KNETWORKMANAGER in Feisty to get any of their wireless to work or else they use KWIFIMANAGER.

I hope that by following your guide and the answer to my question, the wireless installation experience will be a painless and stress free one.

---

### Post by bluefightingcat on 2007-09-16
Hi funsport,

Yes I uninstalled KNetwork Manager. I think its just a really crap programme. Instead I use KNemo and  Wireless Assistant. 

Let me know if you need any other help. Good luck!

BFC

---

### Post by amppa on 2007-10-26
Thank you. I've got my Buffalo running.

But still a little problem. My wlan cannot handle heavy loads. If I try to watch video over wlan it crashes immediately. Is there any solution for that?

---

### Post by bluefightingcat on 2007-10-26
Hi,

I have a similar problem. But usually it only happens to me when I go over 100kb/s when downloading files. Usually video works fine for me. 

Unfortunately I don't have a solution for this. NDISwrapper is definitely not the best way to run the wlan adapter but at this moment its the only thing that seems to work. 

BFC

---

### Post by amshuman on 2007-11-15
Hi BFC,
 I am very new to Linux. I too have the Buffalo G54 USB airstation. I recently installed PCLinuxOS 2007 on my machine and used your hacked "ini" file. It worked like a charm (thanks to you!).

I was installing couple of packages like gtkpod, xmms etc. I ran into kldeInit failed to start problem and used apt-get update &&  apt-get dist-upgrade and the problem went away. I distinctly remember rebooting the machine after this and everything was working fine.

Then I installed skype. It worked at that time but after a reboot, I am unable to connect to the internet. I requested for help in the PCLOS forum (URL -- [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=35476.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=35476.0) )

Since you are knowledgeable with Buffalo G54 airstation, I am making a post here too.I've tried whatever I could so far.  I want to keep reinstalling Linux as the last option. I would appreciate if you could show me some pointers on how to proceed. 

Thanks & regards,
Amsh .K

---

### Post by bluefightingcat on 2007-11-16
DEar Amsh,

Can you tell me what you have tried so far? I am not really an expert but I will try and help you. 

First of all is the airstation still recognised. Use "lsusb" in the command line to find out.  

Is ndiswrapper loaded as a module? Use "lsmod" to check this. 

Use "iwconfig" to see whether your system recognises the airstation. 

Let me know what these produce.

BFC

---

### Post by amshuman on 2007-11-16
Dear BFC,
 Here is what I have tried so far:
From PCLOS control center, I removed the existing wireless device and tried to reinstall it.

I selected the "wusb54g_hacked.ini" file I used during installation (I had downloaded your text file earlier this week)
. Here is the log from "PCLinuxOS Tools Log" window:

18:45:39 drakconnect[8654]: ### Program is exiting ###
18:45:42 drakconnect[8662]: ### Program is starting ###
18:45:46 drakconnect[8662]: ### Program is exiting ###
18:45:47 drakconnect[8666]: ### Program is starting ###
18:45:51 drakconnect[8666]: running: /bin/rpm -q --qf %{name} wireless-tools
18:45:53 drakconnect[8666]: running: dmidecode
18:45:53 drakconnect[8666]: Found settings for driver "ndiswrapper" in category "network::connection::wireless"
18:45:53 drakconnect[8666]: No kernel_module package for module "ndiswrapper" is required, skipping
18:45:53 drakconnect[8666]: Required tools package for module "ndiswrapper" is already installed, skipping
18:45:53 drakconnect[8666]: Thirdparty package ndiswrapper-firmware (firmware) is required but not available
18:45:58 drakconnect[8666]: running: rmmod ndiswrapper
18:45:58 drakconnect[8666]: running: /sbin/modprobe ndiswrapper


A pop-up window with this message showed up:
"Error Unable to find the ndiswrapper interface"

When I clicked ok, another pop-up window showed up:
"Firmware files are required The required files can also be installed from this URL: http://ndiswrapper.sourceforge.net/mediawiki/index.php/list"

Then, I tried the following:

I removed ndiswrapper using these commands:

modprobe -r ndiswrapper
rm -r /etc/ndiswrapper/
rm -r /etc/modprobe.d/ndiswrapper
rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

Then I downloaded ndiswrapper version 1.49 from sourceforge website using my XP machine and copied it to the Linux machine through USB flash drive.

I installed the latest version using these commands:
tar xvfz ndiswrapper-1.49.tar.gz
cd ndiswrapper-1.49
sudo make uninstall
sudo make
sudo make install

Then I used ndiswrapper -i WUSB54G_hacked.ini. (This one worked before).

I rebooted the machine.

"ndiswrapper -l" command displayed device present with an id something like 0411:xxxx.

I tried the PCLOS control center again to install the airstation. Installing the new version of ndiswrapper didn't help at all. I am getting the same pop-up error messages.

I will try the commands "lsusb"m "lsmod" and "iwconfig" as soon as I go back home from work and post the results.

Thanks for your help!

Regards,
Amsh .K

---

### Post by amshuman on 2007-11-16
Dear BFC,

The strangest thing happened today!!!  My internet connection just worked!!!! I am going to do couple of reboots and logins from different accounts I created to verify that it works consistently and this is not just a one time fluke behavior.

I will keep you posted on how things go. (Your hacked ini file was a lifesaver!)

Thanks & regards,
Amsh .K

P.S.
The commeand lsusb had this entry:
Bus 004 Device 003: ID 0411:0050 Melco., Inc.
I'm pretty sure this corresponds to Buffalo G4, but don't understand why this says Melco.

---

### Post by bluefightingcat on 2007-11-18
Thats great news. 

I think Melco is the chip that is used to make the system. But its definitely the correct one. Hopefully it will continue working!!

BFC

---

### Post by amshuman on 2007-11-20
So far so good! I've rebooted couple of times, logged on as root and through different user accounts and the connection is still up. 

Thanks & regards,
Amsh. K

---

