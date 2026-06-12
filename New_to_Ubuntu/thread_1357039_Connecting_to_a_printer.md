---
title: "Connecting to a printer"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by cjnkns on 2009-12-16
I realize this is the UBUNTU forums so I apologize for this.
But, people on these forums are just so damn helpful :)

I have a printer HP7410 all-in-one plugged into my router.

Anyway, I have an ubuntu 9.10 lappy that I can easily connect to my printer wirlessly. I just go to printers hit search and there it is no big deal.

But, my wife needs to me to hook up her XP laptop to the printer the same way. I have no idea how to do this.

There are two opitions I see on the dialog one to connect over the net. And the other ask for some path to the printer \\serer\printer.

What do I used to connect this for her? Sorry to ask an xp question here but I dont' have any issues with my Ubuntu laptop ;)

---

### Post by halitech on 2009-12-16
You don't mention if the laptop is running 32bit or 64bit XP but here is the driver download page.

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=ca&lang=en&product=391194&](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=ca&lang=en&product=391194&)

As far as installing, 
1. select network printer
2. Connect to a printer on the internet or a home or work network
- for the URL, enter [http://ipaddress.of.the.printer/](http://ipaddress.of.the.printer/)
3. select have disk for the driver and browse to where you extracted the files
4. continue as normal

For the IP address, you may want to set a static IP on the machine or use the router settings to assign a static IP based on the MAC address
Hopefully this will get you going

---

### Post by cjnkns on 2009-12-16
> You don't mention if the laptop is running 32bit or 64bit XP but here is the driver download page.

[http://h10025.www1.hp.com/ewfrf/wc/s...roduct=391194&](http://h10025.www1.hp.com/ewfrf/wc/s...roduct=391194&)

As far as installing, 
1. select network printer
2. Connect to a printer on the internet or a home or work network
- for the URL, enter [http://ipaddress.of.the.printer/](http://ipaddress.of.the.printer/)
3. select have disk for the driver and browse to where you extracted the files
4. continue as normal

For the IP address, you may want to set a static IP on the machine or use the router settings to assign a static IP based on the MAC address
Hopefully this will get you going


I downloaded the driver for this last night and installed it on the 32bit xp lappy. I guess I think I did there really was no confirmation page when the install was done. The install page with the progress bars looked like they finished and then there was nothing else....

When I go to connect to the printer vial the [http://ipaddress](http://ipaddress) method I get the xp error message telling me it can't find it. I know it's wrong because Ubuntu finds it just fine. :)

At least I know I am doing it the right way. I'll try again when she gets home from work . 

Thanks for your help!

---

### Post by halitech on 2009-12-16
Open CUPS and see what address Ubuntu is using and then use the exact same address. Might need :631 or something more to it then just the IP address. Possible it might also need IPP instead of HTTP at the beginning

---

