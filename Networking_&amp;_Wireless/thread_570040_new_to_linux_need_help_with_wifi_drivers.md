---
title: "new to linux need help with wifi drivers"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by FreeThePenguin on 2007-10-07
ok, i am planning on using ndiswrapper, which i have d/l but its a .tar.gz file so i have a few questions about that first.

-do i need to extract it, if so how?

-The [sticky thread]("http://ubuntuforums.org/showthread.php?t=564419") says to type: *sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9*  however the tar.gz archive is not named this nor is anytihng in it.  So how do i know what to type here?

The second thing is i've found the drivers on the cd, but i dont know which to use, here are the options:
-Vista
-Win98
-Win2k
-WinME
-WinXP
-X64

btw, the adaptor is Realtek RTL8187

---

### Post by climatewarrior on 2007-10-07
This is from the NDIS wrappersite
    
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)




      Chipset: Realtek RTL8187B
    *
      usbid: (as reported by lsusb ) 0bda:8189
    *
      Driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true) used winXP driver contained in RTL8187B_logo_6.1074.0406_silent_install.zip
    *
      Other: Works with WEP, have not tried other encryptions, using ndiswrapper from kernel 2.6.20 (Ubuntu)

It says you should us the XP driver form the site they provide

And this is a really good guide that is going to explain how to set up your ndiswrapper without internet connection.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you get lost during the process or encounter any problems please post again

---

### Post by kevdog on 2007-10-07
There are a couple of ways to complete your problem:

#1 - Ndiswrapper as stated by previous poster -- I think you need the win98 drivers along with ndiswrapper

#2 - There is a built-in driver that we can try -- Its a little buggy meaning there is a trick to get it to work.  This is nothing however you need to install to get it going.  Here is how to do it:

At command line type
gksu gedit /etc/modprobe.d/blacklist

Remove the # signs in front of the lines that say
#r8187
#r818x

Save and exit the file

Now lets load the kernel modules
sudo modprobe r8187
sudo modprobe r818x

Now lets check if the driver is associated with your card:
lshw -C network

Look under the section related to your wireless card, make sure it is not UNCLAIMED and look for a statement stating driver=
Also look for a line that statesL logical name.  Im going to refer to this value as <interface>

If you have this line then you are in business.  Proceeding at command line (make sure you have any encryption turned off on your router for now without any MAC filtering):

sudo ifdown <interface>
sudo ifup <interface>
sudo iwconfig <interface> essid "ESSID_in_Quotes_followed_by_x"   <----- Example - if your essid = router, then the value in quotes would be "routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

Let me know how you make out!

---

### Post by FreeThePenguin on 2007-10-07
> **kevdog said:**
> There are a couple of ways to complete your problem:

Remove the # signs in front of the lines that say
#r8187
#r818x



Ok, i have:

blacklist r818x
blacklist r8187

as you can see they are not commented out.  Also i was wondering if this would affect updates, i've hear ndis wrapper causes more work when it comes time to update

---

### Post by FreeThePenguin on 2007-10-08
> **climatewarrior said:**
> This is from the NDIS wrappersite
    
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)




      Chipset: Realtek RTL8187B
    *
      usbid: (as reported by lsusb ) 0bda:8189
    *
      Driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true) used winXP driver contained in RTL8187B_logo_6.1074.0406_silent_install.zip
    *
      Other: Works with WEP, have not tried other encryptions, using ndiswrapper from kernel 2.6.20 (Ubuntu)

It says you should us the XP driver form the site they provide

And this is a really good guide that is going to explain how to set up your ndiswrapper without internet connection.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you get lost during the process or encounter any problems please post again

ok, well i found the driver but thats not the filename.  I followed the link, then to the 64bit link.  i d/l the ndiswrapper 1.48 and extracted it but there are no control.* files...  what now?

---

### Post by kevdog on 2007-10-08
Sorry, in my instructions I meant to say:

Put a # sign in front of the lines that say
blacklist r818x
blacklist r8187

so that it looks like the following:
#blacklist r818x
#blacklist r8187

Sorry.  If this approach doesnt work we can go through ndiswrapper.

---

### Post by FreeThePenguin on 2007-10-08
> **kevdog said:**
> 
Now lets load the kernel modules
sudo modprobe r8187
sudo modprobe r818x


ok, i managed to get this to work, i guess it didn't return anything, btw its rtl8187

> **kevdog said:**
> 
Now lets check if the driver is associated with your card:
lshw -C network

Look under the section related to your wireless card, make sure it is not UNCLAIMED and look for a statement stating driver=
Also look for a line that statesL logical name.  


well, i dont see UNCLAIMED anywhere,  ther is no driver=, and it says WARNING: you should run this program as super-user...  ok i don't know what super-user is.... is it anything like superman?  anyway im going to ignore these minor details and continue...

