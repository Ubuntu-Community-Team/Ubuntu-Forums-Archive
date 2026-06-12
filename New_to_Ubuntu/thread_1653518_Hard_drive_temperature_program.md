---
title: "Hard drive temperature program?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by mustis81 on 2010-12-27
Specifically i would like a program that sits in the upper toolbar and displays the internal temperature of the hard drive or cpu core.

---

### Post by frustratednerd on 2010-12-27
You can do this by installing the "computertemp" package. Go into Terminal and copy&paste the following:

```
sudo apt-get install computertemp
```

After you have it installed, you can add it to the upper panel by right-clicking the panel and selecting "Add to Panel...", then selecting "Computer Temperature Applet".

---

### Post by karthick87 on 2010-12-27
Install hddtemp
```
sudo apt-get install hddtemp
```
**Output:**  
```
karthick@Ubuntu-desktop:~$ sudo hddtemp /dev/sda
/dev/sda: ST3160813AS: 36°C

```

---

### Post by karthick87 on 2010-12-27
Also have a look at these links for applets,

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

---

### Post by amjjawad on 2010-12-27
> **karthick87 said:**
> Install hddtemp
```
sudo apt-get install hddtemp
```**Output:**  
```
karthick@Ubuntu-desktop:~$ sudo hddtemp /dev/sda
/dev/sda: ST3160813AS: 36°C

```

Any idea what's the temp of the HDD that I need to worry about?

---

### Post by aytech on 2010-12-27
> **amjjawad said:**
> Any idea what's the temp of the HDD that I need to worry about?
 
Desktop or laptop? 
Temp arount 40 on desktop HDDs is fine, depending on the model and load. If it gets over 50, close to 60, that might be the problem, again, depending on the model. Manufacturers usually specify temp threshold max in the specs for the drive.

---

### Post by amjjawad on 2010-12-27
> **aytech said:**
> Desktop or laptop? 
Temp arount 40 on desktop HDDs is fine, depending on the model and load. If it gets over 50, close to 60, that might be the problem, again, depending on the model. Manufacturers usually specify temp threshold max in the specs for the drive.

Desktop - SATA 500GB.

I'll try to search for that later. It's good to know the temp but I know for sure that I'm so kind with that HDD :)

Thanks!

---

### Post by mustis81 on 2010-12-27
Thank you, all of these suggestions are great. I went with frustratednerd's solution because of the simplicity of the app. Thanks again everyone else.

---

