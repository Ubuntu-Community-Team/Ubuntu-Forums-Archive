---
title: "Help with wireless connection."
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by al3x416 on 2007-01-29
So far, this is what I have figured out ~

I have installed my Netgear MA111v2 Drivers (From the install cd) through ndiswrapper, and the light is on (blinks occasionaly).

The hardware shows up in the device manager under usb, and not at all using the command lshw.

When I try to change the key/essid in iwconfig, it doesnt change. IE, sudo iwconfig wlan0 essid [essid] doesnt change anything.

iwlist shows my network in the list.

wifi radar doesnt show any networks.

---

### Post by al3x416 on 2007-01-29
Bump to top before I go off to sleep.. still awaiting help.

---

### Post by phossal on 2007-01-29
What is the output to:
```
ndiswrapper -l
```

---

### Post by al3x416 on 2007-01-29
> **phossal said:**
> What is the output to:
```
ndiswrapper -l
```

netgear ma111v2 hardware installed, driver installed.

it varies though.. sometimes I see it say present instead of installed.

---

### Post by phossal on 2007-01-29
Run:
```
dmesg
```
and scan for rtl8187, etc. You're looking for variants on the rt*818* drivers.

[edit] Does the computer in question connect to the net (with another connection)?

---

### Post by phossal on 2007-01-29
Here is my guess: Your hardware is properly installed, recognized, but the use of the ndiswrapper drivers is being preempted by drivers that *should* be blacklisted.

---

### Post by al3x416 on 2007-01-30
Here is what I have so far..

Using dmesg, I cant find any text driver names like you stated, but I saw my netgear ma111v2 lines.

Also, I dont think they're are two drivers currently.. so I dont think I can blacklist any.

---

### Post by phossal on 2007-01-30
There are lots of reasons for it, but not being able to set the key/essid, even when using sudo, is common when the device is loaded with the wrong driver.

How did you install ndiswrapper? And did you do all of the modprobe/depmod steps?

---

### Post by al3x416 on 2007-01-30
I popped in the Install disk, got ndiswrapper off off of my live cd., took MA111v2.inf and .sys out of the CD:/Driver/ folder, put it on the desktop, and followed all the steps from the help section of ubuntu.com.

---

### Post by phossal on 2007-01-30
What's the output to *this:*
```
lsusb | grep NetGear
```

---

### Post by al3x416 on 2007-01-30
Screenshot attached.

---

### Post by phossal on 2007-01-30
lol That was a good idea. You can use GIMP to grab just the bash window, too. Is there an error message when you attempt to set the essid? Or does it just ignore it? By the way, you *do* have WEP/WPA disabled, correct? You want to reduce the potential problems to a minimum while setting up your initial connection.

```
sudo iwconfig wlan0 essid <ESSID>
```

What is the output, if any?

---

### Post by al3x416 on 2007-01-30
Unfortunatly, I'm trying to connect to a router not owned by me. Therefore, I cant turn WEP off, which is what they use to make sure only people they allow connect.

It ignores the command when I use it.

---

### Post by phossal on 2007-01-30
*Ignores* it? What does that mean? It just presents a new line, with no error messages, and when you check iwconfig the name still isn't set?

---

### Post by al3x416 on 2007-01-30
Exxactly.

---

### Post by phossal on 2007-01-30
What driver did you use?

---

### Post by al3x416 on 2007-01-30
Driver, as in..

I took the .inf and .sys from the WINXP folder of the DRIVER folder out of the cd, and used those?

---

### Post by phossal on 2007-01-30
What were the files named?

---

### Post by al3x416 on 2007-01-30
MA111v2.inf & MA111v2.sys.

---

### Post by phossal on 2007-01-30
This is a rabbit hole. :D Look, from the limited research I'm able to do without the hardware, there aren't very many *reports of successful installation*. However, there are a few. Check out this site, which indicates the use of a *different driver*, and a support module *ON UBUNTU in 2006*:
[http://www.qbik.ch/usb/devices/showdev.php?id=2911](http://www.qbik.ch/usb/devices/showdev.php?id=2911)

---

### Post by al3x416 on 2007-01-30
I installed that driver through ndiswrapper, and uninstalled the old one. It says Driver installed, but nothing else.

What next?

---

### Post by phossal on 2007-01-30
Let me double back on what I said previously, I think you *were* using the correct drivers. I think you're using the wrong version of ndiswrapper. You're using ndiswrapper-utils-1.8. You want the latest one. The CD offers version 1.8, but you can download and compile 1.35. 

I'm out of answers, really. But I'll willing to keep moving forward with hunches until you resolve to by new hardware. ;)

