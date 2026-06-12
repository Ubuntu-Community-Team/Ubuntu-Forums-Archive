---
title: "Best Bandwidth Meter with GUI support"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by chandru155 on 2009-09-01
My BroadBand during Day hours is limited one. So i need to track the broadband usage. In Xp, i use Shapulse Bandwidth meter which is nice that shows current session usage, daily and monthly usage in GUI mode. Like that, can anyone tell me the name of the software like this?  I tried in google, but i got one command line program only

---

### Post by jerrrys on 2009-09-01
I just use real time monitor, but you may find something here

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by XCan on 2009-09-01
It would be rather cool to have something like netlimiter (free version).

---

### Post by chandru155 on 2009-09-04
I tried them already. But they are not giving any historical data. Now i am using vnstat. But i what i want is

1.Currnet usage data(How much internet usage is used from logon, like the one displayed in "SYstem Monitor-->Resources-->Network History")
2.Today usage(How much used today")
3.Option to Reset usage.

Vnstat failed to do the First Option. So i am using SYstem (Monitor-->Resources-->Network History). Also its not showing the correct one. It updates its data for every 5 minutes. So the usage is not correctly updated.

Any help? An other software which will be used for my requirements.

(My broadband plan is Limited one. Night 2am to 8am,its free. During day hour, just 1.5GB per month. So on average, i can use 50MB. So i need to track history.
I can see the yesterday usage in my ISP webportal. But they wont update today;s history in their site. So any suggestions)

---

### Post by scragar on 2009-09-04
You can change the rate at which the system monitor get's information by editing the preferences.

I also recommend you look into running:
```
sudo iftop
```
This will show the most intensive interenet usage at present on a graph, along with current usage, peak usage and rates of download and upload.
Unfotunately it's not something you can just turn off, it has to run continously to update the information, if you stop it when you restart it the counting will start again from 0.

---

### Post by The Thug on 2009-09-04
Why not use VNStat in conjunction with Conky.

I use VNStat to monitor my 3g usage at home and although not a real graphical tool, it serves my purpose well giving daily, weekly & monthly usage figures.

---

### Post by abdusamed on 2010-08-29
What you need is NTM


I'm looking for a manager which is able to tell me each process's bandwith share pie

---

