---
title: "wlan0 doesnt show up"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by river_plate_2005 on 2007-04-05
1. i installed ubuntu
2. i installed ndswipper 1.8 and common
3. ran: sudo ndswipper -i /home/blha/blah/sis163u.inf
4. it installed
5. ran: sudo ndswipper -l
6. said hardwore exists
7. ran: sudo modprobe ndswipper (also just modeprobe ndswipper)
8. i got no errors, it just went to the next line, didnt say anything
9. i did wiconfig and it listed eth0 and like 2 others but not wlan0.
 

so i am thinking it know my drives are there and it instaled it but i cant seem to find wlan0..
any suggestions?

---

### Post by sargeras on 2007-04-05
Are one of the others Eth1 or Eth2 or something?  I have seen (even on my laptop) that wireless connections are, by default, registered as Eth1 rather than wlan0.  Also, I notice that you wrote ndiswipper .... did you mean ndiswrapper?  I personally, have not seen ndiswipper before, but just wanted to make sure.

Regards

---

### Post by timcs on 2007-04-05
On the other drivers that I have been working with I have had to type 

sudo ndiswrapper -m

this creates a file under /etc/modprobe.d/ndiswrapper which contains the reference to the wlan0 device. It may also mean you will have to reboot afterwards.

---

### Post by river_plate_2005 on 2007-04-05
i just checked on ubuntu and when i ran: iwconfig it came up wtih

l0 no wireless extension
eth0 no wireless extension
st0 (ithink) no wireless extension

and yes i tred doin sudp ndiswrapper -m and it added somethin to module..
but it still didnt have wlan0 in networking under admin.

when i run: sudo modprobe ndiswrapper ...what is suppose to happen...mine just goes to the next line, so i dont know if this part is working. for eg

mycomputer@desktop: sudo modeprobe ndiswrapper
mycomputer@desktop: 

oh and btw iam using trendnet tew 424ub wireless usb dongle

---

### Post by timcs on 2007-04-05
If you haven't already tried, reboot. 

Different devices acted in different ways to the sudo modprobe ndiswrapper. My netgear wg111 started flashing but this was after I had rebooted the system.

---

### Post by river_plate_2005 on 2007-04-05
hey,
i just triend everything again and reeboted my machine, when i go to networking its the same thing again, it shows my modem, ethernet but no wireless.

this is a screenshot of where iam at:

---

### Post by jdralphs on 2007-04-06
mine is doing the exact same thing with a broadcom bcm4318.

---

### Post by river_plate_2005 on 2007-04-06
damnn...ye whish this problem could be fixed, cuz withouht internet i cant even run my ubuntu...aim stuckwith xp :(

---

### Post by timcs on 2007-04-06
Not knowing too much about the gear you have, I am guessing that ubuntu may have a native driver that is conflicting with the ndiswrapper driver.

If the chipset is of a bcm variety then see if you get anything when you type :

sudo lsmod | grep bcm

perhaps if you do post back the output

---

### Post by river_plate_2005 on 2007-04-06
hey man.
i jus rand :sudo lsmod | grep bcm
it jus went to the nex line didnt give me erros didnt say anything...

and my computer its  a emachines t3104 and i updraded my ram to 1 gb..if that helps

---

### Post by Izaksly on 2007-04-06
i have the same problem,
and broadcom wireless cards arent helping

---

### Post by n0ah420 on 2007-04-06
Your wlan is probably set as eth1.  If you so desire you can change that.  The caveat is that it is not the smartest thing to do and really doesnt matter, since the name of your device is trivial.  You could call it anything you want (to an extent and with enough effort).  Anyway just edit /etc/iftab as root.  In that file you will see the device name and its mac address.  make sure you change the correct one and reboot.  Voila, you now have a wlan0 instead of an eth1.

Here is a good amount of ndiswrapper info:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Stay away from the kernel drivers for 4318 chips unless you enjoy pain.

---

### Post by graz79 on 2007-04-08
> **timcs said:**
> Not knowing too much about the gear you have, I am guessing that ubuntu may have a native driver that is conflicting with the ndiswrapper driver.

If the chipset is of a bcm variety then see if you get anything when you type :

sudo lsmod | grep bcm

perhaps if you do post back the output

I get 
bcm43xx               127252   0
ieee80211softmac  33792     1 bcm43xx
ieee80211             35272     2 bcm43xx, ieee80211softmac  

Thanks for any help (as this has been driving me insane)
Graz

---

### Post by Alekc on 2007-04-08
Same problem here with wl-138g :(

It was working so great with edge :/

Edit: i've solved with
> rmmod ndiswrapper
modprobe ndiswrapper

(for complete procedure [http://blog.alekc.org/2007/04/08/install-wl-138g-on-feisty-fawn/](http://blog.alekc.org/2007/04/08/install-wl-138g-on-feisty-fawn/))

---

