---
title: "what to do to to set cpu frequency to performance?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-01
I always have to set it manually....thank you

---

### Post by Delever on 2009-01-01
You can change it from command line:

```
sudo cpufreq-set -g performance
```

You can set it permanently by going to gconf-editor:

```
gconf-editor
```

With that launched, choose apps -> gnome-power-manager -> cpufreq. You then need to change the policy_ac to "performance" (without quotes).
This setting should be used next time you reboot GNOME session.

---

### Post by eshant_engineer on 2009-01-01
I want this from start-up then what should i add to session?

---

### Post by Delever on 2009-01-01
> **eshant_engineer said:**
> I want this from start-up then what should i add to session?

No, using gconf-editor and changing that value should be enough i think.

---

### Post by jordanmthomas on 2009-01-01
If you want it to happen regardless of whether you've started gnome or not, just add
```
cpufreq-set -g performance
``` as the last line in /etc/rc.local

I'm sure there are better ways that'll get it set before your system even boots, but this is what I do to set mine to ondemand.

---

### Post by eshant_engineer on 2009-01-01
> **Delever said:**
> You can change it from command line:

```
sudo cpufreq-set -g performance
```

You can set it permanently by going to gconf-editor:

```
gconf-editor
```

With that launched, choose apps -> gnome-power-manager -> cpufreq. You then need to change the policy_ac to "performance" (without quotes).
This setting should be used next time you reboot GNOME session.

cpufreq option is not given    under gnome-power-manager(using 8.10 intrepid)

---

### Post by polobreaka on 2009-02-20
i am wondering about this as well. i always have to change it manually in my panel for each CPU. is there a way to change it from the start up and how can i change both CPU (cpu0 and cpu1) from the start up?

Thanks.

---

### Post by sdennie on 2009-02-20
First I will say that setting the governor to "performance" is almost always not needed.  Unless you are running niced CPU intensive things in the background, you will notice absolutely no difference between ondemand and performance.

However, there are many ways to set the frequency governor.  The one that will work on all machines is:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sudo sh -c "echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor"

```

You can put that in /etc/rc.local and make it permanent as well (though, from there, the sudo part is not needed).

---

### Post by polobreaka on 2009-02-20
reason i wanted to do this is because i keep getting random hang ups. it will stay frozen for a couple of mins. everytime it does that, i check the log and it comes up with clocksource tsc unstable. so far by changing it to performance i havent had a hang up for couple of days since i left my comp on. i dont know if it has anything to do with it, but it helped me with the random hang ups. i was also suggested in the 'known issue/bug in intrepid' thread.

---

### Post by sdennie on 2009-02-20
In that case, sure, try the commands I provided above.  See if it helps.  If it does, find/file a bug and see if you can give more information that will help procure a fix.

---

### Post by polobreaka on 2009-02-20
> **sdennie said:**
> In that case, sure, try the commands I provided above.  See if it helps.  If it does, find/file a bug and see if you can give more information that will help procure a fix.



where do i add the 2 lines in the rc.local? here is how my rc.local looks like.

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

---

### Post by polobreaka on 2009-02-20
i think i figured it out.

i paste your 2 line in here:

> #!/bin/sh -e
#
# rc.local
[COLOR="Red"]sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sh -c "echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor"[/COLOR] 
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0 

i just restarted my comp to see if it sticks. i noticed my cupfreq panel shows performance. awesome! thanks for your help.

---

