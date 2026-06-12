---
title: "/etc/resolv.conf: persisting search domain changees"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by freeregistration on 2007-02-02
after searching through the forums and web for hours, i still couldn't find an answer to this issue. i need to add a list of domain names to the search domains list. if i manually edit the /etc/resolv.conf (or add domain suffixes via System->Administration->Networking), it works until the resolv.conf file is automatically overwritten. how do i persist the search domain names in resolv.conf.

thanks.

NOTE: i am running Edgy Eft.

---

### Post by handy on 2007-02-02
The following [_***How-To***_]("http://ubuntuforums.org/showthread.php?t=282034") should help you, just add your addresses seperated with commas & a semi colon at the end.

You will see what I mean when you look at the how-to.

Hopefully that's all you need... :)

---

### Post by freeregistration on 2007-02-02
thanks for the link. i have looked at similar discussions before posting this question here but they only describe how to persist the domain-name-servers and not about persisting the search domains. basically, i want to  persist the first line in /etc/resolv.conf file.

search a.b.com  x.b.com j.b.com b.com

by default (i.e. the overwrites), it has only has b.com

thanks.

---

### Post by kah00na on 2007-10-24
I have been dealing with this for months.  My "search" line in the /etc/resolv.conf file gets over written every time I  reboot.  I finally found the answer.

ANSWER:
The resolv.conf gets over written everytime your DHCP client asks the DHCP server for a new IP address or to renew the one it already has.  The DHCP server gives it a new list of search domains every time.  What you want to do is SUPERSEDE those settings.  Here's how:

1.     Before starting I see this:
```
$ grep search /etc/resolv.conf
search domain.com
```

2.   sudo vi /etc/dhcp3/dhclient.conf 
     Find this line:  #supersede domain-name "fugue.com home.vix.com";
     Uncomment it and change the domain names inside the double-quotes to the ones you want it to use.  Separate them with spaces and save the changes.
          EXAMPLE:   #supersede domain-name "domain.com sub.domain.com";
3.  Restart your DHCP client:      sudo dhclient

You should now see those new lines in your /etc/resolv.conf:
```
$ grep search /etc/resolv.conf
search domain.com sub.domain.com
```

Hopefully this gets you going.
*You may hate "vi". Use whatever text program you prefer.*

---

