---
title: "Wireless USB Adapter has to be unplugged and replugged before it will work"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by skyeric on 2010-04-11
Hi, this is more of an annoyance than an actual serious problem really but I'd like some help all the same.
When starting my ubuntu 9.10 computer I have to unplug and plug back in my Netgear Wireless WG111v3 USB adapter before it will 'wake up' and connect to the internet. As I said this isn't a major issue and is really me not wanting to bend down to unplug it and re-plug it but yea, its becoming annoying.
Any help appreciated, thanks,
Eric

---

### Post by spiky001 on 2010-04-11
try typing in term ifconfig wlan0 down
                        ifconfig wlan0 up

sudo ifconfig

---

### Post by skyeric on 2010-04-11
> **spiky001 said:**
> try typing in term ifconfig wlan0 down
                        ifconfig wlan0 up

sudo ifconfig

you want me to copy and paste output?

---

### Post by spiky001 on 2010-04-11
that should turn off wlan0 then back on to make it work providing wlan0 is your wirless connection

---

### Post by skyeric on 2010-04-11
sorry have only had ubuntu a few days don't really understand the terminal fully yet.
I inserted that command and it gave some details about my connection as output.. (I think). I restarted my computer and I still have the same problem, my wireless adapter isn't activated and I don't connect untill I unplug and replug my wireles adapter.

---

### Post by spiky001 on 2010-04-11
ok in the top right cornor you have the network manager if you right click it you should see enable wireless if it's ticked un tick it give it a min then retick it should restart wireless

---

### Post by skyeric on 2010-04-11
when i first start my computer I only have the option to tick/untick 'enable networking'. Untill i unplug and re-plug my wireless adapter I don't even have the option to 'enable wireless'.
I think it's more of a problem with the computer not auto-detecting that the wireless adapter is plugged into a USB slot and untill I unplug and re-plug the wireless adapter it doesn't really recognise its there although again I'm not really sure..

---

### Post by spiky001 on 2010-04-11
ok is the adaptor working now if so open a terminal applications/accessories/terminal type
```
ifconfig
```

---

### Post by skyeric on 2010-04-11
Yea it's working at the moment, have entered that, what am I looking for here? Sorry I'm kinda useless with this only just started using ubuntu! thanks for the help..

---

### Post by spiky001 on 2010-04-11
sorry my fault can you post output

---

### Post by skyeric on 2010-04-11
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:7c:39:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:33:ac:46  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe33:ac46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3393435 (3.3 MB)  TX bytes:855709 (855.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-33-AC-46-33-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by spiky001 on 2010-04-11
ok when it wont start as in when you restart pc open terminal type
```
sudo ifconfig wlan0 up
``` 
the sudo is to give root priverlages type your password it should turn on wireless

---

### Post by skyeric on 2010-04-11
Okay i'll try it now, will be a few minutes gotta restart..

---

### Post by skyeric on 2010-04-11
Okayyy, after first starting my computer and entering it (before unplugging and replugging wireless adapter) I get:
'~$ sudo ifconfig wlan0 up
[sudo] password for eric: 
wlan0: ERROR while getting interface flags: No such device'

After unplugging and replugging so that I get connected and the wireless adapter starts working it comes up with absolutely nothing.

---

### Post by spiky001 on 2010-04-11
ok it looks like a driver problem seems strange how it works but wont load on start up I know from googerling the same probs have been reported what make is it, maybe some1 else can help with prob as well

---

### Post by skyeric on 2010-04-11
It is a Netgear WG111v3 Wireless USB Adapter.
I seem to remember it having the exact same problem when this computer was running Windows although have only used my laptop for a long time now so maybe I'm just imagining that..

---

### Post by spiky001 on 2010-04-11
ok you will need to usesomething called ndsi wrapper with the windows drivers
[http://ubuntuforums.org/showthread.php?t=1330614](http://ubuntuforums.org/showthread.php?t=1330614)

[http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/](http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/)

here is a couple of posts I have found take a look, not being funny you might want to gain abit more experiance 1st and google abit

---

### Post by anewguy on 2010-04-11
Sorry I didn't get back to you on this yet.  I haven't really found anything helpful, so I thought maybe checking the logs might be a good idea.  When you restart your computer, but before you unplug/plugin the adapter (just leave it in place), please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

sudo dmsg > ~/dmsg_before <press enter>

This will probably output quite a lot of information, so using the redirect to put the output in a file.

gedit ~/dmsg_before <press enter>

This will call up an editor and open the file we just created.  Look through it and see if you see any error messages, particularly pertaining to your adapter or to your USB ports.  If you find something that looks suspicious please post it back here.

Now unplug and plug in your adapter (leave the terminal window open).

type:

sudo dmesg > ~/dmesg_after <press enter>

gedit ~/dmesg_after <press enter>

Now check the file again for any messages about USB and/or your adapter - not just error messages, but anything pertaining to the device.

Please post back here with anything you find.

BTW - are you plugging the device directly into your computer or into a USB hub?  Is there another USB port you could try in place of the one you've been using?  Is the port USB 1 or USB 2?  Is the device USB 1 or USB 2?

Thanks
dave ;)

---

### Post by anewguy on 2010-04-11
> **spiky001 said:**
> ok you will need to usesomething called ndsi wrapper with the windows drivers
[http://ubuntuforums.org/showthread.php?t=1330614](http://ubuntuforums.org/showthread.php?t=1330614)

[http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/](http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/)

here is a couple of posts I have found take a look, not being funny you might want to gain abit more experiance 1st and google abit

I don't think he needs ndiswrapper unless there is something specifically stated about the Windows driver getting around this problem, since his adapter *DOES* work (i.e., a driver is loaded and working).

I think this is more of a USB problem - quite possibly the port itself.

Dave ;)

---

### Post by skyeric on 2010-04-11
> **anewguy said:**
> 
BTW - are you plugging the device directly into your computer or into a USB hub?  Is there another USB port you could try in place of the one you've been using?  Is the port USB 1 or USB 2?  Is the device USB 1 or USB 2? 


Okayy well before I restarted I moved it into a USB port on the front of my computer.. worked fine straight away :) 

thank you both so much for your help.

EDIT: thats not entirely true - it was previously in a USB hub on the back of my computer, i got rid of the hub and put it in the front, works fine. thanks again

---

### Post by spiky001 on 2010-04-11
thks to anewguy cheers

---

### Post by anewguy on 2010-04-11
Don't ask me why, because I don't have a clue, but I've had problems with my USB hub initializing on restart and used to have to do the unplug/plugin thing.  When I moved the hub to a different port it worked, so that's why I suggested that to you.  I'm not sure why it works, but have a suspicion:  I think it's the timing of the machine initializing, when the USB drivers are loaded, whether the port is USB 1 or USB 2, and when the hub is recognized that results in the device not initializing.  In your case, with the wireless adapter being on a hub, I could definitely see this being a problem - the timing above plus the timing of when the wireless is trying to be loaded at restart.

At any rate, I'm just glad it worked out for you!

Dave ;)

---

