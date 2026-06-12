---
title: "Slow Internet"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by darchorse on 2007-08-27
Hello Everyone,

My internet is very slow on my Ubuntu (feisty faun) PC. Just a bit faster than dial up. The connection is a business grade 512/512 broadband connection. I also have a widows machine connected to the router and it is much quicker than the Ubuntu machine. They are using the same hardware and both are using firefox.

I have no experience of tweeking Ubuntu and I would like some info on where to start.

 TIA 

Darchorse

---

### Post by ittiam on 2007-08-27
Probably your ipv6 may be running, you need to disable it. Howto is [http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

---

### Post by darchorse on 2007-08-27
Thank you for the reply. Unfortunately I do not understand what they are talking about when they say "add these lines". Add them to where and how?

Is there a post anywhere that starts at the terminal command line?

TIA

darc

---

### Post by pidey on 2007-08-27
My understanding is that you are supposed to type
sudo nano /etc/modprobe.d/aliases

and then edit the file there.

However, I am also having a the same problem (I think), and this did not help one whit.

Other symptoms I am facing is that other computers on the network are normal speed (though this is the only non-windows based machine) , when this computer is booted into windows its fine.  Ping speeds are normal.  WOrth noting is that ubuntuforums.org is still fast.   Are you facing similar symptoms?

---

### Post by will71110 on 2007-08-28
How are you connecting to your LAN or WAN (if your strictly using USB).

USB?
LAN though a hub or directly to the router?
Wireless?

---

### Post by pidey on 2007-08-28
For me atleast: I am using a wired router, which is shared with another computer.  The other computer is normal in speed, its just webpages are significantly slower in linux than in windows.


*edit* Its probably relevant that I tried both firefox and another browser, I think it was epipfany.... or something, both were slow.

---

### Post by darchorse on 2007-08-28
Re: Slow Internet
For me atleast: I am using a router, which is shared with another computer. The other computer is normal in speed, its just webpages are significantly slower in linux than in windows.

Same here - I'm using a router with an ethernet wired connection. The windows machine is way quicker. The machine I am using with ubuntu installed was a windows machine and it was at least as fast as the other windows PC.  It must be something to do with the OS??? 

Darc

---

### Post by will71110 on 2007-08-28
Be aware that the longer you use a browser the faster it'll get if you are caching webpages (browsing the same page of course).  If you goto edit -> Preferences -> Network and look at how much you cache.  Mine is defaulted to 50 Megs. You can increase this if you like but it wont speed things up, just make more room for caching.

If you get near this limit and you goto a new page it will slow down because the Caching has to delete files.  Clearing it would fix that but you'll start the caching all over.

EDIT:  Some people think that disabling IPv6 will speed it up.  Look though this form.  They talk about it in about the middle of the thread.  [http://ubuntuforums.org/showthread.php?t=268635](http://ubuntuforums.org/showthread.php?t=268635)

---

### Post by ittiam on 2007-08-28
Disabling ipv6 worked in my case and I am pretty sure it worked for others too.

---

### Post by pidey on 2007-08-30
I disabled IP6, it didn't help at all.  It also isn't a cache problem.  I am talking abhorrently slow times.  Like accessing google takes 5+ minutes.

My ping times appear normal, and my download speeds appear normal (I was downloading linux updates at 700+kB/s)  But for some reason webpages take abyssaly long to load up.  I'd like to be able to use a linux based system primarially, but at five minutes per webpage it simply is not possible.

---

### Post by pidey on 2007-08-31
*bump*

Sorry for doubleposting, but this has reached thread five and I haven't heard any solutions for my problem, does anyone know what is wrong?  Again, I have disabled IPv6, that didn't do anything.  Webpages load VERY slow (5+ minutes for google) despite download speeds (when I was updating libraries or whatever they were called it was over 700kb/s)  and ping times being normal.

---

### Post by will71110 on 2007-08-31
Look in your sys logs and see of anything look abnormal when you open firefox (sys logs will update live and you can watch them as you open the program up).  If you do see something funky when you try and use firefox,  post it here.

---

### Post by gtdaqua on 2007-08-31
ok- what browser are you using?
can u post the "ifconfig" (from console) results? 

When you say ping respones are ok, how are u pinging? by IP address or by names?

what is your DNS server? This could be the most likely issue. (type "nslookup" and in the following prompt type "server" to know ur default DNS server)

If this is a home connection or a simple DHCP in a ADSL router, then your router is your DNS server. Change this to a public DNS (OpenDNS - 208.67.222.222, 208.67.220.220)

You need to add these entries in the file "resolv.conf"

# sudo nano /etc/resolv.conf

add the following lines: (if there are any other lines, you may want to comment them out by prefixing a "#" at the start of the line.)

nameserver 208.67.222.222
nameserver 208.67.220.220

then restart your networking services:

#sudo /etc/init.d/networking restart

Try this and let us know how it went. If it still doesnt work, then we will edit the dhcp configuration file in /etc/dhcp3/dhclient.conf.

---

### Post by gtdaqua on 2007-08-31
by default your dhclient.conf file overwrites the resolv.conf file.

So edit the dhclient.conf file:

#sudo nano /etc/dhcp3/dhclient.conf   

you will find a line beginning with 

"prepend domain-name-servers"

If that line begins with a "#", then remove that "#" so that that the entry is activated.

make it look like this (without quotes)

"prepend domain-name-servers 208.67.222.222, 208.67.220.220;"

The next line would begin with "request subnet-mask, broadcast-address...." etc
In that setting, remove the words "domain-name-servers" or "name-servers" (not sure exactly, coz I have removed that in mine when I had slow connection issues)

What you are actually doing above is forcing Ubuntu to use the OpenDNS servers for name resoultion and NOT to use the setting that you would receive from your DHCP server (probably ur router in this case)

Restart the network.
#sudo /etc/init.d/networking restart

Test your connection.

---

