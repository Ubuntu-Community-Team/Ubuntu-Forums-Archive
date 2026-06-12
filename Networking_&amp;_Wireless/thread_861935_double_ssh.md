---
title: "double ssh"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by ample on 2008-07-17
im trying to double ssh, but i when i try to ssh into the second machine i never get prompted for a password and eventually i have to kill the process. i have X11 forwarding enabled but it doesnt help. also, i don't want to disable passwords on the second machine. anyone know what im doing wrong?

---

### Post by kamaji792 on 2008-07-17
Just a few basics.

Can the two machines see each other on the network?

If you want to ssh into a machine it needs to be running an ssh server like open-ssh.

Do you have a firewall running?

From your comments I guess the above are sorted.  I have never used ssh between Linux boxes; always Windows box connecting to a Linux box running open-ssh.  I do notice that if the Linux box does not have an Internet connection then it does take a long time to display the password prompt.  Possible as long as 45 seconds.

If you are still having problems post some details on your set up.

---

### Post by stitchmysmile93 on 2008-07-17
Make sure you have ssh installed on both machines..

---

### Post by ample on 2008-07-18
both machines have ssh and sshd.  the second machine is on a private network and cannot be ssh'd directly into from home, so i have been trying to ssh into our web server, which can see the second machine, then ssh into the second machine.  maybe theres a better way?

---

### Post by dmizer on 2008-07-18
i do this constantly, but there may be a problem if you want X from the second machine.

what is the command you're using to ssh into the second machine?

---

### Post by ample on 2008-07-18
i dont need X especially.  forwarding x was one of many things ive tried just to get it working.
the commands ive used to log into the second machine are:
 ssh username@comp_name
 ssh -X username@comp_name
 ssh -Y username@comp_name

also tried this to start x on the first machine(kept crashing, can check the error it gives if it might help):
 xinit xterm -- :1

---

### Post by dmizer on 2008-07-18
can you ping "comp_name"?

is your local network dhcp or static?

---

### Post by jimv on 2008-07-18
can you ssh from the webserver to the machine in question when you're sitting at the webserver?

---

### Post by ample on 2008-07-18
yes jimv.
no dmizer, not from home. its dhcp.

i just tried to ping the second machine from the first and it timedout.  so the server cannot see the second machine, but only when i ssh in(i say that because i have ssh'd directly from the server into the second machine while at work)

---

### Post by dmizer on 2008-07-18
on the server, please post the contents of /etc/hosts and /etc/nsswitch.conf

---

### Post by ample on 2008-07-18
hosts file shouldnt matter.  ive tried both the comp_name and its ip address.

nsswitch.conf:
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by ample on 2008-07-25
any suggestions?

---

### Post by dmizer on 2008-07-26
only to look for firewall interference.  you can list firewall rules with the following command:
```
sudo iptables -L
```

---

