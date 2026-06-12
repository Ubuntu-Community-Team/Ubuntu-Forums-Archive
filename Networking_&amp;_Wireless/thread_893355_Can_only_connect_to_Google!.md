---
title: "Can only connect to Google!"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by deafpanda on 2008-08-18
Hi all,

I'm new to linux.

Using ubuntu 8.04.

I've set up my network with the correct settings.  I can ping any site in network tools.  However, firefox times out when I attempt to connect to anything but Google.  Synaptic times out when I try to use that too.

After extensive searches, it seemed that the problem was tcp_window_scaling.  Have set net.ipv4.tcp_window_scaling = 0 in /etc/sysctl.conf.  Still no joy!

Can anyone help a poor newbie who would love not to have to rely on windows?

Thanks a lot,
Will

---

### Post by dmizer on 2008-08-18
Please try disabling ipv6 according to these directions: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by deafpanda on 2008-08-18
Hi, thanls for your response.

I've already disabled ipv6, both on firefox and in /etc/modprobe.d/aliases.  Followed the instructions in that link anyway, and still no luck.

I am sort of connected to the internet, but the only site I can access is Google.  Very odd.

Any ideas?

---

### Post by prshah on 2008-08-18
> **deafpanda said:**
> However, firefox times out when I attempt to connect to anything but Google.

Hi, I had the same problem, you can take a look at my [(solved) post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") on this; you could also [review the entire thread]("http://ubuntuforums.org/showpost.php?p=4514356").

---

### Post by deafpanda on 2008-08-18
Thanks, that gives me some hope at least...
I've altered those settings on my router.  I'm not sure how to alter the settings on ubuntu though...on your old post it had the intructions for DHCP, I'm using static IP though.  Sorry to be a newb, but do you know how I'd go about doing this? :)

Thanks a lot

---

### Post by deafpanda on 2008-08-18
cat /etc/network/interfaces gives me:

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.158.0.2

auto eth0

---

### Post by prshah on 2008-08-18
> **deafpanda said:**
> 
I've altered those settings on my router.  I'm not sure how to alter the settings on ubuntu though...

I didn't make any changes to ubuntu; my ubuntu mtu is set to 1500 as usual; if the post above didn't solve your problem, I'm guessing your problem is different from my problem...

---

### Post by deafpanda on 2008-08-18
Well thanks, it seems it was the same problem!  I had to add the line:

mtu 1492

and then it worked!  Very pleased.

---

### Post by prshah on 2008-08-18
> **deafpanda said:**
> 
and then it worked!  

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

### Post by pantherattack on 2010-05-23
Thank you very much! I've been trying to solve this for the past couple of days.

My router's configuration page had no option to change the MTU. But changing it from 'automatic' to 1492 on my desktop did the trick. I did it through GUI in 10.04:

[LIST=1]
[*]Right click network icon in tray and select 'Edit Connections...'
[*]Select eth0 and press 'Edit...'
[*]Change MTU to 1492
[*]Hit 'Apply...'
[/LIST]

---

