---
title: "Going mad trying to mount old NAS"
date: 2019-07-05
forum: Networking &amp; Wireless
---

### Post by jajayesisgoodjaja on 2019-07-05
I was recently given an old NAS (Omninas KD20). This model was discontinued in 2015 and I have spent the last three days trying to mount it in a Linux container to no avail. I am very close to just chucking it in the bin!

Here's what I have tried:

I've created a directory call test on the NAS which is public. I can connect to this in Windows (however I had to re-enable SMBv1). I can connect to the share in Linux with smbclient and also with Gigolo. I cannot seem to mount the share using the mount command.


```
$ sudo mount -t cifs //192.168.1.56/test/ /home/cifs/ -o username=john,password=john
mount error(112): Host is down
```

I thought maybe it's the SMBv1 issue? dmesg contains an error mentioning dialect level, so let's try that.

```
$ sudo mount -t cifs //192.168.1.56/test/ /home/cifs/ -o username=john,password=john,vers=1.0
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

There is no error after this command in dmesg. 
Very weird because smbclient works!

```
$ sudo smbclient -L 192.168.1.56/test -U john
Enter john's password:
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]

        Sharename       Type      Comment
        ---------       ----      -------
        test            Disk
        iTunes          Disk      Default_iTunes_share
        disk            Disk      Default_share
        IPC$            IPC       IPC Service (OMNINAS Series)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]

        Server               Comment
        ---------            -------
        LAPTOP-UMPSESSF
        OMNINAS-434369       OMNINAS Series
        RTORRENT             Samba 4.2.14-Debian

        Workgroup            Master
        ---------            -------
        WORKGROUP            OMNINAS-434369
```

I can also access the share using Gigolo on another laptop. I simply type in the IP address, check 'Windows Share' and then it can connect. I can then open it in a terminal and see the files.[IMG]https://i.imgur.com/RW5qrt4.jpg[/IMG]

This is incredibly frustrating because I can't do the one thing I need to do with this :( Does anyone have any ideas?!

---

### Post by jajayesisgoodjaja on 2019-07-05
I have also tried to mount with the sec=ntlm option to no avail:

```

$ sudo mount -t cifs //192.168.1.56/test/ /home/cifs/ -o username=john,password=john,vers=1.0,sec=ntlm
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I have also added the following to /etc/samba/smb.conf:
```

    # Allow access to SMB1 shares on other servers
    client ipc min protocol = NT1
    client min protocol = NT1

    # Allow access to shares on other servers ONLY via SMB1
    client ipc max protocol = NT1
    client max protocol = NT1

    # Allow access to shares on this Samba instance via SMB1
    server min protocol = NT1

    # Allow access to shares on this Samba instance ONLY via SMB1
    server max protocol = NT1

```

However I still receive 'Operation not permitted'.

---

### Post by LwIh%*7 on 2019-07-05
Hi,

First things first could you try if possible these threads:

