---
title: "Need network help asap..."
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by jbaker on 2006-10-27
I need help asap...
When I start the ubuntu server i get a fail status on starting basic networking... Why is that and how can it be fixed?

I have two NIC cards both detected by ubuntu, and can activate them in ubuntu using ifconfig eth0 up and the same for eth1
I can look at the information for each card and it says that it is up but cant get changes saved to for boot up process...

Any help would be greatly appreciated...

---

### Post by lloyd_b on 2006-10-27
Could you post a copy of the file "/etc/network/interfaces"?  This defines the interfaces that are brought up by the startup script.

Lloyd B.

---

### Post by jbaker on 2006-10-28
Here is my interfaces file

auto lo 
iface lo loopback

auto eth0
iface eth0 inet static
    address 192.168.0.44
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

auto eth1
iface eth1 inet static
    address 192.168.0.48
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

---

### Post by lloyd_b on 2006-10-28
Okay - static addresses. That simplifies matters.

Next test:  Open a terminal window, and type the following:

```
**sudo /etc/init.d/networking restart**
```

Please post any error messages you get from this.  This is the actual script that is run during initialization, but by running it like this you should see actual error messages instead of that useless "FAIL" message you get during initialization.

BTW: Your network configuration looks a bit weird - Are both network cards on the same network?  If you send a packet to 192.168.0.75, for instance, how is the machine supposed to know which network card to send it via? (I think that it will simply default to eth0, but I'm not really sure on that).

Could you explain exactly what it is you're trying to do with those two network cards? 

Lloyd B.

---

### Post by jbaker on 2006-10-28
First off thanks Lloyd for your help! Its greatly appreciated.

After running that script it said /etc/network/interfaces:2: too few parameters for iface line ifdown: Couldnt read interfaces file /etc/network/interfaces

The other message was the same except replace ifdown with ifup.

What my original intent was for the two NICs was to provide redundency in case either cable were pulled out, unpluged or chewed through.

Jason

---

### Post by lloyd_b on 2006-10-28
Experiment time.

In "/etc/network/interfaces", comment out all of the lines for "eth1". You comment out a line by putting a "#" (pound, hash, sharp, whetever you want to call that character) at the beginning of the line.  Then try the "/etc/init.d/networking restart" again.

I'm thinking that having two interfaces with conflicting definitions (which is what you've got) may be the source of the problem.

And if not, well it's simpler to troubleshoot one interface at a time than two at once.:-)

As for your redundancy idea, I don't think it's workable to have both interfaces active at once on the same network.  Even if you had both working, the system would have to decide which of them to use.  Once it made that decision, it would stick with it until you told it otherwise.  

It's relatively simple to set up a shell script to switch from one card to the other - leave the second card unconfigured, and if you see a problem run that command to deconfigure the first card, and configure and activate the second one.  I'm not quite sure how to go about making such a switch automatic, though, which is what I think you're trying to do.  I'm certain that it can be done - I just don't know the exact procedure.

Lloyd B.

---

### Post by jbaker on 2006-10-28
Ok commented out all lines dealing with eth1and did networking restart... still fails on ifup for eth0. I also did an ifconfig -a and saw that eth1 is not up, loopback is fine and eth0 is set to NOARP where I have usually found up.

---

### Post by lloyd_b on 2006-10-28
Okay, let's try manual configuration:

```
[B]sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.0.44 netmask 255.255.255.0
sudo route add default gw 192.168.0.1[/B]

```
If all of those commands work, then you should be able to ping out to the gateway (at 192.168.0.1).  If not, could you copy the EXACT messages that it gives you (To copy from a terminal window, use the mouse to highlight the area of text, move to the other window, and press both mouse buttons at the same time - for a three button mouse, press the middle button instead).

One other thing I just noticed from a previous message:
> Couldnt read interfaces file /etc/network/interfaces


Run this just to be certain verify permissions:

```
[B]cd /etc/network
ls -l interfaces[/B]
```

Note - the second command is "ell ess space dash ell" (The font on these forums make ells look like eyes and vice-versa).  

