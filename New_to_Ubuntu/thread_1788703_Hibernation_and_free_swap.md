---
title: "Hibernation and free swap"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-06-23
Since I upgraded my Acer 3620 laptop from Karmic to Natty a week ago, I've been having some trouble hibernating my Natty.  Often (but not always) it reports:

```
PM:  Not enough free swap  
```

I'm not trying to hibernate a large number of open windows; compared to what I could successfully hibernate on Karmic,  I'm actually trying to hibernate less on Natty, rather than more.

However hibernation seems to be more successful if my last closedown was a restart.   I get the impression that swap isn't being released efficiently after a previous hibernate and something must be occupying part of the available swap memory before a second or third  hibernation begins.  

Any suggestions?

---

### Post by jerrrys on 2011-06-23
u lucky dog...

spent some time in southern thailand

how much swap do you have ?

---

### Post by Sleepy-zz-John on 2011-06-23
Thanks jerrries.    I have 740MB swap,  the same as I had in Karmic,  so hibernation in Natty appears to be working differently somehow.  Last time I tried to hibernate earlier today, I only had one Skype window and one SeaMonkey browser with two tabs up, and I'd previously hibernated this combination plus another browser window successfully.   This last time, however, it wouldn't hibernate and kept giving me the "not enough free swap" prompt,  so it looks as if something is being carried forward and occupying the swap space when it shouldn't!   It's happened several times in the last week since I upgraded to Natty.    

Just at the moment,  following a restart because I couldn't hibernate last time I wanted to close,  I have 7 windows open and I'm showing memory 20% occupied and swap 0% occupied.    Perhaps I should check these figures again after I've hibernated? 

It's too hot and humid here in northern Thailand at the moment.   Of course the grass is always greener...   :)

---

### Post by jerrrys on 2011-06-23
if you want to see where you stand before hibernation you can in terminal

head /proc/meminfo

myself, i think i would double the swap space and see what happens next.  swap has to be a least equal to ram.

---

### Post by Sleepy-zz-John on 2011-06-23
Thanks again.   Since my last posting here,  and following a previous restart,  this time I've successfully hibernated and woken up those same windows that wouldn't hibernate before.

So after one hibernation and wakeup I now have:
System Monitor showing Memory 20% and Swap 2.8% occupied.  
Meminfo gives:
```
MemTotal:        1274792 kB
MemFree:          741468 kB
Buffers:           18840 kB
Cached:           266900 kB
SwapCached:        20380 kB
Active:           260876 kB
Inactive:         232696 kB
Active(anon):     203948 kB
Inactive(anon):   149256 kB
Active(file):      56928 kB
```

Still only a hunch, but I think I should now do some more hibernates and wakeups to check if I'm getting an incremental change to these figures each time.

It's true, my available swap is a lot less than my available RAM,  but why would this suddenly become an issue after upgrading to Natty?

---

### Post by jerrrys on 2011-06-23
i would think that natty simply requires more resources

---

### Post by Sleepy-zz-John on 2011-06-24
I've now done a series of hibernates and wakeups and checked my resources status at each stage:
```
		23 June		24 June		24 June		 24 June
 		After 1st 	After 2nd 	After 3rd	 After 4th
		hibernate	hibernate	hibernate	 hibernate
System Monitor  
Resources tab:  
Mem = 		20%   		23.8%		20.5%		 21.3%
Swap = 		19.5MiB (2.8%)	80MiB (11.3%)	175.3MiB (24.8%) 209.3MiB (29.7%)

head /proc/meminfo
MemTotal:        1274792 kB	1274792 kB	1274792 kB	1274792 kB
MemFree:          741468 kB	 565608 kB	 698952 kB	 747024 kB
Buffers:           18840 kB	  25320 kB	  31696 kB	  22284 kB
Cached:           266900 kB	 383236 kB	 276496 kB	 227456 kB
SwapCached:        20380 kB	  56360 kB	  41772 kB	  52648 kB
Active:           260876 kB	 310168 kB 	 230632 kB	 228068 kB
Inactive:         232696 kB	 358444 kB	 304228 kB 	 258672 kB
Active(anon):     203948 kB	 244972 kB	 190800 kB 	 176744 kB
Inactive(anon):   149256 kB	 186944 kB	 174704 kB	 167988 kB
Active(file):      56928 kB	  65196 kB	  39832 kB	  51324 kB


Note: At 3rd & 4th hibernate attempts I received warning 
"PM: Not enough free swap",  so I closed one open 
window and tried again.  Got same warning again 
but hibernate was nevertheless successful 
``` 

The most significant thing I notice here is my System Monitor - Resources tab - Swap figure which is progressively increasing after each wakeup.   Only a restart brings it down again.   Something new must be getting added to the swapfile at each hibernate.   

So even if I were to increase my swapfile capacity, I can imagine that this progressive increase would eventually catch up with whatever capacity I made available anyway.

I'd appreciate suggestions for my next step in dealing with this problem.  Further tests?   Try reporting it as a bug with the above data?   There's evidently something odd going on,  but I can't draw any conclusions from my head /proc/meminfo figures because they don't seem to back up my Swap figures in System Monitor.

---

### Post by Sleepy-zz-John on 2011-07-04
This thread seems to have died,  so I've made a fresh start on the same topic at <snip>

---

