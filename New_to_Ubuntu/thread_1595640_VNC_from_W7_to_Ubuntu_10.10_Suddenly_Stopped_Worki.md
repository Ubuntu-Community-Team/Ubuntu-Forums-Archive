---
title: "VNC from W7 to Ubuntu 10.10 Suddenly Stopped Working"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Security Gate on 2010-10-13
Hey everyone,

I've started to set up a server at my house, where I eventually want to run it headless, and I can just VNC in from my other Desktop. I installed Ubuntu 10.10, setup remote desktop on the server, and from there was able to do any work remotely. That was nice. I turn the computer off at night, and the next day when I was going to work on it, I cannot VNC in anymore. One day passed, and now every time I try to use VNC it comes up with "Failed to connect to server" I also set a static IP address on the server too, so I know the address isn't changing every so often. 

I did it earlier, so I know I have it set up correctly, but when I restarted the computer, did some magical firewall get setup without my knowledge?

---

### Post by ryokea on 2010-10-13
Forgot to ask if you have a GUI or not before posting. If you do, try this: Open up the Remote Desktop settings. Untick all the boxes then tick the first two and the password one if you wish to have a password. This has worked for me and at least a few other people.

---

### Post by Security Gate on 2010-10-13
Thanks ryokea, but now all that happens is Remote Desktop application hangs for a while, and will eventually say "Others can access your computer using the address localhost."  Which is obviously not connectible.  The really odd thing is, I was able to connect a day ago, then all of a sudden Remote Desktop decided not to work any more.

Would it simply be easier to set-up SSH or some other tunnelling program?

---

### Post by Security Gate on 2010-10-14
Bump.  Any ideas for my quandary?  Know anyone that would be able to help?

---

### Post by luvshines on 2010-10-14
> **Security Gate said:**
> One day passed, and now every time I try to use VNC it comes up with "Failed to connect to server" I also set a static IP address on the server too, so I know the address isn't changing every so often. 

I did it earlier, so I know I have it set up correctly, but when I restarted the computer, did some magical firewall get setup without my knowledge?

We were discussing this issue in another thread where the solution given by ryokea worked for many people.

I have observed it too with my settings and think something is buggy here. **What I am explaining next may be completely insane**

Try this: Let all tick marks be in place (including configure network...). If after 'checking...' it gives a local IP, tick/untick the topmost 'Allow remote...' option.

It will again go for checking. After 3-4 tries it suddenly detected my public IP and I was able to connect thru my public IP

**Surely, this is not a fix** but when I ran wireshark on port 5900 I saw that it first tried to contact some IP and sent HTTP request to get my public IP. That site replied back and I was able to see public ip
For the next 2 tries, it went for another IP which was pingable but HTTP was down and what I got was my private IP
Then again went for the first IP and public IP was up

I think it gets its IP to detect from /usr/share/vino/webservices file

I commented out the one which is not responding correctly
```
# Jorge Pereira
http://blog.jorgepereira.com.br/jorge/org.gnome.vino.Service.php

# Jonh Wendell
#http://www.bani.com.br/vino/vino.php

```

It now detects my public IP most of the time. I'll do more testing on this tommorow, it's already 5:15 AM in India and I am up and posting. Have to catch some sleep now

GOOD LUCK !! Do post what your observations were

---

