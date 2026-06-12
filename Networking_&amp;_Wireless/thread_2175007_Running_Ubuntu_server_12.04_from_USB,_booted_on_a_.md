---
title: "Running Ubuntu server 12.04 from USB, booted on a HP T5125 thin client."
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by Exoduc on 2013-09-17
Hello ubuntuforums,

First post here, i hope you can help me alittle along with this unusual setup im attempting to put together.
In short terms, the idea is as such:
So far i've installed ubuntu server 12.04 on a usb-pen and got it up and running just fine.
Next i attempted to boot from usb (the server installation), on a HP thin client T5125.
While the client boots up fine, reads the usb and starts the OS, i run into what i imagine is driver issues related to the NIC. It will pause at the network configuration on bootup and wait 60 seconds etc etc, untill finally booting up but without the network configured.
The 'sudo lshw -class network' command shows nothing, ifconfig shows nothing. So i guess the network card is completely cut off at this point.
I've been googling and searching all i could, unavailable to find any related topics on this particular setup. This is where you come in! :-)

What i hope you can tell me is: What is the particular network driver required, to make ubuntu understand the HP thin client NIC?
And secondly, How do i install it once i have the driver?

also, i know there might be smarter ways to create a setup similiar to this one, but this is the equipment i have available. It's a work related project, which we'd like to see if we could get working. As you can see, we're stuck here.

Thanks for any help you can give me. :-)

---

### Post by Exoduc on 2013-09-17
Turns out the issue wasnt what i expected at all. This link solved the interface issue for me: [http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/](http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/)

---

