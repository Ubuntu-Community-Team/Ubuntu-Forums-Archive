---
title: "Ubuntu 18.04, HP ProBook 450 G2, WiFi connected, but no internet"
date: 2020-03-18
forum: Networking &amp; Wireless
---

### Post by mkrsteska on 2020-03-18
Hello, 

I have been using Ubuntu for almost a year. Yesterday out of nowhere I lost WiFi connection. I tried restarting my laptop but it got in 'Emergency mode'. 

Then, I reinstalled Ubuntu 18.04. The WiFi was working until I shut down my laptop the first time after the new installation. Now, the WiFi is connected, but there is no internet connection. 

I am uploading the output of the wireless-info script. 

What can I do to fix the issue? 

Thank you!

---

### Post by chili555 on 2020-03-18
Your resolv.conf file is faulty. Let's fix it:

```
sudo rm /etc/resolv.conf
ln -s /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```
Reboot and let us hear the result. Do you connect and reach the internet?

---

### Post by mkrsteska on 2020-03-18
Thank you for your reply. 

I ran the commands above and rebooted my laptop. 

On startup I got a notification 'System error detected'. This happens every time I reboot, since I reinstalled Ubuntu. 

I got WiFi connection, but it loaded some websites partially, some not at all. There is a question mark icon, instead of the WiFi icon in the top right corner. 

Do you have any other suggestion?

---

### Post by chili555 on 2020-03-18
> 
On startup I got a notification 'System error detected'. This happens every time I reboot, since I reinstalled Ubuntu.
I see nothing in your wireless_info that suggests that the error is, in any way, related to wireless. When the notification appears, isn't there a drop-down that you click to get further information? What does it report?

What do these report?

```
cat /var/log/syslog | grep -i warn
cat /var/log/syslog | grep -i error
```If the outputs are lengthy, say more than 15 lines, post the result here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by mkrsteska on 2020-03-18
Hello, 

There is no drop-down on the notification. There are only two options, 'Cancel' and 'Report a problem'. 

Here are the outputs from the commands:

- cat /var/log/syslog | grep -i warn
[https://paste.ubuntu.com/p/cZ4MThpTgh/](https://paste.ubuntu.com/p/cZ4MThpTgh/)


- cat /var/log/syslog | grep -i error
[https://paste.ubuntu.com/p/W9CBFW3yYT/](https://paste.ubuntu.com/p/W9CBFW3yYT/)

Thanks!

---

### Post by chili555 on 2020-03-18
You have many things wrong here, mostly unrelated to wireless or DNS. Unfortunately, most of them are also outside my limited experience.

Here are some examples:> 
ERROR:model_type_store_service_impl.cc(79)] Device Info datatype error was encountered: ModelTypeStore backend initialization failed
I haven't any idea what this is; nor this:> 
 #033[31m[15:56:09.600570 WARNING]#033[0m zeitgeist-daemon.vala:334: Failed to execute child process “zeitgeist-datahub” (No such file or directory)
Nor this:> 
ERROR:database.cc(1584)] History sqlite error 5, errno 0: database is locked, sql: COMMIT
This is what we fixed above:> Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.confThis is alarming:> 
WARNING: systemd-networkd is not running, output will be incomplete.
I suggest that you post a question here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

If it were me, I'd reinstall systemd, Network Manager and sqlite and see if the errors are reduced. If not, I'd just reinstall.

Of course, others over on General Help may have a better suggestion.

---

### Post by mkrsteska on 2020-03-19
Thank you very much for your help!

---

