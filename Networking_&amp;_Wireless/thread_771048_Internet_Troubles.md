---
title: "Internet Troubles"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Damen555 on 2008-04-27
Hello everyone,

I am a complete newbie to Ubuntu, (I just installed it yesterday) and have been trying to hook up the internet almost all day. I have  tried everything under the help on Ubuntu and lots of other stuff that I found on the web but am still having trouble. (though I admittedly skipped some things that I did not understand or were beyond me) 

I am trying to set up my DSL through a router and have had some luck using the DHCP option, which lets me load Google, and do Google searches. However, whenever I try to click on a link, or go somewhere other than Google it stops working. 

If anyone could give me any help I would really appreciate it, thanks =)

---

### Post by superprash2003 on 2008-04-27
this could be a DNS problem.. you might want to try changing DNS servers to opendns.. here's how you do it [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Damen555 on 2008-04-27
Thanks superprash, I took your advice and followed the tutorial, but still no internet :(

Any other advice?

---

### Post by superprash2003 on 2008-04-28
go to the terminal and type ping google.com and also type ping ubuntuforums.org and post results here

---

### Post by Damen555 on 2008-04-28
```
tucker@tucker-desktop:~$ ping google.com
ping: unknown host google.com
tucker@tucker-desktop:~$ ping ubuntuforums.org
ping: unknown host ubuntuforums.org
```

---

### Post by Swiftfeet8 on 2008-04-28
I am assuming that your router/DSL is not blocking outbound ping requests.  In a terminal type "cat /etc/resolv.conf" and post here what the results are.  The resolv.conf file contains the DNS servers that you are going to resolve domain names to.

---

### Post by Damen555 on 2008-04-28
```
bash: cat/etc/resolv.conf: No such file or directory
```

I double checked the spelling.

That doesn't sound very good, I'm guessing that is probably my problem?

---

### Post by jtrindle on 2008-04-28
There's a space after the word "cat" in that command.

---

### Post by Damen555 on 2008-04-28
Oops, my bad.

```
tucker@tucker-desktop:~$ cat /etc/resolv.conf
nameserver 10.0.0.2
```

---

### Post by Swiftfeet8 on 2008-04-28
Ok, is 10.0.0.2 your modem/routers IP address?

If you are able to get into your router I would set the DNS to whatever your ISP has or uses.  Your router should get the DNS information from your modem, but it doesn't always work or is flaky.  That's why I usually just setup the DNS information in my router.  If you don't know what your ISP's DNS servers are you can use the following OpenDNS servers:  

208.67.222.222 
208.67.220.220

Set these up in your router.  If you have troubles let me know and I can help you.

---

### Post by Damen555 on 2008-04-28
AHA! That did the trick :)

My internet is up and running, and I am now posting this via Ubuntu, and can now begin to explore the system in earnest. Thanks swiftfeet and everyone else that helped me out =)

I used the 

208.67.222.222
208.67.220.220

servers as I don't know my ISP's DNS servers, I heard somewhere else that these are actually oftentimes faster then other DNS servers. I hope that is true as I will be running on them for a while.

Thanks again everyone!!

---

