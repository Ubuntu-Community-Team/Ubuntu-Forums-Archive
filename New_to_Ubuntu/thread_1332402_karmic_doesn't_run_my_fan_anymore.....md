---
title: "karmic doesn't run my fan anymore...."
date: 2009-11-20
forum: New to Ubuntu
---

### Post by bm13084 on 2009-11-20
I've been severely overheating the last few days, and i thought my fan died... but for some reason karmic randomly stopped running my fan when it gets hot.  thought it was dust in my heatsync, but it wasn't.  the fan powers on when i boot up if the laptop is still hot from the last powerdown... any ideas?

laptop: acer aspire 5720z
os: karmic koala fully updated

edited to add: been running koala since its release.

---

### Post by bm13084 on 2009-11-20
while researching my bug, i found a known bug that gives me a workaround if anyone is having the same problem.  coming out of hibernate apparently makes the fan run 100% of the time, which is better than 0% of the time.  it kicked my fan on when i came out of hibernate... more proof to me that the fan isn't roached...

anyhow, here's hoping an update fixes my real issue soon. until then, ill just hibernate instead of powering down.

---

### Post by hatchetjuggla on 2009-11-25
I'm having the exact same issue on an acer Aspire 5315. Same workaround also works. Booting a 8.10 live disk the fan works fine. Open Suse 10.2 live disk had the same problem.

---

### Post by ukripper on 2009-11-25
can you install this package:
```
sudo apt-get install mbmon
```

and then run it by 
```
sudo mbmon
```

and post output of first 5 readings.

And also to get thorough probe of your system, install lm-sensors taken from [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Follow below steps:

Install and Configure lm-sensors

   1. Install the lm-sensors package (see InstallingSoftware).
   2. Run sudo sensors-detect and answer YES to all YES/no questions. I generally use the ISA bus rather than the SMBus bus, your choice to this question!.
   3. At the end of sensors-detect, a list of modules that needs to be loaded will displayed. Type "yes" to have sensors-detect insert those modules into /etc/modules, or edit /etc/modules yourself.
   4. Next, run "sudo /etc/init.d/module-init-tools". This will read the changes you made to /etc/modules in step 3, and insert the new modules into the kernel. 

Test lm-sensors

Next, you should test that lm-sensors works correctly. Run the "sensors" command and check the output.

---

### Post by clive littlewood on 2009-11-25
Hi 

It appears from previous threads that the answer is to flash the latest bios from your local Acer support site.

BE CAREFUL though and follow instructions to the letter, as this an destroy your system if done incorrectly.

Hope this helps

Clive

---

