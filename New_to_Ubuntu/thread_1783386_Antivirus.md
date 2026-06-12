---
title: "Antivirus"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by kjjj11223344 on 2011-06-15
First of all, does Ubuntu 11.04 require antivirus software. Second of all, does anyone know of a free one for this OS. I tried avg for Linux but it is all terminal-based (I would prefer it be gui). Thanks for the help.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
it is not needed 
its uses are scanning windows and scanning email to prevent passing them on
install clamav if you need/want it
to update the virus database use the command 
sudo freshclam

---

### Post by kjjj11223344 on 2011-06-15
So Linux automatically scans everything? Also, I tried this command and it says not found.

---

### Post by ivanovnegro on 2011-06-15
Very simple, you dont need an antivirus. Enjoy your system! ;)

---

### Post by kjjj11223344 on 2011-06-15
Okay thanks. One last thing, I don't want to start a new thread for this, but is there anyway to verify if intel speedstep is working, what my voltages are, etc. I have tried cpu-g but it shows either a static 1.6ghz (with an i7-2600k) or a static 4.5ghz when overclocked (I have speedstep and c1 state enabled in BIOS)? By the way, does Linux even support these?

---

### Post by lisati on 2011-06-15
I think it has been said in various ways elsewhere on this forum that you should never attribute something to malware (viruses etc) that would better be explained by carelessness, ignorance, or stupidity. Most of the time, a healthy dose of good sense about which websites you visit, which emails you read, and advice that you heed will be your best defense. :D

Enjoy!

---

### Post by mikodo on 2011-06-15
> **kjjj11223344 said:**
> First of all, does Ubuntu 11.04 require antivirus software. Second of all, does anyone know of a free one for this OS. I tried avg for Linux but it is all terminal-based (I would prefer it be gui). Thanks for the help.

1. Conventional wisdom usually indicate that none is needed.

2. There is an continually updated Antiviral on-demand scanner called Clamtk Virus Scanner. It is available in Ubuntu Software Center and Synaptic. If you download and install it from these it may not be the  newest version, but whichever version is installed; it will be updated continually with the newest Virus Definitions. I have run it regularly for the last three years and never have I had a virus in Linux. 

Web site Homepage:  [http://clamtk.sourceforge.net/index.html](http://clamtk.sourceforge.net/index.html)

---

### Post by kjjj11223344 on 2011-06-15
> **mikodo said:**
> 1. Conventional wisdom usually indicate that none is needed.

2. There is an continually updated Antiviral on-demand scanner called Clamtk Virus Scanner. It is available in Ubuntu Software Center and Synaptic. If you download and install it from these it may not be the  newest version, but whichever version is installed; it will be updated continually with the newest Virus Definitions. I have run it regularly for the last three years and never have I had a virus in Linux. 

Web site Homepage:  [http://clamtk.sourceforge.net/index.html](http://clamtk.sourceforge.net/index.html)
Okay thanks I will check it out.

Any information on whether cpu c states and speedstep are supported in Ubuntu, and if there is a pprogram like cpu-z that will work with Sandy Bridge.

---

### Post by amauk on 2011-06-15
```
sudo lshw
```will give you lots (and I mean lots) of info about hardware

There's also lm-sensors, which will read any hardware sensors (temperatures, fan speeds, voltages, etc.) your system has

---

### Post by ivanovnegro on 2011-06-15
> **kjjj11223344 said:**
> 

Any information on whether cpu c states and speedstep are supported in Ubuntu, and if there is a pprogram like cpu-z that will work with Sandy Bridge.

I am sorry but you should really open up a new thread on this. 
Its not nice to mix different questions, just an advice. ;)

---

### Post by kjjj11223344 on 2011-06-15
> **amauk said:**
> ```
sudo lshw
```will give you lots (and I mean lots) of info about hardware

There's also lm-sensors, which will read any hardware sensors (temperatures, fan speeds, voltages, etc.) your system has
Great Im-sensors is what I needed. Now, how the heck do you install this? It came as "[ lm_sensors-3.3.0.tar.bz2]("http://dl.lm-sensors.org/lm-sensors/releases/lm_sensors-3.3.0.tar.bz2")". I have always been a Windows user so Ubuntu is kind of new to me.

---

### Post by ojdon on 2011-06-15
Like other users have said above, no you don't need a Anti-Virus. This is because the way Linux is set up you will need to actually type in a password to do actual damage to the system. Pretty simple yet effective way of doing things. Yes, there is anti-virus software available but they are only really useful for Linux servers which is connected to Windows-based machines in order to keep viruses out of the Network. So unless you are running a server there is no need to get one!

Hope that clears everything up!

---

### Post by amauk on 2011-06-15
You don't typically download files off of websites to install
Use the package management (Ubuntu software center)

---

### Post by pqwoerituytrueiwoq on 2011-06-15
sudo apt-get install lm-sensors
you may want to install the sensors-applet package for this

---

### Post by kjjj11223344 on 2011-06-15
> **pqwoerituytrueiwoq said:**
> sudo apt-get install lm-sensors
you may want to install the sensors-applet package for this
Thanks for being so helpful guys. I find it in the software center and installed. Now how do do I run it? Sorry for the newbie questions again.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
to add the applet right click your panel go to add to panel
look for hardware sensors monitor

---

### Post by amauk on 2011-06-15
> **kjjj11223344 said:**
> Now how do do I run it?```
sensors
```

---

### Post by kjjj11223344 on 2011-06-15
> **amauk said:**
> ```
sensors
```
I tried typing sensors and it says no sensors found! Make sure you loaded all the kernel drivers you need. Try sensors-detect to find out which these are.

---

### Post by amauk on 2011-06-15
> **kjjj11223344 said:**
> I tried typing sensors and it says no sensors found! Make sure you loaded all the kernel drivers you need. Try sensors-detect to find out which these are.Then run the sensors-detect program```
sudo sensors-detect
```

---

### Post by kjjj11223344 on 2011-06-15
> **amauk said:**
> Then run the sensors-detect program```
sudo sensors-detect
```

I forgot to mention I tried this and I got another error. I will post what I got in like 10 minutes when I get back on computer.
Edit:
Okay, I was forgetting to type "sudo" before the sensors detect. I have now gone through the sensors detect program and answered yes to everything. At the end it says "Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them." I still get the same error when using the sensors command. Is there something else that I need to do?
Edit #2:
Okay was able to successfully install it as a root user.

---

