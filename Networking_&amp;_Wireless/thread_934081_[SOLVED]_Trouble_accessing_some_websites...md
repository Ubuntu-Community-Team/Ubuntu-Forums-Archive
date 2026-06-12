---
title: "[SOLVED] Trouble accessing some websites.."
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by toallpointswest on 2008-09-30
Hello all, 

 I'm still having trouble accessing a few websites. I tried the fix from this forum [http://ubuntuforums.org/showpost.php?p=4132456&postcount=5](http://ubuntuforums.org/showpost.php?p=4132456&postcount=5) but it hasn't helped. I dual boot, and the Windows drive can get to all of the sites but my Hardy cannot. I connect through a Comcast branded Linksys WCG200v2-CC using a Realtek nic. 

Sites like CNN.com, NBC.com, ABC.com don't come up but Ubuntuforums, and nearly everything else does. I'm stumped!

---

### Post by rlzyoner on 2008-09-30
Can you telnet to the problem sites on port 80

telnet [www.cnn.com](www.cnn.com) 80

---

### Post by superprash2003 on 2008-09-30
try switching your dns servers to opendns . their ips are 208.67.222.222 and 208.67.220.220
for reference : [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by toallpointswest on 2008-09-30
> **rlzyoner said:**
> Can you telnet to the problem sites on port 80

telnet [www.cnn.com](www.cnn.com) 80

I tried that and here was the result: 
```

xx@xxxxx:~$ telnet www.cnn.com 80
Trying 157.166.224.26...
Trying 157.166.226.26...
Trying 157.166.255.18...
Trying 157.166.224.25...
telnet: Unable to connect to remote host: Connection refused

```

This also answers the DNS question as CNN's address resolves. I just can't get there (or rather have traffic get back). Oddly, this works fine in Windows on the same system.

---

### Post by superprash2003 on 2008-10-01
what happens when you type 157.166.224.25 in your browser

---

### Post by toallpointswest on 2008-10-02
> **superprash2003 said:**
> what happens when you type 157.166.224.25 in your browser

I get
```
Failed to Connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at 157.166.224.25.

        


        
        

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

```
We know it's not a DNS problem, as the sites all resolve. I think it has something to do with the sysctl settings.  In my first post there are some settings in sysctl, does anyone know what they mean?

---

### Post by superprash2003 on 2008-10-02
try installing opera from synaptic and then try surfing..

---

### Post by toallpointswest on 2008-10-06
> **superprash2003 said:**
> try installing opera from synaptic and then try surfing..

I would but if telnet didn't work, why would a different client help? I doubt this is a layer 7 issue.

---

### Post by toallpointswest on 2008-10-11
SOLVED! Turns out that it was a bad firewall rule on my system somehow. I started up Firestarter, reset all the rules and viola! Works like a charm!

---

