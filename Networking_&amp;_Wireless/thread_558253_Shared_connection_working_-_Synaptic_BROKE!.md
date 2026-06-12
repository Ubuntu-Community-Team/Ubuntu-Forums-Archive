---
title: "Shared connection working - Synaptic BROKE!"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by brucewestfall on 2007-09-23
Not just Synaptic, but apt-get also.  

I had a very difficulty time getting my Ubuntu Compaq laptop to share a connection with the Ubuntu desktop HP Pavilion computer.  Both came with Windows, both are now completely Ubuntu 7.04.  I really do forget what I did to get this working ( embarrassed confession: I restarted it once and it just worked, FINALLY!)

The internet works - I'm writing from the laptop, but Synaptic and apt-get cannot get a connection to download updates.  The notification icon shows that some communication is happening, since it keeps adding to how many packages can be upgraded (from 7 a while ago to 119 just now.

Here is what an apt-get command gets:

root@edwin-compaq:/home/bruce# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
  Could not connect to 192.168.1.1:8080 (192.168.1.1). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg                            
  Could not connect to 192.168.1.1:8080 (192.168.1.1). - connect (113 No route to host)
...

It just keeps going thru the list til I stop it.

I could find no similar conditions on the board.

Ideas anyone?

---

### Post by brucewestfall on 2007-09-23
This forum works FAST!  I found the answer.

I am using the manual network configuration icon in the system tray.  All settings were made there.  I manually set the ip adress for the desktop network card (dsl connection thru separate network card.) and the ip and DNS settings for the laptop.

At some time, I also changed the network settings found at 
System -> Preferences -> Network Proxy
 I had set the proxy to the Desktop there.  After it was switched to 'Direct Internet Connection' and I restarted Synaptic works fine.

Soon my Laptop will be up-to-date again!

---

### Post by mk1_salami on 2007-09-24
ahhhhhhhh mate, you've really helped me out here.

Thank-you!
I have just set up my wireless connection and had this exact problem. I never though to check in the network proxy area.

Thanks again :)

---

### Post by brucewestfall on 2007-09-24
Do I get any more beans since I helped someone?

Cause this sure ain't MY first cup of Ubuntu! (4th computer and several distributed discs!)

---

