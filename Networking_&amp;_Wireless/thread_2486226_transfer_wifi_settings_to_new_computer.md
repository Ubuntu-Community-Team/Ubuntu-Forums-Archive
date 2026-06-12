---
title: "transfer wifi settings to new computer"
date: 2023-04-23
forum: Networking &amp; Wireless
---

### Post by matrooswolf on 2023-04-23
Hi,

I just installed a new computer and I travel a lot, so I have lots of wifi's I connect to. Is there an easy way to transfer all my wifi settings (names + passwords) to my new computer? 

Thanks!

---

### Post by chili555 on 2023-04-23
If you are using Network Manager, these are stored in /etc/NetworkManager/system-connections. I suggest that you copy all of the contents to a USB key or similar and then copy them from the USB to the same location on the new computer. Restart NM:

```
sudo systemctl restart NetworkManager
```You should be all set.

---

### Post by matrooswolf on 2023-04-24
Hi,

Thank you!

Only thing I was wondering is that I read somewhere that mac addresses are stored in the wifi connections and that simply copying would not work because of the new computer has a different mac address. I haven't had the opportunity to try it out, so I don't know if it's true...

---

### Post by chili555 on 2023-04-24
The file does not contain MAC addresses; it contains uuids. A universally unique identifier (UUID) is a 128-bit label used for information in computer systems. When generated according to the standard methods, UUIDs are, for practical purposes, unique. 

Here is a redacted example from my machine:

```
[connection]
id=GBR5
[COLOR="#FF0000"]uuid[/COLOR]=1cb51962-1b1e-4753-9985-778b04a52cb2
type=wifi
interface-name=wlp61s0
timestamp=1681133116

[wifi]
mode=infrastructure
ssid=GBR5

[wifi-security]
key-mgmt=sae
psk=xxxxyyyyzzzz

[ipv4]
method=auto

[ipv6]
addr-gen-mode=default
method=auto

[proxy]
```I believe that the uuid may be transfered without any issues. There are, however, two things that need intervention. First, as you see above, my wireless interface is wlp61s0. When you change to a different computer, the interface will almost certainly not be wlp61s0. You will need to list your interfaces and change the system-connections as needed:
```
ip a
```

Second, when you transfer the settings from a USB, you are likely to end up with the wrong permissions. Correct them with:
```
cd /etc/NetworkManager/system-connections
sudo chmod 0600 *
```Check:
```
ls -al
```You should see that the files are readable and writable only by root and owned by root; for example:
```
-rw------- 1 root root  274 Apr 10 09:29 GBR5.nmconnection
```If they are not owned by root, correct them:
```
sudo chown root:root *
```

Please let us know how it goes. The searchers and I will be very interested.

---

### Post by matrooswolf on 2023-04-24
Hi

Thank you.
But how do I open those files? They are binary files and don't open with a text editor, or am I doing something wrong?

I'll copy the files and then try some of the networks I normally go, Friday probably.

---

### Post by chili555 on 2023-04-24
Since they are owned by root, you need elevated privileges, i.e. sudo, to see or change them. Read them with:

```
sudo cat /etc/NetworkManager/system-connections/myrouter.connection
```Make your own text copy:```
sudo cat /etc/NetworkManager/system-connections/myrouter.connection > myrouter.txt
```

Edit with:

```
sudo nano /etc/NetworkManager/system-connections/myrouter.connection
```After making any changes, save (Ctrl+o followed by Enter) and exit (Ctrl+x).

> I'll copy the files and then try some of the networks I normally goThat's another perfectly valid approach. Simply use the copies as a cheat sheet to give you the passwords, etc. Can't miss.

---

### Post by matrooswolf on 2023-04-26
copying the nmconnections just worked. Apparently both computers have the same interface-name

So, all good!

Thanks

---

