---
title: "CPU Temperature is going high 70C"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by EmreCFT on 2011-07-10
I have just experienced similar issue. 
Ubuntu 11.04 installed at my laptop (check my signature) with an external cooler under it. 
I open skype , making webcam connection and cpu temperature rises to 69 C.
I closed skype off, opened firefox windows and thunderbird. Still temperature same. 
I closed all running applications and then temperature reduced through 60 C. (still too much)
Also i realised that after long time working with ubuntu, laptop fan makes more noise. 

After those i closed ubuntu and opened laptop with windows 7 ultimate. I did same things but cpu temperature is between 43 and 49 C. 

I am not sure whether it was a random stuff or related with ubuntu. Just gone surprised abit..
(used xsensors app. to check temp. for ubuntu and @win7 ultimate core temp software )

---

### Post by pqwoerituytrueiwoq on 2011-07-10
go to power management in windows 7 look at the cpu speed under advanced
it very well could be set to only run at 40 or 60 percent 
since ubuntu is set to be able to access 100% it would generate more heat

---

### Post by Mark Phelps on 2011-07-10
Ubuntu 11.04, unlike Win7, appears NOT to support CPU scaling for your processor.  So, the only options available for you are the following:
1) See if there is some way to get CPU scaling support
2) Quit using Ubuntu and use Win7 instead.

And, yeah, the second is a really unpopular suggestion in these forums -- but unless you can do 1), continuing to use Ubuntu with your laptop is overheating the CPU and other components -- and risking permanent damage.

---

### Post by EmreCFT on 2011-07-10
Adding sensors (for monitoring) and then
Adding the following to  /etc/modules: (sudo gedit /etc/modules)
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

seems helped me for now btw. After that, i ran all those apps again, also worked more firefox windows, a running video..etc and temperature is betwween 48-50 C.

---

