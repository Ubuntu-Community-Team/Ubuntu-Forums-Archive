---
title: "wireless troubles with new laptop"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by rfrey74 on 2007-02-07
I searched quite a lot before posting this, so if there is a post that is specifically for this scenario, please point me to it, otherwise, all help is appreciated.

I just got a new laptop --  the infamous HP Pavilion dv9000z.  The problem is that the wireless network card is not detected at boot.  There is no entry in my /etc/network/interfaces for it.  System >> Administration >> Networking does not show the wireless card in the list.  However, here is where it gets weird.  I installed ndiswrapper with the Windows driver.  When I type sudo ndiswrapper -l, I get:

Installed ndis drivers:
bcmwl5     driver present, hardware present

So I added:

auto wlan0
iface wlan0 inet dhcp

to my /etc/network/interfaces file and tried sudo ifup -a, which gave me

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

So, ndis can see the hardware, but ifup cannot.  The next logical step was to run sudo lspci | grep Broadcom.  The results of which were:

0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev01).

So its there, but its not there.  In case you're wondering, lsmod | grep bcm returns nothing, and I did run sudo ndiswrapper -m and sudo modprobe ndiswrapper with no errors.  So now comes the plea for help.  How do I get this thing connected to the Internet?

---

### Post by gradedcheese on 2007-02-07
ifup doesn't take a -a parameter, perhaps you're thinking "ifconfig -a"?  You can do:

sudo ifconfig wlan0 up

(or "sudo ifup wlan0").  This doesn't answer your main question though (and I'm afraid I don't know much about ndiswrapper).

---

### Post by rfrey74 on 2007-02-07
Thanks for the reply.  If you type ifup --help, you will notice that it does indeed have a -a parameter.  I tried your suggestion of sudo ifconfig wlan0 up to no avail.  The output is

wlan0: ERROR while getting interface flags: No such device

Similarly, sudo ifup wlan0 gives me the same error message as sudo ifup -a.  So in short, still no love.

---

### Post by gradedcheese on 2007-02-07
Ah, ok, good to know.  So wlan0 does show up if you do "ifconfig -a", right?

What does "lsmod | grep ndis" give you? (ie: is the ndiswapper module loaded?)

---

### Post by rfrey74 on 2007-02-07
The only interfaces that are reported for sudo ifconfig -a are eth0, lo, sit0.  Those are my ethernet card (non-wireless), the loopback, and sit0 is not familiar to me.

As for lsmod | grep ndis, 

ndiswrapper 189876 0
usbcore 139172 4 ndiswrapper,ehci_hcd,ohci_hcd

---

### Post by gradedcheese on 2007-02-07
Ok.  Keep in mind that if wlan0 isn't seen by ifconfig, then it doesn't exist and you certainly can't ifup it.  I don't know what sit0 is either, does it have wireless extensions?  Try:

iwconfig

that should list all interfaces and tell you if any of them are WiFi.  It looks like ndiswrapper is indeed loaded and available.

---

### Post by rfrey74 on 2007-02-07
The ouput for sudo iwconfig is

lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

---

### Post by gradedcheese on 2007-02-07
Ok, that's not good: no WiFi device is seen at the moment.  I also don't like lspci giving you "Broadcom Corporation: Unknown device 4311", that certainly doesn't help ndiswrapper figure out what to do, I imagine.  What you may want to try next is to just search google for the model of your laptop and 'linux' or the like.  Try to find out what Broadcom chipset is really in there and you might also stumble across a solution (and maybe even a proper driver).

---

### Post by eldiosyeldiablo on 2007-07-23
Did you get this card to work?

Thx,
David

---

### Post by kevdog on 2007-07-24
Couple of basics:

1. Is the wireless card turned on?? - Sometimes there is a switch on the case or something.
2. Is the wireless card activated in the BIOS??

Assuming yes to the following, please post:
lshw -C network

Thanks.

---

### Post by gangolli on 2007-07-24
By any chance are you missing a modprobe alias

I have in /etc/modprobe.d/ndiswrapper:
> 
alias wlan0 ndiswrapper


---

### Post by rfrey74 on 2007-07-24
Yes I did get this card working.  Please check out this post for more details on how I got the entire laptop running to my approval.

[http://ubuntuforums.org/showthread.php?t=433881](http://ubuntuforums.org/showthread.php?t=433881)

---

### Post by eldiosyeldiablo on 2007-07-25
rfrey74. I followed your steps as you had them listed but the eth1 does not come up when I ifup it.

I have created a thread [here]("http://ubuntuforums.org/showthread.php?p=3081779") to try to resolve it.

Thx for all of your help

---

### Post by eldiosyeldiablo on 2007-07-25
I have this line in there now but I have also tried replacing the wlan0 with eth1 also to no avail..
```
dwilson@laptop-ubuntu:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
```

---

### Post by rfrey74 on 2007-07-28
Is it that you are not connecting to the internet, or that your card is not detected?  If your card is detected, the circular light next to the wireless card on/off switch will be blue, if not, it will be amber.  As for my lappy, the wireless card is Broadcom, and the card is detected as eth1.  If your card is detected but you don't have access to the internet, you need to install the Network Manager Applet on your gnome-panel.  Left click on the applet and you should get a list of networks in your area.  Double click on the one you want to connect to.  If your card is not detected, and you followed the instructions on my other post to the letter, then I don't know what the problem is.  Sorry.  You may want to check the ndis sight on sourceforge for more info on how to use ndiswrapper.

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

---

