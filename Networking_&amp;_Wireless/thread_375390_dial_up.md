---
title: "dial up"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Linux&amp;Lizards on 2007-03-03
Hey guys I just bought a new modem 
here is the FCC number cjemul-35739-m5-e


Any one know how to set it up with ubuntu?
I have never set up dialip so this will be a first.

---

### Post by Linux&amp;Lizards on 2007-03-03
anybody know of which driver to use?

---

### Post by Linux&amp;Lizards on 2007-03-04
come on guys this is for a friend.

he just spent $80 on a new internal modem and I would liek to get it working....

---

### Post by yabbadabbadont on 2007-03-04
If it is a crippled "Winmodem", then good luck.  If it is a true hardware modem, then it should "just work".  If it is a winmodem have him return it and buy an external serial modem.  Then you are pretty much guaranteed to get a true hardware modem.

A simple google search turned up: [http://www.linmodems.galeon.com/latest.htm](http://www.linmodems.galeon.com/latest.htm)

It appears that it is a winmodem and it's status is listed as unknown.

Hopefully, someone else has used this modem before and will be able to help you.  :D

---

### Post by FLPCGuy on 2007-03-04
Be more careful when selecting a dial-up modem for Linux.  The 'Best' I've seen is the Best Data 56SX V.92 'full, real' external serial modem available from several sources.  If you can't get your partiy soft modem with drivers to work, this is your best bet.  Best Data no longer produces these modems and sold off existing supplies to others but provides some support on their website.

used  5.99 +s/h
[http://www.geeks.com/details.asp?invtid=56SX92WB-BULK&cat](http://www.geeks.com/details.asp?invtid=56SX92WB-BULK&cat)

new $19.99 US free shipping
[http://www.gearxs.com/gearxs/product_info.php?products_id=3464](http://www.gearxs.com/gearxs/product_info.php?products_id=3464)

I bought two of the used ones and they work great with NO drivers required for Linux.  (Windows 2000/XP does require the drivers included on the CD as it ironically has no compatible drivers built-in).

One of the two used ones I got was older and included a pin converter dongle. It didn't work (probably a bad dongle) but Comp Geeks exchanged it within 30 days.

[LEFT]                                        [http://www.markshuttleworth.com/arch...#comment-10942](http://www.markshuttleworth.com/arch...#comment-10942)
    [LEFT]"At the moment ubuntu/kubuntu is booby-trapped against dial-up users:[/LEFT]
    [LEFT]dial-up modem users must comment out the 'auth' line in /etc/ppp/options and create an empty /etc/resolv.conf file. Once these two arcane measures are taken, dial-up modems work fine. This problem has been incorporated in every kubuntu since at least 5.04."[/LEFT]
    
   Setting up a modem is fairly simple but not intuitive.
// backup original in case you mess up
// change auth to noauth or comment it out with ## 
// grant access rights to USERNAME

From a terminal run 
$ sudo cp /etc/ppp/options /etc/ppp/options.bk 
$ sudo gedit /etc/ppp/options 

$ sudo adduser USERNAME dip 
[/LEFT]
    [LEFT] $ sudo adduser USERNAME dialout
                                        [LEFT] $ sudo pppconfig
[/LEFT]

[/LEFT]
 This runs the text-based PPP configuration app. Setup your default ISP info as 'provider'.   
You connect from the terminal with **pon**  disconnect with **poff**.  **plog** shows log file.
Once connected, use System, Admin...,Synaptic to download KPPP for an easy graphical interface applet.

---

