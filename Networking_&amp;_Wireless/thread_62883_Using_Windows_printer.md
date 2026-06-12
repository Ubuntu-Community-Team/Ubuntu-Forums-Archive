---
title: "Using Windows printer"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by Mozzer on 2005-09-06
When I tried to install the printer attached to my Windows machine I found that there is no built in driver. So I downloaded a set from lexmark.co.uk called print-drivers-linux-glibc2-x86.deb which should cover my E320. (I assume a deb will work as it did for Ndiswrapper.) Then I renamed it to lexmark.deb and did this in root terminal:

root@ubuntu:/home/mozzer # sudo dpkg -i lexmark.deb
Selecting previously deselected package drivers-lexprtdrv.
(Reading database ... 89080 files and directories currently installed.)
Unpacking drivers-lexprtdrv (from lexmark.deb) ...
Setting up drivers-lexprtdrv (5.3.1-2) ...
   -- Updating symbolic links

However when I went back to install the printer I found the list had not been updated. I know there's an option to install extra drivers but I don't know exactly what the .deb did or if it installed drivers or what. If anyone can shed any light I'll be very grateful.

Mozzer

---

### Post by xy77 on 2005-09-06
I didn't find any Lexmark E320 Printer listed on [www.linuxprinting.org](www.linuxprinting.org) (which is a good ressource for information on printing with linux), but you could try one of E310 E312 E321 or perhaps the E210 that come with cups. (Perhaps something generic like E+ Ep or E works as well). Give it a try.

General advice: If you have the chance to buy a new printer and want to use it with linux check linuxprinting.org. It will give you a good hint on which models work best.

- David (xy77)

---

### Post by Mozzer on 2005-09-06
I found some more info... according to [this page](http://www.linuxprinting.org/pipermail/lexmark-list/2004q2/002521.html) you can use the Generic PCL-5c driver ljet4. So I set it up like that. When it came to user name and password, I followed the advice of other threads and put it as guest with no password. However, when I saved this info and went back in, it had no user name and a 7 letter password. When I tried to change this it kept changing back. I tried to print anyway and got this status message:

nt_status_access_denied: unable to connect to samba host.

What's going on?

---

### Post by s_p_a_r_k_y on 2005-09-06
create a username on your windows machine with a password, then use that username/password combination to connect

---

### Post by Mozzer on 2005-10-18
I've tried that but still when I put in the correct user name and password and close, it resets to no username and a 7 letter password. Why is it doing this?

EDIT: Never mind, fixed it using the HOWTO. That's one step further away from M$!

---

### Post by 11hjpphty76lkjj on 2005-10-21
Hey,

Sorry what how to are you talking about?  I need this info lol

Thanks!

Aaron

---

### Post by Mozzer on 2005-10-25
OK, here's how I did it...

On your Windows machine, make sure you have told your printer to be shared with the network and give it an easy name to remember (for this example I will call it printer1). Then make sure you have a windows user name and password that you can remember (e.g. user1 and password1). Also find out your computer's network name by right-clicking on My Computer, choose properties and the Computer Name tab. Here it will be known as windows1.

On your Ubuntu machine click System, Administration, Printing and double click New Printer. Choose Network Printer and Windows (SMB). Now add all your information (Host = windows1, Printer = printer1, Username = user1, Password = password1).

Now click forward and see if your printer is listed. If it is, great! If not, go to [www.linuxprinting.org](www.linuxprinting.org) and find your printer on there. If there is a driver specifically for your machine then download it. If not there might be a generic one that will do the job (e.g. I used a Generic PCL-5 driver for my Lexmark).

If you need to install the driver then do so using the button. Now click Apply.

Finally check /etc/cups/printers.conf to make sure it's all configured properly.

---

