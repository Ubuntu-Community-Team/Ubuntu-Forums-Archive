---
title: "ssh timed out connection"
date: 2020-01-29
forum: Networking &amp; Wireless
---

### Post by giax11 on 2020-01-29
hi guys i have a problem with a remote ssh connection: until 3 days ago still working but now no and give me the error fro fixed i try to add in the etc/ssh/sshd_config  
ClientAliveInterval 600 
TCPKeepAlive yes 
ClientAliveCountMax 10 
and restart the server after this still not working and i try to purge and reinstall openssh-server and openssh-client  so i modify again the file etc/ssh/sshd_config whit  
ClientAliveInterval 600 
TCPKeepAlive yes 
ClientAliveCountMax 10 
and still not working so i was think was a problem about the firewall e i try 
sudo ufw allow ssh 
sudo ufw allow port/tcp 
but still not working someone know what i can try?? thanks alot

---

### Post by TheFu on 2020-01-29
Troubleshooting ssh Connections [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by kevdog on 2020-01-29
Why dont you try to connect with ssh -vvv ......   and post the output.  A lot of times this verbose output will give a hint what the problem might be.

---

### Post by giax11 on 2020-01-30
OpenSSH_8.0p1 Ubuntu-6build1, OpenSSL 1.1.1c  28 May 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname **.**.**.** is address
debug2: ssh_connect_direct
debug1: Connecting to **.**.**.** [**.**.**.**] port 5562.
debug1: connect to address **.**.**.** port 5562: Connection timed out
ssh: connect to host **.**.**.** port 5562: Connection timed out


this is the output 
i change here my public ip **.**.**.** only for the forum

---

### Post by TheFu on 2020-01-30
Add another 'v' .... ssh -vvvv ....

---

### Post by giax11 on 2020-01-30
same mate!

---

