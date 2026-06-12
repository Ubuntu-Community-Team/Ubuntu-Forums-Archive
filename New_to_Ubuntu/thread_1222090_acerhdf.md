---
title: "acerhdf?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by heine on 2009-07-24
Hi.

I have recently installed UNR on my AAO and I'm quite happy with my new OS. Yesterday I installed the two tweaks I found missing, the WiFi LED tweak and the Fan tweak, following the instructions in this guide [https://help.ubuntu.com/community/AA1/Fixes](https://help.ubuntu.com/community/AA1/Fixes) everything went fine and but now I'm wondering is there a way to check whether the kernel module works or not? 

and how do I update it when a new version is released?

---

### Post by cariboo on 2009-07-24
IF everything works, the drivers are working properly. Ubuntu does a new release every 6 months, in April and October. When a new version is made available just press Alt-F2 and type:

```
gksu update-manager -d
```

The above command will start the upgrade process. 

There are also the normal security and bug fix updates that you will be notified about, usually once a week, unless it is a critical update.

---

### Post by heine on 2009-07-24
Is there a way to check if the Acerhdf actually is doing its job?, the reason is that my fan has been off ever since I installed the tweak and sometimes I find it a bit hot.

---

### Post by Jarige on 2010-04-13
This might be a little late, but you could check whether it is running with this command:
```
dmesg|grep acerhdf
```
This will return the time (between the [] thingys (brakets?)) and version of acerhdf that's running. If there's no error, then acerhdf is doing it's job. If there's an error, then it may not be running. If it's not running, it would probably fall back to the bios fan control, which turns on at about 30 degrees (far to quickly imo).


And since some new kernel update, you may find that it stopped working (and fallback will be used). You can find the configuration file here:
/etc/modprobe.d/acerhdf.conf

If it doesn't exist, create one:
```
sudo gedit /etc/modprobe.d/acerhdf.conf
```
(the file will only be created if you safe it using gedit!)
You can put this inside the config file:
```

# fan control for acer aspire one fan
# according to: http://piie.net/files/acerhdf_README.txt
# check status with: dmesg|grep acerhdf
# read temperature with: cat /sys/class/thermal/thermal_zone0/temp
options acerhdf interval=5 fanon=60000 fanoff=55000 kernelmode=1

```
The last line is the only line that should be editted. Fanon is the temperature in degrees x1000 at which the fan will go on. So basicly this file tells the fan to go on at 60 degrees. And fanoff, as it says, says when the fan should be turned off. In this case 55 degrees.

It is strongly advised NOT to make the difference between fanon and fanoff bigger then 5 degrees! And do not make fanon larger then 65 degrees!
I don't know why the temperatures are multiplied by 1000 btw. I hope you'll find this usefull after this long time :)

Source:
[http://ubuntuforums.org/showthread.php?t=1424043](http://ubuntuforums.org/showthread.php?t=1424043)
[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=19702](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=19702)

Credits go to them, not me.

---