At any rate, please post the output of that command.  I just want to make sure that the permissions on the file aren't weird.

Lloyd B.

---

### Post by jbaker on 2006-10-28
ls -l interfaces provides the following output
-rw-r--r-- 1 root root 414 2006-10-28 01:33 interfaces

now nothing happened for the sudo ifconfig eth0 down command and the sudo route add default gw 192.168.0.1

When I entered in the sudo ifconfig eth0 192.168.0.44 netmask 255.255.255.0 I got an error message that said:

irq 3: nobody cared try booting with the irqpoll option
handlers:
<e00de180> (usb_hcd_irq+0x0/0x70 usbcore
Disabling IRQ #3

Whats that mean and how can I get that fixed?

---

### Post by lloyd_b on 2006-10-28
It sounds like you've got an IRQ conflict (I haven't seen one of those in a LONG time).

What's really weird is that the error came from the USB subsystem.  I wonder why...

What type of NIC's are you using?

Lloyd B.

---

### Post by jbaker on 2006-10-28
Well aside from the NICs which I will get to later I am using a lexar usb drive 1GB. I am not sure if that has anything to do with it.

Now just experimenting I used the same commands to manually configure the other ethernet adapter and that was a success! I uncommented the previous adapter and commented the original you and I were/are working on...

I did an LSPCI (in lower case of course) and saw that I have a DECchip 21041 and a Lite-On LNE100TX

Hope that helps and sorry if I threw you off your train of thought by switching things up a bit.

---

### Post by jbaker on 2006-10-28
Sorry Couldnt figure out how to delete this post... I had a repeat of the answer to your last question up here...

---

### Post by lloyd_b on 2006-10-28
If you reboot now, the network should come up okay on it's own (with only the #2 card active, that is).  Could you verify that? I just want to make sure that we're making genuine progress.

Lloyd B.

---

### Post by jbaker on 2006-10-28
I have already rebooted and everything has come up fine :D nothing failed :) going to try and enable the other card by uncommenting and restarting the network. Hopefully that doesnt mess things up..

---

### Post by lloyd_b on 2006-10-28
Okay, time for some detective work:

```
lspci -vv
```

(That's dash vee vee, not dash double-U)

This will give a detailed list of pci devices, and include all of their options.  What I'm trying to do is figure out which card is the DECchip and which the LiteOn.

Watch for entries that show "Ethernet". They'll look something like this (This is from one of my machines)
```
00:0c.0 Ethernet controller: Winbond Electronics Corp W89C940
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 9
        Region 0: I/O ports at da00 [size=32]
        Expansion ROM at efff0000 [disabled] [size=32K]
```

The important info:  The name (of course). The 00:0c.0 tells us the device ID.  Then note the "Interrupt" setting (since we had that weird IRQ related error).

Then, 
```
cd /sys/devices/pci0000:00/{address}
```

Where {address} is that device ID.  In that directory will be an entry named "net:eth#", where # is 0 or 1.  This will tell us which card is eth0 and which is eth1.

I'm still thinking about where to go from there...

Lloyd B.

---

### Post by jbaker on 2006-10-28
I uncommented the other adapter and it paniced. so im going back through and just going to delete the portion dealing with the DECchip 21041 or eth0 other than that it works great! Thanks!:KS

---

### Post by jbaker on 2006-10-28
I booted up the the servers install cd and did the rescue option and it states that the DECchip 21041 is on eth0. Will that help you out?

---

### Post by lloyd_b on 2006-10-28
I'm glad it's working.  And you got an education on manually configuring etherenet cards at no extra charge :-)

I had to edit this, as I was *assuming* that the DECchip was working, and posted a message about the wrong card.  Oh well.

I would suggest opening up a new thread, mentioning the panic message you got and referencing the DECchip card.  Maybe someone who has some experience with that hardware will have a clue.

I'm fresh out of ideas. 

Lloyd B.

---

### Post by jbaker on 2006-10-28
Thank you so much for your help! It has been a great pleasure to work with you!


Jason:KS :)

---