---

### Post by al3x416 on 2007-01-30
Oh, I got thrown off by your last post completely. I get what you're saying now from reading the comments on the links you gave me.

---

### Post by al3x416 on 2007-01-30
I've actually been trying to figure this out for awhile.. I never found a good guide. How exactly do I compile things like this?

---

### Post by phossal on 2007-01-30
Tutorials abound. Here is *[one]("http://ubuntuforums.org/showthread.php?t=347889")*

---

### Post by al3x416 on 2007-01-30
Unfortunatly, after following all the steps, ndiswrapper the command didnt work, and reported  Uknown command.

---

### Post by phossal on 2007-01-30
You must've pulled errors somewhere. Did you install build-essential and the linux headers as indicated in "prerequisite commands"?

What version of Ubuntu are you running under?

---

### Post by al3x416 on 2007-01-30
Yes, but they reported at the end E:/ error error blah blah that I dont recall.

Edgy, 6.10

---

### Post by phossal on 2007-01-30
Yeah, mate. You can't have errors. build-essential is probably on the cd. You might get it that way. Same for the headers. You may need to run cat 5 to the machine and hook it up, so you can download packages.

---

### Post by al3x416 on 2007-01-30
Good news and bad news.

I got the newer version of ndiswrapper installed, and installed the device again. (See screenshot below).

Unfortunatly, I still cant change iwconfig therefore I cant connect. (Also see screenshot below, taken after I tried to change the ESSID.

[edit] Took you're advice on the GIMP screenshot thing. Another reason to love Gimp.. and linux all around.

---

### Post by phossal on 2007-01-30
Are you still trying to set the key at the same time, or just the essid? For example, when you try to change essid, are you always including the key argument, or have you tried setting each one individually? The key argument is finicky, which is why I suggested disabling WEP. It's *much* easier to diagnose without it.

---

### Post by al3x416 on 2007-01-30
I've been only trying to do the ESSID through the command..

iwconfig wlan0 essid PurpleStar

Is that correct?

---

### Post by phossal on 2007-01-30
With sudo, though:
```
sudo iwconfig wlan0 essid PurpleStar
```

I saw in your previous post that you're doing it correctly.

---

### Post by phossal on 2007-01-30
This is interesting, check this out:

```
bash 3.1:**[SIZE="1"][COLOR="Blue"]sudo iwconfig wlan0 essid NOESSIDPRESENT[/COLOR][/SIZE]**
bash 3.1:iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2346 B   Fragment thr=2400 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

It *appears* as if it's not working, as if it's being ignored, when the ESSID is not present! Perhaps you're not getting a signal, or the router isn't broadcasting an ESSID, etc.

---

### Post by al3x416 on 2007-01-30
I'm sure I'm getting a connection, since I can connect through windows.

*Hint Hint* I just disabled WEP on the router.

---

### Post by phossal on 2007-01-30
> **al3x416 said:**
> *Hint Hint* I just disabled WEP on the router.

?!

---

### Post by al3x416 on 2007-01-30
Maybe that'll help me out.. alot. I will go see if that does anything.

---

### Post by al3x416 on 2007-01-30
Maybe it is getting no signal.. but my network is in iwlist, not in wifiradar.. and I cant change the iwconfig still, so iw-stuff isnt helpful. And wifi-radar doesnt even think my network exists.

Arghh I dont know where to go.

---

### Post by al3x416 on 2007-01-30
Good news. I booted up uBunut again and it connected, miraculously. The only weird thing is, in Firefox, it says Looking for Websites for a little while, then connects. Its rather weird.

---

### Post by phossal on 2007-01-30
lol Wow. Congrats, mate.

---

### Post by phossal on 2007-01-30
Write a tutorial. Seriously.

---

