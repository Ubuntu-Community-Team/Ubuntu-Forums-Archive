---
title: "Grub Password &amp; WPA Wireless help"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-01-11
Hi,

I recently added a password to Grub. 

Unfortunately, it appear to kill my wireless internet (w/WPA encryption) signal,, which normally loads at startup & works flawlessly.

It's as if the internet connection starts fine, then is interrupted by the grub login procedure, then I have no wireless connection once the Grub password in typed & processed:( 

Adding the grub password also "cleared out" my wireless WLAN0 network interface configs.


An ideas how to get a Grub password to not interfere with the encrypted wireless connection?

Running Ubuntu Edgy.

Thanks!

---

### Post by x64Jimbo on 2007-01-11
Ummmmm.... I think you may be mistaking GRUB for something else. GRUB is the Grand Unified Boot Loader and is long gone from any sort of memory by the time your OS has booted up, so it could not be what has messed with your WPA settings. Are you maybe referring to GDM?

---

### Post by DapperMe17 on 2007-01-11
Jimbo,

My broadband connection initiates with startup.

I installed a password to the boot loader (Ubuntu/Recovery mode/Memtest). I then rebooted & entered the password at the boot prompt. Ubuntu then continued to load normally. My internet connection was then gone. I checked my network config file (WPA), which was reset & therefor I could not connect. 

Should adding a boot password (by updateing the config) have a changing effect on my network config file?

---

### Post by x64Jimbo on 2007-01-11
Absolutely not. I believe your problem lies elsewhere. The GRUB password should only affect whether or not your system CAN boot, but will have no effect on the system at all once the password has been entered. It was probably a bizarre coincidence.

---

### Post by DapperMe17 on 2007-01-11
Jimbo,


When I start the PC...
1) My wireless USB initiates/starts/lights-on first
2) Grub starts and asks for password
3) Ubuntu loads

4) I must always "restart" the wireless network via terminal, in order to regain the wireless connection (lost because of Grub password interuption?!?):( 

***After rechecking the network config files, there are no mysterious changes taking place, as I thought prior.


Just the wireless connection being interrupted...is there a way to delay the internet connection until after the Grub password is entered???

---

### Post by spd106 on 2007-01-11
What happens when you boot without the wireless USB, then plug it in once logged in?

---

### Post by DapperMe17 on 2007-01-11
Same results as before...have to restart network in terminal to get back broadband connect.

I started PC with USB adapter unpluffed, then plugged it in after the Grub password was processed.


?

---

### Post by x64Jimbo on 2007-01-13
You guys don't seem to understand how GRUB works. It's a bootloader. A tiny piece of software that resides in your master boot record. It is NOT part of the operating system, and as such, it is impossible that it is affecting your OS's ability to properly detect hardware. My guess is that you got an update from a repository that changed your netcard driver, and then you set up the GRUB password, rebooted, and then it doesn't work anymore. If you really want to see for yourself, disable the GRUB password and reboot. I bet it won't help.

---

### Post by DapperMe17 on 2007-01-15
Jimbo, 

Yes, the internet connection DOES work after disabling the grub password. 

And the same internet connection WILL NOT when the grub password is enabled. I have to manually restart the network connection via terminal, in order to establish the connection.


Tell me this...when using a broadband connection, isn't the connection established immediately after startup (lights on the adapter do blink)?


If so, just tell me if ther is a setting in Ubuntu that allows the user to manually establish internet connection AFTER the Grub process.

Thanks

---

### Post by DapperMe17 on 2007-01-15
Jimbo,

I've posted a Grub config file....

My internet connection is broken & needs a network restart under the first entry.  
My internet connection connects just fine if I select recovery mode (no network restart needed)

Could the kernel line config for the default maybe need to be changed to contain something from the recovery mode???




## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
		password --md5 xxxx		
savedefault
quiet
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
		password --md5 xxxx
quiet
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by x64Jimbo on 2007-01-18
So you're telling me that when you take the password off your GRUB file, the network card works fine? But when you re-enable the password, it doesn't? This is too weird. Have you tried using a different method of managing your net device? Network Manager is a good program, and I've found that it makes most devices behave even when they don't want to.

---

### Post by DapperMe17 on 2007-01-20
Yes, Jimbo, you're correct.

That is why I was wondering if the "default" grub config file should be modified, to look & behave as the "recovery" mode file does?

Maybe there is a conflict issue with the WPA encryption method.

---

### Post by x64Jimbo on 2007-01-21
You don't want your default boot to be the same as recovery mode, I can tell you that. Why are you using a GRUB password? Can't you do the same with a BIOS password? And that would prevent others from even booting a LiveCD to access your files.

---

