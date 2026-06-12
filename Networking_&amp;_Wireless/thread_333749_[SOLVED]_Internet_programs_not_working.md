---
title: "[SOLVED] Internet programs not working"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by Phoenixzeus on 2007-01-07
Hi, I am relatively new to Ubuntu (about 6 months or so..)
The problem is...

I could not browse the internet with mozilla or update programs with synaptic. I followed the Disabling Ipv6 walkthrough and that has now allowed me to access websites and has got Firefox working correctly, however this still leaves synaptics (or any internet activities not in Firefox not working.)

I can ping any website all with 100% packet return and browse any website in Firefox perfectly.

All internet activities work perfect on all the other (windows based) computers in the house.

I think the problem lyes with a way of disabling ipv6 for all programs not just Firefox, however as I said I am new and most likely wrong.

I am on DSL internet with Iprimus

Any help would be very much appreciated.
Thanks,
Phoenixzeus

---

### Post by scrooge_74 on 2007-01-07
What error messages you get with synaptic?

---

### Post by Phoenixzeus on 2007-01-07
Ok, when I open synaptic and click re-load (because it has to reload database to get most recent updates) it brings up the window and remains on 0%, and if you wait long enough it then says
"status: failed, size 0kb, package Release.gpg, [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg" and then if you wait longer all 6 update files will fail with the same problem.

If you do the apt-get command in terminal it will also come back with a timed out error

I am running 6.10 Edgy

Thanks for your help
Phoenixzeus

---

### Post by scrooge_74 on 2007-01-07
See if you can use a mirror closer to home, maybe that is your problem.  It could be there is some communication problem or the servers are down

---

### Post by Phoenixzeus on 2007-01-07
Nope it only shows Main mirror, American mirror and Australian mirror and all of them send back the same problem :(

---

### Post by scrooge_74 on 2007-01-07
Try other mirrors

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by Phoenixzeus on 2007-01-07
How do I use them mirrors for Synaptics or other internet based programs? All i can find to do with them is to download Ubuntu

---

### Post by scrooge_74 on 2007-01-08
you have to make changes to a file call sources.list which is in /etc/apt

Or you can make changes from inside Synaptic to the same file

Somewhere in that page or you will have to look further there should be a list of mirrors, those mirrors there usually manage also the updates

---

### Post by handy on 2007-01-08
Check out the DNS section of [_**this How-To**_]("http://ubuntuforums.org/showthread.php?t=282034"), it should solve your problem...

---

### Post by Phoenixzeus on 2007-01-08
Handy,
In the bit that says 
"Editing the /etc/dhcp3/dhclient.conf

(If you are unfamiliar with using the Terminal have a look down this page for the Text & the Terminal section.)

Enter the following line in the Terminal:

sudo gedit /etc/dhcp3/dhclient.conf

and just before the request line in your dhclient.conf file that you are looking at in gedit, add the following line, or remove the comment # from the start of the line if it is allready exists):

prepend domain-name-servers 208.67.222.222, 208.67.220.220;"

I HAVE:

"#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,"

Do I remove just the # from the above line or remove the prepend line compeletly and re-type what you wrote?

Many thanks
Phoenixzeus

---

### Post by Phoenixzeus on 2007-01-08
Thanks guys for all your help, I got synaptics working thanks to handy's guide
:)

---

### Post by handy on 2007-01-09
hi, Pheonixzeus :) 

Just remove the **#**, seeing **that** at the start of the line means that it is commented out.

Then delete the numbers at the end & add either your ISP's DNS addresses, or use OpenDNS addresses.

If you use OpenDNS you must edit your router/modem's firmware as per the how-to.

Any problems, let us know here?

---

### Post by handy on 2007-01-09
Ooops!  I do sometimes answer & not notice that there are more pages, sorry about that! :)

---

