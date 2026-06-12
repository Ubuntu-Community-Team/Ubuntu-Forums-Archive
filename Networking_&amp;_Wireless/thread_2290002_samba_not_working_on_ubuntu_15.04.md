---
title: "samba not working on ubuntu 15.04"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by offir on 2015-08-08
i have ubuntu 15.04 install

i install samba from [COLOR="#0000FF"]ubuntu software center
[/COLOR]
and when i type samba in terminal 
i get some kind of error
and not the gui 

```
[2015/08/08 18:36:16.250371,  0] ../lib/util/debug.c:597(reopen_logs_internal)
  Unable to open new log file '/var/log/samba/log.%m': Permission denied
[2015/08/08 18:36:16.251118,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.13-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013

```

i try ```
sudo samba
``` 
and type my password 
then Nothing happend

---

### Post by TheFu on 2015-08-08
Huh?  Samba is a service. There isn't any GUI that I'm aware. Your expectations are wrong.

Perhaps reviewing the file sharing chapter in the Ubuntu Server Guide would help?
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

---

### Post by nlee2 on 2015-08-08
> **offir said:**
> i have ubuntu 15.04 install


and when i type samba in terminal 
i get some kind of error
and not the gui 



Have you tried gadmin-samba?

---

### Post by offir on 2015-08-08
> Huh? Samba is a service. There isn't any GUI that I'm aware. Your expectations are wrong.
Already used it several times in previous installations
Supposed to be graphical interface



> Have you tried gadmin-samba? 
no
samba Always worked Up to now

I want to know first why Samba graphical interface does not work

---

### Post by bab1 on 2015-08-09
> **offir said:**
> Already used it several times in previous installations
Supposed to be graphical interface
...
I want to know first why Samba graphical interface does not work
What your attachment shows is ***system-config-samba***.  Which is a python application that uses a  GUI for creating,
modifying, and deleting samba shares and users.  It is NOT Samba itself.

My guess is that you are not calling the application correctly The command [FONT=Courier New][SIZE=3]samba [/SIZE][/FONT] is for this```
 /usr/sbin/samba
```...that is the binary for the *_Samba Server to provide AD and SMB/CIFS services to clients_*, not ***system-config-samba***.

It's always helpful to correctly identify what it is you are having problems with.  This application is not really needed for the Samba to function.  For a simple Samba File Server installation you just need to define the shares at the bottom of the default /etc/samba/smb.conf file.



If you really feel you need ***system-config-samba***,  I would remove what you have installed with this command```
sudo apt-get purge system-config-samba
```...and follow up with ```
sudo apt-get autoremove
```
Trey and take note of what text goes by on the screen as it relates to both  ***python*** and ***system-config-samba***.

Then I would install ***system-config-samba*** in the same manner using this command```
sudo apt-get install system-config-samba
```

---

### Post by offir on 2015-08-09
As I wrote in a previous post
I installed samba a few times before 

Each time the installation was exactly the same thing
Go to [COLOR="#0000FF"]ubuntu software center[/COLOR] Choose samba and install
And nothing more

Later
I ran the software's graphical interface through
[COLOR="#0000FF"]applications menu[/COLOR]  -----> [COLOR="#FF0000"]system tools[/COLOR]  ----> [COLOR="#FF8C00"]administration[/COLOR] ----> [COLOR="#800080"]samba[/COLOR] 

Always the same

The only reason now
I wrote samba in terminal is To see what error message appears



> What your attachment shows is system-config-samba. Which is a python application that uses a GUI for creating,
modifying, and deleting samba shares and users. It is NOT Samba itself.

My guess is that you are not calling the application correctly The command samba is for this


```
 /usr/sbin/samba
```

...that is the binary for the Samba Server to provide AD and SMB/CIFS services to clients, not system-config-samba.

It's always helpful to correctly identify what it is you are having problems with. This application is not really needed for the Samba to function. For a simple Samba File Server installation you just need to define the shares at the bottom of the default /etc/samba/smb.conf file.


So what is the command to run the graphical interface of Samba
From the terminal ?

---

### Post by Morbius1 on 2015-08-09
>  So what is the command to run the graphical interface of Samba
The command to run system-config-samba is:
```
gksu system-config-samba
```
And that is what the system-config-samba.desktop file is set to. Unfortunately that will produce an error message since someone fell asleep at the wheel somewhere.

A workaround until someone volunteers to fix this ( Samba is the red-haired stepchild of Linux ) is to issue the following command:
```
sudo touch /etc/libuser.conf
```
Then run:
```
gksu system-config-samba
```

---

### Post by offir on 2015-08-09
Thank you
Now it works

It never happened in previous installations
What is different now ?

---

### Post by revmarkp on 2016-05-06
Thanks Moribus1 what you said Aug 2015 still applies as of Apr 2016 and Xubuntu 16.04

---

### Post by raydar on 2016-05-12
Workaround needed, and works. on Ubuntu Gnome 16.04. Thanks!

---

### Post by boozzz on 2016-05-13
I'm getting the following output when I run
```
sudo touch /etc/libuser.conf
```
on ubuntu 16.04 with kernel 4.4.0-22-generic on x86 64-bit. Doesn't work for me :(.

```
(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-zHtOmSSzko: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-ClyzV7x1ED: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-BvBYm2X8kh: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-8vKFCqSvI3: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-irmrXJFjeU: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-f64fyae3W8: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-vzCYVe6IBH: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-7OrsYp2g2n: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht


(gksu:3936): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Failed to connect to socket /tmp/dbus-PcaOA2rQp9: Verbindungsaufbau abgelehnt
GConf-Fehler: D-BUS-Hintergrunddienst läuft nicht
```

---

