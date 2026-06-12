---
title: "No sensors found!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by gshockxc on 2008-12-14
I installed the 'sensors-applet' and everything seemed to work fine, but it says that there are no sensors found. Huh???  This is the same hardware that I had my XP system running on, and I used MotherBoard Monitor 5 (MBM 5), and that worked fine.  So I'm not sure why this isn't.  Anyone have any suggestions?  

Thanks.

-gshockxc

---

### Post by zzHanks on 2008-12-14
It looks like you have not installed them
Try this
```
sudo apt-get install lm-sensors hddtemp libsensors3
```

Hope this helps

---

### Post by jerome1232 on 2008-12-14
You may also need to run 'sensors-detect'
```
sudo sensors-detect
```

---

### Post by mkvnmtr on 2008-12-14
Depending on your hardware you will need to be watching your terminal during this process. On mine it took a couple of minutes and asked me several times to give a yes or no.

---

### Post by gshockxc on 2008-12-30
> **jerome1232 said:**
> You may also need to run 'sensors-detect'
```
sudo sensors-detect
```

I tried that in a terminal window, and it gave me a "command not found".

Thanks for the help.  If you have other suggestions, keep them coming.

Regards,

---

### Post by gshockxc on 2008-12-30
> **zzHanks said:**
> It looks like you have not installed them
Try this
```
sudo apt-get install lm-sensors hddtemp libsensors3
```

Hope this helps

I ran the code you gave and this is the output I got:

```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Thanks for the help.

-gshockxc

---

### Post by jerome1232 on 2008-12-30
That means there's another package manager working, just try it again in a few minutes.

---

### Post by gshockxc on 2008-12-30
> **jerome1232 said:**
> That means there's another package manager working, just try it again in a few minutes.

Thanks.  It seemed to work the second time.  I removed the applet from the panel, and re-added it, and it still says "No Sensors found!"  I'm not sure what else to do.  Do I have to restart something from the terminal window, or log off, and log back in?  Or do I need a complete restart?

Thanks for all the help.

-gshockxc

---

### Post by jerome1232 on 2008-12-30
did you run 'sudo sensors-detect' after installing those other packages? If so then yes you might need to restart.

---

### Post by gshockxc on 2008-12-30
> **jerome1232 said:**
> did you run 'sudo sensors-detect' after installing those other packages? If so then yes you might need to restart.

Yes, I did that.  And it configured the hddtemp program with no errors.  So I assumed that everything worked okay.  I'll restart the machine and see what happens.

Thanks, 

-gshockxc

---

### Post by cariboo on 2008-12-30
When you run sensors-detect at the end of the process it should tell you what modules need to be installed in order for the sensors-applet to work, what I do is use modprobe to install the modules, then there is no need to reboot for example:

```
sudo modprobe i2c-nforce2
```

Jim

---

### Post by gshockxc on 2008-12-30
> **cariboo907 said:**
> When you run sensors-detect at the end of the process it should tell you what modules need to be installed in order for the sensors-applet to work, what I do is use modprobe to install the modules, then there is no need to reboot for example:

```
sudo modprobe i2c-nforce2
```

Jim

OK, I ran that code, and it just went back to the terminal prompt.  No errors.  So I ran sudo sensors-detect, and it went through a much more involved detection and added some code to /etc/modules.  Then I re-ran the 
```

sudo apt-get install lm-sensors hddtemp libsensors3

```

And it said that everything installed was already the latest version.  But the applet on the panel still shows, "No sensors found"  I'm going to restart again and see what happens.

Thanks for your help.

-gshockxc

---

### Post by whiteman on 2011-01-08
Didnt work for me either. I have a dell tower xps 400. It said something about wrng chip or somesuch.

---

### Post by sammiev on 2011-01-08
> **gshockxc said:**
> OK, I ran that code, and it just went back to the terminal prompt.  No errors.  So I ran sudo sensors-detect, and it went through a much more involved detection and added some code to /etc/modules.  Then I re-ran the 
```

sudo apt-get install lm-sensors hddtemp libsensors3

```

And it said that everything installed was already the latest version.  But the applet on the panel still shows, "No sensors found"  I'm going to restart again and see what happens.

Thanks for your help.

-gshockxc

Even after applying the code from post #11 I had to reboot for the applet to show the correct info and not "No sensors found". GL :) 

Thanks for the great thread folks! :)

---

