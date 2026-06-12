---
title: "Weird problem with internet connection"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by omeomi on 2006-11-01
I'm having a quite weird problem with my internet connection. I just installed 6.06 on a old laptop, and after some tweaking I got the wireless connection to work. But now the strange thing: I can open websites using Firefox but I can't use the internet for anything else! :confused: :confused: 
So apt-get doesn't work, email doesn't work etc. etc. 
Only Firefox connects properly. :-k 

So anyone has any thoughts on how this can be fixed??

---

### Post by scallywag on 2006-11-01
I am having this same issue and I hope someone will come up with a solution. This is my first go at linux and I know nothing! Be gentle but please help us!

---

### Post by omeomi on 2006-11-02
Some additional info:
when i try "sudo apt-get update" for example, I get this:
"0% [Connecting to archive.ubuntu.com (1.0.0.0)]"

Could it be a problem with the IP-address?

---

### Post by omeomi on 2006-11-02
Found the solution! Problem was with the DNS. In my /etc/resolv.conf file there was only 1 entry which was the address of my router. I changed it to the addresses of my ISP and it works!

---

### Post by scallywag on 2006-11-02
great! Now as someone who has no idea how to fix it could you possibly give me step by step instructions. I am totally linux stupid!

---

### Post by scallywag on 2006-11-02
Well that does not seem to be the problem for me. My DNS using GUI shows the ISP is correct. This really rots. I want to get it working right and can't find the solution!

---

### Post by omeomi on 2006-11-02
Well you should check using terminal.
- Open terminal and type: cat /etc/resolv.conf
- You should get an ouput like this (one or more lines):
```
nameserver xxx.xxx.xxx.xxx
```
Where the xxx.xxx.xxx.xxx is an IP-address which should match the one you got from your ISP (check their website to see what it is)
If the IP is 192.168.1.1 or something similar refering to your router/modem then you need to change it. 
- Type: sudo nano /etc/revolv.conf
- Delete the line is the file and type the correct one(s) (as above)
- Save the file

Now it should work. A possible problem you could run into after this is that when you restart, the changes are undone. If so, please post here and I will tell you what to do.

---

### Post by scallywag on 2006-11-06
yes the changes are not perm. they change back on restart. any way to fix it? and thanks

---

### Post by wieman01 on 2006-11-06
To fix the changes, do this:
> sudo chattr +i /etc/resolv.conf

---

### Post by scallywag on 2006-11-06
OK But what is that supposed to do? It did nothing when I did it.

---

### Post by wieman01 on 2006-11-07
That fixes the file once you have updated it. That's all. Add a name server of your choice, then make it read-only.

---

