---
title: "Orinoco wireless card causes Breezy LiveCD to freeze at 95%"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by bazzle on 2005-10-22
Hi, folks.

I have an Enterasys re-branded Orinoco Classic Gold card (FCC ID: IMRWLPCE24H, w/ Lucent Hermes chipset) in my HP Pavillion ze4145 notebook.

When I boot off the Ubuntu LiveCD, during the "Detecting network hardware" phase, it gets to 95% (Starting PC card services...) and then locks (I've left it there about 20 minutes and no dice). I have to hold the power in for a few seconds in order to get out of it, Ctrl+Alt+Delete won't cut it.

I tried booting with the string:

live hw-detect/start_pcmcia=false

as mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=54091](http://ubuntuforums.org/showthread.php?t=54091)

That gets me to the point where the desktop should come up (I hear the music go "Ding, ding, ding, di-") and then it freezes. Again, I can only get out of it by holding in the power in for a few seconds.

If I remove the card entirely, the system will boot fine (audio/video/mouse working, etc.). However, my computer is pretty useless without the network card. ;) I know the card works in Windows XP, so it is not a hardware issue.

Any hints on how to get this working? I am not a complete Linux newbie, but pretty close.

---

### Post by dbott67 on 2005-10-22
What happens if you boot without it and then insert it once Ubuntu is up & running?

-Dave

---

### Post by bazzle on 2005-10-22
[QUOTE=dbott67]What happens if you boot without it and then insert it once Ubuntu is up & running?

-Dave[/QUOTE]

Hi, Dave!