$ sudo ifdown wlan0

this seemed to work ok, appeard to have shutdown the adaptor, next i typed

$ sudo ifup wlan0

```

There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/[mac addres]
Sending on   LPF/wlan0/[mac addres]
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

this appears to be of no luck, but i continue on with high hopes :)

$ sudo iwconfig wlan0 mode Managed

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

```

only to have them crushed...

---

### Post by kevdog on 2007-10-08
You seem to be close, but missing a few steps

Can you post the following

lshw -C network
iwlist scan

Thanks

---

### Post by FreeThePenguin on 2007-10-11
ok, i finally got a chance to do this... heres what i got

$ lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [mac address]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

$ iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results




```

---

### Post by kevdog on 2007-10-11
What driver are you trying to use now?? ndiswrapper or rtl8187??  I dont care -- either is good with me, but lets just stick with one and see if we can work it through, if not, then we switch to the other one.

---

### Post by FreeThePenguin on 2007-10-12
> **kevdog said:**
> What driver are you trying to use now?? ndiswrapper or rtl8187??  I dont care -- either is good with me, but lets just stick with one and see if we can work it through, if not, then we switch to the other one.

We'll im trying the rtl8187 now, i started to use ndiswrapper but things didn't add up.  My wireless just quit working in windows now, so I will have to figure out what the problem is there now and make sure the nic is even going to work.

---

### Post by FreeThePenguin on 2007-10-13
well i got it working in windows again... what do i need to do to get this working in linux?

---

### Post by climatewarrior on 2007-10-18
Gutsy Gibbon the new version of ubuntu is out. I suggest that you upgrade or reinstall to see if wour wireless card is now supported out of the box so that you dont have to anything to set it up. If it still doesnt work the post again

---

### Post by Woutervdkrol on 2007-10-18
Nope.. it is not :( I got the same problem with the same adapter. 

Can you, when someone is giving help, please explain it as non-linux as possible :D So clear steps please, trying to get rid of windows here, but ubuntu without your network adapter working isnt all that great...

---

### Post by climatewarrior on 2007-10-20
Ok, Im sorry I will try to explain things better. Just tell me where you left off in hte installation process. Did you already get Ndiswrapper(the program that makes windows wireless cards drivers work in linux) and network adapter driver?

---

### Post by climatewarrior on 2007-10-20
Ok I went and fetched the windows 98 driver that you need for NDISwrapper. I renamed it with a .txt so that I could upload it here. Yo have to remove that .txt from the file name ofthe driver so that it works otherwise it wont.

Basically rename it as this

Netrtuw.inf

Ok the type this in the terminal terminal is located in applications/accesories

echo 'blacklist rtl8187' | sudo tee -a /etc/modprobe.d/blacklist 

What this does is tell the computer that you dont want to use the open source driver.

Ok then install NDISwrapper, just download it from another computer and pass it on to Ubuntu using a flash drive.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

That is a good guide on how to do that


Once you have NDISwrapper installed put the renamed driver ( the one I gave you) in your Home Folder

Then type this in the terminal

ndiswrapper -i Netrtuw.inf

This tells NDISwrapper to use this driver.

Then type this in the terminal to check that the driver installed properly

Ndiswrapper-l

If this instructions dont work please post the output of this (the message the terminal gives you)

Then type this in the terminal

Sudo modprobe ndiswrapper

and then this

Sudo ndiswrapper-m


And voila! you should have internet.

If not please post again.

I hope this helps you

Bye

---

### Post by climatewarrior on 2007-10-21
Actually if im not mistaken you can install NDISwrapper from your Ubuntu Gutsy Gibbon cd. Just go to System/Administration/Synaptic Package Manager. Insert your Ubuntu cd and look for NDISwrapper in the Synaptic Package Manager and click for installation.

---

### Post by Woutervdkrol on 2007-10-21
Thanks in advance, the future is looking bright again :) I'll try it tomorrow and post results.

Thnx for your help, this "ubuntu-family" is really a great resource and a great help!

=D>

---

### Post by Woutervdkrol on 2007-10-21
Mhm wait.. Just tried, didn't work. But I feel I'm getting SOO close now! Can't wait to just use Ubuntu. So please help me out :)

I first did the blacklisting thing, which worked as a charm.

Then tried to "ndiswrapper -i Netrtuw.inf". There came the problem:

[QUOTE=My Computer / Ubuntu]Couldn't create etc/ndiswrapper/netrtuw: permission denied at usr/sbin/ndiswrapper-1.9 line 152[/QUOTE]

After that I did the modprobe thing, got this line back:

> bash: Sudo: command not found

Aaargh can't wait :D respond soon and you'll be loved :KS 

Thanks a million anyway for trying to help me out, really appreciate it!

---

### Post by climatewarrior on 2007-10-21
Instead of ndiswrapper -i Netrtuw.inf

do 

sudo ndiswrapper -i Netrtuw.inf

(what sudo does is give you administrator rights, in other words in order for you to change any system configuration or file you need to have administrative rights, this is for safety. Every time you encounter a you are denied permission type the coomand with sudo at the beginning)
 
and instead of

Sudo modprobe ndiswrapper

do 

sudo modprobe ndiswrapper

sorry this was a typo of mine

and instead of

Sudo ndiswrapper-m

do

sudo ndiswrapper-m

that should do it for you

also if at any point the terminal says that it couldnt find the diver in folder/folder/folder (just an example) then copy the driver there. If you indeed need to copy it somewhere it will probably be somewhere where you need administrative rights. Just go to that folder and before opening it right click it and press open with administrator rights and the you should be able to copy it in there.

Bye! I hope you finally solve your problem

---

### Post by Woutervdkrol on 2007-10-22
> wouter@wouter-ubuntu:~$ ndiswrapper -i Netrtuw.inf

driver netrtuw is already installed

wouter@wouter-ubuntu:~$ ndiswrapper-l

bash: ndiswrapper-l: command not found

wouter@wouter-ubuntu:~$ ndiswrapper -l

netrtuw : invalid driver!

wouter@wouter-ubuntu:~$ sudo modprobe ndiswrapper


wouter@wouter-ubuntu:~$ sudo ndiswrapper -m

module configuration already contains alias directive

wouter@wouter-ubuntu:~$ 



When I did the "sudo ndiswrapper -i Netrtuw.inf" it said 

> can't find file in folder "."

And I can't find folder . as well :) any ideas? And I tried some folders right-click, but I didn't find the open as admin option :S?

thnx

---

### Post by entomology_guy on 2007-10-22
Some advice on another part of the Ubuntu forums site worked great for me.

I am running Xubuntu 6.06 and was trying to get a TRENDnet usb wireles adapter to work.

lsusb yielded

0bda:8189 Realtek Semiconductor Corp.

I downloaded the drivers at

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

I unpacked it and read the documentation.  The following worked for me.

./makedrv

./wlan0up

iwconfig wlan0 essid "default"

./wlan0dhcp

---

### Post by Woutervdkrol on 2007-10-23
> **entomology_guy said:**
> Some advice on another part of the Ubuntu forums site worked great for me.

I am running Xubuntu 6.06 and was trying to get a TRENDnet usb wireles adapter to work.

lsusb yielded

0bda:8189 Realtek Semiconductor Corp.

I downloaded the drivers at

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

I unpacked it and read the documentation.  The following worked for me.

./makedrv

./wlan0up

iwconfig wlan0 essid "default"

./wlan0dhcp

The site could not be reached, a]maybe you can upload it here?

And the ./bla is what you need to write in the terminal?

---

### Post by kevdog on 2007-10-24
Woutervdkrol

Can you provide me a quick summary of your problem, the chipset of your card, your method of driver install, and any error methods you have received.  There seem to be a lot of posters to this thread, and the topic of this thread has deviated from the original poster.

---

### Post by Woutervdkrol on 2007-10-24
> **kevdog said:**
> Woutervdkrol

Can you provide me a quick summary of your problem, the chipset of your card, your method of driver install, and any error methods you have received.  There seem to be a lot of posters to this thread, and the topic of this thread has deviated from the original poster.

Ive got a laptop with a Realtek 8187B wireless chipset onboard. I installed Ubuntu 7.10 succesfully, but it didn't recognized my wireless card. And from there on I'm stuck, with the methods given in this topic so far not working.

This is a shame really, I want to go from Vista to Ubuntu so bad, but without internet it is somewhat useless now :(

Really appreciate your help, eagerly awaiting your answer.

This is btw my first exp with Ubuntu/Linux, so every step is a new one for me. Please in your answers be as Linux-Noob-Friendly (I know now where the terminal is located, not more than that :)) Thnx in advance for your help!

---

### Post by FreeThePenguin on 2007-10-25
Ok, im back.  I started with trying ndiswrapper originally and ran into trouble...  I have feisty fawn so i don't know if its on the cd (im at work now can't check).  I've done the following:

> **climatewarrior said:**
> 
Ok then install NDISwrapper, just download it from another computer and pass it on to Ubuntu using a flash drive.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

That is a good guide on how to do that


i followed the instructions and this is what i posted back:

> **FreeThePenguin said:**
> 
I followed the link, then to the 64bit link.  i d/l the ndiswrapper 1.48 and extracted it but there are no control.* files...  what now?


So that is where i am at with ndiswrapper.  how hard is it to upgrade to 7.1? i am going to upgrade to vista anyway and i wont loose anytinhg in ubuntu maybe i'll just do a full install of both and start over.

---

