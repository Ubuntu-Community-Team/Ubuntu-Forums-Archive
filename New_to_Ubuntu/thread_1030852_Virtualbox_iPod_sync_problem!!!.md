---
title: "Virtualbox iPod sync problem!!!"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-04
Alright, this is what I get for trying to sync my ipod in virtual box. A unresponsive box. Can anyone fix this? I have tried a couple of guides, but none of them worked.[-X


[IMG]http://taylorthomas.weebly.com/uploads/5/0/3/2/503275/screenshot.png[/IMG]

---

### Post by HotShotDJ on 2009-01-04
Why are you trying to mount any device before the OS has finished booting up?

---

### Post by taylor102387 on 2009-01-04
Because, it's the same either way.

---

### Post by HotShotDJ on 2009-01-04
Ok.  I don't have an iPod.  Do these things come with drivers for Windows or is support built into Windows?  In any case, plug in the device, open VirtualBox, but DON'T start a session, just highlight your Windows XP VM and then click Settings.  Click on USB.  Point your mouse to the white box below the phrase "USB Device Filters" and right click then select Add Filter From Device.  Select your iPod from the pop-up list.  Now click OK.  Remove your iPOD from the USB port.  Now start your Windows XP session.  If there are drivers to install for the iPOD, do that first (and probably reboot your Windows VM).  Now, plug in the iPOD.  What happens now?

---

### Post by jimmy the saint on 2009-01-04
Mine is usually greyed out as well, but it still works when I click it.  Do other usb devices work?

---

### Post by sam_delta on 2009-01-04
i had to add a line to /etc/fstab file in order to make my usb work in virtualbox.

are other usb devices working in virtualbox? if not, tell me and ill tell you how to add the line to /etc/fstab

sam

---

### Post by taylor102387 on 2009-01-05
No, no devices work with virtualbox. How do I edit the file, and what do I put?

---

### Post by sam_delta on 2009-01-07
alright, this is what i had to do. please, follow every steps below.

first, go into system>administration>users and groups;
click unlock on the lower right area, and type your password; 
click on managa groups in the right side
search for the group vboxusers, and click on properties
under properties, make sure that both your user AND root are checked
under properties, copy the Group ID number

to make a backup of the fstab file type the follwoing (just in case you make somthing wrong)
```
sudo cp /etc/fstab /etc/fstab.backup
```

ok, with the group id, now we will edit the file, open a terminal and type
```
sudo gedit /etc/fstab
```
a text editor will open, at the end of the file, paste the line that is in the coded square. (read the important note first)
**IMPORTANT NOTE replace the number "1001" with the group id of vboxusers group we obtained in previous steps, the number may vary from computer to computer, in my case, it was 1001, in yours might be diferent.**
```
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

save the file, and reload fstab with th e following command
```
sudo mount -a
```

should work now.

in case you need to restore the fstab to the backup we made, type "sudo mv /etc/fstab.backup /etc/fstab"

tell me how it goes
sam

---

