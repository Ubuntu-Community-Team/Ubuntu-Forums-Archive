---
title: "Wireless connection with WPA in bash startup script"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by Daylight81 on 2006-12-12
Hello there,

Some time ago i found a way (tnx to a post on this forum =D>)to get a wireless connection with WPA on a Dell Inspiron 6400 with ubuntu dapper (and intel pro wireless 3945).

This was accomplished in 4 steps:
First executing the following command in the terminal (a code appears afterwards):
1. wpa_passphrase ssid psk (eg: wpa_passphrase ssidname password)

Copy the code into a config file:
2. sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf

Execute the following command:
3. sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf

Finally, in order to get an IP-address, execute the following command:
4. sudo dhclient

Unfortunately, it is really annoying to do steps 3 and 4 manually in the terminal each time i want a networkconnection. In order to get things going a bit more automatically, i thought putting these commands into a bash file and make a startup script out of it. I did this the following way: 

1. Made bashfile "networkscript":

```
#!/bin/bash
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf&
sudo dhclient
echo "Network started"
```

btw: the first command in this bash-file ends with "&" ..this should put the process (which is started by the command) into the background as a daemon.

2. Made bashfile executable:

```
sudo chmod +x netwerkscript
```


3. Check whether bash-file works:

```
./netwerkscript

```
btw: it worked...so far so good (i think)

4. Placed bashfile in startup:


```
cd /etc/init.d
sudo update-rc.d netwerkscript defaults
```



:arrow: When i finally reboot, nothing seems to happen: if i start firefox, no connection is found and i have to establish the connection manually again via the terminal. 

My question is now: What is the reason why no connection is made with the network? Is it because the sudo-commands in the bash script require root-permission (but i thought that root itself accomplished the startup?:roll:) Has anyone got experience with this? :confused: 

Any tips pointing in the right direction are really appreciated!! :wink:

---

