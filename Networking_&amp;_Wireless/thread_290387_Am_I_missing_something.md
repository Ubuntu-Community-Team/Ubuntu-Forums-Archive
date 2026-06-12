---
title: "Am I missing something"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by fothers on 2006-11-01
Hi

I installed Ubuntu today and everything seems to work except the internet. I can ping my Dlink Modem/Router and it seems to work. I can open the setup page thru firefox (10.1.1.1) and everything seems ok. It has all settings as per XP (Why wouldn't it).
But if I try to view a web page or download mail it just times out. ?
Anyone got any idea's ?
I'm connected to a wireless modem/router (Dlink DSL-G604T/AU) via an eithernet cable. When I look in the Network Configeration Panel both show up and say thay are active. 
Do I have to turn something else on.

Hope someone can point me in the right direction.

Thanks

---

### Post by swamytk on 2006-11-01
Power off your machine (NOT Reboot) and boot it in Linux directly. Let me know the result

---

### Post by fothers on 2006-11-01
Hi

I powered off my machine and loaded Ubuntu (I hope you mean turn it off and then turn it back on without CD in drive).
I still have no connectivity via mail or firefox. 
However someone on "Geeks to Go" suggested typing 216.239.51.99 into the browser and see if google comes up. It did and I can search for something and it works, but if I click on a link then it times out.
Maybe something in my setup thats pointing the connection to the wrong DNS ?? or the port is locked ?

Any help would be appreciated.

Thanks

---

### Post by Swab on 2006-11-01
DNS issue perhaps?  Can you ping anything beyond the router by IP?  Try ping 4.2.2.2

Edit: Didn't read your post properly, OK so yes a DNS issue.  Try editing /etc/resolv.conf  you can add it nameservers there..

nameserver ipaddress
nameserver ipaddress

Check your ISPs home page for nameserver addresses.

---

### Post by fothers on 2006-11-01
Tried 4.2.2.2  and 216.239.51.99 (Google) and both seem ok with 179 and 248 ms respectivly and no loss ?
someone on GTG said to try "nslookup www.google.com" but I'm not sure in what application to try it in ?
Thanks

---

### Post by Swab on 2006-11-01
> **fothers said:**
> Tried 4.2.2.2  and 216.239.51.99 (Google) and both seem ok with 179 and 248 ms respectivly and no loss ?
someone on GTG said to try "nslookup www.google.com" but I'm not sure in what application to try it in ?
Thanks

nslookup [www.google.com](www.google.com) .. just type it on the command line.  But I think you should try adding nameservers to your resolv.conf, type..

sudo gedit /etc/resolv.conf 

and add in your nameservers.

---

### Post by fothers on 2006-11-01
sorry ???


sudo gedit /etc/resolv.conf ?

is this a command line in terminal or a program ?

(I know dumb question)
I opened the file in text edit but it said I didn't have permission to save it. How do I save it as I didn't set up any accounts so I wouls assume I'm loged in as admin?

thanks

---

### Post by Swab on 2006-11-01
> **fothers said:**
> sorry ???


sudo gedit /etc/resolv.conf ?

is this a command line in terminal or a program ?

(I know dumb question)
I opened the file in text edit but it said I didn't have permission to save it. How do I save it as I didn't set up any accounts so I wouls assume I'm loged in as admin?

thanks

yes type it at the command line, then enter your password.  Edit the file and save it.

---

### Post by fothers on 2006-11-01
Hi 

Thanks everyone for your help.

Problem fixed, in terminal I typed

sudo gedit /etc/resolv.conf

as instructed and changed the nameserver to my IP and saved file and now it works. I will try the email now

Thanks again

---

### Post by fothers on 2006-11-01
Hi

problem almost fixed

when I restart my system the etc/resolv.conf file has reverted back to the old setting. another file must be writing to it, any thoughts

thanks

---

### Post by stream303 on 2006-11-13
Common situation.  Dhclient is overwriting it (on purpose).  To force your resolv.conf to contain your isp's dns addresses every time dhclient writes it out:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

OR even easier

Put your isp dns nameserver addresses in your router's setup page and restart networking.  If it doesn't show up, the above option will definitely work.

---

### Post by whistlerspa on 2006-11-17
Open Firefox, use ctrl + T to get a new tab type in the url box about:config. Then search for ipv6. Then toggle the value from false to true. That's how I solved it - ipv6 tunneling seems to be the problem. Evolution probably doesn't work for the same reason.

---

