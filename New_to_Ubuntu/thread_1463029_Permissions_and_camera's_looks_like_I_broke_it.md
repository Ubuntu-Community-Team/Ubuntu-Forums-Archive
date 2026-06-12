---
title: "Permissions and camera's looks like I broke it"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Hardhat_Harry on 2010-04-26
Well I was doing quite well on this Ubuntu lark until I needed to alter my permissions to allow a Vuze update and it looks like I inadvertently set all permissions to root.

I did the chown root:root /etc/sudoers
             chown 440 /etc/sudoers

to sort it out and managed to fix my scanner but I cannot access my digital camera throught Thunbar filemanager. In the left hand window Digicam is available but when I click on it it responds 

Rejected send message, 1 matched rules; type="method_call", sender=":1.2560" (uid=1000 pid=12967 comm="exo-mount) interface="org.freedesktop.Hal.Device.Volume" member="Mount" error name="(unset)" requested_reply=0 destination="org.freedesktop.Hal" (uid=0 pid=785 comm="hald)).

lsusb returns

Bus 003 Device 004: ID 0733:3350 ViewQuest Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b8:082e Seiko Epson Corp. 0x082e  DX-60x0 MFP scanner
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so the device is on 003/004

I tried  sudo chmod 777 /dev/bus/usb/003/004 to give it read / write / execute but no change and looked for articles to fix it but I can't find anything regarding this.

Can someone help??

Thanks

---

### Post by Hospadar on 2010-04-26
Do you know exactly what command you did that messed up your permissions?  If you really set *everything* wrong, the easiest fix might realistically be a re-install

---

### Post by cariboo on 2010-04-26
In the future when installing programs that need root access use sudo, instead of changing permissions. As Hospadar said, if you screwed up the permissions to badly, and not documented what you changed, it may end up being quicker to re-install. As an experiment I once set all permissions to 777, it took me 3 days to straighten everything out. If you have a seperate home directory, a re-install should take less than an hour.

---

### Post by Hardhat_Harry on 2010-04-26
It was either sudo chown -R hhh:hhh / when in the vuze folder or

sudo chown -R hhh:hhh /vuze

When I did it it returned a long list of changes, I thought at the time that wasn't what I expected.

If I reinstall do I loose all my apps?

---

### Post by durand on 2010-04-26
Yes, but you can back them up. If you installed all of them via apt, you can just save the package list and then reinstall them in the same way. You might want to backup your files and settings as well. Try a live cd!

---

