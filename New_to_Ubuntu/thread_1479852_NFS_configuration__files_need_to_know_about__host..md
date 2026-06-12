---
title: "NFS configuration  files need to know about  host.allow &amp; host.deny  files ?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by honey_bee on 2010-05-11
Hi,
          I want to configure NSF in my Linux machine.My server IP address is 192.168.1.10 and clients machines start from 192.168.1.20 to 192.168.1.30 .
 
 There is a confusion in my mind about  the files [FONT=Times New Roman] [/FONT]/etc/hosts.allow[FONT=Times New Roman], and [/FONT]/etc/hosts.deny file.I know that [FONT=Times New Roman]: [/FONT]/etc/exports files is the main file to configure NSF server but in which situation we use host.allow and host.deny file ?
 
My [FONT=Times New Roman] [/FONT]/etc/exports file configuration is 
[FONT=Times New Roman][SIZE=3]/home *(rw,sync)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/music *(rw,sync)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]my client machines access the files but for security reasons i know that host.allow and host.deney will be use so what configuration should i write in these two files ?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]thanks in adavance,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]honey[/SIZE][/FONT]

---

### Post by mbzn on 2010-05-11
Try downloading these, alot of reading but worth the time..

[http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf](http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf)

[www.iitk.ac.in/LDP/LDP/nag2/nag2.pdf](www.iitk.ac.in/LDP/LDP/nag2/nag2.pdf)

Hope it helps

Edit: Also try [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by honey_bee on 2010-05-11
thanks for the reply.
well I just want an opinion if I set **hosts.deny** to just this: 
 
```
 
ALL: ALL

```
 
and in host.allow i use the following code
 
```
 
ALL:192.168.1.10/255.255.255.0 EXPECT 192.168.1.11 192.168.1.12 192.168.1.13

```
 
is it a valid command. The description of host.allow  is it should allow all clients expect the clients which have the ip address from range 
 
192.168.11 to 192.168.13 
 
should not access NFS .
 
Is my script ok correct or u think there is a need to add some more thing
 
thanks

---

### Post by louieb on 2010-05-11
I use NFS on my home network - the only file I modified was /etc/exports.  Not even sure what the purpose is of  hosts allow or hosts deny. 

Anyway to set up mine I used.  [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

---

### Post by honey_bee on 2010-05-11
well if some one want to use host.allow and host.deny then what you will do ? I know that if we only use /etc/exports file and add our shares then the clients will access it but for a secure NFS you need  entriey in these two above files. any idea how to configure these two files .....?

---

### Post by mbzn on 2010-05-11
Don't know much about host.deny/allow, but i do know that the deny overrules the allow so 'deny all' might not be the best choice.

---

### Post by gmargo on 2010-05-11
Do you seriously need the "security" of /etc/hosts.{allow,deny}?  Why?  You're on an internal network.

If you really want to restrict NFS so only a select few machines can mount it, just use the /etc/exports file.:
```

[FONT=Times New Roman][SIZE=3]/home 192.168.1.0/24(rw,sync)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/music 192.168.1.0/24(rw,sync)[/SIZE][/FONT]

```Or, more specifically, to limit to just 192.168.1.20 through .30 (I'll only show the /home line):
```

/home 192.168.1.20/30(rw,sync) 192.168.1.24/30(rw,sync) 192.168.1.28/31(rw,sync) 192.168.1.30/32(rw,sync)

```(Just in case you're interested, I used "ipcalc" to translate the ip range to a set of addr/mask formats):
```

$ ipcalc -r 192.168.1.20-192.168.1.30
deaggregate 192.168.1.20 - 192.168.1.30
192.168.1.20/30
192.168.1.24/30
192.168.1.28/31
192.168.1.30/32

```

---

### Post by MrWES on 2010-05-11
I agree. Unless you're forwarding a port from the router, you don't need /etc/hosts.allow or deny.


Bill

---

