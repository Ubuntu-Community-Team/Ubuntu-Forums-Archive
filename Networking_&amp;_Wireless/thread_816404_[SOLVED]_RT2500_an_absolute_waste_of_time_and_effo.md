---
title: "[SOLVED] RT2500 an absolute waste of time and effort - any better suggestions?"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by NEUR0M4NCER on 2008-06-02
I had a few issues with this card in Gutsy, but it worked.

RT2500 in Hardy has been the bane of my life. I've tried suggestions posted in myriad places, from ndiswrapper (on a 64bit system = headache... in fact, scratch that - ndiswrapper ITSELF = headache) to serialmonkey to supposed 'better' drivers in unstable & testing. I could've sworn that when I looked at the supported list of wireless chipsets, the rt2500 was right up there - how can that be so when (at the very least) the drivers that come with Ubuntu are simply awful?

Incorrectly setting the wrong transfer rate to 1mb is daft and forgivable. Weaker connection than the same hardware running XP is a bit annoying, but again, at least you can get online. Then when the connection decides to randomly work/NOT work, it gets beyond a joke. I hate seeing this in other rant threads, but i'm > < this close to calling it a day with Hardy until I can find something more viable.

As I type this on my Eee, i'm randomly trying to connect to my network on the desktop, and it's just more infuriating every time it comes up with nothing... or... yes, there it is: Connected with zero signal strength. Joy.

To make matters worse, i've got my partner asking 'why can't you just give up and put Vista on it?'. Well, no, not asking. Taunting me with her laptop (Vista) which, she confidently tells me, is SOOOOO much better than my (yeah, we claimed ownership of the computers after I refused to put Vista on the desktop) computer - because hers WORKS.

Normally - at least with every other Linux 'hiccup' (i'm going to start referring to them as rungs on a ladder to... somewhere good) I first assume I broke something, then try to fix it. Best way to learn, right? Then, if that's not the case, I scour the web for known issues and workarounds (and think up some for myself - honest!). If nothing works, i'll bite the bullet and do a fresh install, see if I can replicate the problem, figure out what did it, and not do it again. Workflow, see?

No amount of effort, logic or re-installations can solve the rt2500 drama. I reckon it's magic. Or propaganda. Or perhaps aliens.

Is there a way of making it work? I dunno. Pretty much every thread i've read has been solved my either fixing a stupid mistake on the OP's end, or the connection magically working again!

So I went to PC World, convinced that the card would simply not work anymore: "Do you know if this is Linux compatible?" I asked. Laugh? I nearly cried. Stupid me.

The one I bought (Netgear WG311) is apparently nigh on impossible to get working with 64bit Linux - at least I could find that out after a little searching - no wall+head=pain there. A simple 'nope'.

Next idea: my Eee has lovely fast internet - y'reckon there's a PCI with the same chipset available that I can use the Eee's driver with? And out of interest, does anyone know of another distro that handles the rt2500 better than Ubuntu? Guess I should have a go at another one anyway, playing with Ubuntu has been so much fun.

If you've read this far, please... PLEASE. If you know anything that I can do, let me know. Hell, i'll give out my home address for a letter, come meet you anywhere in the country, whatever. It's not a case of getting it working now - it's a battle for superiority over the evil Ralink.

/rant

---

### Post by pytheas22 on 2008-06-02
I'm sorry you're having such trouble.  I've had issues too with the Ralink drivers that ship with Ubuntu, like the interface randomly crashes.  But using the legacy drivers from serialmonkey solved the problem.  I have two USB sticks, one using rt73 and one on rt2500.  I've never used rt2500 to actually connect to a network (I bought it expressly for wardriving purposes), but it works great in monitor mode sniffing packets under the serialmonkey drivers (but yes, the default drivers in Ubuntu were a joke for that card).  I don't know if it's the same card as you have, though.

If you want to give rt2500 a final shot, post the output of the lspci command and I'll do my best to help you.  If it worked alright in Gutsy, then there must be a way to make it work in Hardy--if worst comes to worst you could always downgrade to the Gutsy kernel.

---

### Post by lswb on 2008-06-02
I don't know about any 64 vs 32 bit issues, but the r2x00 drivers shipped with HH do have some issues. I have an older laptop with dapper and using the legacy rt2500 driver and  combination of programs could connect most anywhere. On Hardy, with the r2x00 driver, there is no support for ad hoc mode and some other missing functionality. When I built and installed a legacy rt2500 driver I was able to get everything to work, but (get ready) NetworkManager does not work with the older drivers!

It became moot for me after I installed an intel 2200 pci card so I could keep the rt2500 card with the older machine. But, I feel your pain! I'm still not happy about the way NetworkManager doesn't really manage networking.

---

### Post by pytheas22 on 2008-06-02
> When I built and installed a legacy rt2500 driver I was able to get everything to work, but (get ready) NetworkManager does not work with the older drivers!

This is a good point; to the original poster: were you trying to use Network Manager to connect after installing the legacy drivers from serialmonkey?  It won't work (even though it might pretend that it can); you have to use Rutilt (sudo apt-get install rutilt).  It's dumb, yes, but it's what you have to do.

You also have to make sure that you blacklist the default Ralink drivers by adding them to /etc/modprobe.d/blacklist before the serialmonkey ones will work.

---

### Post by NEUR0M4NCER on 2008-06-02
Hey - thanks for listening :)


