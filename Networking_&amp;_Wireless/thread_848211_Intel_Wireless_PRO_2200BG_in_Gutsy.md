---
title: "Intel Wireless PRO 2200BG in Gutsy"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by kathrync on 2008-07-03
I am having problems getting wireless working under Gutsy using an Intel PRO 2200BG wireless card.

When I originally installed Gutsy, it just worked fine first time.  A couple of weeks ago, my hard drive failed, so after replacing it, I reinstalled Gutsy using the same CD as I used originally. and now it doesn't work.  I have installed a new card and it's still not working, so I presuming this is a software problem and not a hardware problem.

I have run lshw -C network and got the following back:
```

*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth3
       version: 05
       serial: 00:16:6f:cd:20:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

```

The thing that stands out here is the statement right at the end, "wireless=radio off"  I don't know what to do about it though...I have tried switching it on and off using the button on my keyboard to no avail.  Does anyone have any things I can try?  I am new to this, so go easy!

Oh, if it helps, I am currently using a USB wireless adaptor which works fine, but I would prefer to go back to the card for transport reasons.  Interestingly, when the USB whatsit is in place, the Intel card shows up in the network list accessed from the top right, although with no networks associated with it.  When I remove the USB whatsit, the network card vanishes too, like the computer no longer recognises it.  I don't know what is going on here (maybe there is some software on the USB thing) but it might mean something to someone.....

Thanks for the help

Kathryn

---

### Post by chili555 on 2008-07-03
On some laptops, it can be tricky to get these to respond to the switch. Let's try a few things. First, is there an LED that is supposed to turn on when the wireless is on? Sometimes the switch works the wireless just fine and the LED doesn't work. Try manipulating the key combination just once and re-run *sudo lshw -C network*. Did 'wireless=radio off' disappear?

Second, do:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1
```Now does the 'wireless=radio off' disappear?

Third, try:```
sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```Does wireless spring to life?

---

### Post by kathrync on 2008-07-03
Thanks for the reply!

I had actually just got it working be activating the acerhk module (it is an acer laptop) as described for the Aspire 1640Z and Aspire 1690 on this page: [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

This has successfully activated the button and I can now turn the wireless on and off and connect to the internet successfully.

However, the changes don't stay...when I shut the machine down, I have to go through the whole thing again (except adding the options ipw2200 led=1 line to the appropriate file).  How do I make these changes stay so I don't have to spend 5 minutes faffing whenever I start up?

Cheers

Kathryn

---

### Post by chili555 on 2008-07-03
Let's try the kwik-n-durty way. *sudo gedit /etc/rc.local* and add the following above 'exit 0':```
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled
```Proofread, save and close. Reboot. Does it work?

---

### Post by kathrync on 2008-07-03
Hi again

Ok, so now when I boot, the wireless works straight off the bat, LED and all.  Thanks!

There is one problem which seems to have appeared though.  If I knock the wireless button, it switches off as expected.  But no amount of pressing it will make it turn back on again!  Other than that, it all works fine, I just have to be careful not to knock the button.

Thanks for your help

Kathryn

---

