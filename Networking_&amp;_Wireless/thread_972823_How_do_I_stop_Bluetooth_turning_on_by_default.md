---
title: "How do I stop Bluetooth turning on by default?"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by ch_123 on 2008-11-06
Well, the question is pretty much as just as it is in the title. When I had 8.04, bluetooth would only turn on when I asked it (or at least I assumed that was the case - I don't think I've ever had need for Bluetooth in Linux). Now everytime I turn on my laptop, 8.10 turns on Bluetooth automatically which is a grand waste of battery power, and a potential security liability. So, how do I stop it turning on during startup? Machine is a Thinkpad T61 running 8.10 64-bit.

---

### Post by abhver on 2008-11-06
You can install a bluetooth manager called Blueman. it has the option to turn off the bluetooth.

Here is the website link:

[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

Currently the site link seems to be broken. You can download it from Softpedia also:

[http://linux.softpedia.com/get/Utilities/Blueman-30673.shtml](http://linux.softpedia.com/get/Utilities/Blueman-30673.shtml)

---

### Post by BUGabundo on 2008-11-06
> **ch_123 said:**
> So, how do I stop it turning on during startup? 

gksu gedit /etc/defaults/bluetooth

change 
BLUETOOTH_ENABLE=1
to
BLUETOOTH_ENABLE=0

---

### Post by ch_123 on 2008-11-06
> **BUGabundo said:**
> gksu gedit /etc/defaults/bluetooth

change 
BLUETOOTH_ENABLE=1
to
BLUETOOTH_ENABLE=0

There is no such folder under /etc/ called "defaults". And I am able to turn the Bluetooth off, its just that Im trying to prevent it turning on during startup.

---

### Post by blue13130 on 2008-11-06
should be /etc/default/bluetooth

---

### Post by blue13130 on 2008-11-06
To disable the service from starting at boot run this command:
```
sudo update-rc.d -f bluetooth remove
```

To re-enable it to start at boot run this:
```
sudo update-rc.d bluetooth defaults
```

To start it later on run this:
```
sudo /etc/init.d/bluetooth start
```

For more info on update-rc.d:
```
man update-rc.d
```

---

### Post by ch_123 on 2008-11-20
I have tried the methods suggested by blue13130 and BUgabundo and it still turns on at boot... Any more ideas?

---

### Post by cygn on 2008-12-18
I've got the same problem with a thinkpad T42. It always gets enabled during booting. It should only be enabled if it was enabled the last time. As I don't use it I'd be happy if I could just disable it completely.

---

### Post by BUGabundo on 2008-12-19
> **cygn said:**
> It always gets enabled during booting.

that's your BIOS... it has an option that turns it on at boot.

---

### Post by cygn on 2008-12-19
> **BUGabundo said:**
> that's your BIOS... it has an option that turns it on at boot.

I don't have an option for bluetooth in my bios. The bluetooth LED is turned on during ubuntu's boot process.

---

### Post by rhcm123 on 2008-12-19
> **ch_123 said:**
> Well, the question is pretty much as just as it is in the title. When I had 8.04, bluetooth would only turn on when I asked it (or at least I assumed that was the case - I don't think I've ever had need for Bluetooth in Linux). Now everytime I turn on my laptop, 8.10 turns on Bluetooth automatically which is a grand waste of battery power, and a potential security liability. So, how do I stop it turning on during startup? Machine is a Thinkpad T61 running 8.10 64-bit.

go to system -> administration -> services
uncheck bluetooth. This will stop bluetooth as a system service.
you should now reboot and it should (in theory) be off.

---

### Post by aaron.lwe on 2010-01-23
I googled to find this post, though it's a little too long ago ;-)

I have this exact problem now with ubuntu 9.10, is there any solution to this?
There is no /etc/default/bluetooth file, and disable bluetooth service will not stop bluetooth device getting activated.

I don't think this has anything to do with BIOS, as vista will not activate bluetooth device during bootup.

Thanks.

---

### Post by skit on 2010-01-24
Same here. Tried all the previous "solutions".

---

### Post by aaron.lwe on 2010-05-05
run this:
sudo echo "options rfkill master_switch_mode=0" > /etc/modprobe.d/rfkill.conf
this will stop bluetooth being activated during boot.

See: [http://comments.gmane.org/gmane.linu...cpi.devel/1955]("http://comments.gmane.org/gmane.linux.acpi.ibm-acpi.devel/1955")

---

