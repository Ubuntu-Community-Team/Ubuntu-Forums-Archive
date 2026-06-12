---
title: "Got Link Lights but no ping.  Where do I start?"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by lile001 on 2010-11-26
I know just enough about this stuff to be dangerous.  Here is the situation:
Using Ubuntu 10.04 9 on a machine about 9 months old.  Internet was working OK on this setup at one time.  I do not know of any changes that would affect internet connectivity on the Ubuntu machine, however Ubuntu still mystifies me rather thoroughly. 

I have a wireless/wired router, and the computer is connected through a hardwire to one of the ports.  I have link lights on that port.  I have swapped out the CAT6 cable to that port.  The computer I am typing on right now is connected through the wireless link, and obviously working.  A Windows box is also connected hardwired and getting on the net OK.  

I can't ping anything from the Ubuntu box.  I can ping an address from the WIndows box, but on the Ubuntu box it claims "Network Unreachable".  Pinging something like Yahoo.com also gives an error message.  Of course any browser complains that it is "offline".  

What shall I try next to figure out what is wrong?  Ping is about the only thing I know how to do in troubleshooting an internet connection, besides checking the cables. 

What is the simplest thing to check next?

---

### Post by Xik on 2010-11-26
Go to Network Connections (System>Preferences>Network Connection).

Select the network connection it's currently connected to.

Edit...

Go to IPv4 settings and make sure "Automatic (DHCP)" is selected besides "Method".

Leave "DHCP Client ID" blank.

Check the box besides "Require IPv4 addressing for this connection to complete."

Go to IPv6 Settings and select "Ignore" besides "Method".

And apply.

Hope that works.

Xik.

---

### Post by MooPi on 2010-11-26
Can you open a terminal ( which is located under Accesories menu) type each of these seperately. Each will deposit text files with info in your home folder. Copy that text info back here. ```
lspci>mypci
less /etc/network/interfaces>interfaces
ifconfig>myconnections
```

---

### Post by lile001 on 2010-11-26
> **Xik said:**
> Go to Network Connections (System>Preferences>Network Connection).

Select the network connection it's currently connected to.

Edit...

Go to IPv4 settings and make sure "Automatic (DHCP)" is selected besides "Method".

Leave "DHCP Client ID" blank.

Check the box besides "Require IPv4 addressing for this connection to complete."

Go to IPv6 Settings and select "Ignore" besides "Method".

And apply.

Hope that works.

Xik.

Nope, no luck.  It's something harder than that, which THANK YOU THANK YOU is a very simple and straightforward thing for a N00B to check.  I really like it when people try the simplest thing first.  

On to the dreaded terminal.....

---

### Post by lile001 on 2010-11-26
> **MooPi said:**
> Can you open a terminal ( which is located under Accesories menu) type each of these seperately. Each will deposit text files with info in your home folder. Copy that text info back here. ```
lspci>mypci
less /etc/network/interfaces>interfaces
ifconfig>myconnections
```

Thanks!  


Three files should be attached to this message, if things work like they seem to.

---

### Post by lile001 on 2010-11-26
> **lile001 said:**
> Thanks!  


Three files should be attached to this message, if things work like they seem to.


Sorry, Windoze trashed the linefeeds, making them harder to read.

---

### Post by MooPi on 2010-11-26
Okay lets try something simple in terminal again.```
gksudo /etc/network/interfaces
``` Add this to the end of the file ,proofread save and close. ```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
Lastly ```
ifconfig eth0 up
```
Check and see if your connection starts. If not reboot and check again.

---

### Post by lile001 on 2010-11-26
> **MooPi said:**
> Okay lets try something simple in terminal again.```
gksudo /etc/network/interfaces
``` Add this to the end of the file ,proofread save and close. ```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```Lastly ```
ifconfig eth0 up
```Check and see if your connection starts. If not reboot and check again.

Hooray!  That did it!  Now posting from the formerly dead Ubuntu machine!  

Ummmm... What did we do?

---

### Post by MooPi on 2010-11-26
Told your computer to use the existing hardware when it starts. Please mark as solved.

---