[https://ubuntuforums.org/showthread.php?t=2325264](https://ubuntuforums.org/showthread.php?t=2325264)
[https://ubuntuforums.org/showthread.php?t=2391756](https://ubuntuforums.org/showthread.php?t=2391756)
[https://ubuntuforums.org/showthread.php?t=2375117](https://ubuntuforums.org/showthread.php?t=2375117)
[https://ubuntuforums.org/showthread.php?t=2352299](https://ubuntuforums.org/showthread.php?t=2352299)

All these seem to be related to the NAS setup, could you please try these out if and when you have time available?

---

### Post by slickymaster on 2019-07-05
Thread moved to **Networking & Wireless** for a better fit

---

### Post by jajayesisgoodjaja on 2019-07-05
> **ImpWarfare said:**
> Hi,

First things first could you try if possible these threads:

[https://ubuntuforums.org/showthread.php?t=2325264](https://ubuntuforums.org/showthread.php?t=2325264)
[https://ubuntuforums.org/showthread.php?t=2391756](https://ubuntuforums.org/showthread.php?t=2391756)
[https://ubuntuforums.org/showthread.php?t=2375117](https://ubuntuforums.org/showthread.php?t=2375117)
[https://ubuntuforums.org/showthread.php?t=2352299](https://ubuntuforums.org/showthread.php?t=2352299)

All these seem to be related to the NAS setup, could you please try these out if and when you have time available?

Thankyou for these suggestions! I'm going to try them one by one.


[https://ubuntuforums.org/showthread.php?t=2325264](https://ubuntuforums.org/showthread.php?t=2325264)
I tried supplying a uid to no avail :( 
smbtree -d3 didn't contain any errors either.

[https://ubuntuforums.org/showthread.php?t=2391756](https://ubuntuforums.org/showthread.php?t=2391756)
I tried vers=1.0,sec=ntlm and also sec=none and nounix. All combinations resulted in 'Operation not permitted".

[https://ubuntuforums.org/showthread.php?t=2375117](https://ubuntuforums.org/showthread.php?t=2375117) 
This guy's issue was solved by adding vers=1.0 which I already have :(

[https://ubuntuforums.org/showthread.php?t=2352299](https://ubuntuforums.org/showthread.php?t=2352299)
Unfortunately this issue was resolved by simply adding sudo, which I am already using :(

---

### Post by jajayesisgoodjaja on 2019-07-05
I nmaped the NAS to make sure the issue isn't something on that side of the equation. I didn't see anything obvious but here's the output just in case:
```

root@ubuntu-test:~# nmap --top-ports 10000 -A 192.168.1.56Starting Nmap 7.70 ( https://nmap.org ) at 2019-07-05 16:55 UTC
Nmap scan report for 192.168.1.56
Host is up (0.00024s latency).
Not shown: 8301 closed ports
PORT    STATE SERVICE     VERSION
80/tcp  open  http        Apache httpd 2.0.54 ((Unix) PHP/5.2.8)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.0.54 (Unix) PHP/5.2.8
|_http-title: OMNINAS
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.0.32 (workgroup: WORKGROUP)
515/tcp open  printer
548/tcp open  afp         Netatalk 3.0 (name: OMNINAS-434369; protocol 3.3)
| afp-serverinfo: 
|   Server Flags: 
|     Flags hex: 0x8f79
|     Super Client: true
|     UUIDs: true
|     UTF8 Server Name: true
|     Open Directory: true
|     Reconnect: false
|     Server Notifications: true
|     TCP/IP: true
|     Server Signature: true
|     Server Messages: true
|     Password Saving Prohibited: false
|     Password Changing: false
|     Copy File: true
|   Server Name: OMNINAS-434369
|   Machine Type: Netatalk3.0
|   AFP Versions: AFP2.2, AFPX03, AFP3.1, AFP3.2, AFP3.3
|   UAMs: DHX2, DHCAST128
|   Server Signature: 354d0dcc13edd0a0794f20b34c06d122
|   Network Addresses: 
|     192.168.1.56
|_  UTF8 Server Name: OMNINAS-434369
MAC Address: 80:EE:73:43:43:69 (Shuttle)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.19 - 2.6.36
Network Distance: 1 hop
Service Info: OS: Unix

Host script results:
|_clock-skew: mean: 2h00m00s, deviation: 2h49m43s, median: 0s
|_nbstat: NetBIOS name: OMNINAS-434369, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.32)
|   Computer name: OMNINAS-434369
|   NetBIOS computer name: 
|   Domain name: localdomain
|   FQDN: OMNINAS-434369.localdomain
|_  System time: 2019-07-05T12:56:16-04:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_smb2-time: Protocol negotiation failed (SMB2)

TRACEROUTE
HOP RTT     ADDRESS
1   0.25 ms 192.168.1.56

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 59.95 seconds

```

---

### Post by Autodave on 2019-07-05
I wonder if this was not shut down while it was being run on Windows.  If the machine that was using it did not have fast boot disabled, that might be the cause.  Can you connect it to a Win machine (with Fast Boot disabled and then shut it down and see if it is then released?

---

### Post by jajayesisgoodjaja on 2019-07-05
Interesting idea! I opened the web browser for the NAS on a Windows machine and clicked shutdown, I heard a beep from the NAS and it turned off and was no longer accessible. I turned it back on with the power button and verified it was back on by opening the web admin page. I then tried to mount it again and got the same error "Operation not permitted" :(


Is that what you meant by connect from a Windows machine and shut it down? I'm not sure how to check if FastBoot is enabled.

Is there a way to find the exact error here? Operation not permitted isn't very illuminating.

---

### Post by jajayesisgoodjaja on 2019-07-05
I think I have figured it out. I'm using a Ubuntu LXC container on a Proxmox host. When I use an Ubuntu VM, the NAS mounts fine. No idea how to solve it so I'm just going to switch to the VM.

---

