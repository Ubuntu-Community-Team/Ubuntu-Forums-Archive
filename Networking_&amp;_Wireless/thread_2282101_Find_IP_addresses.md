---
title: "Find IP addresses"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by John F on 2015-06-11
Is there a program that will list the IP addresses and basic information of all computers on the local network? (similar to "Fing" for Android).


John F

---

### Post by SeijiSensei on 2015-06-11
Try [nmap]("http://nmap.org/").  It's in the repositories.

```
nmap -sP 10.10.10.0/24
```

will ping each address seriatim and report which machines are up and their hostnames if reverse DNS resolution is set up on the network.

```
sudo nmap -sT 10.10.10.0/24
```
will attempt to connect to each machine's TCP ports and identify which are open.  
```

PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
143/tcp  open  imap
445/tcp  open  microsoft-ds
873/tcp  open  rsync
993/tcp  open  imaps
995/tcp  open  pop3s
1002/tcp open  windows-icfw
2049/tcp open  nfs
3306/tcp open  mysql
3551/tcp open  apcupsd

```
Notice that you have to be root to run this type of scan; you can do a ping scan as a ordinary user.

There are many other scans available; use "man nmap" or read the documentation linked above.

---

### Post by John F on 2015-06-11
Many thanks - that is a great deal more than what I was looking for but reading up and experimenting promises to be interesting.

---

### Post by SeijiSensei on 2015-06-12
In one of the Matrix films, Trinity uses nmap to hack into a computer!

---

