---
title: "Modem Autodetect failure"
date: 2005-07-17
forum: Networking &amp; Wireless
---

### Post by Amberlicious121 on 2005-07-17
I am testing a USRobotics dial-up modem in my test machine which has 2 hard drives, one with W98 the other one obviously Ubuntu Linux.  Unfortunately, Win finds my new hardware while Ubuntu does not.  I cannot install gnome-ppp because it tells me that it doesnt' exist.  I tried a LAN card and an ethernet card as well and none seem to be recognized by Ubuntu, but win finds them just fine and the generic drivers work as well.

When I open a terminal in Ubuntu and enter "pppd" it returns the response from the pppd as follows:

    pppd: The remote system is required to authenticate itself
    pppd: but I couldn't find any suitable secret (password) for it to use to do so.
    pppd: (None of the available passwords would let it use an IP address.)

What am I missing?  The Ubuntu help files are a little thin and I've found no help topics on the subject.  Yes I'm a new Linux user and so far I love Ubuntu, I just need to resolve this to get any real use out of it.

Thanks.

---

### Post by autocrosser on 2005-07-24
Well-try System>Network Settings>Interface Properties>Modem & hit the Autodetect button--Is the USRobotics a USB modem? If so you should see /dev/ttyACM0--You can use the networking panel to connect out--its a pain (admin password everytime) but it works--when you have a good connect-out, you should use Synaptic & get Gnome PPP--you might have to add the "extra" respositories to find it--check out [http://ubuntuguide.org/](http://ubuntuguide.org/)

Hope this helps!!

Cheers!!
Dean

---

