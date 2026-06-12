---
title: "Automatically load a CIFS/NFS/Samba share on boot when using wifi"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by niko123456 on 2014-01-07
Struggled with this. So here's a solution.

First determine which terminal command will successfully mount your drive. In my case (a USB drive plugged into my router using the Readyshare function..). It was important for me to add the sec=ntlm field for the command to work. 

```
mount -t cifs //192.168.0.1/USB_storage /home/nicholas/NAS -o username=admin,password=password,**sec=ntlm**,rw
```



1. Open a terminal and..
```
iwconfig
```

Take note of which wireless extension is in use. In my case it is 'eth1'. Also take note of the exact spelling of the ESSID (the network you connect to). 

2. Create a new file called 'mount' in the /etc/network/if-up.d/ directory. 
```
sudo gedit /etc/network/if-up.d/mount
```

3. Copy and paste the following script.. You need to replace <interface> with a new value, like 'eth1', and <ESSID> with the name of the wifi network you connect to. You need to paste in the terminal command that successfully mounts your drive. Remove all characters '<' and '>'

```
#!/bin/bash
if [ "$IFACE" = "<interface>" ]
then
    if iwconfig|grep -c <ESSID>
    then
        sleep 10s
	<mount -t cifs //192.168.0.1/USB_storage /home/nicholas/NAS -o username=admin,password=password,sec=ntlm,rw>
    fi
fi

```

4. Create a new file called 'umount' in the /etc/network/if-down.d/ directory. 
```
sudo gedit /etc/network/if-down.d/umount
```

5. Copy and paste the following script into /etc/network/if-down.d/umount. You might need to replace 'eth1'. You will need to change the location of where you are mounting your drive. 

```
#!/bin/bash
if [ "$IFACE" = "eth1" ]
then
    if cat /etc/mtab|grep -c /home/nicholas/NAS
    then
        umount -t cifs /home/nicholas/NAS
    fi
fi

```

6. Reboot.. With luck it will automatically connect when your wireless comes online and detach when your wireless goes offline.

---

### Post by TheFu on 2014-01-07
Might I suggest **autofs**? 
Also, using wifi for remote storage access is asking for trouble. Wired ethernet on very stable connections is needed for almost all remote file systems. Wifi may appear to be stable to humans, but it is not.

---

### Post by niko123456 on 2014-01-07
> **TheFu said:**
> Might I suggest **autofs**? 
Also, using wifi for remote storage access is asking for trouble. Wired ethernet on very stable connections is needed for almost all remote file systems. Wifi may appear to be stable to humans, but it is not.

I considered looking into autofs. I don't know much about it. 

One issue I had when trying to figure all this out was that /etc/fstab was not the solution - this is loaded before a wireless connection is established and doesn't work. 

My file system isn't critical. I don't want wires all over the house. I used a wifi solution.

---

