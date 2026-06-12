---
title: "/proc/net/dev file providing wrong value for Receive bytes - packets for bond0 interf"
date: 2017-08-23
forum: Networking &amp; Wireless
---

### Post by zyriljamez on 2017-08-23
I am running a script to collect the content of the file /proc/net/dev and parse it to get value for Receive bytes - Packets for each interface. Intermittently I am getting wrong value for bond0 interface. 

Script is reading the content of the file /proc/net/dev each second and printing current value, previous value and the difference for "Receive bytes - packets" for bond0 interface. In between the value shows huge increment and then goes down. This value is supposed to increase continuously. So the value provided by /proc/net/dev  is wrong sometimes.

Sample output:

```
current value is 298668567235 Previous value is 298668505872 Difference is 61363.0
current value is 298668663924 Previous value is 298668567235 Difference is 96689.0
current value is 298668880728 Previous value is 298668663924 Difference is 216804.0
current value is 298668988291 Previous value is 298668880728 Difference is 107563.0
current value is 309539575778 Previous value is 298668988291 Difference is 10870587487.0 -------> [COLOR=#d04437][FONT=Arial]Huge increment in value[/FONT][/COLOR]
current value is 298669598780 Previous value is 309539575778 Difference is -10869976998.0 ------> [COLOR=#d04437][FONT=Arial]Value goes down at this point[/FONT][/COLOR]
Wrong value : *******************298669598780 309539575778
current value is 298669696553 Previous value is 298669598780 Difference is 97773.0 -----------> [COLOR=#14892c][FONT=Arial]Next value onwards incrementing properly[/FONT][/COLOR]
current value is 298669933950 Previous value is 298669696553 Difference is 237397.0
current value is 298670364302 Previous value is 298669933950 Difference is 430352.0
[COLOR=#333333][FONT=Arial]current value is 298670397145 Previous value is 298670364302 Difference is 32843.0
```

Please provide inputs regarding this issue.[/FONT][/COLOR]

---

### Post by Doug S on 2017-08-24
Hi, and welcome to Ubuntu forums.

> **zyriljamez said:**
> I am running a script to collect the content of the file /proc/net/dev and parse it to get value for Receive bytes - Packets for each interface. 

Could you post your script?

> **zyriljamez said:**
> Intermittently I am getting wrong value for bond0 interface.

Define "Intermittently": Once a week, once a day, ... Once per minute

---

### Post by zyriljamez on 2017-08-29
> **Doug S said:**
> 



Could you post your script?
Its a simple python script which will read content of the /proc/net/dev file each second and using regular expression it will extract Receive bytes - packets count for a particular interface(here bond0 interface). Please find the script attached.

Script : [ATTACH]276536[/ATTACH]



> **Doug S said:**
> 

Define "Intermittently": Once a week, once a day, ... Once per minute
I could observe this anomaly once in 2 or 3 minutes.

---

### Post by Doug S on 2017-08-29
It might be an idea to echo the problem cases, so that you can check the raw data before parsing. i.e.:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
#

import re
import time

previous = 0

while True:
    time.sleep(1)
    f = open('/proc/net/dev', 'r')
    data = f.readlines()
    for item in data:
        match=re.search('br0:\s([0-9]+)',item)
        if match is not None:
            current = match.group(1)
            diff = float(current) - float(previous)
#           print "current value is "+current+" Previous value is "+str(previous)+" Difference is "+str(diff)
            if diff < 0:
                print "Wrong value : *******************"+current+" "+previous
                print item
            previous = current

```And/or to always echo the line, just while debugging. i.e.:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
#

import re
import time

previous = 0

while True:
    time.sleep(1)
    f = open('/proc/net/dev', 'r')
    data = f.readlines()
    for item in data:
        match=re.search('br0:\s([0-9]+)',item)
        if match is not None:
            print item
            current = match.group(1)
            diff = float(current) - float(previous)
            print "current value is "+current+" Previous value is "+str(previous)+" Difference is "+str(diff)
            if diff < 0:
                print "Wrong value : *******************"+current+" "+previous
            previous = current

```which gives:
```
doug@s15:~/temp4$ ./readstat.py
   br0: 497046699280 30233577    0    0    0     0          0         0 1966359091 29705280    0    0    0     0       0          0

current value is 497046699280 Previous value is 0 Difference is 4.9704669928e+11
   br0: 497046699326 30233578    0    0    0     0          0         0 1966359417 29705281    0    0    0     0       0          0

current value is 497046699326 Previous value is 497046699280 Difference is 46.0
   br0: 497046699372 30233579    0    0    0     0          0         0 1966359743 29705282    0    0    0     0       0          0

current value is 497046699372 Previous value is 497046699326 Difference is 46.0
   br0: 497046699418 30233580    0    0    0     0          0         0 1966360069 29705283    0    0    0     0       0          0

current value is 497046699418 Previous value is 497046699372 Difference is 46.0
   br0: 497046699464 30233581    0    0    0     0          0         0 1966360395 29705284    0    0    0     0       0          0

```By the way, I do not have any bond stuff, so used my bridge IF, br0.

