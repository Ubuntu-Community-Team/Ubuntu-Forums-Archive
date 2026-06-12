---
title: "Problems getting belkin F5D7050 usb wi-fi adapter to work"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by spd998 on 2007-03-17
I recently updated ubuntu 6.06 to 6.10 and now I can't get my wi-fi adapter to work. It worked perfectly in dapper using ndiswrapper but when I tried to install it in edgy with ndiswrapper it just won't work. The light on the adapter doesn't start flickering and I really have no idea why this wont work anymore. Any help would be appreciated :).

---

### Post by spd998 on 2007-03-18
Please help me :(

---

### Post by bhutz on 2007-03-18
ok, so I've only just started using Ubuntu but really annoyed by lack of support for it in Ubuntu.

Anyway, I started here to get things working (oh and I didn't use ndiswrapper)...
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking")

and then here...
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

If you follow through everything mentioned in "2.2. Steps" I think you should find out where it is your card is failing....i.e. Check for Device Recognition, Check for driver, Check for router connection, Check for ip address assignment, Connected but no internet

I need to finish going through the guide to find out why my connection is soooo slow and keeps disconnecting (I think)

---

### Post by spd998 on 2007-03-18
Thank you for your help I will try some of the steps and see if I get anywhere :) .

---

### Post by bhutz on 2007-03-19
Any luck?
Mine seems to be ok but it is very temperamental...I think the position of the USB stand is making a difference, I might try it on my windows machine in the same room and see if it acts in the same way.

---

### Post by spd998 on 2007-03-19
> **bhutz said:**
> Any luck?
Mine seems to be ok but it is very temperamental...I think the position of the USB stand is making a difference, I might try it on my windows machine in the same room and see if it acts in the same way.
Still couldn't get it to work in edgy :(. I have just updated to feisty now and so I will try it again and see if it works with feisty.

---

### Post by spd998 on 2007-03-19
I just tried it in feisty with no luck and worked through the troubleshooting guide with no success. I'm really annoyed as it worked perfectly in ubuntu 6.06.

---

### Post by bhutz on 2007-03-19
Just installed Ubuntu on an old PC and if this is anything to go by Linux is gonna make my blood pressure go bonkers...I'm pretty tempted to take the USB stick back and go for a USB stick that supports Linux straight out of the box...if that even exists :confused:

---

### Post by port on 2007-03-19
I just installed ubuntu ultimate 1.3 and I am trying to get my belkin F5D7050 usb wireless card to work with it. Kernel is 2.6.17-11

I am following the guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73") which works on my other machine running ubuntu 6.06 it uses rt73.ko and shows up as rausb0
On my ubuntu ultimate machine i run ./Configure and i put in /usr/src/linux-headers-2.6.17-11 in as  the kernel source directory. I then run sudo make all and it outputs this:
make[1]: Entering directory '/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** No rule to make target `WUSB`. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2

Can someone help?

---

### Post by spd998 on 2007-03-19
> **bhutz said:**
> Just installed Ubuntu on an old PC and if this is anything to go by Linux is gonna make my blood pressure go bonkers...I'm pretty tempted to take the USB stick back and go for a USB stick that supports Linux straight out of the box...if that even exists :confused:

I was thinking of trying to finds a card which supports ubuntu well too. It's such a shame that the wi-fi adapter support isn't very good as everything else is awesome and just works for me. I'm gonna keep trying at getting the damn wi-fi to work though.

---

### Post by spd998 on 2007-03-19
> **port said:**
> I just installed ubuntu ultimate 1.3 and I am trying to get my belkin F5D7050 usb wireless card to work with it. Kernel is 2.6.17-11

I am following the guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73") which works on my other machine running ubuntu 6.06 it uses rt73.ko and shows up as rausb0
On my ubuntu ultimate machine i run ./Configure and i put in /usr/src/linux-headers-2.6.17-11 in as  the kernel source directory. I then run sudo make all and it outputs this:
make[1]: Entering directory '/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** No rule to make target `WUSB`. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2

Can someone help?

I'm new to this all so I won't be much help but have you got the build-essential package installed?

---

### Post by port on 2007-03-19
Yes,  i run:
sudo apt-get install build-essential and it outputs:
build-essential is already the newest version.

---

### Post by spd998 on 2007-03-19
> **port said:**
> Yes,  i run:
sudo apt-get install build-essential and it outputs:
build-essential is already the newest version.

Ok, I wish I could help more but I'm new to ubuntu myself so...

---

### Post by spd998 on 2007-03-19
> **port said:**
> Yes,  i run:
sudo apt-get install build-essential and it outputs:
build-essential is already the newest version.

I've just found this [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

I'm going to try it myself and see if it works for me. Hope that's of some help.

---

### Post by port on 2007-03-19
That does not work either, everything is fine until i get to the 'make' part. The only error im getting is "No rule to make target `WUSB`. STOP"
Anyone have any ideas how to fix this error ?

---

### Post by port on 2007-03-19
well i found out that you cant have spaces in the directory. That fixed the make problem. Everything compiles, but when i try to enable the device , nothing happens, no lights.

EDIT: I just had to restart and it works now.

---

### Post by spd998 on 2007-03-21
YESSSSSSSSSSSSSSSSSSSSSSSSSS!!!!!!!!!!!!!!! I've got the damn thing to work eventually! :):):):):):):):) I followed this guide [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)) 
Then to get WPA working I added to the etc/network/interface file:

auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "MYESSID"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="YOUR KEY"
        pre-up ifconfig rausb0 up

---

### Post by normal on 2007-03-26
Exactly how would one be expected to obtain build-essential if the Kubuntu has no viable method of connecting to the internet for even five minutes?

---

### Post by spd998 on 2007-03-26
> **normal said:**
> Exactly how would one be expected to obtain build-essential if the Kubuntu has no viable method of connecting to the internet for even five minutes?

How is this relevant?

---

### Post by spd998 on 2007-03-26
> **normal said:**
> Exactly how would one be expected to obtain build-essential if the Kubuntu has no viable method of connecting to the internet for even five minutes?

[http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/) it should be somewhere there. Sorry if I totally misunderstood you.

---

### Post by normal on 2007-03-26
So would I have to download every dependent package one by one?  How would I install it afterward?

---

### Post by spd998 on 2007-03-26
> **normal said:**
> So would I have to download every dependent package one by one?  How would I install it afterward?

Can I just ask are you/can you connect to the internet with ubuntu in anyway? Plus i'm a bit of a noob myself so i'm not too sure. I will try and search and see if I can find anything to help you.

---

### Post by spd998 on 2007-03-26
Just had a thought, the build-essential package might be on the edgy cd, put the cd in if you have one then run synaptic click refresh or whatever it is and then search for build-essential, that might work.

---

### Post by normal on 2007-03-26
I have Adept.  How do I add the CD to the repositories?

---

### Post by spd998 on 2007-03-27
> **normal said:**
> I have Adept.  How do I add the CD to the repositories?

It should already be in the list of repositories after you have installed kubuntu I believe. Just put in the kubuntu cd, refresh the list of packages in adept and search for build-essential. Hopefully that will work.

---

### Post by normal on 2007-03-27
It wasn't, and my problem has already been solved.  Apparently I had to use ```
sudo apt-cdrom /media/cdrom1
``` to add the CD to the repository list.

---

### Post by spd998 on 2007-03-28
> **normal said:**
> It wasn't, and my problem has already been solved.  Apparently I had to use ```
sudo apt-cdrom /media/cdrom1
``` to add the CD to the repository list.

Ok I didn't know that. Good to hear you have got it to work.

---