I guess I would say that "Nothing" happens... no freeze-ups or anything (which is good!) but also no lights come on on the NIC itself (there is normally a green light that stays on constantly), and I don't get any indication from Ubuntu that it's detected new hardware (though admittedly, I'm not exactly sure where to look for this).

Under Applications >> System Tools >> Network Tools, there are only two network devices recognized: lo and eth0 (built-in Ethernet port). In System >> Administration >> Networking it sees my built-in Ethernet and modem ports, but no wireless. And finally in System >> Administration >> Device Manager, I see an entry for OZ6912 Cardbus controlller (which I assume is what handles the PC card), but there is nothing underneath it like there is for my built-in Ethernet controller.

I should also mention that I've had this NIC working under Kanotix before (which is also Debian-based), so I know that it is at least capable of running under Linux. :)

---

### Post by dbott67 on 2005-10-22
Let me do a quick search of some other posts I've made regarding manually loading wireless drivers and then configuring it from the command line.

Back in a flash...

---

### Post by dbott67 on 2005-10-22
Hi Bazzle,

Okay... to manually load the wifi drivers, you'll need to find out the name of the orinoco driver.  Once you've got that, then open a terminal and type:
```
modprobe orinoco_driver_name
```
```
/etc/init.d/networking restart
```
Next, type the following command to get the name of the wireless interface: 
```
iwconfig
```
Some wifi cards are listed as wlan0; others may be eth1.  Your mileage may vary.

Once you've got the interface name, in this case I'll assume it's wlan0, we have to activate it:
```
sudo ifup wlan0
```
And then request an IP address from your AP:
```
sudo dhclient wlan0
```
One last command you can try is:
```
iwlist wlan0 scanning
```
to see if your wireless NIC can see your AP.

Hope this helps.
-Dave

---

### Post by dbott67 on 2005-10-22
By the way, if this works, you can write a bash script that contains the core commands and save it.

```
#!/bin/bash

# Script to load and activate wifi drivers for Orinoco card
modprobe orinoco_driver
/etc/init.d/networking restart

sudo ifup wlan0
sudo dhclient wlan0
```

Save file as wifi.sh to USB or floppy and make it executable and you can run it whenever you need it.

-Dave

---

### Post by bazzle on 2005-10-22
Wow! Thank you so much for all the help!! :D 

> Okay... to manually load the wifi drivers, you'll need to find out the name of the orinoco driver.

I wasn't totally positive on how to do that, but I booted off the Kanotix LiveCD and saw that they use the line:

```
modprobe orinoco_cs
```

So I:

1. Booted up with the card removed
2. Once at the desktop, inserted the card into the slot
3. Went to Applications >> Accessories >> Terminal and opened a shell prompt.
4. Entered the command:

```
sudo modprobe orinoco_cs
```
(if I didn't do sudo, it gave me a bunch of "operation not permitted" errors). This didn't seem to do anything, just kicked me back to the $ prompt.

5. Entered the command:

```
sudo /etc/init.d/networking restart
```
(ditto above re: sudo)
Which gave me a message "Reconfiguring network interfaces..."

6. I then entered:

```
iwconfig
```

which gave me three interfaces, but all of them say "no wireless extensions":

lo
eth0
sit0

Neither eth1 nor wlan0 is present. Therefore, I couldn't proceed with the rest of your instructions. None of das blinkenlights are working either, so it seems like communication is not happening.

Just FYI, under Kanotix, the wireless interface is under eth0 but it obviously won't be here since it was not in the computer when it started. :) But I can go in there and jot down any settings which might help make this easier. I really would like to get Ubuntu installed though, because there is a Ubuntu conference in Montreal next week and I'd like to be a bit informed before I attend! ;)

Now that you've given me a few more keywords, I will try searching the forums too to see if I can figure out why it's not picking up the card. But if you have any other suggestions, I'm all ears! :) Thanks again.

---

### Post by dbott67 on 2005-10-22
One other thing that you may want to do next time your in Kanotix is to backup the various network config files and maybe print them out for reference, as well as a listing of the various modules that get loaded.

sudo cat /etc/network/interfaces
lsmod

If you print them out, you might be able to compare them to the Ubuntu versions.

-Dave

---

### Post by bazzle on 2005-10-22
Ok, I found another thread with a similar problem: [http://ubuntuforums.org/showthread.php?t=28371](http://ubuntuforums.org/showthread.php?t=28371)

I followed the instructions given there:

1. Booted computer without card
2. Went to Applications >> Accessories >> Terminal to open shell prompt
3. Entered iwconfig and got:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

4. Tried:

```

lsmod | grep orinoco
lsmod | grep hermes

```

neither of which returned anything.

5. Inserted card

6. Did:
```

sudo modprobe orinoco
sudo modprobe orinoco_cs
sudo modprobe hermes

```

then:

```

lsmod | grep orinoco

```

which this time gave me:

```

orinoco_cs          8456  0
orinoco            33932  1 orinoco_cs
hermes              6912  2 orinoco_cs,orinoco
pcmcia             24584  3 orinoco_cs
pcmcia_core        44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

(lsmod | grep hermes gave me that "hermes" line again)

7. I tried the networking restart and iwconfig commands, but they gave me same output as before.

8. Per ming0's post, I tried:

```

sudo cardctl eject

```

and removed the card, tried putting the card back in and... 

**SYSTEM FREEZE**, hehe.

So it seems once those drivers are loaded that causes my system to bug out?

I will now try your suggestion and compare the output from lsmod under Kanotix with that of Ubuntu.

---

### Post by bazzle on 2005-10-23
I've attached four files, with the output from the commands you gave me in both Kanotix and Ubuntu. I couldn't see anything immediately off, but then most of it is kind of Greek to me. :\

Also, here is the output from iwconfig under Kanotix:

```

$ iwconfig
lo      no wireless extensions.

eth0    IEEE 802.11-DS ESSID:"" Nickname:"HERMES I"
        Mode:Managed  Frequency:2.462GHz  Access Point: 00:0F:B5:6F:9E:1E
        Bit Rate:11 Mb/s  Tx-Power=15 dBm  Sensitivity:1/3
        Retry limit:4  RTS thr:off  Fragment thr:off
        Power Management:off
        Link QUality=17/92  Signal level=-68 dBm  Noise level=-85 dBm
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0  Missed beacon:0
        
eth1    no wireless extensions.

```

On another note, by searching around I found this post too, which seems to describe my symtoms exactly (not sure about the TI thing though): [http://ubuntuforums.org/showpost.php?p=303016&postcount=7](http://ubuntuforums.org/showpost.php?p=303016&postcount=7)

Unfortunately I don't have an option in my BIOS to disable any kind of power management, including PCI Bus. :\ Any idea if there's something related to boot options I could pass in which might alleviate this problem?

---

### Post by bazzle on 2005-10-23
Per some folks on IRC, the next thing I'm going to try is using ndiswrapper. Though I "shouldn't" need to use this, I don't think, since this card should be recognized with the native drivers. 

The lack of power to the card makes me think there is a bigger issue, and that in all likelihood ndiswrapper isn't going to help me either. I'm wondering if the problem stems from something other than the network card.. the PCMCIA slot or something... but I will post back when I get a chance to rule ndiswrapper in or rule it out. :)

---

