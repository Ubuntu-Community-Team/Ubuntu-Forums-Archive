---
title: "Can't connect to the internet (wired broadband)"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by torgeir89 on 2007-11-04
Been searching through forums/google'ing for hours now..

I'm new to linux, but got it installed properly and so on. Now, the problem: I can't get connected to the internet. 

I've got a wired connection, and I get green lights on my ethernet card when I connect the wire. 
My ISP uses DHCP, so I've put my connection to that under "network settings", and added the two DNS servers I got from my ISP under "DNS".
When I use the same wire on the computer I am posting from, which has Windows XP installed, it works without any problems.

Still, no internet connection (tried to ping, firefox, etc etc). 

Any help would be highly appreciated (please don't make me go back to Windows  ), let me know if you need any output from any commands or something like that.

(posted this in the newbie-forum as well, then realized that this is probably a more suitable place :) )

---

### Post by DilfATX on 2007-11-04
I have had the same problem with my old trusty SHARP notebook that is over five years old..I have XUBUNTU running on it now.. I tried all three UBUNTU, KUBUNTU, XUBUNTU and none of them could recognize the ethernet port when I tried using broadband wired connection to it.  I simply bought a popular cheap brand wireless card and it worked just fine.. 

On the ethernet Linux recognizes that its connected and shows the speed but no IP address or any of that type of info.. I have been asking for this info on differ sites and searched on and off for few months now..and for some reason nobody seems to want to tackle this or help me out.. 

If you find a solution it might be some good info for me to use aswell since we have simliar issues..

---

### Post by dennis1200 on 2007-11-05
I was trying to connect to my office network, but both wireless and wired don't work (I'll leave wireless out of this post, as it probably involves Linux/WPA/bcm4318 fiasco). I can connect to the network, even get an IP and administer the router, but no internet access. The other computers in the office (Macs) all connect to the internet just fine. I've tried ifdown/up, dhclient, and rebooting, and we don't have anything like MAC filters setup that would keep my computer out. It's on  a 10.1.1.x setup instead of the usual 192.168.0.x, but that shouldn't make a lick of difference.

---

### Post by sipickles on 2007-11-05
I needed to put 

noapic

in my boot line. I think you cn edit this in;

/boot/grub/menu.lst


near the end.


mine looks like this:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=47690c44-0041-4765-a593-f38ab347872a ro quiet splash noapic
initrd		/boot/initrd.img-2.6.22-14-generic


Happy penguins!

---

### Post by sipickles on 2007-11-05
dennis, 


I got my WPA wireless working (easier than wired! lol!). I had to use wicd instead of network manager..... which I had to use a wired link to install!

Blimey.... windows anyone?

---

### Post by dennis1200 on 2007-11-10
I can do WPA using the new network configuration tool (not NetworkManager, not wicd, just good ol' network-admin). My problem is also only at work, not at home. At home I can do wired/wireless, no problem. And all that without a noapic or any extra configuration (other than ndiswrapper for the bcm4318).

Like I said, the wired at work even gives me an IP address on the local network, but I just can't access the internet. And the even weirder part is that back when I had Feisty, I could use it at work on the wired network (but not wireless; WPA problems). Now I'm a step backwards.

I really don't enjoy the Mac interface, and find GNOME to be way more productive and useful for workflow (not least of which due to the ability to alt-tab between several windows within one program and having multiple desktops). Heck, I even have Dreamweaver running perfectly in WINE. But it won't be at ALL productive if I have no internet.

---

### Post by kevdog on 2007-11-10
When things are not working at work (or where ever) are you receiving an IP address.

Things that might be a problem

Driver -- check with lshw -C network
Firewall - make sure to disable
route command - no gateway specified
DNS problem - dns server problem

```

ifconfig
lshw - C network
route -n <--- lists gateway
/etc/dhcp3/dhclient.conf -> File that controls your dns settings: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

```

More details from you would help me to diagnose your problem.

---

### Post by DilfATX on 2007-11-12
I figured out that if I unplug my ethernet cable from my computer and also the power source from the modem..for about ten minutes and then plug everything back in my computer now receives internet easily.. 

The issue is now..why coulnd't it do it without me having to do that?

---

### Post by sionghua on 2007-11-13
same problem here wired network not working. Works fine in Windows.

---

### Post by DilfATX on 2007-11-21
I found the solution on another thread.. I have to unconnect the ethernet cable and unplug my router from its power source for about 10 minutes to give it time to reset itself..then plug it in from my computer to my laptop then power my router back up.  IT only seems to give internet to the laptop if I do this.

---

### Post by abbyb1987 on 2008-07-14
hey friends...
you can check out this blog for help on this connection problem
i think it may help 
[www.ubuntrix.co.nr]("http://www.ubuntrix.co.nr")
:guitar:

---

### Post by Bipin on 2008-07-15
aye i gotta same prob here 
where should i enter the connection username and password 
can anybody help me 
but hey ma pc detects my nic card though 
but i dont know where to enter username n password

---

