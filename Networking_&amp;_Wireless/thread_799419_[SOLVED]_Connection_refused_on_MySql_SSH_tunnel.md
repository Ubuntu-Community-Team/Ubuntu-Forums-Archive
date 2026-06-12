---
title: "[SOLVED] Connection refused on MySql SSH tunnel"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by evanb on 2008-05-19
I have 64-bit Ubuntu 7.10 server running as a virtual machine in VMWare Server on a 64-bit Ubuntu 7.10 desktop. On the server VM I have installed MySql and sshd and want to connect to MySql via a tunnel from the desktop. VMWare Server I installed from VMWare's site; all the other bits on the server VM and desktop machine are from Ubuntu packages. ~/.ssh/config contains```
LocalForward 3306 server_VM_name:3306
```When I run this command```
mysql -u root -p -h 127.0.0.1 mysql
```on the client over the tunnel I get this error:```
Lost connection to MySQL server at 'reading initial communication packet', system error: 0
```Simultaneously, on the server VM's console I see```
channel 5: open failed: connect failed: Connection refused
```When I run the same command on the server, mysql successfully starts. This tells me the tunnel is working but mysqld won't accept the connection. /etc/mysql/my.conf contains```
bind-address = 127.0.0.1
```and does not have the skip-networking setting.

I have used ssh tunnels with Linux and Windows many times without much trouble. In fact, I have successfully tunnelled an http connection from the desktop to lighttpd running on the server VM.

Any idea what I'm doing wrong or missing?

---

### Post by evanb on 2008-06-06
> **evanb said:**
> ```
LocalForward 3306 server_VM_name:3306
```It turns out that this was the problem. I failed to fully understand that "server_VM_name" is applied by the server's sshd from THE SERVER's perspective. That is, from the server a connection is made to "server_VM_name". To MySQL this looks like an outside connection, which my configuration does not allow.

The correct forward string is```
LocalForward 3306 127.0.0.1:3306
```This looks like (is, actually) a connection to a local TCP port, which is allowed.

(Notice that using "localhost" instead of "127.0.0.1" won't work due to MySQL's treatment of "localhost" as a request for a Unix socket connection, which can't be made from a tunnel or any remote machine.)

What's funny (in retrospect) is that I (re)discovered this when I looked at a ssh configuration file at work and found that I'd had, and solved, this problem maybe a year ago. D'oh! #-o

---

### Post by dave9191 on 2008-06-23
Thank you so much :D

No one else seems to have solutions or answers and this works like a charm.

---

