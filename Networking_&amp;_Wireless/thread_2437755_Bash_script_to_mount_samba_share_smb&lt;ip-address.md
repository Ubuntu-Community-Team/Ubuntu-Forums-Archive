---
title: "Bash script to mount samba share smb://&lt;ip-address&gt;/shared-folder"
date: 2020-02-28
forum: Networking &amp; Wireless
---

### Post by crabbychicken on 2020-02-28
Hi,

I am running the following bootable usb systems.

usb ubuntu 18.04 live 

or

usb ubuntu 18.04 persistent - created using mkusb

-----

Both boot and I can connect to my shared folder on my router as follows:

Go to my file manager - click other locations - type in smb://192.168.1.1 - click volume1 icon and - voila - my files - NO PROBLEM.

I can do this on both bootable usbs.

Here is my problem...

I want to write a bash script that will run at startup - perform a few tasks and then at the end copy a file to the shared folder signifying the operation was completed successfully - I am running this on headless systems without a monitor - no leds or anything to tell me if the task was performed - hence the file copy to the shared folder on the router.

I have tried this on the live system and it fails to mount:

```
sudo mkdir /media/my_share
```

```
sudo mount -t  cifs //192.168.1.1/volume1 /media/myshare
```

There is no password on the router share

I get the following error - cifs-utils is installed

```
Password for root@//192.168.1.1/volume1:  
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


Any idea what is going wrong? This should be a basic operation?

I am running as root since I am running on a live ubuntu system - with and without persistent.

Big thanks.

---

### Post by Morbius1 on 2020-02-29
Regrettably "Host is down" has two causes: 

** The host is in fact down.

** You are speaking gibberish when you make the initial contact.

Nautilus will connect using the smb1 dialect whereas cifs will use between smb2.1 and smb3. My guess is that the server you are trying to connect to doesn't understand the smb2.1-to-smb3 dialect. 

Try connecting with smb1:
```
sudo mount -t  cifs //192.168.1.1/volume1 /media/myshare -o guest,vers=1.0,sec=ntlm
```

**vers=1.0** = forces cifs to use smb1
**sec=ntlm** = since we use smb1 it would make sense to use the older security mode of ntlm since both of them were concurrent.

---

