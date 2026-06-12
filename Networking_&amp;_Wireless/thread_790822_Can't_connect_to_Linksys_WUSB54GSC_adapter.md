---
title: "Can't connect to Linksys WUSB54GSC adapter"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Morty007 on 2008-05-11
I just installed Hardy on my XP machine. (The middle option when you put in the Hardy cd)

Install went fine, but I can’t connect to the internet and am on a wireless network. I have a Linksys WUSB54GSC adapter. 

After weeks of reading on the forums, I have installed wifi radar, thinking that would be the easiest for me. It seemed to detect a network (I think) but I can’t connect at all. I know my network name, and I know the WEP number. It connects to a AT&T 2wire modem/router. 

 I have a Seagate external hard drive attached, and I copied the Linksys folder to it, so if you need that to help me then I can access those Linksys files while in ubuntu. Below is my ip and iwconfig log.

I love linux, and want to get my system up an running.

I need easy step by step posts if possible. 



marc@marc-desktop:~$ iwconfig 
lo        no wireless extensions.  eth0      no wireless extensions. 
marc@marc-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:44:c3:1c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1460 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:74040 (72.3 KB)  TX bytes:74040 (72.3 KB) 
 
marc@marc-desktop:~$

---

### Post by Morty007 on 2008-05-11
Anybody able to help a guy out?

---

### Post by HunterThomson on 2008-05-11
Ya, you need to install these drivers for your wusb54gsc 

here is a link to the drivers 

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2)

here is a link to a vidio on how to set them up

[http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/](http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/)

AND
[http://infinityexists.com/2007/06/14/episode-3-wireless-hacking-deauth/](http://infinityexists.com/2007/06/14/episode-3-wireless-hacking-deauth/)

---

### Post by q1u2i3z on 2008-05-11
becaus of the chip linksys 54gs is not supported tried all the tricks no satisfaction go google linux wless for a list of all the supported wifi cards. you will be happier with one that works!

---

### Post by Morty007 on 2008-05-11
Thanks for the reply Hunter.


 
I watched the video but it's a little aloof for me. I've got the file, but can you type what I need to put in terminal?

---

### Post by HunterThomson on 2008-05-11
> **q1u2i3z said:**
> becaus of the chip linksys 54gs is not supported tried all the tricks no satisfaction go google linux wless for a list of all the supported wifi cards. you will be happier with one that works!

Ya it is for the WUSB54GC NOT WUSP54GSC but give it a shot. I'll check back to see if you have any problems... I have a WUSB54GC

---

### Post by HunterThomson on 2008-05-11
> **Morty007 said:**
> Thanks for the reply Hunter.


 
I watched the video but it's a little aloof for me. I've got the file, but can you type what I need to put in terminal?

I just kept stoping and starting the vid step by step. I will check the show notes for a wright up

---

### Post by HunterThomson on 2008-05-11
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

Ok check that out...... 

Or really don't it is long and confusing and you are using driver that are written for Linux not the windows ones.BUT you modify /etc/modprobe.d not (/etc/modprobeconfig???) thing you do in backtrack

Step 6 will do you good though.

---

### Post by Morty007 on 2008-05-11
Sorry, that's way too much for me. Is there anything else maybe?

---

### Post by HunterThomson on 2008-05-11
If you just follow the steps in the video (= and start.... step by step) then when you run into problems. Then tell me what you did and what step you got stuck on. Then I will find the ansore and tell you what to do next:)

---

### Post by Morty007 on 2008-05-11
Ok, is the first thing I type : Set\IP\ address rt73-k2, etc?

---

### Post by HunterThomson on 2008-05-11
> **Morty007 said:**
> Ok, is the first thing I type : Set\IP\ address rt73-k2, etc?

Sorry for the lateness I was watching a move and for got to check. 

I don't know what you are talking about really....

Did the driver install and set up go well?

Are you now trying to connect to your WEP? 

OR what have you done and what are you doing now elaborate.

---

### Post by Morty007 on 2008-05-11
Well I seem to have had more success just fooling around on my own so far. (That's not meant to be mean, btw.) I just don't know what to do with that video.

I messed around with the network settings and at least now the 2 computer icons up top are "on" but still no internet. Below is what I have now. I put in my WEP key and all that jazz. 

Its a shame that this has to be so painful. I think I just need to be told what code to put in here, line by line. 

[IMG]http://i3.photobucket.com/albums/y70/morty007/Screenshot-NetworkSettings.png[/IMG]

---

### Post by HunterThomson on 2008-05-11
sorry for not keeping up with you... Normally I am responding to the min.

It looks to me that you still don't have your wireless adapter on or the drivers installed. You should see a wireless adapter in that GUI.

I'll watch the video and try to be more help full now.

could you run these commands in the terminal and post what it says.

ifconfig -a

and then

iwconfig

---

### Post by HunterThomson on 2008-05-11
Ok plug in the usb adapter and follow this...and downlad the driver form here

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2)

Make a new folder "Documents" and name it "Wdriver" then cut and past the driver file that you downloaded to this file.
Then run this comand-

sudo modprobe -r rt73

Then run this to open the folder-

cd ~/Documents/Wdriver

Then run these to install the drivers-


sudo tar -xf rt73-k2wlz-2.0.1.tar.bz2

