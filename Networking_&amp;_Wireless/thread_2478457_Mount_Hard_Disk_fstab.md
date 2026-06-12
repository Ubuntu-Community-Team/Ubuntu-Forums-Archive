---
title: "Mount Hard Disk fstab"
date: 2022-08-27
forum: Networking &amp; Wireless
---

### Post by eqypjd53mq on 2022-08-27
Hello everybody

I have upgraded my Xbunutu from 20.4 to 22.4.

I have got a hard disk plugged on internet provider box.
Before on the fstab file, I had this command :

```
//192.168.1.1/usb1    /media/Commun    cifs _netdev,rw,iocharset=utf8,users,uid=1000,nofail,sec=none,vers=1.0 0
```

The mount was fine, without issue. Since I have upgraded my OS, I do not access to my hard disk. This one is graphically visible on the desktop, but I can not mount it.
[IMG]https://www.cjoint.com/doc/22_08/LHBj3w7Dfrx_Capture-d%E2%80%99%C3%A9cran-2022-08-27-11-54-45.png[/IMG]
[IMG]https://www.cjoint.com/c/LHBj3w7Dfrx[/IMG]

On started I have this issue :

```
IFS: VFS: \\192.168.1.1 fail to connect to IPC (src=-6)[COLOR=#000000]cifs: VFS: cifs_mount failed w/retourn code = -6
[FAILED] Failed to mount /media/Commun. [/COLOR]See systemctl stats "media-Commun\\x4OUSB3.mount" for details
```

Fichier[COLOR=#333333][FONT=Verdana] /etc/samba/[/FONT][/COLOR]smb.conf

```
client min protocol = NT1server min protocol = NT1
#facultatif 
ntlm auth = ntlmv1-permitted

[public]
  comment = public anonymous access
  path = livebox/USB1
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes

```

[COLOR=#333333][FONT=Verdana]I have tried with that



Thank you for your help![/FONT][/COLOR]

---

### Post by TheFu on 2022-08-27
I cannot help much, except to say that CIFS v1 is terribly non-secure and that connecting storage to a router that is also connected to the internet is usually making all those files available to the world due to security failures in the router software.  Pretty much every router that supports this has been cracked, usually 3+ times.  Sure, it seems like a very useful feature, but ... I am not making this up.  [https://threatpost.com/millions-routers-exposed-bug-usb-module-kcodes-netusb/177506/](https://threatpost.com/millions-routers-exposed-bug-usb-module-kcodes-netusb/177506/)  Issues with USB storage were found over a decade ago and every few years new issues are found and made public.

If the router has been patched, which should happen at least quarterly, if not more often, then CIFS v1 would have been moved to a more current version that isn't 15+ yrs old.
You can run an nmap scan against the smb server (your router?) to see which protocols are supported. Here's the command:
```
sudo nmap --script smb-protocols 192.168.1.1 
```

When I run it:
```
$ sudo nmap --script smb-protocols 172.22.22.6
Starting Nmap 7.80 ( https://nmap.org ) at 2022-08-27 10:50 EDT
Nmap scan report for hadar (172.22.22.6)
Host is up (0.00036s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 0C:9D:92:zz:yy:xx (Asustek Computer)

Host script results:
| smb-protocols: 
|   dialects: 
|     2.10
|     3.00
|     3.02
|_    3.11

```
So the minimal protocol supported by mine is 2.10. If I had any choice, I'd use 3.11.  Newer is more secure and faster.  MSFT has been busy the last decade improving it, though I'd still never use CIFS over the internet.

BTW, if you use the fstab, then the mount will appear as a local drive inside any file manager.  Using smb:// in the URL uses a completely different method from Gnome. Not very intuitive that these are unrelated, but they are. Pick one.  The fstab provides more control and is more stable, IME.

Some things are just bad ideas.

OTOH, perhaps the intent is to make all the files with nefarious payloads available? 

The smb v1 is the real issue. Sorry I cannot really help.

---

### Post by eqypjd53mq on 2022-08-28
Please see that

```
sudo nmap --script smb-protocols 192.168.1.1
Starting Nmap 7.80 ( https://nmap.org ) at 2022-08-28 07:46 CEST
Nmap scan report for livebox.home (192.168.1.1)
Host is up (0.00095s latency).
Not shown: 990 filtered ports
PORT      STATE  SERVICE
53/tcp    open   domain
80/tcp    open   http
113/tcp   closed ident
135/tcp   closed msrpc
139/tcp   open   netbios-ssn
443/tcp   open   https
445/tcp   open   microsoft-ds
631/tcp   open   ipp
49152/tcp open   unknown
49153/tcp open   unknown
MAC Address: ***** (Sagemcom Broadband SAS)

Host script results:
| smb-protocols: 
|   dialects: 
|_    NT LM 0.12 (SMBv1) [dangerous, but default]

Nmap done: 1 IP address (1 host up) scanned in 5.08 seconds


```

Can I enable SMBv1 on my OS anyway?

Thank you

---

