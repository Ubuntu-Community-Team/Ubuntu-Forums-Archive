---
title: "Can't see one particular website (which I know is working)"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by rupert-1 on 2013-12-11
Hello

I have been having this problem for nearly a month and haven't found a solution anywhere.

 I cannot connect to one  url "outlook.office365.com" in any browser (Firefox, Chrome, Opera) on  my installation of Ubuntu 13.10 however if I reboot the computer in Mint  then the site works fine.  

ns-lookup returns

rupert@rupert-cp:~$ nslookup outlook.office365.com
Server:        127.0.1.1
Address:    127.0.1.1#53

Non-authoritative answer:
outlook.office365.com    canonical name = outlook.office365.com.glbdns.microsoft.com.
outlook.office365.com.glbdns.microsoft.com    canonical name = outlook-emeawest.office365.com.
Name:    outlook-emeawest.office365.com
Address: 132.245.193.140
Name:    outlook-emeawest.office365.com
Address: 132.245.228.2
Name:    outlook-emeawest.office365.com
Address: 132.245.228.6
Name:    outlook-emeawest.office365.com
Address: 132.245.228.9
Name:    outlook-emeawest.office365.com
Address: 132.245.193.137
Name:    outlook-emeawest.office365.com
Address: 132.245.193.130
Name:    outlook-emeawest.office365.com
Address: 132.245.193.134
Name:    outlook-emeawest.office365.com
Address: 157.56.255.233
Name:    outlook-emeawest.office365.com
Address: 157.56.255.226
Name:    outlook-emeawest.office365.com
Address: 157.56.255.230
Name:    outlook-emeawest.office365.com
Address: 132.245.224.162
Name:    outlook-emeawest.office365.com
Address: 132.245.224.169
Name:    outlook-emeawest.office365.com
Address: 132.245.194.249
Name:    outlook-emeawest.office365.com
Address: 132.245.211.246
Name:    outlook-emeawest.office365.com
Address: 132.245.211.242
Name:    outlook-emeawest.office365.com
Address: 132.245.224.172

pinging either the url or a selection of the ips gets nothing as does traceroute.

Any help on this would be really appreciated.

Rupert

---

### Post by philinux on 2013-12-11
Down for me too but.

[http://www.downforeveryoneorjustme.com/outlook.office365.com](http://www.downforeveryoneorjustme.com/outlook.office365.com)

---

### Post by rupert-1 on 2013-12-11
downforeveryoneorjustme says
It's just you  [http://outlook.office365.com](http://outlook.office365.com) is up.

My problem is I don't even know where to start with solving this.

Rupert

---

### Post by philinux on 2013-12-11
Pinging that site does not work for me either.

---

### Post by philinux on 2013-12-11
Try [https://outlook.office365.com](https://outlook.office365.com)

Without the s it does not work on Ubuntu but on my smart phone it goes to above link then to login.

---

### Post by rupert-1 on 2013-12-11
Sorry I should have explained I am connecting to [https://outlook.office365.com](https://outlook.office365.com) from [https://portal.microsoftonline.com/default.aspx](https://portal.microsoftonline.com/default.aspx) - my company uses 365.  I can log in which takes me to the portal URL but I can't then go to the outlook site.

---

### Post by rupert-1 on 2013-12-11
So I finally stopped bleating and started thinking.

On a laptop with Windows 7 where everything works, I tried pinging and tracert and although they resolved the URL to an IP they didn't work.

Is it possible that Microsoft have got the site so tightly screwed down to prevent hackers that it is also stopping Ubuntu connecting?  Another thing I was able to see the site in October.

---

### Post by steeldriver on 2013-12-11
I can't ping it either (so presumably it blocks ICMP), and when I try to access it from either Ubuntu or Windows it redirects to [https://login.microsoftonline.com/](https://login.microsoftonline.com/)

Assuming you are already logged in to [https://login.microsoftonline.com/](https://login.microsoftonline.com/) then perhaps it is a cookie management issue? Have you tried clearing any MS cookies and then logging in again?

Or maybe the page requires a proprietary plugin e.g. ActiveX?

---

### Post by slooksterpsv on 2013-12-11
Try these few items:

```

ping6 outlook.office365.com

```

If that works try disabling IPv6.

That's where I'd start looking.

I'd also try using a proxy service to see if you can get to the page. If a proxy works fine, it's something within the OS. Where Mint (12.04 works) and others work, it shouldn't be a useragent string. Hmm...

That's where I'd begin... I'll try to think of other options to figure out what's wrong.

---

### Post by rupert-1 on 2013-12-11
I tried clearing Cookies and temp files to no avail.

If it was a plugin would I not get some sort of warning about missing plugins?

Rupert

---

### Post by houstonbofh on 2013-12-11
Since it works on one OS and not another it is an OS setting. Try lowing your local MTU and see if that helps.  It could just be trying to break "unbreakable" packets.

---

### Post by rupert-1 on 2013-12-12
Hello
I will give that a try.
It is currently on "automatic", what would be a good higher value?

---

### Post by houstonbofh on 2013-12-13
Lower, not higher...  Try 1200 to test.  If it works, you can start raising it...  Default is 1500.

---

### Post by rupert-1 on 2013-12-13
Brilliant, reducing it to 1200 fixed it.  I will try inching it back up.  What difference will a lower MTU make?

Thanks everyone for your help, I really appreciate it.

---

### Post by houstonbofh on 2013-12-15
It is essentially, "How fast can you eat a burger as the bites get smaller..."

---

