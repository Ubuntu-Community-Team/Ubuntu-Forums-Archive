---
title: "DNS settings lost (Dapper Drake)"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by j.robinson on 2006-10-11
Greetings
My D-Link ADSL Router works fine with Windows and other flavours of Linux. However I can't (easily) connect to the 'net with Ubuntu 6.06. Investigations (on this forum and others) show this to be a problem for some other users. 

What happens is the address of the router (10.1.1.1) is found and written into the DNS settings (and the resolv.conf). So I manually put in my primary and secondard DNS IPs and all works for a little while.  However some time later these are over written again by 10.1.1.1....!

Is there any easy solution to my wows? Is this a "bug", or is my Router at fault. PS I'm a Linux newbie. 

Kind regards
John

---

### Post by wieman01 on 2006-10-11
Ok, try this to make it stick (assuming you're using DHCP):
> sudo gedit /etc/resolvconf/resolv.conf.d/base
Add your setting:
> nameserver [COLOR="Red"]192.168.xxx.xxx[/COLOR]
Now replace [COLOR="Red"]192.168.xxx.xxx[/COLOR] with your preferred DNS. Save the file & restart the computer.

If that does not work, there'll be another approach. :-)

---

### Post by handy on 2006-10-11
This is probably the other way :) One of these 2 should do it for you... :KS 

[  Try **_*Option 3*_** from **_*post 13*_** of this thread?]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2")

---

### Post by wieman01 on 2006-10-11
Comes in... handy. :-) Thanks, buddy.

---

### Post by handy on 2006-10-11
> **wieman01 said:**
> Comes in... handy. :-) Thanks, buddy.

Why do I get the impression that you were expecting me? :-D

---

### Post by wieman01 on 2006-10-11
> **handy said:**
> Why do I get the impression that you were expecting me? :-D
I dunno... But indeed I was. :-) History repeats itself. Even in here. Haha.

---

### Post by handy on 2006-10-11
> **wieman01 said:**
> I dunno... But indeed I was. :-) History repeats itself. Even in here. Haha.

Sometimes I think *especially in here*... :)

---

