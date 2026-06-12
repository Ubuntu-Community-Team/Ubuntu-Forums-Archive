---
title: "2wire wireless usb adapter"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by nucnuc on 2008-04-18
Hello,

I am a fairly new linux user. I've been experimenting with ubuntu for a few months, and now I'm attempting to put it on my main desktop.

I have a 2wire wireless usb adapter, but I cannot get it working.
First I tried this guide:
[http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)
Mine is a different one than the one in the guide, The bottom one on this page:
[http://www.2wire.com/?p=410](http://www.2wire.com/?p=410)

That didn't work.

Then I tried this one
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-f23c29cc02764d709130d736be45147457c69eab](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-f23c29cc02764d709130d736be45147457c69eab)

lsusb is not being consistent about what it sees.
Sometimes it shows 5 entries (one is the mouse, one is some nonexistent device, and the other 3 are all empty? 0000:0000)
Sometimes it shows 6 entries, and I think one of them is the wireless USB (it has an ID, but no name... I'll check the ID when I get home tonight if that will help)
Sometimes it shows absolutely nothing (by nothing I mean it goes down to the next line, and never goes back to the prompt).

anyway
one time I got the id to show up I tried to install the driver
ndiswrapper -l gave me this
driver name : driver installed
       device (ID:HERE) present

I got some error messages with the tail /var/log/messages, but I didn't write them all down (mostly because it was really really late. Again I'll check when I get home tonight).

ifconfig just returned
eth0      something about no wireless
lo           something about no wireless

at this point the guide said 
"Your wireless card should appear with an interface name of wlan0. If it doesn't appear here, then the driver is not working properly."

I'll give more detailed information when I get home tonight, but does anyone have any thoughts?
or specific information I need to look up (besides the ID and error messages) that might help?

---

### Post by dstew on 2008-04-18
Sounds like the USB hardware is having issues, especially if it doesn't show up consistently. It could be a problem with the wireless adapter, or with the USB on the computer. Does the adapter work OK on another computer? Are there any other USB devices you can plug into your Ubuntu computer to see if they show up in lsusb? Try switching USB plugs around. Are you using an exernal hub? Is the hub OK?

---

### Post by nucnuc on 2008-04-18
It was working at least until windows exploded a few days ago (long story).
I'll try it on another computer.

I'm using a USB mouse, and that works fine... I'll try switching the plugs tonight.

no external hub.

---

### Post by nucnuc on 2008-04-18
I plugged it in to my other (windows) computer, and it worked right away, so I'm pretty sure the hardware is good.
Tried switching the plugs, didn't work.
I checked the error log, but there were no errors between when I tried to install the drivers and now.


This is what I did
(removed the stuff I did yesterday)
~$ sudo ndiswrapper -i WLTWOALL.INF
~$ ndiswrapper -l
wltwoall : driver installed
    device (1630:FF81) present
~$ sudo depmod -a (the adapter did not turn on at this point)
~$ sudo modprobe ndiswrapper
~$ tail /var/log/messages
bunch of stuff, but nothing between the startup and now
~$ iwconfig
lo            no wire hangers
eth0       no wire hangers

Rebooted here
This time now the lights on the adapter are on
reboot holds on right after the lights came on with 3 bars in the ubuntu loading screen
Is there a way to force it to display that list of processes as they load? (it came up automatically when bluetooth services (I don't even have bluetooth) froze my computer during startup for quite some time)

~$ lsusb
terminal goes to a blank white line and never returns
~$ ndiswrapper -l
same
~$ iwconfig
lo       no wireless extensions.
eth0  no wireless extensions.

I'm not sure what to try next.


Edit:
I removed the drivers and rebooted
now when I do lsusb I see "ID 0d4e:1000 Agere System Netherland BV"
instead of "ID 1630:ff81" (no device name)
in the hardware information I see Agere USB client instead of the 2 wire usb thing

Edit again:
Got the drivers back on, but I still cannot see anything in ndiswrapper -l or lsusb, and iwconfig still just shows lo and eth0
when I reboot it lists the Agere thing again. Do I need to install drivers for Agere too?
Does anyone know where I can find them?

---

### Post by nucnuc on 2008-04-19
I think I found drivers for the Agere thing (wlagsall.inf... ironic for network driver name... "lags all"), but now I cannot get Agere to show back up.

---

### Post by nucnuc on 2008-04-19
Trying to clean up the huge mess I made, I reinstalled ubuntu.

I downloaded/built/installed the more recent version of ndiswrapper.
Now this happens
#mostly same as above
~$ sudo depmod -a
~$ sudo modprobe ndiswrapper
Segmentation fault

The top light (power) turns on at the segmentation fault.

edit:
tried a different copy of the same drivers (downloaded from the 2wire website, because the CD is kind of scratched)
Now I don't get the segmentation fault.
When I do sudo modprobe ndiswrapper both lights turn on (power and signal), but the terminal screen doesn't respond after that
new terminal screens also freeze when I use commands like lsusb and ndiswrapper -l.



Is there some way to do this using the restricted drivers manager?
Am I doing something wrong?
Is it just impossible for this device?
Can anyone recommend a different wireless card (PCI or USB is fine, preferably not very expensive) that will work?

---

### Post by nucnuc on 2008-04-20
Well I'm finally able to post from the ubuntu machine.

I gave up on the wireless, and flipped the entire network upside down.
I should have just done that from the start... took a couple hours instead of a couple days <_<

Anyway I guess I no longer need an answer to the original question.

---

