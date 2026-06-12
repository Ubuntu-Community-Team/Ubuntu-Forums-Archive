---
title: "Atheros wireless card suddenly stopped working!"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by hs2008 on 2008-12-18
Please help!  I'm a total noob.  I installed ath5k on my ubuntu 8.10 compaq laptop.  The wireless worked GREAT for a few days.  But then all of a sudden, this morning, nothing.  I know my router still works.  My wife's laptop is connecting just fine.

I don't even get the 'Enable wireless' in the upper right hand corner.  I didn't do any updates or anything (as it wasn't even connected to the internet while I was at work).  It just stopped working!

NO idea what to do

---

### Post by stoogiebuncho on 2008-12-18
Do you mean that you don't have the Network Manager icon on your top panel?  Can you tell if the Network Manager program is even running?

If it's not, I believe the command to start it up again is 
```
nm-applet --sm-disable
```
(at least that's the command that starts it in my System > Preferences > Sessions - someone please correct me if I'm wrong)

---

### Post by hs2008 on 2008-12-19
The network manager icon is there...but the option of 'Enable wireless' is not there.  Only 'Enable Networking'.

It was there, but then this morning, it vanished...I tried to install the linux backdoor stuff earlier...but no luck.  ath5k was working just fine for me...but then it just completely died.  And I'm at a complete loss.

please help!

---

### Post by stoogiebuncho on 2008-12-19
Hmmm, I'm afraid I don't know much about that.  Hopefully someone comes along who knows more than me.

You might also try posting this in the Networking and Wireless forum - there might be more people there who could help you.

[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by krisstaar on 2008-12-19
I had the exact same problem after installing updates...
This resolved the issue for me:
```
sudo apt-get remove --purge linux-backports-modules-intrepid-generic
```

-Reboot

Reinstall backports-modules:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```


Hope this works for you as well...

---

### Post by porchrat on 2008-12-19
Did you by any chance do a kernel header update just before this happened?  That does tend to throw these drivers out sometimes, I know people say it isn't an issue anymore, but it could be that you merely need to reload the drivers to take account for the new kernel header names.

At least let us get some more info as to whether or not the machine currently sees drivers.  I'm sure by now you are sick of typing this command, but please post the ouput for us:

```
lshw -C network
```

---

### Post by hs2008 on 2008-12-20
It stopped working before I did any updates.  I then tried to install the linux backdoor module thing...and still no luck.  I then tried to reinstall the ath5k drivers.  No good.  I went to hardware drivers and disabled and the enabled the wireless drivers...still no luck.

nothing appears to be working for this thing!

I'll post that output as soon as I get back to my laptop.  I'm using my ubuntu desktop at the moment.

---

### Post by hs2008 on 2008-12-20
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:46:df:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.4 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:39:57:cc:e9:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by nothingspecial on 2008-12-20
Ok 
Start by disabling the ath5k driver```
.

gksudo /etc/modules
```

Then either delete or comment ath5k (comment means put a # infront of it)

Then go[[COLOR="Red"] here[/COLOR]]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/")

Click on the one that says nov. 

Download it to your home directory.

Then -```

tar -xvf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz 
```
```

cd madwifi-hal-0.10.5.6-r3875-20081105
```
```
 make
```
```
sudo make install
```

Then to make the driver load eveytime you boot```





gksudo gedit /etc/modules
```


paste this to the bottom of the file

```
ath_pci
```

save
close
reboot

---

### Post by hs2008 on 2008-12-20
Ok well that worked great, but it's not finding the networks that I know are available in my area.  Any ideas for that?  They were working before, but now are not.

Thanks for everyones help.  Being a noob is rough here..but I love ubuntu so much...I don't want to stop!

---

### Post by unutbu on 2008-12-20
How about post the output of
```

iwlist scan
sudo /etc/init.d/networking restart
```

---

### Post by hs2008 on 2008-12-20
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

shea@shea-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for shea: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

---

### Post by hs2008 on 2008-12-20
I fear that I may have done too much to be able to get it clean!  I'm not sure if I've got like...3 different driver set things installed for this (linux backdoor modules, ath5k, madwifi)

I just don't know!

---

### Post by unutbu on 2008-12-21
There is a way to find out which driver you are currently using.
There is also a way to specify the driver you want, and to blacklist the others.

I could guide you through that, but I'm not confident this will solve your problem. It might only take you back to your original problem, when the wireless card mysteriously stopped working. 

If you had said the wireless card stopped *after* doing a kernel update, then I think we would all know what to do: reinstall the ath5k driver. However, since the problem started before the update, I'm mystified. (Hm... are you sure the problem started *before* the update? If so, how did you download the update packages, or linux-backports-modules-intrepid-generic for that matter?)

Anyway, if you'd like to try the blacklisting idea, we could try that. Otherwise, if no one else has a better idea, I think the easiest way might be to backup your data and reinstall.

---

### Post by nothingspecial on 2008-12-21
> **unutbu said:**
>  Otherwise, if no one else has a better idea, I think the easiest way might be to backup your data and reinstall.

Try [[COLOR="Yellow"]wicd[/COLOR]]("http://wicd.sourceforge.net/download.php") first. It`s another network manager. I find it`s more stable than the default one.

---

