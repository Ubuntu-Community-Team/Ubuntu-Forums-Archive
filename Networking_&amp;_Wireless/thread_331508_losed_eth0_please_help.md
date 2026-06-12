---
title: "losed eth0 please help"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Firecad2006 on 2007-01-04
hi this is my first post so heres my problem im using Ubuntu 6.10 and eth0 was working great untell my little sister came and closed the lid on my laptop and when i opened it again i couldn't get back on the internet, i tried restarting the computer but nothing, i went all over the forms try to find out how to solve my problem but nothing works. please help it driving me crazy.

---

### Post by scrooge_74 on 2007-01-04
try from a terminal window
sudo ifdown eth0

then

sudo ifup eth0

if that doesnt work try

sudo dhclient eth0

---

### Post by Firecad2006 on 2007-01-04
i tried sudo ifdown eth0 and it says sudo: if: command not found but ifup said interface eth0 already configured, sudo dhclient eth0 gave my a list 

DHCPDICOVER on eth0 to 255.255.255.255 port 67 interval 4,9,10,16,10,12 no working leases in persistent database - sleeping

---

### Post by scrooge_74 on 2007-01-04
sudo ifdown eth0 not working?

it seems you can talk with your router, maybe reboot the router and reboot the pc

the check the network manager and see if the card is active and using dhcp

---

### Post by Firecad2006 on 2007-01-04
i went to system>adim.> network setting and clicked on DNC tab under DNC servers theres to numbers 12.23.80.2 and 12.155.8.2 does that mean anything? i have one other windows laptop running on the router.

---

### Post by scrooge_74 on 2007-01-04
those seem to be the DNS numbers assign by your router or your ISP

Maybe you can disable eth0 from there and then enable it again, maybe it will work.

Any body else have any other ideas?

---

### Post by Firecad2006 on 2007-01-04
no it still not working, i tryed ifup and ifdown again but ifup says interface eth0 already configured and ifdown says fail to open temorary statfile /var/run/network/.ifstate.tep: Permission denied

---

### Post by scrooge_74 on 2007-01-04
can you disable the card from inside the GUI?

Sorry but I am running out of ideas, everytime I had a similar problem those commands got me out of it

---

### Post by Firecad2006 on 2007-01-04
i a little new to Ubuntu so wheres the gui?

---

### Post by scrooge_74 on 2007-01-04
Sorry the GUI is your desktop manager in this case is GNOME, your graphical enviroment

---

### Post by Firecad2006 on 2007-01-04
ok thank and yes i can turrn it off but still notingi just can figer out why closing the lip would do this?

---

### Post by scrooge_74 on 2007-01-04
I f you can turn your card out you should be able to start it again and then get an ip from the router, have you try to reboot the router and then start the laptop maybe that will clean something up and let it connect

About closing the lid you can check this thread [http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto](http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto)

---

### Post by Firecad2006 on 2007-01-04
ill give it a shot

---

### Post by Firecad2006 on 2007-01-04
still nothing, why is nothing working?

---

### Post by scrooge_74 on 2007-01-04
Another thread with better explanation about hibernate [http://www.ubuntuforums.org/showthread.php?t=321369](http://www.ubuntuforums.org/showthread.php?t=321369)

Can you ping your router from a terminal window?

---

### Post by Firecad2006 on 2007-01-04
i pinged and it says Network is unreachable

---

### Post by Firecad2006 on 2007-01-04
eth0 is sending packets i have like 116 now does that mean anything?

---

### Post by Firecad2006 on 2007-01-04
do mind if i add you to my msn list just for know im happy your helping me thank you

---

### Post by Henry Rayker on 2007-01-04
when you tried the ifdown and got a permissions issue, that's because you didn't put the sudo in front of it. Try ```
sudo ifdown eth0
```to see if it still gives you that same message. If that works, use ```
sudo ifup eth0
``` to re-up it.

---

### Post by scrooge_74 on 2007-01-04
> **Firecad2006 said:**
> do mind if i add you to my msn list just for know im happy your helping me thank you

Ok, go ahead,I just try to help out, it seems you can't reach the network

which still it is odd

check this file and tell us what you have there

do gedit /etc/network/interfaces

---

### Post by scrooge_74 on 2007-01-04
you should check in the power managment in the System tab the options you have for closing the lid and things like that.


i have mine to only black the screen when I close the lid, still Linux does not handle well power saving features on laptops.  But there is a thread with a solution

---

### Post by Firecad2006 on 2007-01-04
sudo ifdown eth0 disconnected it so i used sudo ifup eth0 but i get the some message as before

---

### Post by Firecad2006 on 2007-01-04
there nothing in that interface

---

### Post by scrooge_74 on 2007-01-04
> **Firecad2006 said:**
> there nothing in that interface

This is the last I can think of, ](*,) 

my /etc/network/interface file has the following, and you should at least have auto lo and auto eth0

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Firecad2006 on 2007-01-04
were do i put that at?

---

### Post by Firecad2006 on 2007-01-04
im going crazy im just going re-install start over im going to back-up my files and start over thanks for your help

---

### Post by Firecad2006 on 2007-01-04
i found this thread but i typed in sudo gedit /etc/network/interfaces but theres nothing in that file? [http://www.ubuntuforums.org/showthread.php?t=330790&highlight=no+network](http://www.ubuntuforums.org/showthread.php?t=330790&highlight=no+network)

---

### Post by Firecad2006 on 2007-01-05
i think my modem went out im on the live cd now so i don't know

---

### Post by scrooge_74 on 2007-01-05
> **Firecad2006 said:**
> i think my modem went out im on the live cd now so i don't know

Are you using a modem to connect to the internet or an ethernet card?

---

### Post by Firecad2006 on 2007-01-05
it high speed if thats what you mean cat5

---

### Post by Firecad2006 on 2007-01-05
i know it not my router i was on the live cd last night and the internet was working?

---

### Post by koenn on 2007-01-05
no guarantees, but if it was my problem, i'd try to remove that file
```
sudo rm -f /var/run/network/.ifstate.tep
```

I suspect that when closing the lid, your laptop did a hibernate and saved the state of the network card in that file - maybe if you remove it, you'll be able to get a new ip address
by running

```
sudo dhclient
```

---

### Post by Firecad2006 on 2007-01-05
for the first command it says rm: invalid option -- / try `rm --help' for more info?

](*,)

---

### Post by koenn on 2007-01-06
and did you try rm --help for more info ? 

it looks to me that you forgot the "f" - can you check it again ?

---

### Post by Firecad2006 on 2007-01-07
yes i looked in the help menu but i didn't see and thing about rm and i type just what you told my i tryed like 5 timed i got the something. i just going to for get it forget this studied computer it makes me hate computers even more now its not lunix its the fact computers will always have problems and theres no perfect computer. 

thank you for all your help.:KS

---

### Post by rbhigday on 2007-01-07
Please post the result of the following

```
iwconfig
```

---

### Post by Firecad2006 on 2007-01-07
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

---

