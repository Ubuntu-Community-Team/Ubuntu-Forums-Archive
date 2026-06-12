---
title: "can't get to https://ubuntuforums.org/ using ubuntu"
date: 2021-06-13
forum: Networking &amp; Wireless
---

### Post by jhlaks on 2021-06-13
Hi All-

My linux ubuntu browsers (chrome or firefox) cannot get to [https://ubuntuforums.org:](https://ubuntuforums.org:) "This site can't be reached... DNS_PROBE_FINISHED_NXDOMAIN".  I have the same issue with other websites, but not with all websites.  If it weren't for windows, I would not be able to post this thread.  Has anyone been able to solve this issue?

Thanks
-J

---

### Post by QIII on 2021-06-13
It is not likely that this issue exists for too many of us, given that we are all here.  Thus, there may be very few who have "solved" the issue.

It would be helpful if you would give us some information about your system and the release of Ubuntu you are using.

---

### Post by jhlaks on 2021-06-14
Thank you for the reply.  I have seen this posted on other forums, but without any coherent solution.  I am still hopeful someone has a full solution... I am contemplating doing a factory reset.

system: DELL XPS 13 9310
Distributor ID: Ubuntu
Description: 20.04.1 LTS (fossa-bulbasaur x39)
Release: 20.04
Codename: focal

Thanks,
-J

---

### Post by oldfred on 2021-06-14
If we have issues with Forum, I run this to see if somewhere a connection is down.

mtr [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by jhlaks on 2021-06-15
Hi oldfred-

The issue cannot be a connection problem.  My ubuntu browsers can get to some typical websites (e.g., google search), but not to others like this forum.  At the same time, my windows machine can always reach this forum.  I guess I'll give this a few more days before doing a factory reset.  God, I hope I do not have to do that.

-J

---

### Post by QIII on 2021-06-15
"Factory reset"?  Is this a Dell that came with Ubuntu pre-installed?

---

### Post by CharlesA on 2021-06-15
> **jhlaks said:**
> Hi oldfred-

The issue cannot be a connection problem.  My ubuntu browsers can get to some typical websites (e.g., google search), but not to others like this forum.  At the same time, my windows machine can always reach this forum.  I guess I'll give this a few more days before doing a factory reset.  God, I hope I do not have to do that.

-J

Just for your information:
The errors you got in the OP appeared because your machine was able to resolve the IP address for ubuntuforums.org.

You can do a couple tests to verify that is the issue or not.

```
nslookup ubuntuforums.org
```

This will try to use your default DNS servers (mine are at 192.168.1.67):

```
 nslookup ubuntuforums.org
Server:         192.168.1.67
Address:        192.168.1.67#53

Non-authoritative answer:
Name:   ubuntuforums.org
Address: 91.189.94.16
Name:   ubuntuforums.org
Address: 91.189.94.12

```

```
nslookup ubuntuforums.org 8.8.8.8
```

This will try to do the lookup using Google's DNS servers:

```
nslookup ubuntuforums.org 8.8.8.8
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   ubuntuforums.org
Address: 91.189.94.12
Name:   ubuntuforums.org
Address: 91.189.94.16

```

That may help you determine if this is an issue with a specific DNS server or a set of DNS servers.

Are you using the servers provided by your ISP?

---

### Post by jhlaks on 2021-06-16
Hi CharlesA-

Thanks for the excellent suggestions.  I finally decided to do a factory reset (yes, this was a Dell w/ Ubuntu reinstalled) and found that it did not fix the issue... could reach some websites and not others.  I then rebooted my router and voila... all websites are reachable.  If anyone know why this happens, it would be good to know.  Let me list the details again:
1) Windows machines can reach any website, no problem
2) Linux machines can only reach some websites
3) In particular, this forum is not reachable
4) Android phone cannot reach this forum either

Thanks again for all those who replied.

-J

---

### Post by jhlaks on 2021-06-16
One other detail which I omitted.  Using only one router, but the windows machine is connected wired and the linux/androids are connected wireless.

-J

---

### Post by CharlesA on 2021-06-16
> **jhlaks said:**
> Hi CharlesA-

Thanks for the excellent suggestions.  I finally decided to do a factory reset (yes, this was a Dell w/ Ubuntu reinstalled) and found that it did not fix the issue... could reach some websites and not others.  I then rebooted my router and voila... all websites are reachable.  If anyone know why this happens, it would be good to know.  Let me list the details again:
1) Windows machines can reach any website, no problem
2) Linux machines can only reach some websites
3) In particular, this forum is not reachable
4) Android phone cannot reach this forum either

Thanks again for all those who replied.

-J

If you have it happen again, I would suggest running those nslookup commands on the windows machine and again on the Linux machine and see if we get different results.

My bet is one of them will fail, but it's hard to tell why without the exact ioutput returned.

> **jhlaks said:**
> One other detail which I omitted.  Using only one router, but the windows machine is connected wired and the linux/androids are connected wireless.

-J

Wired vs wireless shouldn't be an issue unless the wireless link is going down. Were you able to get to other machines locally via wireless when you couldn't get to the forums? Sounds like restarting the router reset the wireless too, so maybe that was the root issue.

---

### Post by jhlaks on 2021-06-17
Hi CharlelsA-

It is somehow related to the wireless, but it is not a complete failure... wireless devices can get to some websites, but not others.  So, I think you are on the right track w/ the dns somehow.  If/when the problem resurfaces I'll post again after running your commands.

-J

---

### Post by rsteinmetz70112 on 2021-06-19
I've had similar issues with different browsers and it's always been something in the network. Sometimes a reboot fixes it, sometimes it doesn't. It sometimes has been the ISPs DNS servers.

---

