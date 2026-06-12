---
title: "slow download speed in ubuntu than windows"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by jeeban37 on 2011-02-11
in UBUNTU  my download speed is 5 times slower than Windows 7 how to increase plz reply:confused:

---

### Post by Bölvaður on 2011-02-11
Very vague description of what the problem is.

Please describe everything you do. Do you have wifi? if so which card? (you can find it if you open the terminal Applications&#8594;Accessories&#8594;Terminal and write **lshw**)
Do you connect via lan cable?
What are you downloading?
What are you comparing when you say 5 times slower? And what is the download rate for both?
Might it be your ISP having problems or the server you are connecting to?

More help please:confused:

---

### Post by jeeban37 on 2011-02-11
i am using bsnl 3g device
i hav checked the download speed in windows 7 is around 100-150 kBps but in ubuntu speed is not exceeding 20 kBps.it happens at same time.i hav checked this wid my both same configuration laptop

---

### Post by Bölvaður on 2011-02-12
Just to start with we should let everyone know which modem you got, people that later reads this thread and have similar problems might want to know that.

open the terminal (applications&#8594;accessories&#8594;terminal)
```
lsusb
```

find out which one of these is your g3 dongle and report.


This is very dated but might help
[http://www.marengo-ltd.com/blog/?p=62](http://www.marengo-ltd.com/blog/?p=62)

I dunno if ubuntu is using this, if not then never mind, I just thought this line interesting
> 
Init3 = ATQ0 V1 &D2 &C1 S0=0 +IFC=2,2

Im very sorry but I do not know much about this, I have only used two of those on different machines and just noticed those dongles work much better on very new releases of ubuntu and not so on older ones.
But I'll come here again to check when you know which dongle you got, then it gets easier to google for the answer.

---

### Post by robsoles on 2011-02-12
Sorry for butting in but my curiosity is making me want to know what test you ran to establish the speed difference.

If you use [s]n[COLOR=black][http://speedtest.org]("http://speedtest.org/")_[/]("http://speedtest.org/")_[/COLOR][/s] [http://speedtest.net](http://speedtest.net) (sorry!) from both operating systems three times in a row each (to gain idea of average) if the average of results is that different maybe you could share the 'forum links' from speedtest.net to show us just how bad the difference is?


On top of the modem info Bölvaður is asking for, please tell us what version of Ubuntu is it that you are running to get these results with?

---

