---
title: "Auto disconnect if limit traffic reached"
date: 2016-10-05
forum: Networking &amp; Wireless
---

### Post by Daniyal_Javani on 2016-10-05
Currently I use [ntm]("https://sourceforge.net/projects/netramon/files/NTM/ntm-1.x/") but it's last update is for 2011 and I have many problem with that in Ubuntu 16.04.1 . Is there any alternative for that?
If no, can you please help me to extract daily traffic usage in vnstat to write a script for that with cron like the follow script?
```
unit=$(vnstat -s -i ppp0 | sed -n 6p |  awk '{ print $9 $7 }' | head -c 1) 
amount=$(vnstat -s -i ppp0 | sed -n 6p |  awk '{ print $8 $7 }' | rev | cut -c 2- | rev)
day=$(vnstat -s -i ppp0 | sed -n 6p |  awk '{ print $1 $7 }' | rev | cut -c 2- | rev)
//The bug is in the three lines above, I can't extract the daily usage because the number of lines change in some execution of vnstat
max=34
if [ "$day" == 'today' ]; then
    if [ "$unit" == 'M' ]; then
        if (( $(echo "$amount > $max" |bc -l) )); then
            if ! [ -f "/home/vahid/bash/dialogue" ]; then
                touch /home/vahid/bash/dialogue
                poff dsl-provider
                zenity --error --text="The limit is reached" --display=:0.0
                rm /home/vahid/bash/dialogue
            fi
        fi
    fi
fi
```

---

### Post by Vergo on 2016-10-06
```
amount=$(vnstat --oneline -i ppp0 | cut -d\; -f6 | cut -d' ' -f1)
unit=$(vnstat --oneline -i ppp0 | cut -d\; -f6 | cut -d' ' -f2 | cut -b1)
```
and forget the day as that will always be the current day:
```

       --oneline
              Show traffic summary for selected interface using one line with a parseable format. The  output  contains  15  fields
              with  ; used as field delimeter. The 1st field contains the version information of the output that will be changed in
              future versions of vnStat if the field structure changes. The following fields in order 2) interface name,  3)  time&#8208;
              stamp  for  today,  4) rx for today, 5) tx for today, 6) total for today, 7) average traffic rate for today, 8) time&#8208;
              stamp for current month, 9) rx for current month, 10) tx for current month, 11) total for current month, 12)  average
              traffic rate for today, 13) all time total rx, 14) all time total tx, 15) all time total traffic.
```

If you want to simplify even further, you could use the database export feature --exportdb (database dump in older version with --dumpdb):
```
vnstat --exportdb -i ppp0 | grep 'd;0' | cut -d\; -f4,5 | sed 's:;: + :g' | bc
```

The d;0 is always the current day and fields 4 and 5 represent the current rx and tx in MiB.

---

### Post by Daniyal_Javani on 2016-10-06
Nice! thanks, that works great.

---

