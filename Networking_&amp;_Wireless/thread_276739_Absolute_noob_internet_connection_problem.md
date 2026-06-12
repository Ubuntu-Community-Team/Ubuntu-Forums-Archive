---
title: "Absolute noob internet connection problem"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by protos on 2006-10-13
Hi - from South Africa here (same uni as Mr. Shuttlewoth 8) ). Completely new to Ubuntu and Linux - but after yet another windows crash that resulted in quite a bit of data loss has me wanting to try Ubuntu.

So I got the Live CD in the mail today - install fine - all ok - except no internet access :( . On my windows boot - I did not need to configure anything to get the internet working. My NIC connects directly to the apartment building's network which conencts me to the internet. When I set up the computer in the building, all the ISP asked me for was my MAC # I think. There is no authentication and no settings at all. The DNS and IP is assigned automatically.

On Ubuntu, the network card is picked up as eth0, I make sure it is activated and set to DHCP but still no luck. It shows the same DNS that Windows uses when I go to manually edit. But trying to ping [www.google.com](www.google.com) or even the DNS server has no result.

One thing I have noticed is it does not show my network card as the default gateway when I check Networking. I select it as default gateway, press OK, but as soon as I go back it is blank. 

Any ideas? An o/s without internet is useless to me.

Thanks a lot

---

### Post by fouadz on 2006-10-13
Hi,

Can you post the result for ifconfig ?

Thank you

---

### Post by handy on 2006-10-13
Welcome :)

Try turning off **ipv6** in Firefox as follows: 

Enter **about:config** in the ff address field.

Enter ipv6 in the new **Filter:** field.

Now double click on the one & only line left in the display window of ff, to change it's boolean value to **true**.

Close ff & restart, you will most likely now have access to the web! :KS

You will have to do the same simply task each time you boot from the Live-CD.  Just once after installation on your Hard Disk Drive.

---

### Post by protos on 2006-10-14
Will try the ipv6 trick as soon as I get a chance - thanks for that advice hope it works.

As far as the results of the ipconfig - how do I check this :confused: . Complete noob remember 8) . I'm sure I have to go into terminal and time sudo something hahaha. 

Thanks again for the help.

---

### Post by handy on 2006-10-14
Please let us know how you go, we are learning too...

---

### Post by drakshug on 2006-10-14
Hi. I've posted a few posts on the internet problem and I've finally got it running perfectly.
After installing and doing pppoeconf the connection would run until a reboot and then nothing.
This time round I didn't touch ipv6 or any config files. When setting up my connection I did not allow the connection to start on boot.Now I manually start using pon dsl-provider and it works every time.
I think that there was something happening on boot with the config and by not allowing it to automatically connect I have circumvented this.
Now that the net is up and running the xp partition will be backed up and wiped and my box will only run ubuntu:-D

---

### Post by handy on 2006-10-14
And another one joins... :D  Very :cool:

---

### Post by mips on 2006-10-14
> **protos said:**
> 
One thing I have noticed is it does not show my network card as the default gateway when I check Networking. 

Just keep in mind that the address of your ethernet card is NOT your gateway. Your gateway is the next-hop address/router.

---

### Post by protos on 2006-10-15
Sorry guys - how do I check ipconfig so that I can post the results here?

---

### Post by mips on 2006-10-15
Open a terminal and type:

ifconfig -a
cat /etc/network/interfaces
route -n

---

### Post by protos on 2006-10-23
OK guys - found some time off exams to try to get this working again.

On the advice of someone on IRC - I tried entering:

sudo dhclient eth0

The result is as follows:

Listening on LPF/eth0/...
Sending on LPG/eth0/...
Sending on socket/fallback
DHCPDISCOVER on eth0 255.255.255.255 port 67 interval 6
DHCPOFFER on 1x2.1x.2x2.5x (edited)
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPPACK from 1x2.1x.2x2.5x
SI0CADDRT Netwok is unreachable
bound to 1x7.1x.2x2.5x

Tried disabling ipV6 - no help.

Any ideas?

---

### Post by mips on 2006-10-23
> **protos said:**
> 
Any ideas?

Maybe provide the info requested...

---

### Post by protos on 2006-10-23
Sorry entering
ipconfig -a into the terminal gives an error.

Is it supposed to be sudo ipcongig -a?

What about the other 2 lines you gave me to try? :confused:

---

### Post by alaman on 2006-10-23
the command should be "ifconfig -a"

The other two commands were -->

cat /etc/network/interfaces
route -an

These will help us help you figure this out.

---

