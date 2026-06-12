---
title: "Internet Traffic?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by raaki on 2008-06-11
hi Ubuntu users,

 am new to Ubuntu.can any one tell me how to measure the internet traffic i used.

i can use 1GB of traffic per week in my hostel ,if i cross more than 1GB my internet connection will be blocked

present using  ifconfig -a to measure, but when i reboot, counter is setting to 0.

i want an application such that it count doesn't reset to zero on each reboot

any ideas?

---

### Post by jetsam on 2008-06-15
I was surprised how hard it was to find such a thing.  Most of the search results I got pulled up complicated network monitors intended for network administrators.  

You might try vnstat.  

Install with:
```
sudo apt-get install vnstat
```

Then initialize the database:
```
sudo vnstat -u -i [COLOR="Blue"]eth0[/COLOR]
```

Change [COLOR="Blue"]eth0[/COLOR] in that command to the name of your network interface.  

I haven't used this program much so I don't know all the details, but these commands seem useful:
**vnstat**  --> Shows today's usage.
**vnstat -d**  -->Breaks down stats by day.
**vnstat -w**  -->Breaks down stats by week.  Probably the one you want for your situation.
**vnstat -m**  -->Shows stats by month. 
**sudo vnstat -u**  --> Force an updates of the database.  

The vnstat homepage has more info here:  [http://humdi.net/vnstat/]("http://humdi.net/vnstat/")

Hope that helps.  It doesn't seem right for the hostel to impose that policy and not give you an easy way to check your usage.

---

