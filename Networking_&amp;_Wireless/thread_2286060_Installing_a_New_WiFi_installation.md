---
title: "Installing a New WiFi installation :"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by BlinkinCat on 2015-07-09
Hi all,

I am in the process of installing a New WiFi connection and would appreciate some help.

I have installed correct program I believe (forget name) which requires installation of Arch Linux.

Have done this but am now stuck on part that requires me to enter the output of : date -u +%V`uname`|sha256sum|sed 's/\W//g'

It appears obvious that 'uname' is simply replaced by my username, but I don't know how to run this command.

Any assistance will be appreciated.

Thank you ...

---

### Post by Vladlenin5000 on 2015-07-09
Sorry but what you posted is complete gibberish. Perhaps if you actually explain what do you intend to do...

---

### Post by BlinkinCat on 2015-07-09
oops - My lack of knowledge often it seems gets me into trouble..

I guess the simple answer is - I just do not have a clue how to install WiFi under Xubuntu...

Help appreciated.

---

### Post by BlinkinCat on 2015-07-09
I have the WIFI Network Name and Password.

---

### Post by Vladlenin5000 on 2015-07-09
If your wifi device was already recognized and running all you had to do is select the network from the list and type the password when requested.
Assuming your device requires troubleshooting, i.e. not something that works "out of the box", then start here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by BlinkinCat on 2015-07-09
Thanks Vladlenn5000

Maybe there isn't a problem. WiFi light on modem is "On"

Can't see where option to enter N/W Name and password are.

---

### Post by Vladlenin5000 on 2015-07-09
In Ubuntu or flavours network is always managed by network-manager and accessible from its indicator  (near the clock, where all the other indicators are).
When the WIFI device is supported you don't need to do anything but click on the indicator, select the desired network and type the password when requested.
When it's not - as it seems to be the case - then please follow the troubleshooting give and post the result of the 'wireless-script' mentioned there.

---

### Post by BlinkinCat on 2015-07-09
Thanks kindly - I found  where Network Name should be entered but couldn't work out where the password would go - not prompted.

Will follow the thread - thanks...

---

### Post by BlinkinCat on 2015-07-09
Sorry about the delay - had a problem with forgotten P/W

pastebinit - [http://paste.ubuntu.com/11851379/](http://paste.ubuntu.com/11851379/)

---

### Post by Vladlenin5000 on 2015-07-09
There's no WiFi device listed. If you're sure you have one it's either damaged, disconnected or disabled in BIOS. But most likely you don't have one.

---

### Post by BlinkinCat on 2015-07-09
Hi - This time I switched modem off and the on again.

When I did that this time had info from ISP posted.

Maybe that it is O.K. now.

Will run script again to verify ... thanks.

---

### Post by BlinkinCat on 2015-07-09
Hi

Hopefully will be O.K. now...

pastebinit - [http://paste.ubuntu.com/11851510/](http://paste.ubuntu.com/11851510/)

---

### Post by Vladlenin5000 on 2015-07-09
Again, only Ethernet is showing.

And modem??? What does it have to do with WiFi?
This is turning into a very confusing thread. What hardware exactly are we talking about?

---

### Post by BlinkinCat on 2015-07-09
Hi,

I have another problem that I will have to attend to first.

However there is a provision to configure VPN and to edit the various options in boxes.

I have no idea what the info is required for these boxes.

I am afraid I will have to come back to this in 40 minutes or so..

---

### Post by BlinkinCat on 2015-07-10
40 minutes I said - then 8 hours later I get back...

After trying to take steps to recify problem, it appears I deleted something that I shouldn't have.

ISP couldn't help or fix.

Eventually had problem recified by technician. (What he did exactly I just can't say).

Will mark as solved - Sorry for messing you around Vladlenin5000.

---

