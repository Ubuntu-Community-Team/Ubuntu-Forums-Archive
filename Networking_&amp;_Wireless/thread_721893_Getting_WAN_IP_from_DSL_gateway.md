---
title: "Getting WAN IP from DSL gateway"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by awilki01 on 2008-03-11
My ISP assigns my DSL gateway/router a dynamic IP.  I am trying to ensure I always have access to my Ubuntu linux box on the public Internet for remote access.

Without going the dyndns or no-ip method (I believe they cost money), and given the fact that my gateway does not support SNMP, I need to figure out how to get my IP address emailed to me on a daily basis.

I can access the gateway in a browser and open the URL that gives me the IP address.  I just need to figure out how to send the HTML code or file to an email address using some sort of automated method.  I could even parse out the IP address info and just send that as well.

Can anyone point me in a direction to get started in automating this?

---

### Post by lloyd_b on 2008-03-12
> **awilki01 said:**
> My ISP assigns my DSL gateway/router a dynamic IP.  I am trying to ensure I always have access to my Ubuntu linux box on the public Internet for remote access.

Without going the dyndns or no-ip method (I believe they cost money), and given the fact that my gateway does not support SNMP, I need to figure out how to get my IP address emailed to me on a daily basis.

I can access the gateway in a browser and open the URL that gives me the IP address.  I just need to figure out how to send the HTML code or file to an email address using some sort of automated method.  I could even parse out the IP address info and just send that as well.

Can anyone point me in a direction to get started in automating this?

Look at the "wget" command ("man wget" in a terminal window).

Here's a simple example, fetching the info from [www.whatsmyip.com:](www.whatsmyip.com:)
```
wget -O myip.txt http://whatismyip.com/automation/n09230945.asp
```
Then look in the file "myip.txt".

Lloyd B.

---

### Post by awilki01 on 2008-06-09
Thanks, I'll try this out.

What about sending email?  Would I install metamail for that?  I'm assuming I would have to use a cron job do all of this, correct?

---

