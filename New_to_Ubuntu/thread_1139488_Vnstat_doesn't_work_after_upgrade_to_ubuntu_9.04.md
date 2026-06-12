---
title: "Vnstat doesn't work after upgrade to ubuntu 9.04"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by plutov03 on 2009-04-27
Hi,everybody.
I installed Vnstat on my 8.10 machine and it worked perfectly,when i upgraded to 9.04,it didn't work anymore.It seems that vnstat stopped working since 24th,I've already reinstalled it but that didn't help.

pluto@pluto-desktop:~$ vnstat -d

 eth0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   26.03.     45.09 MB  |    3.47 MB  |   48.56 MB   %
   27.03.    451.89 MB  |   19.27 MB  |  471.16 MB   %%%%%%%%%%%%%:
   28.03.     58.91 MB  |    3.49 MB  |   62.40 MB   %
   29.03.    220.23 MB  |   23.33 MB  |  243.56 MB   %%%%%%:
   30.03.    264.37 MB  |   16.83 MB  |  281.20 MB   %%%%%%%%
   31.03.    180.98 MB  |   16.10 MB  |  197.08 MB   %%%%%%
   01.04.     51.08 MB  |    7.63 MB  |   58.71 MB   %
   02.04.    149.42 MB  |    5.55 MB  |  154.98 MB   %%%%
   03.04.      6.19 MB  |     853 kB  |    7.03 MB
   04.04.     14.91 MB  |    4.09 MB  |   19.00 MB
   05.04.     27.91 MB  |    2.77 MB  |   30.68 MB
   06.04.    101.83 MB  |    8.75 MB  |  110.58 MB   %%%
   07.04.     86.77 MB  |    4.42 MB  |   91.19 MB   %%
   08.04.     25.34 MB  |    2.43 MB  |   27.77 MB
   09.04.     10.19 MB  |    1.38 MB  |   11.57 MB
   10.04.     25.53 MB  |    1.82 MB  |   27.36 MB
   11.04.     59.78 MB  |    9.15 MB  |   68.93 MB   %%
   12.04.    212.67 MB  |   20.53 MB  |  233.21 MB   %%%%%%:
   13.04.    169.92 MB  |    9.60 MB  |  179.52 MB   %%%%%
   14.04.    177.85 MB  |   10.58 MB  |  188.43 MB   %%%%%
   15.04.    274.62 MB  |   15.71 MB  |  290.33 MB   %%%%%%%%
   16.04.    416.46 MB  |   15.46 MB  |  431.92 MB   %%%%%%%%%%%%%
   17.04.     84.56 MB  |    5.61 MB  |   90.17 MB   %%
   18.04.    218.13 MB  |   11.55 MB  |  229.67 MB   %%%%%%%
   19.04.     34.11 MB  |    2.49 MB  |   36.60 MB   %
   20.04.    110.65 MB  |    6.57 MB  |  117.22 MB   %%%
   21.04.    116.00 MB  |    8.74 MB  |  124.75 MB   %%%
   22.04.     84.52 MB  |    6.31 MB  |   90.83 MB   %%
   23.04.    381.67 MB  |   19.32 MB  |  400.99 MB   %%%%%%%%%%%:
   24.04.    792.37 MB  |   25.15 MB  |  817.52 MB   %%%%%%%%%%%%%%%%%%%%%%%%:
------------------------+-------------+----------------------------------------
 estimated     1.41 GB  |      45 MB  |    1.45 GB


Did i do anything wrong?
sorry for my english.
Thanks in advanced

---

### Post by imsdal678 on 2009-05-02
got the same problem
i just installed ubuntu server 9.04

installed vnstat and downloaded a 70 MB file to check, but still get this msg:
Not enough data available yet.

---

### Post by dnairb on 2009-05-04
It's possible that vnstat is monitoring the wrong interface (IIRC on Hardy Heron, it monitored eth1 on my machine, which is now wlan0 on Jaunty, even though nothing physically has changed on my box).

You need to check which interface you want to monitor using iwconfig or ifconfig in terminal.

Then, again in terminal:

```
sudo vnstat -u -i <interface>
```

Where <interface> is eth1, wlan0, or whatever your interface is.

---

### Post by dnairb on 2009-05-04
BTW, you can setup a launcher on your desktop, which will give a static window with vnstat's output. Create the launcher, and in the command box, type:

```
xterm -bg white -fg black -T "**WINDOW TITLE**" -hold -e vnstat --days -i **INTERFACE**
```

change --days to --weeks, --months or even --hours as preferred.

---

