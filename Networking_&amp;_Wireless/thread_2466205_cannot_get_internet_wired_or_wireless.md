---
title: "cannot get internet wired or wireless"
date: 2021-08-22
forum: Networking &amp; Wireless
---

### Post by jgw on 2021-08-22
I now have a machine that doesn't seem to like the internet.  I have another machine that does.  both machines are within 3 feet of me and both get the internet from the same source.  I have switched out the cables between the machines and one machine doesn't like to do anything whilst the other is just dandy.  Then I went to wireless.  I installed a tp-link and both machines tell me that the signal strength is excellent.  The bad machine, however, tells me that but refuses to connect.  It actually connected about an hour ago but then the connection went away whilst the signal strength is excellent.  

So, I know that the wired line is good and the wifi is good on one machine but not on the other.  I have also re-booted the bad machine which made no difference.  Anybody have any thoughts on this one?

Thank you............

---

### Post by praseodym on 2021-08-23
Can you hookup via smartphone tethering? Please check the wireless script from the sticky thread and show the outputs here

---

### Post by jgw on 2021-08-23
Thanks for the reply!

I have gathered some results from your suggestions+  They can be found at [https://pastebin.com/qQDSADDY](https://pastebin.com/qQDSADDY)

Some other stuff.  I have TP-LINK_7496C2 right next to the machine and wifi settings tells me that the signal is excellent.  The TP-LINK_7496C2 has a direct line to the main router plugged into it.  I tested that line before I plugged it in and its just fine on another machine.  When I am in settings I can click on the TP-LINK_7496C2 and it does absolutely nothing!  Then I noticed that the system also created another TP-LINK_7496C2 1 (it was not there this morning!) and that actually connected! (first time in 2 days).  This just gets stranger and stranger.   The line I have plugged in also works on another machine but not this one.  I fear I have a serious network problem.  I have spent 2 days on this and, suddenly, its working and makes no sense.  These things don't normally fix themselves!

---

### Post by praseodym on 2021-08-24
Please show
```

lsmod
iwconfig
iwlist chan
sudo iwlist scan
dmesg | grep carl
```

---

### Post by jgw on 2021-08-25
I am now getting wifi on the offending machine although the machine will still not accept, and run with, a cable from the modem.  So, I took that same cable and plugged it into a tp-link extender and that's what is now running that machine.  I have about 5 different wifi system plugins and tried them all and they all failed so I plugged in the one that I knew was working.   I have also tried three different cables and all worked for the tp-link so I knew they were good but wouldn't work on the offending machine.  I'm going to try a usb to ethernet thing to see if its the current ethernet connector that's bad although it looks right, no wires are cut and lights blink at that connector, etc.   When I setup the extender that didn't work for some time and, then, miraculously it just connected.  That was yesterday and it worked yesterday and worked again today too!  

I'm going to set this as solved.

I still don't trust my network but it seems to be working just fine so I'm gonna just leave it alone for now.

---

### Post by praseodym on 2021-08-26
Change the LAN driver, same device here:
```

sudo apt install r8168-dkms dkms build-essential
echo 'blacklist r8169' | sudo tee /etc/modprobe.d/blacklist-r8169.conf
```
Reboot

---

