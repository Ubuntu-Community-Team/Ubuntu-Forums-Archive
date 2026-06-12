---
title: "Network Connection Problem!"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by exit84 on 2011-01-28
Greetings!

I have Ubuntu 10.04 installed on an HP 8000 Elite PC.  Actually, I have a dual boot setup with windows7...I primarily work in windows, but enjoy using Linux also.

Yesterday, I booted into Linux for the first time in a couple of weeks, and updated my system.  I worked in Linux all day yesterday, with no issues.

This morning, when I booted into Linux, I had no network connectivity.  I rebooted into Windows, and I everything worked with no network problems.

I attempted to try and fix this myself.  After reading a bit, I decided perhaps I had a driver problem and downloaded installed [this driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3025&lang=eng").  Unfortunately, that did nothing and I still am experiencing the same problem.  I'm not adept with Linux at all, so perhaps I messed up the process.

When I hover my cursor over the "network" icon in the top right corner of my screen, I get "Wired network connection 'Auto eth0' active."  When I right-click it and look at connection information, I have an ip address.  But I am unable to browse the internet.

Thanks in advance for any assistance!

---

### Post by cariboo on 2011-01-28
If you are getting an ip address, but can't access the internet, it sounds like you may have a dns problem. Can you ping Google by name?

```
ping www.google.com
```

Can you ping it by number?

```
ping 72.14.213.103
```

---

### Post by exit84 on 2011-01-28
When I try to ping google by name, I get an "unknown host" error.  When I try to ping it by number, it just sits there...I waited around 10 minutes, and still never got a response, error or otherwise.

---

### Post by JKyleOKC on 2011-01-28
You might also have a "gateway" problem. Post the output of "route -n" which will show how your routing table is configured. When you paste it into the message editor, highlight all the lines and then click the "#" icon at the top of the editor window, to keep the formatting so that it will be easier for us to read...

---

### Post by exit84 on 2011-01-28
Output of "route -n" below:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
138.47.102.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         138.47.102.1    0.0.0.0         UG    0      0        0 eth0
```

---

### Post by JKyleOKC on 2011-01-28
Compare the listed addresses with those you get in Windows when you view the status display for the network when in Control Panel (the way to do this varies with different versions of Windows). The address you have set for the gateway (the bottom line of your list) does not look like a normal gateway address, but more like an address from your router. However not all ISPs follow the addressing conventions with which I'm familiar, so it may be okay -- comparing to the addresses that Windows uses should show whether it is or not.

---

### Post by exit84 on 2011-01-28
In Windows, under my Network Connection Details, the "IPv4 Default Gateway" is shown as 138.47.102.1.  Do I need to check "Destination" and "Genmask" in Windows, too?  I do not know where or how to verify those two values in windows.

---

### Post by JKyleOKC on 2011-01-28
No, only the gateway address was in question. Since they are the same, it's almost certainly okay, so the problem is most likely a missing or bad DNS server address as other posters have suggested.

---

### Post by exit84 on 2011-01-29
Okay...so how do I fix it?

---

### Post by JKyleOKC on 2011-01-29
I don't use Network Manager here (disabled it many months ago because my setup wasn't quite compatible with it) so my instructions may not match exactly what you see, but first open the "edit" option after you click its icon. As I recall there will then be a list of your network interfaces, which may have just one entry. Select the one you are using and click "edit" which should get you a dialog with several tabs, one of which will be for "DNS."

Click that tab, and add the address "8.8.8.8" without the quotes to it. If there's a checkbox to obtain the DNS automatically, made sure it's not checked. This will set Google's DNS server as the one to use, which should get you connected although it may not be the best one for you. Once on line, you can do a Google search for "DNS server" (with the quotes this time) to get dozens of possibilities...

Hopefully someone else will chime in and correct these instructions if I've mis-remembered the procedure!

---

### Post by exit84 on 2011-01-31
Jim, I booted into Ubuntu this morning to attempt to fix the DNS problem, and low and behold, I didn't need to:  I could browse with no problems.  Go figure.  I'm on a college campus, so who knows?...whatever was causing the problem in my network cleared itself.

Thanks for your help!  Perhaps it's the pessimist in me, but I have a sneaky feeling I may be back with a similar problem.  :)

---