Yeah, I tried both RutilT and Wicd and... Wireless Radar is it called? Also blacklisted rt2500pci... then all rt2500 drivers I could find reference to. No luck.

**edit** this line of actions ended with another fresh install, after hosing Xorg, and not being bothered to go through the rigmarole of fixing it.

Thanks for the offer of help Pytheas22, i'll gladly take you up on it - just putting baby to bed and making sure everybody's happy this end, then i'll get back to you.

If it helps in the interim though, from memory, lspci gives the right card (Belkin F5D7000 (V3 if I remember correctly), using rt2500pci driver (a lot of this info is starting to get burned into my retinas, I think)...

Thanks again

---

### Post by NEUR0M4NCER on 2008-06-03
lspci gives```

neur0m4ncer@box:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
04:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
neur0m4ncer@box:~$ 
```

---

### Post by NEUR0M4NCER on 2008-06-03
It gets better. Followed [these](http://ubuntuforums.org/showthread.php?t=784031&highlight=rt2500+64+hardy) instructions, which didn't work - then followed the 'revert' instructions. Now I can't even search for network... no wlan0. Annoying. lspci gives the same result as above, jusy nm-applet says no interface found.

Ugh.

---

### Post by pytheas22 on 2008-06-03
Thanks for the information.  Unless you disagree, I think the best approach to take is to use the legacy drivers from serialmonkey--some quick Internet searches indicate that, as you say, this card seems badly broken using the default drivers in Hardy.  If it doesn't work this way, ndiswrapper is the next option, but you shouldn't need that.  I know you've already tried serialmonkey, but I think it's worth a second shot, because it should really work.  Here is what I think you should do:

1. make sure all of the rt2x00 modules are good and blacklisted

```
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit

```

2. get build tools if you haven't already (I know you probably have, but just to be safe):
```

sudo apt-get install build-essential
```

3. get legacy driver source:
```

wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
```

4. unpack, build and install:
```

tar -xzvf rt25*
cd rt25*
cd Module
make
sudo make install
```

5. reboot

6. now see if the card works (using Rutilt, not NM).  If it doesn't, please post the output at this point of:
```

iwconfig
ifconfig
cat /etc/modprobe.d/blacklist
iwlist ra0 scan
```

---

### Post by NEUR0M4NCER on 2008-06-04
I'm tentatively excited -

<whispers>it's working...

The only difference I can tell is that your instructions blacklisted more drivers than the other turorial did - that, and the fact that I compiled RutilT from source (having had to download it on the laptop and transfer it across...).

Wow. Thank-you so much!

I hope it stays up (no pun intended). I guess the only questions I have now are to do with RutilT - in the site survey tab it says Link=0 and Channel=0 - is this right?

Also, looking through the options (never got it working before, so it's kinda new to me), I see 'Turbo Rate'. It sounds sexy. I wanna enable it :)- should I?

Thanks again for your patience and help!

...now to google the hell out of RutilT and get it connecting on startup...

---

### Post by pytheas22 on 2008-06-04
I'm glad it finally works.  I read once that some of the rt2x00 drivers (that is, the ones that ship by default with Ubuntu) can interfere even with devices that they shouldn't be touching--e.g. rt61pci could be mucking up the operation of the rt2500 legacy driver even though rt61pci should not have anything to do with the devices that rt2500 would control.  That's why I had you blacklist all of the rt2x00 drivers; maybe that made the difference.

Also for future reference, keep in mind that you can always install packages on a machine without an Internet connection by downloading them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .  Usually this method is easier than compiling.  Of course, maybe building Rutilt from source made the difference.

> I hope it stays up (no pun intended). I guess the only questions I have now are to do with RutilT - in the site survey tab it says Link=0 and Channel=0 - is this right?

Probably not.  I don't think you can be on channel 0.  What does iwconfig say about the signal strength and channel?  If iwconfig gives the same misinformation, then the problem probably lies with the driver itself.  If iwconfig gives good information, then it's probably Rutilt making some mistake.  Either way, at least it works, right?
> 
Also, looking through the options (never got it working before, so it's kinda new to me), I see 'Turbo Rate'. It sounds sexy. I wanna enable it - should I?

I have no idea what turbo rate does; never tried it.  But it /probably/ couldn't hurt to try.
> 
...now to google the hell out of RutilT and get it connecting on startup... 

I also had to deal with this issue at one point.  The best solution I found was to write a script (only a couple lines) to make Rutilt automatically connect to my home network when I log into Gnome.  Rutilt has some command-line options that allow you to do this; take a look at its man page for details.  Then simply call the script by adding it to the "Startup Programs" list at System>Preferences>Sessions.  You could probably also write a script to add to /etc/init.d to achieve the same result, but that would be a little more involved.

---

### Post by jrickard on 2008-06-04
I have been fooling with this for days.  Your post has got me closest.  But not there.

I'm using a 64-bit picoITX computer with a Hawking Technologies WHUG1 USB wireless adapter.  lsusb indicates it is a 2573 Ralink Technology Corp device.

I did the blacklisting and installed RT73 and rutil and it seems to work.

I can configure a profile and get a link showing 59% and -78dbm to my router.

I can ping other computers on my network.

I can sometimes ping [www.google.com](www.google.com)

But Firefox, apt-get, synaptic, etc. cannot find anything.

Firefox indicates "waiting for www.google.com" ad infinitum....

I must be resolving if I can ping it by name????

But I cannot connect....

Using the Hardy drivers and the 24-18 kernel, I could often ping other computers in my network, but could not connect with FIrefox.  I've followed this procedure and basically have a similar problem.  So at this point I'm not sure its the driver.

Any ideas?

Jack Rickard

---

### Post by pytheas22 on 2008-06-04
> Firefox indicates "waiting for www.google.com" ad infinitum....

I must be resolving if I can ping it by name????

But I cannot connect....

That's strange.  I would suspect as well that it's not the driver, but some kind of configuration problem.  Are you sure your computer or router isn't blocking anything--specifically, make sure the http port (80) is open.  By default Ubuntu doesn't block anything.

What is the output of these commands:
```

host google.com
wget google.com
```

And what happens if you put an IP address into the Firefox address bar instead of a domain name?  For instance 64.233.167.99 is Google's IP and 91.189.94.249 is ubuntu.com.

You say you can ping google sometimes.  Is there anything different going on between when you can ping and when you can't?

---

### Post by jrickard on 2008-06-04
host google.com results in:

google.com has address 72.14.207.99
google.com has address 64.233.187.99
google.com has address 64.233.167.99
google.com mail is handled by 10 smpt2.google.com.
google.com mail is handled by 10 smpt3.google.com.
google.com mail is handled by 10 smpt4.google.com.
google.com mail is handled by 10 smpt1.google.com.

wget google.com results in:

--22:09:57-- [http://google.com/](http://google.com/)
       => 'index.html'
resolving google.com... 64.233.167.99, 72.14.207.99, 64.233.187.99
Connecting to google.com|64.233.167.99|:80... connected.
HTTP request sent, awaiting response....

---

### Post by jrickard on 2008-06-04
There is no difference if I enter an IP number for google in the Firefox address bar.  In fact, I can enter http:// and an IP address for a web server on my own lan and it does not come up either.  It simply says "waiting for http:// and the ip number.

I can generally ping [www.google.com](www.google.com).  

Jack Rickard

---

### Post by jrickard on 2008-06-05
Actually, I'm with the original thread author.  This is a heroic waste of time.

As it turns out, I have installed the rt73 driver and yes, I can ping to anywhere.  However, there are TWO problems I thought were unrelated.  They both appear to have something to do with the driver.

First is of course the web browser won't connect to anything...as described.

The second is that NFS won't mount any shares.  There was a bug reported on this and I assumed it was a software problem.

If I connect using eth0, both problems go away.  If I use wlan1 they both reappear.  I went back and forth several times.

I just can't get this Ralink USB wireless to work...

Jack Rickard

---

### Post by eldragon on 2008-06-05
what got me running for rt73 is what i did here: [http://ubuntuforums.org/showthread.php?t=704260](http://ubuntuforums.org/showthread.php?t=704260)

one last thing i had to do is blacklist ipv6 too (dont know why actually) during my last reinstall.

i used to have an extremely slow connection without disabling ipv6, now ive got a steady 2.2mb xfer from my lan...

---

### Post by jrickard on 2008-06-05
I had already blacklisted IPV6.

Jack Rickard

---

### Post by jrickard on 2008-06-05
The wireless "connection" appears to work fine.  I'm getting 65% on RUtil and about 18 Mbps throughput.  I can ping everything.  

But NFS generates an internal error if I try to mount anything.

And Firefox doesn't connect to anything.  It looks it up, and then goes into the "waiting for...." state.

If I use ethernet, neither of those is a problem.

I have the latest .24-18 kernel which is supposed to have this built in.  But I have done all the blacklisting and installed rt73 per the directions.  It works sufficiently to get connected and ping.  The STATISTICS show a lot of data passing in both directions.  That's why I thought they were two unrelated problems.  But they disappear completely when I go to an ethernet connection.

In fact, I can eliminate the wireless router as well.  I'm connecting my ethernet cable to a Linksys bridge and it works fine.  It looks like ethernet to the computer of course, but it is actually connecting to the same wireless AP.

Jack Rickard

---

### Post by pytheas22 on 2008-06-05
jrickard,

What is the output of the command:
```

cat /etc/modprobe.d/blacklist
```

Also, you might be able to get a better answer if you post in the [serialmonkey forums]("http://rt2x00.serialmonkey.com/phpBB/").  I'm not suggesting this to get you out of here--when I get a chance, hopefully by the end of today, I'll try to take a better look at your problem myself, as I have an rt73 device working great--but I wanted to point out the serialmonkey forums as well.  The developers of the rt73 driver themselves are over there and in my experience are very helpful in solving bugs as long as you provide the right information.

---

### Post by NEUR0M4NCER on 2008-06-05
Hah hah hah - get this:

I finally get wireless working thanks to Pytheas22's great help, then there's a kernel update - It all worked perfectly, simply re-compiling after upgrade (helped that the commands were all still in terminal history though).

THEN!

:shock:

My ADSL line goes wonky!! Can you believe it? Sky reckons it's a faulty micro-filter (it isn't), so i've got to wait for the new one they're sending in the post before I can escalate the issue further!

D'you think it's a sign that I shouldn't spend so much time online?

---

### Post by dmizer on 2008-06-05
> **jrickard said:**
> The wireless "connection" appears to work fine.  I'm getting 65% on RUtil and about 18 Mbps throughput.  I can ping everything.  

But NFS generates an internal error if I try to mount anything.

And Firefox doesn't connect to anything.  It looks it up, and then goes into the "waiting for...." state.

If I use ethernet, neither of those is a problem.

I have the latest .24-18 kernel which is supposed to have this built in.  But I have done all the blacklisting and installed rt73 per the directions.  It works sufficiently to get connected and ping.  The STATISTICS show a lot of data passing in both directions.  That's why I thought they were two unrelated problems.  But they disappear completely when I go to an ethernet connection.

In fact, I can eliminate the wireless router as well.  I'm connecting my ethernet cable to a Linksys bridge and it works fine.  It looks like ethernet to the computer of course, but it is actually connecting to the same wireless AP.

Jack Rickard
since you can ping, but not browse, and you have disabled ipv6 then you likely have a dns resolution issue.

to fix this, try using opendns servers according to the following howto:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by jrickard on 2008-06-06
Here is the output of my blacklist file:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ipv6
blacklist rt2500usb
blacklist rt2500pci
blacklist rt61pci
blacklist rt2x00pci
blacklist rt2400pci
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt73usb


```

Thanks for looking.  I looked at the serialmonkey site and found it almost incomprehensible.

Jack Rickard

---

### Post by pytheas22 on 2008-06-06
Jack Rickard,

I did some looking around and can't find anyone with similar problems as you, but there are some suspicious things about your situation.  First, your interface is named wlan1.  Where's wlan0?  Second, I think that the serialmonkey drivers should name your device rausb*, not wlan*.  So I think it might be the case that something strange is going on with the drivers; possibly they're interfering with each other.

When you get a chance, please post the output of these commands so we'll have a better idea of what's going on:
```

iwconfig
cat /etc/modprobe.d/ralink
modprobe -l | grep rt2
lsusb
```

Please also run this command:
```

sudo -s
echo 'blacklist rt2570' >> /etc/modprobe.d/blacklist
exit
```

to add rt2570 to the blacklist (I read about some people having conflicts between that driver and rt73.  rt2570 shouldn't be installed unless you compiled it, but it can't hurt to blacklist it).

Finally, have you done anything else on this system that could affect the Ralink drivers?  Did you build any drivers besides rt73, like other serialmonkey ones or the ones from Ralink's website, or anything?

If we can't figure it out from this, we can still always to the serialmonkey forums, but I hope we'll find a solution here.

---

### Post by dmizer on 2008-06-06
> **jrickard said:**
> Thanks for looking.  I looked at the serialmonkey site and found it almost incomprehensible.

Jack Rickard

please see post number 21 above yours.  i believe you're having a simple (and common) dns resolution problem.  if the opendns servers do not fix your problem, please let me know.

---

### Post by pytheas22 on 2008-06-06
> please see post number 21 above yours. i believe you're having a simple (and common) dns resolution problem. if the opendns servers do not fix your problem, please let me know.

I don't think DNS is his problem.  He seems to be able to resolve domain names using the 'host' command, and he gets the same faulty behavior in Firefox even if he enters IP addresses in place of domain names.  I'm no expert on DNS, but based on these observations, it seems like DNS resolution is working correctly, isn't it?

---

### Post by dmizer on 2008-06-06
> **pytheas22 said:**
> I don't think DNS is his problem.  He seems to be able to resolve domain names using the 'host' command, and he gets the same faulty behavior in Firefox even if he enters IP addresses in place of domain names.  I'm no expert on DNS, but based on these observations, it seems like DNS resolution is working correctly, isn't it?

if ping works to external sites by both dns and ip, then it seems reasonable that the wireless drivers are working correctly.  something else is wrong here.

it's possible that using opendns will not fix the problem, but it's easy to try and won't hurt anything even if it doesn't work.

i also _highly_ suggest rebooting the router.

---

### Post by jrickard on 2008-06-09
Adding open DNS did nothing.


/etc/modprobe.d/ralink is however interesting.

alias wlan1 rt73
alias ra0 rt2500



I HAD previously compiled rt73.  Now, I've compiled rt2500 as well????

I had originally installed a D-Link USB wireless and it was assigned wlan0.  When I replaced it with the Hawking Technologies WHUG1, it was assigned wlan1.

I've never had an ra0.  

If I delete the first line of the ralink file, it cannot find ra0 or any wireless device.

If I make clean and recompile and make install the rt2500 CVS, it tells me it is adding ra0 to the alias file.  But I don't wind up with a device tied to it.

Jack Rickard

---

### Post by jrickard on 2008-06-09
Yes, I did compile the rt73 drivers from the serialmonkey post here on ubuntu forums.  YOUR post in this thread seems to compile rt2500.  Is this the same driver or different.

iwconfig

lo no wireless extensions

eth0 no wireless extensions

wlan1   RT73 WLAN ESSID:"Riverhouse"
        Mode:Managed Frequency=2.442 GHz Access Point: 00:1A:70:48:7F:E6
        Bit Rate=24 Mb/s
        RTS thr:off Fragment thr:off
        Link Quality=67/100 Signal level:-80 dBm Noise level:-107 dBm
        RX invalid nwid:0 RX invalid crypt:0 RX invalid frag:0
        TX excessive retries:0 Invalid misc:0  Missed beacon:0

---

### Post by jrickard on 2008-06-09
```
jrickard@picoITX:~$ lsusb
Bus 004 Device 004: ID 04a9:3139 Canon, Inc. 
Bus 004 Device 003: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

jrickard@picoITX:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 169.254.200.205
netmask 255.255.0.0
gateway 169.254.135.69


auto wlan1
iface wlan1 inet static
address 169.254.200.205
netmask 255.255.0.0
network 169.254.135.69
gateway 169.254.135.69
	pre-up ifconfig wlan1 up
	pre-up iwconfig wlan1 essid Riverhouse
	pre-up iwconfig wlan1 mode Managed



jrickard@picoITX:/etc$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ipv6
blacklist rt2500usb
blacklist rt2500pci
blacklist rt61pci
blacklist rt2x00pci
blacklist rt2400pci
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt73usb



jrickard@picoITX:~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
autofs4                23044  1 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
sbs                    15112  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
nfs                   262540  2 
lockd                  67720  2 nfs
nfs_acl                 4608  1 nfs
sunrpc                185884  14 nfs,lockd,nfs_acl
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
evdev                  13056  4 
rt73                  215680  1 
serio_raw               7940  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
psmouse                40336  0 
snd_seq_dummy           4868  0 
button                  9232  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
shpchp                 34452  0 
via_agp                11136  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  1 via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
via_rhine              26632  0 
mii                     6400  1 via_rhine
ata_generic             8324  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
pata_via               13316  2 
uhci_hcd               27024  0 
libata                159344  3 ata_generic,pata_acpi,pata_via
scsi_mod              151436  3 sg,sd_mod,libata
usbcore               146028  4 rt73,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 


jrickard@picoITX:/etc$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:63:f6:3d:ad  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11448 (11.1 KB)  TX bytes:11448 (11.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0e:3b:0e:0d:a4  
          inet addr:169.254.200.205  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3204407 (3.0 MB)  TX bytes:42414 (41.4 KB)

jrickard@picoITX:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan1
0.0.0.0         169.254.135.69  0.0.0.0         UG    100    0        0 wlan1


jrickard@picoITX:/etc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

jrickard@picoITX:/etc$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 8b
       serial: 00:40:63:f6:3d:ad
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0e:3b:0e:0d:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=169.254.200.205 multicast=yes wireless=RT73 WLAN
  
  
  
  
  
jrickard@picoITX:/etc$ sudo mount -a
mount.nfs: internal error
mount.nfs: internal error

From dmesg

[   53.927920] rt73: init
[   53.928059] rt73: idVendor = 0x148f, idProduct = 0x2573 
[   57.533739] rt73: using permanent MAC addr
[   57.533753] rt73: Active MAC addr: 00:0e:3b:0e:0d:a4
[   57.533762] rt73: Local MAC = 00:0e:3b:0e:0d:a4
[   57.588456] usbcore: registered new interface driver rt73
[   57.647662] udev: renamed network interface wlan0 to wlan1
[   57.695876] rt73: driver version - 1.0.3.6 CVS
[   57.803368] rt73: using net dev supplied MAC addr
[   57.803382] rt73: Active MAC addr: 00:0e:3b:0e:0d:a4
[   57.803391] rt73: Local MAC = 00:0e:3b:0e:0d:a4
[  



jrickard@picoITX:/etc$ host google.com
google.com has address 64.233.187.99
google.com has address 64.233.167.99
google.com has address 72.14.207.99
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.

jrickard@picoITX:/etc$ wget google.com
--09:52:42--  http://google.com/
           => `index.html'
Resolving google.com... 72.14.207.99, 64.233.167.99, 64.233.187.99
Connecting to google.com|72.14.207.99|:80... connected.
HTTP request sent, awaiting response... 


jrickard@picoITX:/etc$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"Riverhouse"  
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:16:01:1A:6D:9B   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level:-74 dBm  Noise level:-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


jrickard@picoITX:/etc$ uname -r
2.6.24-18-generic
```

---

### Post by dmizer on 2008-06-09
sorry to hear that opendns did not help, but i still do not believe that your problem is ubuntu.

try some simple things like checking ethernet cable connections (between router and modem).  reboot your router (unplug the power, and plug it back in).  do you have another computer with which you can test your wireless network?  is there another wireless network that you can attempt to connect to?

everything you've posted shows that you have a perfectly functional card.  how is your network physically set up?  what kind of equipment are you attached to?

---

### Post by pytheas22 on 2008-06-09
Your card needs to use rt73, from everything I can tell on the Internet.  But rt2500 might think that it should be controlling your card, which could be causing the inconsistencies.

You should remove or comment the second line (the one involving ra0) from /etc/modprobe.d/ralink.

You should also blacklist rt2500:
```

sudo echo 'blacklist rt2500' >> /etc/modprobe.d/blacklist
```

Then recompile rt73 again, just so we know it's a clean build:

```
sudo rmmod rt2500
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
untar -xzvf rt73*
cd rt73*
cd Module
make
sudo make install
sudo modprobe rt73
```

any luck now?

As dmizer says, beyond this, I'm not sure where else to look with regards to the wireless driver.  I see that you're using static IP, so I wonder if there's not an issue with the network topography that's causing the problem.  Is there any way to switch your router temporarily to dhcp and then use dhclient to get an IP address for wlan1, and see if it works then?  If ping and host work, it's not very clear why normal http traffic shouldn't.

A final thought: does your wireless network use encryption?  Because if it does, I don't see anywhere where you're giving it the key, which would explain a lot.

---

### Post by jrickard on 2008-06-09
Thank you for your help dmizer. As I have been wrong before, (several hundred times) I will follow your advice.  But I do not believe it is the problem.

I have rebooted the router.  I have lots of computers on the router.  I can easily link to another wireless router.

Basically, I have three wireless routers running Sveasoft's mesh software.  They all have the same ESSID, and generally, you link to the closest one.  I have three other laptops in the room connecting to the one in this house, which is the same one that I use for this machine.  

But I will reboot the router (which I did last night as well) and check the other computers.  

But I do not believe it is the problem.  And at this point, I'm not at all certain the wireless is the problem.  There is something messed up in Ubuntu.  Why could I PING [www.google.com](www.google.com), or any sight by name, and not be able to get it with wget or http?????  Why if I can ping an internal machine on 169.254.200.220, could I not be able to [http://169.254.200.220](http://169.254.200.220) on the Firefox?

The mesh network uses 169.254.xxx.xxx with a 255.255.xxx.xxx netmask.  The routers link to each other via wireless.  One is connected to cable Internet for WAN, and the other is connected to DSL.  A third isn't connected to WAN but feeds through one of the other two.

I have a desktop a few feet from this picoITX machine that is connected to the AP via ethernet through house wiring.   That is the 169.254.200.220 machine.  The picoITX is normally configured for 168.254.200.205 statically.  If I use Rutil, it will only do DHCP, and for some reason, it keeps coming up 169.254.11.27.  The symptoms do not vary whether I use DHCp or static.

NFS, Firefox, and wget are failing.  They do NOT appear to fail to lookup DNS.  In fact, FIrefox reports that it is looking up [www.google.com](www.google.com).  Then it reports it is connecting to [www.google.com](www.google.com).  And then it reports it is waiting on [www.google.com](www.google.com).  It is this waiting stage that continues without resolution.  

I do not understand the current /sys system with the new kernels.  How do I get from lsusb to the device assignment as wlan0, wlan1, or ra0????  I think this is where the problem is somewhere.  Or as another suggested, that I am somehow associating the wrong module with the driver.  It looks like I have rt2500 and rt73 going on here.  I am unclear what their relationship is.  

Jack Rickard

---

### Post by pytheas22 on 2008-06-09
The more I think about it, the more I think your wireless driver itself must be alright, since you can ping, etc.  It just doesn't make sense for the wireless to be the problem, as other posters have said.

It might be helpful for you to install an Apache server on your Ubuntu machine and see if it will serve html pages to you in Firefox, first if you call 'localhost' and then the IP address of the machine.  This would at least tell you for sure whether the inability to access websites has to do with bringing them in over the network or some internal problem with Ubuntu.

Also, if you have the time, it wouldn't hurt to set up Wireshark both on your Ubuntu machine and your gateway (if possible; I don't know what kind of capabilities you have to run stuff on that, but I'd imagine it has some capability to monitor traffic and possibly dump packets), and try to figure out where the packets are going.  When you request google.com in Firefox, do you see a packet arrive at your gateway, and if so does it get passed on to Google?  And same idea for the return route...  It could be the case that your requests are going out alright but information isn't being let in for some reason.

---

### Post by lswb on 2008-06-09
jrickard,

Maybe I missed seeing it when I read this thread, but is it possible that you have a firewall running that is blocking these incoming connections? The default firewall that installs with 8.04 is called "ufw" (Supposedly stands for Uncomplicated Fire Wall) I use an different one so I'm not really familiar with it but you can check the man page. Apparently the command "ufw disable" will turn it off if you want to check it out.

---

### Post by jrickard on 2008-06-09
sudo ufw status

Firewall not loaded

---

### Post by jrickard on 2008-06-09
Yes.  I can ping.  

I did as you suggested.  I unplugged the wireless adapter and reconnected the ethernet.  By the way, this ethernet cable simply goes to a Linksys wireless bridge that is connected to the SAME wireless LAN and AP.  

I did an apt-get install of Apache2.  

With either ethernet or the wireless adapter, I get IT WORKS (default Apache home page) to either localhost or 169.254.200.205, my static address.  But using the wireless adapter, I cannot get the web server on 169.254.200.220, or for that matter, google.

Same with nfs.  Wirks with ethernet to wireless bridge.  Does NOT work with USB adapter.

I am really thrown by this.  It IS an odd little computer.  It is a tiny picoITX motherboard from Logicsystems.  Came with 7.04 installed but I had teh same problem out of the box.  Upgraded to Hardy Heron without a hitch.  But I cannot get a USB Wifi adapter to work with this.  

The whole concept is to put this little computer inside a Pelco weatherproof enclosure with a Canon A640 camera.  It will use gphoto2 and imagemagick to take a photo every 30 seconds and transfer it to the web site on 220.  Wireless of course.

The Linksys bridge is pretty small.  It would work.  But it is one more thing to fail.  I would really like to get a USB adapter to work with it and this Hawking is otherwise quite the ticket.  It allows an external antenna which the Linksys bridge does not.

In the transition from Windoze to Linux over the past couple of years, I've learned that generally if you beat your head against it long enough, you eventually win.  But this one has got me stumped.  The LINK looks good.  The ping times are excellent.  It looks stable.  But it is blocking the final piece in here somewhere.

I'm quite sure it is not the network.
I'm quite sure it is not DNS.
I'm quite sure it is not the basic link.  

I am very unclear with the new /sys structure just how the kernel detects USB devices and assigns them these names, wlan1 wlan0 ra0 etc.

I'm very unclear as to how this ties into the IP stack and routing tables.

I don't use firewalls or WEP/WAP security at all (save it).

And I guess I'm a little vague on kernel modules, how they are stacked and prioritized, much less how they conflict.

But I've blacklisted everything I've seen blacklisted by anybody.

I did remove ralink from modprobe.d and recompiled rt2500 cvs.  ralink now reads 

alias ra0 rt2500.

But my interface still shows up as wlan1.

If I try sudo ifup ra0, I get 

Ignoring unknown interface ra0=ra0

---

### Post by pytheas22 on 2008-06-10
Try blacklisting rt2500 and compiling rt73 again.  It is my understanding (based on Google searches) that you *do* want to be using rt73, not rt2500.

As I mentioned earlier, it might also not hurt to make a post in the serialmonkey forums describing your symptoms: you can associate with a strong link, can resolve hostnames and can ping anywhere on the Internet, but can't access anything over the http protocol using the wireless interface, even  from local servers, including your own computer.  Someone over there might have a better idea of what could be going wrong, since they're the most familiar of all with the source code.  I agree with you that their site is convoluted, but if you just go to [http://rt2x00.serialmonkey.com/phpBB/](http://rt2x00.serialmonkey.com/phpBB/) and create an account, you'll be able to post easily.

---

### Post by unutbu on 2008-06-10
> 
I do not understand the current /sys system with the new kernels. How do I get
from lsusb to the device assignment as wlan0, wlan1, or ra0?


Look in /etc/udev/rules.d/70-persistent-net.rules for "wlan1". 
You could change wlan1 to whatever you like, but you'll also have to edit /etc/network/interfaces. I can't think of any other place that you would need to change, but I could be wrong.

Also, you might be interested to know that there is another person who posted with a similar problem: [http://ubuntuforums.org/showthread.php?t=813668](http://ubuntuforums.org/showthread.php?t=813668)

1) He could ping by numeric ip address
2) He could ping google.com (DNS ok)
3) He could *not* browse internet using a wired ethernet connection (he was not using wireless)

It turned out that if he simply replaced the ethernet cable connection with a USB connection (his router had both) he could browse the internet!

What I learned from this is that some routers may not treat all interfaces the same. Perhaps his router is broken -- I don't know. But the point is, just because a wired connection from the picoITX to the Linksys bridge works does not necessarily mean that there is nothing wrong with the Linksys bridge. 

Given this, it might be informative to see if you can connect the picoITX to the main router without the Linksys wireless bridge. Try to cut out as many middle-man devices as you can just to see if you can get a working connection with the simplest possible wireless setup. Then if you can, work backwards, adding back one intermediate device at a time.

---

### Post by jrickard on 2008-06-14
> **dmizer said:**
> sorry to hear that opendns did not help, but i still do not believe that your problem is ubuntu.

try some simple things like checking ethernet cable connections (between router and modem).  reboot your router (unplug the power, and plug it back in).  do you have another computer with which you can test your wireless network?  is there another wireless network that you can attempt to connect to?

everything you've posted shows that you have a perfectly functional card.  how is your network physically set up?  what kind of equipment are you attached to?

My apologies.  You were quite right.  It has been frustrating but the problem turns out to be the router.  

Since I had two machines accessing the Internet quite well on the wireless side, and two machines accessing the Internet quite well on the ethernet side of this router, and since it was passing packets via PING, I simply didn't feel the router could be the problem.

Today I received a miniITX system back from System 76 that had been repaired for a broken AC jack on the motherboard.  When I fired it up, they had also upgraded to 8.04.  And IT had EXACTLY the same problem with NFS and with HTTP as the picoITX.  The System 76 uses an atheros chipset, and the PicoITX uses a RALINK on a USB jack.  

Additionally, my IPHONE had not been able to get on the Internet using the home wifi.

I run some alternate firmware on a Linksys wireless AP made by SVEASOFT.
I got on their forum and cruised around a bit.  There was an undercurrent of similar "can ping, can't connect" messages.  James answered each with a vague reference to Intel chipset drivers being flawed and that the Apple would catch up with their 2.0 driver.

So I swapped out the router with another Linksys running stock firmware.  Apple and both weeny Ubuntus are now chirping happily away on the Internet.

Many thanks to those of you who patiently helped me agonize through this.  I learned a lot about wireless configuration and kernel modules.  I also ate three weeks with at least five full all day sessions on this problem, which as you noted, had nothing to do with Ubuntu...

As I say, there are only 10 kinds of people in this world.  Unfortunately, I appear to fall into the latter group.....

Jack Rickard

---

### Post by dmizer on 2008-06-15
> **jrickard said:**
> My apologies.  You were quite right.  It has been frustrating but the problem turns out to be the router.  

Since I had two machines accessing the Internet quite well on the wireless side, and two machines accessing the Internet quite well on the ethernet side of this router, and since it was passing packets via PING, I simply didn't feel the router could be the problem.

Today I received a miniITX system back from System 76 that had been repaired for a broken AC jack on the motherboard.  When I fired it up, they had also upgraded to 8.04.  And IT had EXACTLY the same problem with NFS and with HTTP as the picoITX.  The System 76 uses an atheros chipset, and the PicoITX uses a RALINK on a USB jack.  

Additionally, my IPHONE had not been able to get on the Internet using the home wifi.

I run some alternate firmware on a Linksys wireless AP made by SVEASOFT.
I got on their forum and cruised around a bit.  There was an undercurrent of similar "can ping, can't connect" messages.  James answered each with a vague reference to Intel chipset drivers being flawed and that the Apple would catch up with their 2.0 driver.

So I swapped out the router with another Linksys running stock firmware.  Apple and both weeny Ubuntus are now chirping happily away on the Internet.

Many thanks to those of you who patiently helped me agonize through this.  I learned a lot about wireless configuration and kernel modules.  I also ate three weeks with at least five full all day sessions on this problem, which as you noted, had nothing to do with Ubuntu...

As I say, there are only 10 kinds of people in this world.  Unfortunately, I appear to fall into the latter group.....

Jack Rickard

no apologies necessary.  i am so glad to hear you've got this figured out, as it was really bugging me because it didn't make any sense.  though, i'm quite sure you were far more bugged than i.

---

### Post by NEUR0M4NCER on 2008-06-15
Congratulations to you, Jack! This thread now documents *two* successes!

Not too sure if it's possible, but can you add tags to the thread (or your posts) relevent to the problems you faced? If not, lemme know what you think the best tags would be, and i'll change them on the first post - I get most of the solutions to my Linux problems from searching the forums without even posting, and i'm sure others may benefit from your experience.

Regards

---

