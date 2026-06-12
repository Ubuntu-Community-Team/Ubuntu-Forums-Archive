---
title: "&quot;Error: Cannot open display ':0'&quot; - how do I specify a display?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by j-g-faustus on 2009-06-06
Hi,

I'm on Ubuntu 9.04, and trying to use nvidia-settings from the command line to monitor the temperature of the graphics card:
```

nvidia-settings -c :0 -q GPUCoreTemp

  Attribute 'GPUCoreTemp' (jf-server:0.0): 54.
    'GPUCoreTemp' is an integer attribute.
...

```
This works when I run it myself.

But when I try to run it from an automated script, it fails with the message
> 
ERROR: Cannot open display ':0'.

ERROR: Unable to query attribute GPUCoreTemp specified in query
       'GPUCoreTemp' (no Display connection).


I tried "localhost:0", "jf-server:0" and "127.0.0.1:0", none of them work from command line. 

How can I refer to the display so that it works in both cases? 

And what is this display thing anyway, is there a way I can list the displays on the system? Like I can do "ls /dev/sd*" to list the hard disks?

---

### Post by ad_267 on 2009-06-07
Why do you need the "-c" option? Just use:
```
nvidia-settings -q GPUCoreTemp
```

---

### Post by j-g-faustus on 2009-06-07
Because if I skip the -c option, I get
> ERROR: The control display is undefined; please run `nvidia-settings --help`
       for usage information.


This is perhaps because I run it from an ssh shell?

---

### Post by j-g-faustus on 2009-06-07
Problem solved: The script was running as root, and the :0 variable is apparently not set for root. 
Changing the script to run as my user (sudo -u [myself]), it worked.

---

### Post by ad_267 on 2009-06-07
> **j-g-faustus said:**
> Because if I skip the -c option, I get


This is perhaps because I run it from an ssh shell?

Yeah that's probably why, I didn't think it would need to know the display to get the temperature and it works without that option normally. Glad it's solved now.

---

