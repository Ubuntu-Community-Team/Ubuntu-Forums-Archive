---
title: "Data counter for 3G traffic"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by chloraldo on 2008-07-03
Hi all

I sometimes connect my Laptop (eeePC 900) via USB to my cellphone (SE K800i) for accessing the web. My telephone company offers a limited data amount per month for a reasonable price, then it get's extremely expensive.

Is there an easy way to measure the internet traffic over my phone modem? I obviously don't care about the data going over Wifi and LAN...

Even better: Any idea how to set an alarm or interrupt the connection once the limit has been reached?

Thanks for your replies!

---

### Post by nixscripter on 2008-07-03
I don't know about total, but **ifconfig** can tell you the amount of traffic going over a network interface since it was connected. For example, my wireless card:

```

wlan0_ren Link encap:Ethernet  HWaddr 00:1B:77:9C:BC:F9  
          inet addr:192.168.97.19  Bcast:192.168.97.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe9c:bcf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          [COLOR="Blue"]RX bytes:3010523 (2.8 MB)[/COLOR]  [COLOR="Red"]TX bytes:644700 (629.5 KB)[/COLOR]

```

That was a little web surfing. Blue is received, red is sent. Just go to a terminal and type: ```
ifconfig
``` when you're connected and look at those two fields.

Hope this helps.

---

### Post by mrnobody75 on 2009-12-30
Here is two script!

(a counter script)

# /bin/bash

interface="ppp0"
logfile="/home/username/logfile.txt"

if [ ! -e $logfile ]
    then touch $logfile
    echo 0 > $logfile
    echo 0 >> $logfile
fi
temp1="0"
temp2="0"
while [ 1 -gt 0 ]
do
datafull=`cat /proc/net/dev|tr ":" " "|grep $interface|awk '{ print $2 " " $10 }'`
datain=`echo $datafull|awk '{ print $1 }'`
dataout=`echo $datafull|awk '{ print $2 }'`
if [ -z $datain ] && [ $temp1 -gt 0 ]
    then
    filein1=`cat $logfile|head -n 1|tail -n 1`
    filein2=`cat $logfile|head -n 2|tail -n 1`
    fileout1=`expr $filein1 + $temp1`
    fileout2=`expr $filein2 + $temp2`
    echo $fileout1 > $logfile
    echo $fileout2 >> $logfile
    temp1="0"
    temp2="0"
fi
if [ -z $datain ] && [ $temp1 -eq 0 ]
    then
    datain="0"
    dataout="0"
fi
if [ $datain -lt $temp1 ]
    then
    filein1=`cat $logfile|head -n 1|tail -n 1`
    filein2=`cat $logfile|head -n 2|tail -n 1`
    fileout1=`expr $filein1 + $temp1`
    fileout2=`expr $filein2 + $temp2`
    echo $fileout1 > $logfile
    echo $fileout2 >> $logfile
    temp1=$datain
    temp2=$dataout
fi
if [ $datain -gt $temp1 ]
    then temp1=$datain
    temp2=$dataout
fi
sleep 5
done

(info script)

#!/bin/bash

logfile="/home/username/logfile.txt"

inm="byte"
outm="byte"
in=`cat $logfile|head -n 1|tail -n 1`
out=`cat $logfile|head -n 2|tail -n 1`
inl=`echo $in|wc -c`
outl=`echo $out|wc -c`
if [ $inl -gt 4 ] && [ $inl -lt 8 ]
    then
    temp=`expr $in / 1024`
    in="$temp"
    inm="Kb"
fi
if [ $inl -gt 7 ]
    then
    temp=`expr $in / 1048576`
    in="$temp"
    inm="Mb"
fi
echo $outl
if [ $outl -gt 4 ] && [ $outl -lt 8 ]
    then
    temp=`expr $out / 1024`
    out="$temp"
    outm="Kb"
fi
if [ $outl -gt 7 ]
    then
    temp=`expr $out / 1048576`
    out="$temp"
    outm="Mb"
fi
zenity --info --title "3G info" --text="In: $in $inm, out: $out $outm"

Sorry! I'm not a programmer, but it works.

---

### Post by chmac on 2012-04-04
I realise this is an old thread, but for anyone finding it from a search (as I did) the best tool for the job (from a GUI point of view!) seems to be [NTM]("http://netramon.sourceforge.net/eng/download.html"), which even integrates nicely with indicators.

---

