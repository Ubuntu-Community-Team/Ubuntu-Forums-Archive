---
title: "[SOLVED] Can't connect to the campus network via wifi (Clean Access)"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by FiReSTaRT on 2008-09-19
The way I assume this is supposed to work is:
1) Connect to the network
2) Try to access a web page and get a login screen
3) Log in
4) Get internet access
[http://www.mcmaster.ca/uts/network/wireless/CCAfaq.htm](http://www.mcmaster.ca/uts/network/wireless/CCAfaq.htm)

My problem is that it doesn't establish a connection.

My computer does connect to:
1) An unsecured home network
2) WEP network (however, 128-bit keys have to be entered in hex form)

Any ideas would be appreciated.

---

### Post by timcredible on 2008-09-19
the website says linux is supported, so call the tech support people at the school and ask them to help

---

### Post by FiReSTaRT on 2008-09-19
Their techies were useless.. I had one hover over the computer and he couldn't make a single suggestion.. Worst case scenario I'll take the comp to their office and see if they have someone who knows anything about Linux.

---

### Post by blak on 2008-09-19
My University for some reason claims not to support Linux on our wifi, but they support the iphone? Trust me I understand your frustration. I know there must be a way to connect to my universities wifi with Linux, but no one in their IT seems to have a clue about Linux somehow.

My thread is.... [http://ubuntuforums.org/showthread.php?t=924066](http://ubuntuforums.org/showthread.php?t=924066)

Maybe our threads can help eachother.

Good luck!

-blak

---

### Post by FiReSTaRT on 2008-09-19
Good luck to you too.. I'll see what I can do on Monday.

---

### Post by Nem1976 on 2008-09-19
Do you by change know what access points they are using?  
Can you see the Wireless network and do you actually get an IP address from the Access points?

---

### Post by FiReSTaRT on 2008-09-19
I can see the network but it refuses to connect. IIRC I don't get an IP address, but I've gone through a surgery and a whole lot of painkillers since the first/last time I've tried.

---

### Post by Nem1976 on 2008-09-19
I have the same issue with a Cisco wireless network here at work.  I see the SSID but can't get an IP address from it.  I tried staticly IP's and it doesn't work either.  If I boot into windows it works just fine.  So I know it's not a hardware issue.  I can connect to other networks just fine but this cisco based one.

---

### Post by Whiffle on 2008-09-19
Hmm, I have no issues with clean access on our school network, but we're using PEAP.  What exactly happens when you try to connect to the open network?

---

### Post by FiReSTaRT on 2008-09-19
It shows the connecting animation but it never connects. I have no explanations for it.

---

### Post by FiReSTaRT on 2008-09-22
After doing more research, I believe that the difficulty lies in dealing with unicast DNS servers. I tweaked nsswitch.conf and we'll see if that'll do the trick in a couple of hours. Wish me luck.

---

### Post by FiReSTaRT on 2008-09-24
Well, it turns out that the issue lies in not having Wifi in the buldings I tried to access it from. I was catching a weak signal but wasn't able to connect. When I tried to connect from a fully supported building, it worked like a charm.
Now, all I have to figure out why they don't have WiFi in Science and Engineering buildings? I'd really like to meet the genius who made the decision.

---

