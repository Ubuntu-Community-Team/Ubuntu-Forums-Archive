---
title: "How to prevent change of search domain in resolv.conf?"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by jameskhoo on 2006-09-28
Hi 

Each time, when I restart my network interfaces, the resolve.conf get changed. Well, I am ok with most of the changes, but, I would like certain configuration to be remain unchanged, like the search suffix..How do I config such?

For example, original resolve.conf:
search abc.com.my
search cde.com.my
search fgh.com.my
nameserver 127.0.0.1
nameserver  -------

Everytime the network restart or renew, the resolve.conf is changed to:
search abc.com.my
nameserver 127.0.0.1
nameserver ---------


all my other search suffix gone, any idea how to fix this?

Cheers
James

---

### Post by dante.regis on 2006-09-29
Hi james,

This is probably caused by the dhcp client (dhclient3). If you configure your network to get it's settings via dhcp, it will rewrite the resolv.conf (for almost every dhcp server also tells the client which dns servers and domains to use).

Hope this helps.

---

### Post by jameskhoo on 2006-09-29
Hi Dante

Thanks for your reply, but it's there a work around on this? 
I hate to manually change my resolv.conf every 60 minutes because the IP lease time is up.

When switch to Windows XP, I could enter the network search domain suffix, for example "abc.com.my" in Network Setting, and the setting stay there in regardless how many time the IP being renew.

Any pointers?

Cheers
James

---

### Post by handy on 2006-09-29
For related problems you may find [this thread]("http://ubuntuforums.org/showthread.php?t=188551") helpful?

---

### Post by dannyboy79 on 2006-09-29
or you could write a bash script that would overwrite the resolv.conf with one that you have saved in your home directory whenever you execute for example "resolvefix". just look up how to make a bash script. don't forget to make it executable, i forgot that once and couldn't figure out why it wouldn't run. Ha. I think it's sudo chmod +x /location/filename.

---

### Post by bdk on 2006-09-29
Jameskhoo, are you in control of the DHCP server? If it you are and it is running dhcpd, in dhcpd.conf change the line:

```

option domain-name "abc.com.my";

```

to:

```

option domain-name "abc.com.my def.com.my ghi.com.my";

```

Restart dhcpd:

```

sudo /etc/init.d/dhcp restart

```

Then on your computer refresh your IP:

```

sudo dhclient

```

Then cat your resolv.conf and see that the settings stuck.

I've had this problem for the longest time and this morning I realized what the fix was. I've got several networks that I need to maintain and just typing in the host name sure beats having to type in a fully qualified one.

HTH

*-bdk*

---

### Post by handy on 2006-09-30
**Finally a satisfactory solution for our _windoze-centric router's_ problem**.

After following **option 3** from [http://www.ubuntuforums.org/showthre...=128254&page=2](http://www.ubuntuforums.org/showthre...=128254&page=2) **Post# 13**.

I hope it works for everyone else as well as it does for me... :KS

---

### Post by kah00na on 2007-10-24
The resolv.conf gets over written everytime your DHCP client asks the DHCP server for a new IP address or to renew the one it already has.  The DHCP server gives it a new list of *search* domains and *DNS servers* every time.  What you want to do is SUPERSEDE those settings.  Here's how to do it for both:

1.     Before starting I see this:
```
$ grep search /etc/resolv.conf     ## or use "nameserver" instead of "search"
search domain.com
```

2.   sudo vi /etc/dhcp3/dhclient.conf 
**[SIZE="3"]     === "search" line[/SIZE]**
     Find this line:  ```
#supersede domain-name "fugue.com home.vix.com";
```
     Uncomment it and change the domain names inside the double-quotes to the ones you want it to use.  Separate them with spaces and save the changes.
          EXAMPLE:   #supersede domain-name "domain.com sub.domain.com";
**[SIZE="3"]     === "nameserver" line[/SIZE]**
To save your DNS servers, find this line and replace "127.0.0.1" with the DNS servers you want to use separated with a space:
```
#prepend domain-name-servers 127.0.0.1;
```

3.  Restart your DHCP client:      sudo dhclient

You should now see those new lines in your /etc/resolv.conf:
```
$ grep search /etc/resolv.conf     ## or use "nameserver" instead of "search"
search domain.com sub.domain.com
```

Hopefully this gets you going.
*You may hate "vi". Use whatever text program you prefer.*

---

