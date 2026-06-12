---
title: "Internet stopped working mysteriously"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by skipindadon on 2007-01-31
I haven't had any internet since Friday. I live with a couple of gys who use MAC and Windows and they have no trouble. I can't ping them and they can't ping me but I can ping our router. Resetting the router doesn't help. The MAC guy said it was DNS and I should change my DNS setting to what he has but that also doesn't help. There are other threads like this but none I have found have exactly the same problem as me. Another thread reply asked for messages from dmesg, when I run it the last thing it says is "No IPv6 routers found". The thread said if it was the case then disable IPv6 in the browser. I did that, also without success. The one thing that changed on the network was another computer was connected, but that has been removed now and my problem remains. Any suggestions of what to try would be most welcome.

---

### Post by chippy99 on 2007-01-31
Just an idea, worked for me when I had similar problem but no idea if it will help you. Check that you have
***nameserver 192.168.1.1*** in /etc/resolv.conf (replace 192.x.x.x with your routers address)

---

### Post by skipindadon on 2007-02-01
Thanks, it is all solved (but not really yet). Nameserver 192.x.x.x is in the /etc/resolv.conf file so that wasn't the problem. Some things I didn't mention about my setup are that I was using a wireless box device type thing. It sits behind my computer and communicates with the router over wireless, then a cable comes out and plugs into my ethernet plug. My computer is supposed to think it is on a wire while this device does the wireless part. Anyway, I typed the 192.... address of the router into my browser and instead of getting that I got this wireless box device type thing's login page. So for some reason it changed it's address to the same as the router, so I was never communicating with the router when I tried to ping it. Now if only MAC guy could remember the password for his special device type thing we might be able to fix it. Or get cables.

---

