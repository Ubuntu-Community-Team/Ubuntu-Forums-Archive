---
title: "Unable to connect via Samba on Win 7 - The network path was not found"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by kissa2001 on 2014-04-29
Solution for this problem: [Unable to connect via Samba on Win 7 - The network path was not found]("http://ubuntuforums.org/showthread.php?t=2117229")
("Error code: 0x80070035 The network path was not found" error message in the Windows 7 machine.)
is to **allow an incoming connection in your Ubuntu firewall.**

For example, I use *ufw* firewall, so I executed the command:
```
sudo ufw allow from 192.168.0.100
```where 192.168.0.100 is the IP address of the Windows 7 machine.

Also, check that /etc/samba/smb.conf file has the "browseable = yes" **uncommented**. For example:
```

[nimbus]
    comment = Linux Mint
    path = /home/nimbus
    writeable = yes
    browseable = yes
    valid users = nimbus
```

(I could not send this reply to the original thread because I got the ***Sorry! This thread is closed!*** message.)

---

### Post by tfrue on 2014-04-30
Have you added nimbus to smbpasswd file? If not, try and run:
```
sudo smdpasswd -a nimbus
```
and restart the smbd and nmbd service by running:
```
sudo service smbd restart;sudo service nmbd restart
```
Also, you might want to try and use a different directory instead of /home/nimbus, unless you are trying to set up usershares, but I would either make a new directory like: /share/nimbus/, or I would make a new directory under /media like: /media/nimbus. Also, make sure that you change the owner and group to nimbus and give it the proper permissions to allow read write execute on the directory. 

Type:
```
sudo chown nimbus.nimbus /share/nimbus (Or /media/nimbus)
and
sudo chmod 775 /share/nimbus (Or /media/nimbus and you can refine the permissions if you want to finesse)

```

Good luck,
Chris

If that doesn't work, I would make the share completely open and start from the bottom and work our way up.

So I would remove valid users, and add guest = ok, read only= no. And re-run the restart code again.

---

### Post by Dane_Jorgensen on 2014-04-30
When I ran into this, I added the user to smbpasswd, but didn't restart the service.  Restarting the service fixed it for me.

---

### Post by tfrue on 2014-05-01
If the problem is solved, please mark it as solved. Thanks!

---

