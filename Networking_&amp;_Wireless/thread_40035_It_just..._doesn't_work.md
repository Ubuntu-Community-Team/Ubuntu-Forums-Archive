---
title: "It just... doesn't work"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by mark.johnson on 2005-06-07
I installed Kubuntu, everything seemed to go fine. I entered my IP address, Mask, Gateway, Nameservers, and carried on through the process.
 
When it came to configuring Apt, it took about 10 minutes to do each job. After rebooting, my connection just doesn't work. Nothing. I cant ping anything, use Apt, anything. I know all the network stuff was correct. What's going wrong?

Thanks,
Mark

---

### Post by SNo0py on 2005-06-07
The question is - is it still correct? What does an ifconfig tell you?

---

### Post by brickbat on 2005-06-07
Hi,

You need to provide information.  not just complain. what is your ip address.  What are the settings you have entered? What are you trying to do (in detail)

First, try entering ifconfig at a command prompt and paste the result here and maybe we can help.

ciao
bb

---

### Post by mark.johnson on 2005-06-07
[QUOTE=brickbat]Hi,

You need to provide information.  not just complain. what is your ip address.  What are the settings you have entered? What are you trying to do (in detail)

First, try entering ifconfig at a command prompt and paste the result here and maybe we can help.

ciao
bb[/QUOTE]Yeah, sorry about that, I was feeling a bit stressed and impatient when I made that post.

Ok, my ip address is 192.168.0.12, my DNS are 194.168.0.100 and 4.2.2.1. Im just trying to set up the system for general internet access through my network.

ifconfig displays eth1 and all the details, anlong with lo (do you want the full output of that?)

The connection works fine on MS Windows and even on Knoppix, but there's nothing there on Kubuntu.

Thanks, Mark

---

### Post by Gtaylor on 2005-06-07
Type **dmesg** and see if there are any network related errors in there. And also verify that your DNS/Gateway info are correct, that can often mess things up. If you can run a DHCP client instead of a static just for testing, I'd try that too.

---

### Post by mark.johnson on 2005-06-07
Aha, I did dmesg, and at the end of the output is "eth1: no IPv6 routers present"

Does that suggest anything as to what's up?

Mark

---

### Post by Gtaylor on 2005-06-07
Unfortunately not. That's a normal warning message. If you have a working eth interface and there aren't any kernel errors, I can only suggest one last thing. Look in your **lspci** output and see if your network card is there. If it is, you probably have misconfigured your interface as far as the DNS/GateWay/IP go.

---

### Post by mark.johnson on 2005-06-07
Yep, its there. Looks like I've been stupid again. I'll see if I can get DCHP to work instead. It didn't work when I was installing for some reason.

Thanks for your help,
Mark

---

### Post by Gtaylor on 2005-06-07
Do this:
> 
sudo gedit /etc/network/interfaces

Look for a line that says something like:

iface eth1 inet static

There will be a few lines below this. Comment them out by putting #'s in front of the lines.

Add this:

iface eth1 inet dhcp

Save/quit, do this:
> 
sudo ifdown eth1
sudo ifup eth1

This should fix you up, and best of all there's no setting IP addresses, gateways, etc.

---

