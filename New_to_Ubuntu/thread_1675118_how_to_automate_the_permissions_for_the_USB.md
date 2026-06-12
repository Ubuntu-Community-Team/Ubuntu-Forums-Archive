---
title: "how to automate the permissions for the USB"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by naveenarjuna on 2011-01-25
Hi,

I have a USB to serial port converter. When i connect USB side to my PC in syslog i am able to "converter now attached to ttyUSB0". If i use command ls -l /dev/ttyUSB0 it displaying as below
crw-rw---- 1 root dialout 188, 0 2011-01-26 11:26 /dev/ttyUSB0

I am changing the mode using command sudo chmod 666 /dev/ttyUSB0
 Now if i use ls -l /dev/ttyUSB0
its giving 
crw-rw-rw- 1 root dialout 188, 0 2011-01-26 11:26 /dev/ttyUSB0


Now if i unplug that usb and i again if i am connect it. Again i have to do all the procedure what ever i did before to change the permissions. So is there any way to automate it.

Thanks

---

### Post by amsterdamharu on 2011-01-25
Doesn't anyone of the dialout group have rw right? 

If you want everyone to have access I think you can write a udev rule (I have to look into that).

Maybe there is a way to set a policy in /usr/share/polkit-1/actions/ but I haven't found anything.

I've checked:
```
cd /usr/share/polkit-1/actions/
grep dial *.policy
```

But found no policy related to dialout user being used.

---

### Post by amsterdamharu on 2011-01-25
Could you post how your usb to serial is identified?

To do that plug in your device and run the following commands:
(from) [https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)
```
dmesg
```In my case it shows something like:
```
[ 6300.944699] sd 6:0:0:0: [[COLOR=Red]sdb[/COLOR]] Attached SCSI removable disk
``````
udevadm info --attribute-walk --name /dev/[COLOR=Red]sdb[/COLOR]
```I use
ATTRS{manufacturer}=="Generic "
ATTRS{product}=="USB Storage"
ATTRS{serial}=="000000009451"

So I use the following command (you can rename mounthiddenfat but leave the 91- and .rules part):
```
sudo nano /etc/udev/rules.d/91-mounthiddenfat.rules
```I put in the following content:
```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{manufacturer}=="Generic ", ATTRS{product}=="USB Storage", ATTRS{serial}=="000000009451", ENV{isusb}="mount", RUN+="/usr/local/bin/[COLOR=Red]mounthiddenfat[/COLOR].sh"
```Press control + x then y and enter
Again you can rename mounthiddenfat but change it in the following commands as well:
Now create the bash
```
sudo nano /usr/local/bin/mounthiddenfat.sh
```Copy and paste the following (this has my mount command):
```
#!/bin/sh
if [ "$isusb" = "mount" ]; then
    sleep 5; #(give the usb some time to initialize this is 5 seconds)
    mount -t vfat /dev/sdb1 /mnt # (replace this with your specific command)
fi
```and now make it bootable
```
sudo chmod +x /usr/local/bin/mounthiddenfat.sh
```

---

