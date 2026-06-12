---
title: "Need Some Help Please"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by TheManOfSeveralHats on 2007-08-10
Hello.
I had to install Ndiswrapper to get my wireless card to work, everything worked fine. A while later I had to do a complete computer restart. I reinstalled ubuntu Fiesty Fawn and partioned the whole disk, because I was running out of diskspace so when I partioned the whole disk I had 14.6 out of the 20gb on my laptop instead of having almost nothing.
I needed to reinstall Ndiswrapper and the drivers. After I installed ndiswrapper and went to install the drivers by installing the .inf file it said the file was installed. I did the command Ndiswrapper -l to get a list of installed drivers and it said they were invalid drivers.
I then went to check the folder inwhich the drivers are installed.
In /etc/ndiswrapper there was an empty folder called NET8180, which is the name of the .inf file. When I tried to remove this file using ndiswrapper -r net8180, it said.
Coudln't delete /etc/ndiswrapper/net8180: inappropiate ioctl for device.


I think if I can remove this, and then re install it, it should work.

How can I remove it?


Thanks

---

### Post by noob12 on 2007-08-10
Try 
```

sudo ndiswrapper -e net8180

```

May have to capitalize the driver name to match case exactly.

---

### Post by TheManOfSeveralHats on 2007-08-10
It Removed the driver, but it came back almost immediatly afterword.

---

### Post by noob12 on 2007-08-10
What do you mean by "it came back"?  Where did it "come back"?

---

### Post by TheManOfSeveralHats on 2007-08-10
When I removed the Driver, from /etc/ndiswrapper, it was gone but then it came back in that directory. /etc/ndiswrapper/net8180.

---

### Post by noob12 on 2007-08-10
The following will take the interface down and remove the module from the running kernel before trying to remove the windows driver. 
```

sudo /sbin/ifdown wlan0
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r net8180

```

---

### Post by TheManOfSeveralHats on 2007-08-10
I still get

Couldn't Delte /etc/ndiswrapper/net8180: inappropiate ioctl for device

---

### Post by noob12 on 2007-08-10
This sounds like something is still using the device.  If you have NetworkManager active, make sure wireless is disabled and try the sequence above again.  If you still have trouble, you should temporarily remove or comment out the ndiswrapper line in /etc/modules.  Then reboot.  Then do the driver removal, cleaning up whatever you want.  After that you can put ndiswrapper back into /etc/modules.

---

### Post by TheManOfSeveralHats on 2007-08-11
Ndiswrapper is not in Modules.

---

### Post by kevdog on 2007-08-11
You can put it back in with the following:

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by noob12 on 2007-08-13
Hat man: I'm still not sure what you are typing when you get these error messages and why the windows driver would keep getting reinstalled on its own.  Your responses are too terse for me to use to provide a lot of help, and it isn't clear what you actually followed from my instructions.

I'm  pretty sure the ndiswrapper does not get loaded by default so if isn't in /etc/modules, it shouldn't be getting loaded at boot.

I haven't seen behavior like this before and I don't know an explanation for the driver "coming back" on its own.  If you didn't reboot, then maybe it was reloaded as a result of event notifications bringing the interface back up.  Try just fully stopping networking and then unloading and removing the interface.
```

sudo /etc/init.d/networking stop
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r net8180

```
Otherwise, I'm out of ideas.  Good luck.

---

