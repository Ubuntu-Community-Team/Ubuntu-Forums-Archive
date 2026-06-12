---
title: "FTP and Dlink Router"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-11-24
Hello again,
I have been trouble configuring my router to support FTP to my server.

My router is hooked into my modem, and connected to my router via wireless is my server. 

I have installed ftppro on the server, and I able to access FTP from anywhere within the house, even from the router's external IP address. However, as soon as my friend (who isn't on my network) tries to connect:
From Filezilla:

```
Status:    Connecting to xxx.xxx.xxx.xxx:21... 
Status:    Connection established, waiting for welcome message... 
Error:    Connection timed out 
Error:    Could not connect to server
```I have opened port 21 on my router. I had my friend conduct a ping test on my router's external IP, and that too failed.

Any Suggestions?

---Edit

I also tried this from behind a proxy, and it also timed out.

---

### Post by BQAggie2006 on 2009-11-24
You have to set up port forwarding. Log into your router's administration interface, and look for something named similarly. Then, you tell the router to point any traffic coming in or port 21 to go to your server's IP address.

---

### Post by darkeye123 on 2009-11-24
I have the Virtual Server tab set up correctly. But under port forwarding, what UDP port should I unblock? 21? 

After changing these settings I still cannot ping my router or access my FTP.

Thanks you for your time!

---

### Post by darkeye123 on 2009-11-24
I have the Virtual Server tab set up correctly. But under port forwarding, what UDP port should I unblock? 21? 

After changing these settings I still cannot ping my router or access my FTP.

Thank you for your time!

---

### Post by BQAggie2006 on 2009-11-24
It's probably a better idea to unblock the TCP port, not the UDP port, but yes, it's port 21.

As far as not being able to ping your router, it could be configured to block pings from the outside or your ISP could not allow it.

Are you running any kind of Dynamic DNS service or are you just trying to access it by your external IP address?

---

### Post by darkeye123 on 2009-11-24
I am not running any DDNS service. I am just trying to access it from my external IP. 

Thanks again!

Found the source of the ping issue. There is an option disabling it. Should I enable it to allow for pinging, or does it not affect the server problem whatsoever?

---

### Post by BQAggie2006 on 2009-11-24
I guess try to verify that you are using the correct one by going to [http://whatismyip.com](http://whatismyip.com). If you still can't access it, check with your ISP to see if they prohibit you from hosting services from your IP.

---

### Post by darkeye123 on 2009-11-24
Alright. Will check with my ISP. Thanks for your time!

---

