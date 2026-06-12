---
title: "How to configure wine to work with LAN"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by oyankee on 2008-11-13
Hi,
I need to use an application which communicates with server on another PC in local network. It is a client program used to work with database on that PC. It works fine but I need to connect it to the server and when I click to search for it, I see only my mounted filesystems and not network(where I can always add the computer from workgroup, from booted windows).
Does anybody knows what to do?
Thanks for replies.

Computer I need to connect to is under smb://VSVSMV/comp

---

### Post by superprash2003 on 2008-11-13
what may work is, going to the terminal and type winecfg .. wine configurator should open now, now go to the DRIVES section.. and add a drive.. say z : under the path , give /home/username/networkshare .. now before doing this.. go to the terminal and type sudo mount smb://x.x.x.x/sharename /home/username/networkshare

---

### Post by oyankee on 2008-11-13
Thanks, but I cant mount it this way.

```
 sudo mount smb://VSVSMV/S-12-01 /home/onovotny/server_janosikova/

[sudo] password for onovotny: 
mount: chybný typ SS, chybný p&#345;epína&#269;, chybný superblok na smb://VSVSMV/S-12-01,
       chybí kódová stránka nebo pomocný program nebo jiná chyba
       (pro v&#283;t&#353;inou souborových systému (nap&#345;. nfs, cifs) budete
       pot&#345;ebovat pomocný program /sbin/mount.<TYP>)
       V*jistých p&#345;ípadech lze najít pot&#345;ebné informace v*systémovém
       protokolu*&#8211; zkuste nap&#345;íklad &#8222;dmesg | tail&#8220;

```
Tried to translate:
```
Bad type SS, bad switch, bad superblock on  smb://VSVSMV/S-12-01
Missing  code page or helping program or another error.
and something like I will need  helping program /sbin/mount <TYPE>
```


I will try it tomorrow. It is shuted down for now. Thank you.

---

### Post by superprash2003 on 2008-11-14
sorry i gave you the wrong syntax.. try this
smbmount //VSVSMV/S-12-01 /home/onovotny/server_janosikova/

---

### Post by oyankee on 2008-11-18
No success.

```
onovotny@it-onovotny:~$ sudo smbmount //VSVSMV/S-12-01 /home/onovotny/server_janosikova/
[sudo] password for onovotny: 
mount error: could not find target server. TCP name VSVSMV/S-12-01 not found
No ip address specified and hostname not found

```

But Hostname is right. And I can see it in places/network. Will be problem with autentification with domain in which is the computer in. But I can not autent. through Likewise-open. problem with ports. It is here:
[http://ubuntuforums.org/showthread.php?t=981807]("http://ubuntuforums.org/showthread.php?t=981807")
Thank you

---