I tried this using iperf between two computers and for quite awhile and never saw an issue.
I can only assume some issue with the driver for your specific hardware.

---

### Post by zyriljamez on 2017-08-31
> **Doug S said:**
> It might be an idea to echo the problem cases, so that you can check the raw data before parsing.

I printed the raw data before parsing. I could see the erroneous data there as well. Please see the output below.

 ```
bond0: 58502926459 154663225714    0    0    0     0          0 154618834441 28403065716 51580553032    0    0    0     0       0          0
current value is 58502926459 Previous value is 58502898709 Difference is 27750.0


 bond0: [COLOR=#00ff00]**58503173482 **[/COLOR]154663226076    0    0    0     0          0 154618834441 28403309784 51580553381    0    0    0     0       0          0
current value is 58503173482 Previous value is 58502926459 Difference is 247023.0


 bond0: **[COLOR=#ff0000]60525173753 [/COLOR]**154677107282    0    0    0     0          0 154632714686 28403479186 51580554491    0    0    0     0       0          0
current value is 60525173753 Previous value is 58503173482 Difference is 2022000271.0


 bond0: **[COLOR=#00ff00]58503430977 [/COLOR]**158958194444    0    0    0     0          0 158913801737 28403546958 55875521731    0    0    0     0       0          0
current value is 58503430977 Previous value is 60525173753 Difference is -2021742776.0


Wrong value : *******************58503430977 60525173753


 bond0: 58503479784 158958194626    0    0    0     0          0 158913801737 28403590211 55875521910    0    0    0     0       0          0
current value is 58503479784 Previous value is 58503430977 Difference is 48807.0


 bond0: 58503521819 158958194843    0    0    0     0          0 158913801737 28403626566 55875522109    0    0    0     0       0          0
current value is 58503521819 Previous value is 58503479784 Difference is 42035.0
```

> **Doug S said:**
> 
I can only assume some issue with the driver for your specific hardware.

Do you suspect any other reason for this behavior other than driver issue ?

---

### Post by Doug S on 2017-08-31
> **zyriljamez said:**
> Do you suspect any other reason for this behavior other than driver issue ?

Well, I am not sure. However, in the data you provided, I do notice: A lot of transmit errors; A non correcting, not possible, jump in receive packets; A non correcting, not possible, jump in transmit bytes; A ridiculous number of transmit packets, given no transmit bytes, on some lines; A not possible jump in transmit errors on one sample, that just so happens to be extremely close to 2**32.

Why are numbers close to 2*32 (2 to the power of 32) important? Because it might mean issues with 32 bit type drivers screwing up during a carry over onto the next 32 bits. For example not disabling interrupts during the carry over math, opening a window of opportunity to misread the actual value.

The bottom line is that you have severe issues.

EDIT: Adding my spreadsheet information:
```

Rx Bytes	Rx Packets	Rx B diff	Rx P diff	Tx Bytes	Tx Packets	TX errors	Tx B diff	Tx P diff	Tx E diff
58502926459	154663225714					154618834441	28403065716	51580553032			
58503173482	154663226076	247023		362		154618834441	28403309784	51580553381	0		244068		349
60525173753	154677107282	2022000271	13881206	154632714686	28403479186	51580554491	13880245	169402		1110
58503430977	158958194444	-2021742776	4281087162	158913801737	28403546958	55875521731	4281087051	67772		4294967240
58503479784	158958194626	48807		182		158913801737	28403590211	55875521910	0		43253		179
58503521819	158958194843	42035		217		158913801737	28403626566	55875522109	0		36355		199

```

---

### Post by zyriljamez on 2017-09-05
Thanks Doug for analyzing the issue in depth and providing these valuable information. :)

---