cd rt73-k2wrlz-2.0.1

cd Module/     ((OR maybe just))   cd Module

(("mite" need to run  sudo configure    first))

sudo make

sudo make install

Then unplug the adapter and plug it back in
Then run this comand

ifconfig rausb0 up

Should all work grate now:):):):) Let me know I will keep refrshing the page to keep up with you now.

---

### Post by Morty007 on 2008-05-12
I do the first line and then it asks me for my password but when I type nothing comes in the terminal. I type anyway and hit enter and I get a fatal error.

Can anyone help with this? I'm dying to get online and get this thing up and running. 

[IMG]http://i3.photobucket.com/albums/y70/morty007/cantenterpassword.png[/IMG]


[IMG]http://i3.photobucket.com/albums/y70/morty007/fatal.png[/IMG]



This is so frustrating.

---

### Post by HunterThomson on 2008-05-13
When you type your password in a shell no feed back is given, this is normal. You got the error because he rt73 driver are not installed on you system that is fine just keep going on the steps. Look for errors when you do the "make" and "make install" commands. If you get an error when you "make" then try the  "configure" command and "make again.

---

### Post by HunterThomson on 2008-05-13
OK, 
I just called linksys about the addapter. After a long and frutless talk to some laddy who didn't know anything............. I called back and got an Indian guy who new what was up. 

I was asking what chip set was used in the WUSB54GSC and if it was the same chip set in the WUSB54GC. The lady didn't know what a chip set was but she did tell me that the difference between the two adapters was the the WUSB54GSC had speed boost and WUSB54GC did not. I asked what was different between the two adapters that enabled speed boost "Is there a change in hardware or is it just a change in the firmware?" She didn't know and told me to call customer service even though she was in consumer service:). I called consumer service back and got the Indian guy. I asked him what was the difference between the WUSB54GC and WUSB54GSC that creates the ability of speed boost. He told me there is no difference in hardware it is merely a different firmware. I then asked if the same drivers could be used he told me no. I asked if the rt73 enhanced drivers that worked for the WUSB54GC would still work for the WUSB54GSC. He told me no. But give them a shot I want to know for sure. They mite still work.... 

This was still a fruitful call though. This means that you could buy the cheaper WUSB54GC and flash the firmware with the WUSB54GSC firmware and then you would have speed boost. Kind of cool.

---

### Post by HunterThomson on 2008-05-13
I just found a HOW TO written by diepruis that seem vary complete. If you have problems let me know. I will help you:) But also have a look at this HOW TO. A lot of it is making sure you have all the thing you need to compile make and install driver and not so much about installing the driver. So, it may look a lot more complicated then it is. 

HOWEVER,I didn't do any thing more then what I put in my how to. 
SO, maybe not bother reading and confusing yourself this his HOW TO.

Just let me know if you have problems. Also, I see you downloaded the 2.0.1 driver and not the 3.0 driver. Download the 3.0.0 driver and install that one instead. 

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I hope the drivers work for you but I bet there is just another diver you need if this one doesn't work. I will keep looking.

They let you do:

RaLink RT73 USB Enhanced Driver
* Support for Fragmentation Attack
* Interface is called rausb0 instead of wlan0 to prevent some tools incorrectly detecting it as wlanng or hostap driver
* Injection speed can be selected with iwconfig <interface> rate command. The default speed yet is 54 MBit. You may want to lower it to 1 MBit before injection with iwconfig rausb0 rate 1M
* NEW: ToDS packets aren't dropped by the driver anymore. WPA handshake captures are finally possible!
IMPORTANT!
Version 3.0.0 is a new fork from the current serialmonkey CVS. It has fixes for 2.6.24 and 2.6.25 and does not need setting a MAC Address before bringing the interface up. This version includes all the enhancement of the 2.0 series of this driver. If you unplug the card while its still in use, it may crash your system. So close all applications accessing it, bring the interface down and then remove the device.
IMPROVEMENT!
There is a tiny extra in the 3.0.0 driver. Maybe you can find it with iwpriv ;)

---

### Post by HunterThomson on 2008-05-15
There is a good chance that you will have to use ndswrapper for the windows 32 bit driver. Are you running 32bit Ubuntu 64bit ubuntu?

---

### Post by Morty007 on 2008-05-15
32 bit. I'm going to go to Best Buy today and inquire about getting a wired adapter just so I can finally get online.

---

### Post by HunterThomson on 2008-05-16
> **Morty007 said:**
> 32 bit. I'm going to go to Best Buy today and inquire about getting a wired adapter just so I can finally get online.

Ya, you could do that. However, we can get your wireless adapter to work. I did some looking and it seems you have to use ndswrapper for the 32bit window$ driver. Reports say that it works well.

I'll look the forums for a adapter that has native Linux driver and simple/automatic to setup. That seems to be the thing with Linux... Video cards and Wireless cards. BUT hay come a long way... there use to be choke problems.

Well I think your best bet is ether to set up the wusb54gsc with ndiswrapper or buy the wusb54"GC" and use the driver we have been talking about. I will edit this post if I come to find out I am wrong.

I got my wusb54"GC" at Radio Shack for $50. Now I have also seen it at wall-mart for $45 but wall-mart also has the "GSC" so make sure to check the model # on the bottom left on the front of the box... If you go this route.

---

