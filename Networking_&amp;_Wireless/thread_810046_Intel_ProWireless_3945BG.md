---
title: "Intel Pro/Wireless 3945BG"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by nazgyl on 2008-05-27
Hi All,
i have an HP Pavilion dv9775ee, it comes with this chipset Intel Pro/Wireless 3945BG, running ubunto 8.04 hardy

i have followed this forum posts for the past 18 hours, downloaded lots of stuff mentioned in the posts but to no avail

i have followed the following posts:
[http://ubuntuforums.org/showthread.php?t=799118&highlight=3945bg](http://ubuntuforums.org/showthread.php?t=799118&highlight=3945bg)
[http://ubuntuforums.org/showthread.php?t=782548&highlight=3945bg](http://ubuntuforums.org/showthread.php?t=782548&highlight=3945bg)

still not working, please find below some information:

lshw -C network:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:be:62:e7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

sudo lspci :
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

iwconfig:

wlan0     IEEE 802.11g  ESSID:""  Nickname:"Doomish"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist wlan0 scan:
wlan0     Failed to read scan data : Resource temporarily unavailable

i tried to renew or release the network adapters, the wired connection is ok and fine, the wireless is not
please help!!!
another question
using ndiswrapper how can i install the driver? where can i get the driver for this adapter?

Thanks so much for any help

---

### Post by myth1001 on 2008-05-27
I'm using the same adapter with an acer laptop. Mine is working fine right from the moment i install Ubuntu 8.04 with Wubi. Sorry..i'm just a newbie.. can't help you much.

---

### Post by nazgyl on 2008-05-28
Whoooopaaaaa
got it working by using ndiswrapper
and one of the drivers on their website 
just loaded up the driver, and presto
Thanks all, hellooooo ubunto

---

### Post by regonzal on 2008-05-29
Nazgyl, could you please share how you got this working? I have been working on this since yesterday but to no avail.

---

### Post by nazgyl on 2008-05-29
> **regonzal said:**
> Nazgyl, could you please share how you got this working? I have been working on this since yesterday but to no avail.

sure, please note that i am a newbie on linux os,first time im using it
 
i installed ndiswrapper from synaptics package manager
then from ndiswrapper website i looked at the list of drivers they support:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

my card as mentioned above is 3945bg
i downloaded the 2nd driver found on the list 80mg extracted it, there is 3 inf files in the package plus dlls and sys files, i loaded the inf files in ndiswrapper one of them worked which for this wirless card is netw4x32.inf

if u have the same card, i hope it works for you
other than that, i spent 2 days trying all the solutions provided here.

hth

---

### Post by regonzal on 2008-05-29
Thank you for your reply. I will try this out as soon as I get back from work this evening and will let you know how this works for me =) 

Thank you once again. 
:guitar:

---

### Post by chili555 on 2008-05-29
> sudo iwlist wlan0 scan:
wlan0 Failed to read scan data : Resource temporarily unavailableI think this and its resultant connection problem is easily solvable, if you don't want to go ndiswrapper. Please see: [http://ubuntuforums.org/showthread.php?p=5071904#post5071904](http://ubuntuforums.org/showthread.php?p=5071904#post5071904)

---

### Post by regonzal on 2008-05-30
I can confirm that the ndiswrapper method worked for me Nazgyl!Thank you all for your help! 

I cannot take credit for this as Nazgyl guided me in the right direction, and with some searching on this thread [http://ubuntuforums.org/showthread.php?t=765647&page=6](http://ubuntuforums.org/showthread.php?t=765647&page=6) and the post made half-way down the page by Syko21 I was able to get my Intel PRO/Wireless 3945abg card to work. I have added a few extra steps at the end as this ensured my card to connect after booting:

Quote:
Originally Posted by Hieronymus View Post
This problem is still not solved but you can get wireless working by using ndiswrapper.

Code:

lsmod | grep iwl

this will give you an output of the modules loaded to get iwl3945 working. The modules it shows are: iwl3945, iwlwifi_mac80211, cfg80211.
Then we must make sure that these are not loaded again

Code:

sudo nano /etc/modprobe.d/blacklist

and add:

#iwl
blacklist iwl3945
blacklist iwlwifi_mac80211
blacklist cfg80211

then remove the modules:

Code:
[I]
sudo rmmod iwl3945
sudo rmmod iwlwifi_mac80211
sudo rmmod cfg80211[/I]

then install ndiswrapper

Code:

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

-if one does not have access to a wired connection you can simply install it from synaptic by loading the cd-rom and selecting ndiswrapper from synaptic. 


install the windows driver

Code:

sudo ndiswrapper -i drivername.inf 

-the driver I used was the NETW4x32.INF file downloaded from: 
[http://ftp.us.dell.com/network/R164255.EXE]("http://ftp.us.dell.com/network/R164255.EXE")

extract and navigate to the DRIVER folder and extract the aforementioned files. 


make sure it starts at boottime, add ndiswrapper to /etc/modules


Code:

sudo nano /etc/modules


Now reboot and all should be fine

ADD:

I needed to go back to the command line in order to load the module when all was set and done by typing:

sudo modprobe ndiswrapper

After that wireless worked perfectly for me. 

Jeroen
Worked great for me, thanks! This should get a sticky to the front page for the time being since there are a fair amount of users having trouble with their 3945abg cards.

:guitar:

---

### Post by chili555 on 2008-05-30
In */etc/modules*, you only need the name of the module, not sudo modprobe. I also wonder why *ssb* is needed. As far as I know it is a module that is needed by *b44*, the native Broadcom driver. Have I missed something?

---

### Post by regonzal on 2008-05-30
Yes sir you are correct, I apologize for the mistake. 

You only do need to add the module ndiswrapper if I am correct. 

The sudo modprobe ndiswrapper command I needed in order to get the module to start up and detect the connection. 

Thanks for looking into this.

---

### Post by chili555 on 2008-05-30
Here is my */etc/modules* with the preliminaries snipped:```
lp
fuse

# Generated by sensors-detect on Thu Nov  1 15:02:45 2007
# Chip drivers
coretemp
```To get ndiswrapper to load at boot time, you would edit the file to look like:```
lp
fuse

# Generated by sensors-detect on Thu Nov  1 15:02:45 2007
# Chip drivers
coretemp

ndiswrapper
```

---

### Post by zzandeamos on 2008-06-09
Ndiswrapper--NO JOY
Well after very carefully entering all that stuff my wifi still don't
work.  In fact I see no trace of it in n/m.  lspci shows it is there but has no name, was 'logical name:wmaster0'
any handy way to get out of this or just reload?  funny thing is the wired
eth0 is bullit proof, it works no matter what.  In fact Idont know how to turn it off.
FDC

---

### Post by J_rizk on 2008-07-10
When I need to extract the downloaded drivers in order to load them into ndiswrapper, where should I extract them. Please give me the path. Thanks :)

---

### Post by chili555 on 2008-07-10
> where should I extract them. Please give me the pathAnywhere you like. You are either going to point *ndiswrapper* to the correct location like:```
sudo ndiswrapper -i Desktop/Drivers/wherever/windows.inf
```Or, you will get into the correct directory where the .inf is sitting:```
cd Desktop/Drivers/wherever/
sudo ndiswrapper -i windows.inf
```

By default, in Firefox, downloads go to Desktop. which is a place you can see. It is, however, a directory: /home/chili/Desktop.

---

### Post by J_rizk on 2008-07-10
Thanks alot mate !

---

