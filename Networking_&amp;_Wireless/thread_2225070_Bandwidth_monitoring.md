---
title: "Bandwidth monitoring"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2014-05-19
Hi,

I atm use a DSL connection. From the beginning of the next month I will be switching to mobile broadband. I am will be getting higher speeds but its not an unlimited plan.

So want to keep track of the bandwidth I am spending.

Is there any app which will display like a counter on the desktop and update in realtime ?

---

### Post by varunendra on 2014-05-21
I use the command line tool "vnstat" for bandwidth usage logging. It can show the usage in live mode too, but is not meant for that kind of usage. For live monitoring, I use "nload". Both of these are available in default repositories.

Neither of these may be the 'Best' tools for the job, but they are good enough for me. I have created a script using vnstat, and I just edit its "START" date every month. It then starts showing me reports starting from that day. An example of its output (note that it is showing only the bandwidth usage on "ppp0" interface) -
```
         day         rx      |     tx      |    total    |   avg. rate    | Ttl Dnld | Ttl Upld |   G.Total
     ------------------------+-------------+-------------+---------------------------------------+-------------+-----
      05/15/14     70.35 MiB |   77.58 MiB |  147.93 MiB |   14.03 kbit/s |    70.35 |    77.58 |    147.93 | Day  1
      05/16/14     22.80 MiB |    2.45 MiB |   25.25 MiB |    2.39 kbit/s |    93.15 |    80.03 |    173.18 | Day  2
      05/18/14      5.85 MiB |    1.80 MiB |    7.65 MiB |    0.73 kbit/s |       99 |    81.83 |    180.83 | Day  3
      05/19/14      7.30 MiB |    5.53 MiB |   12.83 MiB |    1.22 kbit/s |    106.3 |    87.36 |    193.66 | Day  4
      05/20/14     86.00 MiB |   49.97 MiB |  135.97 MiB |   12.89 kbit/s |    192.3 |   137.33 |    329.63 | Day  5
      05/21/14     21.98 MiB |    6.40 MiB |   28.38 MiB |    4.74 kbit/s |   214.28 |   143.73 |    358.01 | Day  6
     ------------------------+-------------+-------------+---------------------------------------+-------------+-----
	Total used :  DL = 214.28 MiB   UL = 143.73 MiB   G.Ttl = 358.01 MiB    	 Records shown =  6 Days
```

Maybe you can embed these reports in a Conky script to put them more elegantly on the desktop.

---

### Post by linuxyogi on 2014-05-21
I have installed both the tools. I have tried vnstat with some options by reading its help but I am not able tp get the output like yours.

Please give me the exact command for vnstat you are using.

---

### Post by linuxyogi on 2014-05-21
Since I am using DSL atm my interface is eth0. 

So I did the following 

```
$ sudo vnstat -u -i eth0

$ vnstat --iflist
Available interfaces: eth0 lo 

$ sudo vnstatd -d
pidfile lock: Resource temporarily unavailable


$ ps -ef | grep vnst
vnstat    2233  1124  0 21:09 ?        00:00:00 /usr/sbin/vnstatd -d --pidfile /run/vnstat/vnstat.pid
tux       2603  2570  0 21:40 pts/1    00:00:00 grep --color=auto vnst

 2233  1124  0 21:09 ?        00:00:00 /usr/sbin/vnstatd -d --pidfile /

```


```
$ vnstat
Database updated: Wed May 21 21:39:53 2014

   eth0 since 05/21/14

          rx:  5.37 MiB      tx:  0.98 MiB      total:  6.35 MiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       May '14      5.37 MiB |    0.98 MiB |    6.35 MiB |    0.03 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        --     |      --     |      --     |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
         today      5.37 MiB |    0.98 MiB |    6.35 MiB |    0.67 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        --     |      --     |      --     |

```


I guess I will have to do ```
sudo vnstat -u -i ppp0
``` once I establish a connection with the usb dongle.

But still I am ver curious to know the combinations you are using. Your output is much more detailed.

---

### Post by varunendra on 2014-05-21
The vnstat command alone can't produce those details with any combination of options. I have used variables and 'awk' in the script to achieve that. It's crude, but was one of my initial attempts (when I had just begun learning scripting, not than I'm expert now :p), and works.. :)

Here's the entire script (script name : usage.sh, have created its symlink in /bin directory so that I don't have to type full path to run it) -
```
#!/bin/bash

# Shows Internet usage on given interface (default ppp0) from a given time till date.
# Usage : usage.sh m
# or just .. : usage.sh

m1=5  # starting month
d1=15  # starting date

m2=`date +%m`  # ending month
d2=`date +%d`  # ending date

if [ "$1" = "m" ]; then
	read -e -p "Enter interface : " -i "ppp0" IFACE

	read -e -p "Enter FROM month : " -i "$m1" FM
	read -e -p "Enter FROM date : " -i "$d1" FD
	read -e -p "Enter TO month : " -i "$m2" TM
	read -e -p "Enter TO date : " -i "$d2" TD
else
	IFACE=ppp0; FM="$m1"; FD="$d1"; TM="$m2"; TD="$d2"
fi

vnstat -d -i "$IFACE" | awk '{format=" |%9s |%9s |%10s |%5s%2s\n"}
	/day/ {printf "\n" $0 "%10s |%9s |%10s\n","    | Ttl Dnld","Ttl Upld","G.Total"}
	/------/ {printf $0 "%.44s\n",$1}
	$0 ~ FM"/"FD"/"14, $0 ~ TM"/"TD"/"14 {printf $0 format,s1+=$2,s2+=$5,s3=s1+s2,"Day ",s4+=1}
	END {printf "\tTotal used :  DL = %-12s UL = %-12s G.Ttl = %-13s\
	\t Records shown = %2s Days\n\n",s1" MiB",s2" MiB",s3" MiB",s4}' FM=$FM FD=$FD TM=$TM TD=$TD
```

The part between 'if.... else' is unnecessary. I used it just for fun. It is meant to let you manually define start and end dates and months, in case you haven't updated them in the script where variables (m1, d1 etc.) are defined.

---

### Post by linuxyogi on 2014-05-21
Thnanks. I will try the script as soon as I buy the sim.

---

