---
title: "How can I see a daily log of internet bandwidth used on my computer?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by hanzj on 2009-07-27
Hello,
I would like to be able to see how much bandwidth my computer has used for each day. 

What do you folks recommend?

---

### Post by wWales on 2009-07-27
not sure if its exactly what you need, but you can check the System Monitor (under System/Administration/System Monitor on your gnome panel)

It has a gui with a "Resources" tab that tracks data from your session.

alternatively you can start it from the command line by typing:

```
gnome-system-monitor
```

---

### Post by solitaire on 2009-07-27
Check out "vnstat" in the repo's

It logs how much data is sent through your network.

Sample output:
```
user@laptop:~$ vnstat

                     rx      /     tx      /    total    /  estimated
 ppp0 [disabled]:
        06.03.      2.07 GB  /  317.30 MB  /    2.38 GB
         today         0 kB  /       0 kB  /       0 kB  /      --   

 eth1:
     yesterday      3.31 GB  /  810.91 MB  /    4.10 GB
         today    182.78 MB  /    8.36 MB  /  191.14 MB  /    3.07 GB

```

It records and you can output in day's, hours, weeks, months or years...

---

### Post by hanzj on 2009-07-27
wWales,
gnome-system-monitor tracks only a session. I want to track for more than 1 session. I want to track per day, for many days (say, about the last month or 2).

---

### Post by hanzj on 2009-07-27
i installed vnstat.
I then did:

> sudo vnstat -u -i eth0
How do I get something like this: [http://humdi.net/vnstat/cgidemo/](http://humdi.net/vnstat/cgidemo/)

---

### Post by TDurden1937 on 2009-07-27
Why do you want to do this . .  . you have a bandwidth usage limit?

---

### Post by hanzj on 2009-07-27
yes, we have a monthly limit with the ISP.
another reason why: because we have two computers and want to see how much each is using bandwidth.

---

### Post by jose158 on 2009-07-27
> **hanzj said:**
> yes, we have a monthly limit with the ISP.
another reason why: because we have two computers and want to see how much each is using bandwidth.
Competition? :popcorn:

---

### Post by hanzj on 2009-07-27
Well, it may be that the ISP is making a mistake by charging us too many GBs.

---

### Post by TDurden1937 on 2009-07-27
Gotcha - my son is having the same thing happen. Verizon give 5GB no charge then charges 5 cents for every mb over. I found a really cool program that worked on Windo$e O/$ucks, but that would have to be installed with WINE and I doubt it would work right anyway.

It is a real B***tch having that limit. Really kind of cuts out the Angry Video Game Nerd on screwattack.com, lol.

What's your bandwidth usage limit? My son was having a hard time with the limit. He didn't want to admit watching the streaming video's. But once we talked it through he started watching his usage.

Regular Internet surfing should not no way use too many Gb per month usage. That's why I ask what your limit is . . . someone may not be owning up to watching streaming video's or may not be aware of the extremely high cost in bandwidth. I found that once my son knew why he was zipping through his bandwidth he could monitor his own usage.

---

### Post by solitaire on 2009-07-27
> **hanzj said:**
> i installed vnstat.
I then did:


How do I get something like this: [http://humdi.net/vnstat/cgidemo/](http://humdi.net/vnstat/cgidemo/)

You could try this:
[http://www.sqweek.com/sqweek/index.php?p=1](http://www.sqweek.com/sqweek/index.php?p=1)

Personally I've not got this to work but I didn't put too effort into getting it to work :)

hopefully you'll have better luck ^__^

---

