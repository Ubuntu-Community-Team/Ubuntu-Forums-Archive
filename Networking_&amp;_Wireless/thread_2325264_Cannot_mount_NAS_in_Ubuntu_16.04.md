---
title: "Cannot mount NAS in Ubuntu 16.04"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by wazamoo on 2016-05-20
Ok, I have never posted in a forum before (you can find almost everything you need from searching), but I can not find a solution for this. I am new at using Ubuntu. Currently running 16.04 wired to a ASUS RT-AC68P router. Everything runs great, but I can not mount / access my NAS attached (USB) to the router. I can mount it on my two macbookpros. I can see the NAS in the Files (GUI), but when I try to access one of the files, it will not accept my created username and password.
I have also tried to mount the NAS through the Terminal. I've tried manually:
```
sudo mount -t cifs -o username=tribble //rt-ac68p/hal /media/Hal/
```
This results is error:
```
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


```
I have also tried to mount the NAS using fstab entry:
```
//rt-ac68p/iStore /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0
```
This results in the same above error. The contents in the /var/log/syslog are the same as well:
```
May 20 15:11:45 Tribble kernel: [16367.531919] CIFS VFS: Error connecting to socket. Aborting operation.
May 20 15:11:45 Tribble kernel: [16367.532059] CIFS VFS: cifs_mount failed w/return code = -115

```
I have been working on this for days. I've tried creating different users on the router for access to the drive and tried using the router ip address instead of the name (193.168.1.1 vs rt-ac68p, it does not like that). Have any other suggestions on trying to mount this drive? Any help is much appreciated.

---

### Post by bab1 on 2016-05-20
> **wazamoo said:**
> Ok, I have never posted in a forum before (you can find almost everything you need from searching), but I can not find a solution for this. I am new at using Ununtu. Currently running 16.04 wired to a ASUS RT-AC68P router. Everything runs great, but I can not mount / access my NAS attached (USB) to the router. I can mount it on my two macbookpros. I can see the NAS in the Files (GUI), but when I try to access one of the files, it will not accept my created username and password.
I think you need to look at the errors while using the debug switch.  Post the output of this command```
smbtree -d3 

```
Also post this command in a separate set of code blocks```
dpkg -l cifs-utils
```

It appears that you are only using the Ubuntu Samba package as a client to the Samba server that is in the ASUS RT-AC68P.  Most likely this server is not as recent as the Ubuntu Samba packages.  It may be as early as Samba v2 whereas the Ubuntu Samba package is v 4.3.9.  We should be able to see that with the debug information you post

---

### Post by wazamoo on 2016-05-21
Thank you for the reply.
> 
[COLOR=#000000]i think you need to look at the errors while using the debug switch. Post the output of this command[/COLOR][COLOR=#000000]Code:
smbtree -d3[/COLOR]

The output was:
```
tribble@Tribble:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp2s0 ip=192.168.1.178 bcast=192.168.1.255 netmask=255.255.255.0
Enter tribble's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
    \\TRIBBLE                Tribble server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name TRIBBLE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TRIBBLE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TRIBBLE<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
        \\TRIBBLE\IPC$               IPC Service (Tribble server (Samba, Ubuntu))
        \\TRIBBLE\print$             Printer Drivers
    \\HAL                    Hal
resolve_lmhosts: Attempting lmhosts lookup for name HAL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HAL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name HAL<0x20>
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
        \\HAL\IPC$               IPC Service (Hal)
        \\HAL\Users              iStore's Users in LaCie 4big Quadra
        \\HAL\TV Shows           iStore's TV Shows in LaCie 4big Quadra
        \\HAL\Transfer from old laptop    iStore's Transfer from old laptop in LaCie 4big Quadra
        \\HAL\Testing            iStore's Testing in LaCie 4big Quadra
        \\HAL\Stephen's Biking Video    iStore's Stephen's Biking Video in LaCie 4big Quadra
        \\HAL\Stephen's Back-Up    iStore's Stephen's Back-Up in LaCie 4big Quadra
        \\HAL\Shared             iStore's Shared in LaCie 4big Quadra
        \\HAL\Pictures           iStore's Pictures in LaCie 4big Quadra
        \\HAL\Partial transfer from old laptop    iStore's Partial transfer from old laptop in LaCie 4big Quadra
        \\HAL\Movies             iStore's Movies in LaCie 4big Quadra
        \\HAL\Mini Desktop       iStore's Mini Desktop in LaCie 4big Quadra
        \\HAL\iTunes             iStore's iTunes in LaCie 4big Quadra
        \\HAL\Back-Ups           iStore's Back-Ups in LaCie 4big Quadra
        \\HAL\Accident           iStore's Accident in LaCie 4big Quadra

```> 
[COLOR=#000000]Also post this command in a separate set of code blocks[/COLOR][COLOR=#000000]Code:
dpkg -l cifs-utils[/COLOR]


```
tribble@Tribble:~$ dpkg -l cifs-utils
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  cifs-utils     2:6.4-1ubunt amd64        Common Internet File System utili

```

---

### Post by wazamoo on 2016-05-21
Ok, that log led me to research the line:
> [COLOR=#000000][FONT=Ubuntu Mono]Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'[/FONT][/COLOR]
I found [https://discourse.osmc.tv/t/cant-reach-my-smb-shares-after-the-last-osmc-update/15628/41](https://discourse.osmc.tv/t/cant-reach-my-smb-shares-after-the-last-osmc-update/15628/41). What it did was add two lines to the /etc/smb/smb.conf file. It adds:
```

[COLOR=#04090F][FONT=Source Code Pro]client use spnego = no
client NTLMv2 auth = no
[/FONT][/COLOR]
```
I tried this, which now makes it possible for me to access the NAS through the GUI. But I can still not mount the drive through CLI (I want it to be mounted on start up automatically by adding to the fstab). I ran the same command you wanted (smbtree -d3):
```
tribble@Tribble:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface enp2s0 ip=192.168.1.178 bcast=192.168.1.255 netmask=255.255.255.0
Enter tribble's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to 192.168.1.1 at port 445
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
    \\TRIBBLE                Tribble server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name TRIBBLE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TRIBBLE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TRIBBLE<0x20>
Connecting to 127.0.1.1 at port 445
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
        \\TRIBBLE\IPC$               IPC Service (Tribble server (Samba, Ubuntu))
        \\TRIBBLE\print$             Printer Drivers
    \\HAL                    Hal
resolve_lmhosts: Attempting lmhosts lookup for name HAL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HAL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name HAL<0x20>
Connecting to 192.168.1.1 at port 445
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
        \\HAL\IPC$               IPC Service (Hal)
        \\HAL\Users              iStore's Users in LaCie 4big Quadra
        \\HAL\TV Shows           iStore's TV Shows in LaCie 4big Quadra
        \\HAL\Transfer from old laptop    iStore's Transfer from old laptop in LaCie 4big Quadra
        \\HAL\Testing            iStore's Testing in LaCie 4big Quadra
        \\HAL\Stephen's Biking Video    iStore's Stephen's Biking Video in LaCie 4big Quadra
        \\HAL\Stephen's Back-Up    iStore's Stephen's Back-Up in LaCie 4big Quadra
        \\HAL\Shared             iStore's Shared in LaCie 4big Quadra
        \\HAL\Pictures           iStore's Pictures in LaCie 4big Quadra
        \\HAL\Partial transfer from old laptop    iStore's Partial transfer from old laptop in LaCie 4big Quadra
        \\HAL\Movies             iStore's Movies in LaCie 4big Quadra
        \\HAL\Mini Desktop       iStore's Mini Desktop in LaCie 4big Quadra
        \\HAL\iTunes             iStore's iTunes in LaCie 4big Quadra
        \\HAL\Back-Ups           iStore's Back-Ups in LaCie 4big Quadra
        \\HAL\Accident           iStore's Accident in LaCie 4big Quadra

```
This now changes the line from what it was before. I am still looking for where to go from here, but I want to keep you updated.

---

### Post by bab1 on 2016-05-21
What you have done so far is correct.  The ASUS router uses Samba v2 so you have had to disable the latest security method on the client to access the NAS shared files.

Show me the fstab line you are trying to use.  Also list the NETBIOS name of that ASUS router Samba server.  Is it HAL?

---

### Post by wazamoo on 2016-05-21
The line I added to the fstab is:
```
//rt-ac68p/Hal /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0
```
I'm not sure about the "NETBIOS," I'll try looking up what that is. I believe you are talking about the name of the share? I'm not 100% which it is. I'm thinking either Hal or iStore. Those are both names it has. Here is a screenshot of the ASUS router Samba setup page.

---

### Post by bab1 on 2016-05-21
> **wazamoo said:**
> The line I added to the fstab is:
```
//rt-ac68p/Hal /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0
```
I'm not sure about the "NETBIOS," I'll try looking up what that is. I believe you are talking about the name of the share? I'm not 100% which it is. I'm thinking either Hal or iStore. Those are both names it has. Here is a screenshot of the ASUS router Samba setup page.
The NETBIOS name is the name assigned to the computer.  It predates hostnames and DNS naming.  It is part of the "SMB resource" naming.  To call the SMB service (the share) you use this format ```
//NETBIOS_NAME/SHARE_NAME
```
For example I have a Samba server named MAUI with a share named Music.  I call the share with this ```
//MAUI/MUSIC
```...or //maui/music as Samba uses case insensitive names.

The only NETBIOS names I see are TRIBBLE and HAL.  Which one are you looking for.  FWIW, you can also use the IP address of file server.

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> The only NETBIOS names I see are TRIBBLE and HAL.  Which one are you looking for.  FWIW, you can also use the IP address of file server.
I am wanting to connect to HAL. I tried using the IP address in the fstab (thought it would be more direct), but it gives me an error.
fstab new line:
```
//192.168.1.1/Hal /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0
```
error in terminal:
```

tribble@Tribble:~$ sudo mount -a
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by bab1 on 2016-05-21
Does the directory on Tribble (/media/Hal) exist?  What do you get from this command```
ls -l /media
```

[COLOR="#0000CD"]Edit: How about posting the entire fstab?[/COLOR]

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> Does the directory on Tribble (/media/Hal) exist?  What do you get from this command```
ls -l /media
```

[COLOR=#0000CD]Edit: How about posting the entire fstab?[/COLOR]
```
tribble@Tribble:~$ ls -l /media
total 8
drwxrwxrwx  2 root root    4096 May 10 20:15 Hal
drwxr-x---+ 2 root tribble 4096 May  2 19:13 tribble

```
Here is the entire fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=ca5e6a99-9aa6-4031-b445-c5be32eeebdb /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=211a4b12-bbbf-4388-9ae9-0d2b494edade /boot           ext4    defaults        0       2
# /hdd was on /dev/sdb6 during installation
UUID=e63ac8fb-f2d0-40a6-9c99-0e85199475ca /hdd            ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=ef395444-9762-42af-8da6-0955631d6a59 /home           ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=bab139ab-ef6b-4a69-af0a-93277e488805 /var            ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=cff00210-a67c-4c0f-9aed-dc22d91f637e none            swap    sw              0       0
//RT-AC68P/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0

```

---

### Post by bab1 on 2016-05-21
This ```
//192.168.1.1/Hal /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0
```... is not what is in the fstab file.  The fstab shows this```

//RT-AC68P/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,iocharset=utf8,sec=ntlm 0 0

```

The command ```
sudo mount -a 
```would use *//RT-AC68P/Hal/ *instead of *//192.168.1.1/Hal *.

For testing purposes maybe you should do the mount from the command line with this```

sudo mount -t cifs //192.168.1.1/Hal /media/Hal -o defaults
```

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> 
For testing purposes maybe you should do the mount from the command line with this```

sudo mount -t cifs //192.168.1.1/Hal /media/Hal -o defaults
```

Sorry for the confusion with the fstab. I've been trying different mixtures of things to see if anything makes a difference. I tried the above code in the terminal and I get the output:
```
tribble@Tribble:~$ sudo mount -t cifs //192.168.1.1/Hal /media/Hal -o defaults
[sudo] password for tribble: 
Password for root@//192.168.1.1/Hal:  *********
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by bab1 on 2016-05-21
Let's take a different approach here.  Post the output of this```
smbclient -L 192.168.1.1 
```Run this as a mortal user (a humans account) please.

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> Let's take a different approach here.  Post the output of this```
smbclient -L 192.168.1.1 
```Run this as a mortal user (a humans account) please.
Output of above code:
```
tribble@Tribble:~$ smbclient -L 192.168.1.1
WARNING: The "syslog" option is deprecated
Enter tribble's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.33]


    Sharename       Type      Comment
    ---------       ----      -------
    Accident        Disk      iStore's Accident in LaCie 4big Quadra
    Back-Ups        Disk      iStore's Back-Ups in LaCie 4big Quadra
    iTunes          Disk      iStore's iTunes in LaCie 4big Quadra
    Mini Desktop    Disk      iStore's Mini Desktop in LaCie 4big Quadra
    Movies          Disk      iStore's Movies in LaCie 4big Quadra
    Partial transfer from old laptop Disk      iStore's Partial transfer from old laptop in LaCie 4big Quadra
    Pictures        Disk      iStore's Pictures in LaCie 4big Quadra
    Shared          Disk      iStore's Shared in LaCie 4big Quadra
    Stephen's Back-Up Disk      iStore's Stephen's Back-Up in LaCie 4big Quadra
    Stephen's Biking Video Disk      iStore's Stephen's Biking Video in LaCie 4big Quadra
    Testing         Disk      iStore's Testing in LaCie 4big Quadra
    Transfer from old laptop Disk      iStore's Transfer from old laptop in LaCie 4big Quadra
    TV Shows        Disk      iStore's TV Shows in LaCie 4big Quadra
    Users           Disk      iStore's Users in LaCie 4big Quadra
    IPC$            IPC       IPC Service (Hal)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.33]


    Server               Comment
    ---------            -------
    HAL                  Hal
    TRIBBLE              Tribble server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            HAL
tribble@Tribble:~$ 

```

---

### Post by bab1 on 2016-05-21
> **wazamoo said:**
> Output of above code:
```
tribble@Tribble:~$ smbclient -L 192.168.1.1
WARNING: The "syslog" option is deprecated
Enter tribble's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.33]


    Sharename       Type      Comment
    ---------       ----      -------
    [COLOR="#FF0000"]Accident[/COLOR]        Disk      iStore's Accident in LaCie 4big Quadra
   [COLOR="#FF0000"] Back-Ups [/COLOR]       Disk      iStore's Back-Ups in LaCie 4big Quadra
   [COLOR="#FF0000"] iTunes[/COLOR]          Disk      iStore's iTunes in LaCie 4big Quadra
    [COLOR="#FF0000"]Mini Desktop[/COLOR]    Disk      iStore's Mini Desktop in LaCie 4big Quadra
    [COLOR="#FF0000"]Movies[/COLOR]          Disk      iStore's Movies in LaCie 4big Quadra
    Partial transfer from old laptop Disk      iStore's Partial transfer from old laptop in LaCie 4big Quadra
    Pictures        Disk      iStore's Pictures in LaCie 4big Quadra
    Shared          Disk      iStore's Shared in LaCie 4big Quadra
    Stephen's Back-Up Disk      iStore's Stephen's Back-Up in LaCie 4big Quadra
    Stephen's Biking Video Disk      iStore's Stephen's Biking Video in LaCie 4big Quadra
    Testing         Disk      iStore's Testing in LaCie 4big Quadra
    Transfer from old laptop Disk      iStore's Transfer from old laptop in LaCie 4big Quadra
    TV Shows        Disk      iStore's TV Shows in LaCie 4big Quadra
    Users           Disk      iStore's Users in LaCie 4big Quadra
    IPC$            IPC       IPC Service (Hal)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.33]

    Server               Comment
    ---------            -------
    HAL                  Hal
    TRIBBLE              Tribble server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            HAL
tribble@Tribble:~$ 

```
I don't see any sharename of Hal (see the names in red and below in that column).  Let's mount the share Movies instead with this command```
sudo mount -t cifs //192.168.1.1/Movies /media/Hal -o defaults
```It should mount it to the local directory of /media/Hal.  We are just testing here.  If it works then we know the answer to the problem (wrong share name).  To unmount the share you can use this command```
sudo umount /media/Hal
```

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> I don't see any sharename of Hal (see the names in red and below in that column).  Let's mount the share Movies instead with this command```
sudo mount -t cifs //192.168.1.1/Movies /media/Hal -o defaults
```It should mount it to the local directory of /media/Hal.  We are just testing here.  If it works then we know the answer to the problem (wrong share name).  To unmount the share you can use this command```
sudo umount /media/Hal
```
Ok, this is getting really close, I'm getting excited! The first code did not work (as you will see), so I tried a few different ways (changing the username from root). That one mounted!
```

tribble@Tribble:~$ sudo mount -t cifs //192.168.1.1/Movies /media/Hal -o defaults
Password for root@//192.168.1.1/Movies:  *********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
tribble@Tribble:~$ sudo mount -t cifs -o username=tribble //192.168.1.1/Movies /media/Hal
Password for tribble@//192.168.1.1/Movies:  *********
tribble@Tribble:~$ 

```
[ATTACH=CONFIG]269211[/ATTACH]
So, now I'm guessing that I should put everything on the NAS into a single directory (if I want to share everything there with the users). Then use that directory as the mount.

---

### Post by wazamoo on 2016-05-21
Hmmm..... I do not have any write permissions with that.

---

### Post by bab1 on 2016-05-21
> **wazamoo said:**
> Hmmm..... I do not have any write permissions with that.
Yiu can use the edit function to add additional thoughts.  The management (mods) don't like us spamming ourselves.  ;-)

First off you should never use root for anything but administration of the system.  Many bad things happen when you don't know what is really going on.  We can deal with the permissions so that the mortal users can have the access you want.

If you don't mind all users to have access to the entire file system that is shared you only need one share.  The users have to know what each sub-directory holds.  If you have information that you do not want others to see then you need to share different directory (not a sub-directory of the first share).  Think of it as a path you are walking on.  You create 2 directories.  One for your private information and the other for "public" (i.e. everyone) sharing.

So now that we know the system works, you need to think of how you want to lay out the shares.  Then we mount them.  Do you have multiple mortal users logging in to the computer.  If so then the mount via fstab is not really a good idea.  On the other hand, why is it you don't want to just browse to the shares.  Do you use Libre Office with this data?

---

### Post by wazamoo on 2016-05-21
> **bab1 said:**
> 
Yiu can use the edit function to add additional thoughts.  The management (mods) don't like us spamming ourselves.  ;-)

Oops....sorry. Like I said, I'm new posting in forums. (I have not figured out the multi-quote thing too...) I figured out what I did wrong with the multi quote.
> **bab1 said:**
> 
So now that we know the system works, you need to think of how you want to lay out the shares.  Then we mount them.  Do you have multiple mortal users logging in to the computer.  If so then the mount via fstab is not really a good idea.  On the other hand, why is it you don't want to just browse to the shares.  Do you use Libre Office with this data?
I am the only user on this computer. Home use, only approved adults using, and only one login. I may open up some files with Libre Office, but it is mostly just my multimedia files (music, tv shows, movies, etc...). I want to access in my home from any computer. I had this before, but I wanted to make the switch to Ubuntu.

Add on:
I figured out how to add my write permissions now too:
```
tribble@Tribble:~$ sudo mount -t cifs -o username=tribble,uid=tribble //192.168.1.1/Movies /media/Hal
Password for tribble@//192.168.1.1/Movies:  *********
tribble@Tribble:~$
```

---

### Post by bab1 on 2016-05-22
> **wazamoo said:**
> Oops....sorry. Like I said, I'm new posting in forums. (I have not figured out the multi-quote thing too...) I figured out what I did wrong with the multi quote.

I am the only user on this computer. Home use, only approved adults using, and only one login. I may open up some files with Libre Office, but it is mostly just my multimedia files (music, tv shows, movies, etc...). I want to access in my home from any computer. I had this before, but I wanted to make the switch to Ubuntu.

Add on:
I figured out how to add my write permissions now too:
```
tribble@Tribble:~$ sudo mount -t cifs -o username=tribble,uid=tribble //192.168.1.1/Movies /media/Hal
Password for tribble@//192.168.1.1/Movies:  *********
tribble@Tribble:~$
```
The option (-o) username tells Samba the username (your loging) the uid should be a numerical id of the user NOT your username.  You can see your uid by using this command```
getent passwd
```My guess is that it is ```
uid=1000
```Use the number.  The rest of the options can be seen using this command```
man mount.cifs
```
In fact most commands and some applications have man pages.  The syntax is always```
man <command>
```
As you are going to use Libre Office (LO), add the ***nobrl*** option.  This will take care of some LO errors.

Since there is only one username (with multiple humans) and you trust them then I'd just share the entire disk and mount that and /media/Hal or make a new mount point named /media/nas.  You will have to create the share on HAL and then we can mount it.

[COLOR="#0000CD"]Edit: After we get all the mount options set we can translate the command to a line in the *_fstab_* file[/COLOR]

---

### Post by wazamoo on 2016-06-05
Ok, sorry for the long delay, life happens. After reading the entire man for mount.cifs and doing more searches online I made this addition to my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=ca5e6a99-9aa6-4031-b445-c5be32eeebdb /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=211a4b12-bbbf-4388-9ae9-0d2b494edade /boot           ext4    defaults        0       2
# /hdd was on /dev/sdb6 during installation
UUID=e63ac8fb-f2d0-40a6-9c99-0e85199475ca /hdd            ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=ef395444-9762-42af-8da6-0955631d6a59 /home           ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=bab139ab-ef6b-4a69-af0a-93277e488805 /var            ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=cff00210-a67c-4c0f-9aed-dc22d91f637e none            swap    sw              0       0
//192.168.1.1/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,rw,uid=1000,iocharset=utf8,sec=ntlm,nobrl,forceuid 0 0

```
This seems to be working for mounting the NAS, but I do not seem to have any permissions. I cannot edit file names or even write new files to the NAS. ls of the NAS shows:
```
tribble@Tribble:/media/Hal$ ls -l
total 399360
-rw-r--r-- 1 tribble root 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rw-r--r-- 1 tribble root 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxr-xr-x 1 tribble root         0 Dec 31 14:02 Accident
drwxr-xr-x 1 tribble root         0 Mar 15 05:39 Back-Ups
drwxr-xr-x 1 tribble   99         0 Mar 24 19:58 iTunes
drwxr-xr-x 1 tribble root         0 Mar 19 20:18 Mini Desktop
drwxr-xr-x 1 tribble   99         0 Mar 19 19:11 Movies
drwxr-xr-x 1 tribble root         0 Sep  8  2014 Partial transfer from old laptop
drwxr-xr-x 1 tribble   99         0 Apr  4 15:42 Pictures
-rw-r--r-- 1 tribble root     14336 Sep 21  2014 Reef Tank - 29.xls
-rw-r--r-- 1 tribble root   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxr-xr-x 1 tribble root         0 May 10 20:20 Shared
-rwxr-xr-x 1 tribble   99  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxr-xr-x 1 tribble root         0 Nov 29  2015 Stephen's Back-Up
drwxr-xr-x 1 tribble root         0 Dec 15  2013 Stephen's Biking Video
-rw-r--r-- 1 tribble root     15095 Feb 26 21:32 Tank Product Codes.odt
drwxr-xr-x 1 tribble   99         0 Mar  5  2014 Transfer from old laptop
drwxr-xr-x 1 tribble   99         0 May 15 06:14 TV Shows
drwxr-xr-x 1 tribble root         0 May 10 20:21 Users

```I'm tribble, so from looking at this, I would think I could do what I want. Any suggestions on fixing the permissions?

---

### Post by bab1 on 2016-06-05
> **wazamoo said:**
> Ok, sorry for the long delay, life happens. After reading the entire man for mount.cifs and doing more searches online I made this addition to my fstab:
```

//192.168.1.1/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,rw,uid=1000,iocharset=utf8,sec=ntlm,nobrl,forceuid 0 0

```
I assume you mean the above.  Why not also add this for the group```
gid=1000
```> 
This seems to be working for mounting the NAS, but I do not seem to have any permissions. I cannot edit file names or even write new files to the NAS. ls of the NAS shows:
```
tribble@Tribble:/media/Hal$ ls -l
total 399360
-rw-r--r-- 1 tribble root 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rw-r--r-- 1 tribble root 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxr-xr-x 1 tribble root         0 Dec 31 14:02 Accident
drwxr-xr-x 1 tribble root         0 Mar 15 05:39 Back-Ups
drwxr-xr-x 1 tribble   99         0 Mar 24 19:58 iTunes
drwxr-xr-x 1 tribble root         0 Mar 19 20:18 Mini Desktop
drwxr-xr-x 1 tribble   99         0 Mar 19 19:11 Movies
drwxr-xr-x 1 tribble root         0 Sep  8  2014 Partial transfer from old laptop
drwxr-xr-x 1 tribble   99         0 Apr  4 15:42 Pictures
-rw-r--r-- 1 tribble root     14336 Sep 21  2014 Reef Tank - 29.xls
-rw-r--r-- 1 tribble root   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxr-xr-x 1 tribble root         0 May 10 20:20 Shared
-rwxr-xr-x 1 tribble   99  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxr-xr-x 1 tribble root         0 Nov 29  2015 Stephen's Back-Up
drwxr-xr-x 1 tribble root         0 Dec 15  2013 Stephen's Biking Video
-rw-r--r-- 1 tribble root     15095 Feb 26 21:32 Tank Product Codes.odt
drwxr-xr-x 1 tribble   99         0 Mar  5  2014 Transfer from old laptop
drwxr-xr-x 1 tribble   99         0 May 15 06:14 TV Shows
drwxr-xr-x 1 tribble root         0 May 10 20:21 Users

```I'm tribble, so from looking at this, I would think I could do what I want. Any suggestions on fixing the permissions?
I can't see the share configuration or the parent (shared) folder permissions.  Both are important.

---

### Post by wazamoo on 2016-06-08
> **bab1 said:**
> I assume you mean the above.  Why not also add this for the group```
gid=1000
```
Ok, I now made the fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=ca5e6a99-9aa6-4031-b445-c5be32eeebdb /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=211a4b12-bbbf-4388-9ae9-0d2b494edade /boot           ext4    defaults        0       2
# /hdd was on /dev/sdb6 during installation
UUID=e63ac8fb-f2d0-40a6-9c99-0e85199475ca /hdd            ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=ef395444-9762-42af-8da6-0955631d6a59 /home           ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=bab139ab-ef6b-4a69-af0a-93277e488805 /var            ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=cff00210-a67c-4c0f-9aed-dc22d91f637e none            swap    sw              0       0
//192.168.1.1/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,rw,uid=1000,gid=1000,iocharset=utf8,sec=ntlm,nobrl,forceuid,forcegid 0 0

```
[QUOTE=bab1]I can't see the share configuration or the parent (shared) folder permissions. Both are important.[/QUOTE]
I believe you want to see the smb.conf file in /etc/samba/smb.conf and the share folder permissions:
```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 


#======================= Global Settings =======================


[global]


client use spnego = no
client NTLMv2 auth = no


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin



```
```
tribble@Tribble:/media$ cd /media
tribble@Tribble:/media$ ls -l
total 4
drwxr-xr-x  1 tribble root       0 May 21 21:50 Hal
drwxr-x---+ 2 root    tribble 4096 Jun  8 05:38 tribble
tribble@Tribble:/media$ cd /media/Hal
tribble@Tribble:/media/Hal$ ls -l
total 394576
-rw-r--r-- 1 tribble root 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rw-r--r-- 1 tribble root 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxr-xr-x 1 tribble root         0 Dec 31 14:02 Accident
drwxr-xr-x 1 tribble root         0 Mar 15 05:39 Back-Ups
drwxr-xr-x 1 tribble   99         0 Mar 24 19:58 iTunes
drwxr-xr-x 1 tribble root         0 Mar 19 20:18 Mini Desktop
drwxr-xr-x 1 tribble   99         0 Mar 19 19:11 Movies
drwxr-xr-x 1 tribble root         0 Sep  8  2014 Partial transfer from old laptop
drwxr-xr-x 1 tribble   99         0 Apr  4 15:42 Pictures
-rw-r--r-- 1 tribble root     14336 Sep 21  2014 Reef Tank - 29.xls
-rw-r--r-- 1 tribble root   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxr-xr-x 1 tribble root         0 May 10 20:20 Shared
-rwxr-xr-x 1 tribble   99  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxr-xr-x 1 tribble root         0 Nov 29  2015 Stephen's Back-Up
drwxr-xr-x 1 tribble root         0 Dec 15  2013 Stephen's Biking Video
-rw-r--r-- 1 tribble root     15095 Feb 26 21:32 Tank Product Codes.odt
drwxr-xr-x 1 tribble   99         0 Mar  5  2014 Transfer from old laptop
drwxr-xr-x 1 tribble   99         0 May 15 06:14 TV Shows
drwxr-xr-x 1 tribble root         0 May 10 20:21 Users

```

Is this what you were looking for?

---

### Post by bab1 on 2016-06-08
> **wazamoo said:**
> Ok, I now made the fstab:
```

[COLOR="#800080"]**UUID=bab139ab-ef6b-4a69-af0a-93277e488805**[/COLOR] /var            ext4    defaults        0       2

//192.168.1.1/Hal/ /media/Hal cifs credentials=/home/tribble/.halcredentials,rw,uid=1000,gid=1000,iocharset=utf8,sec=ntlm,nobrl,forceuid,forcegid 0 0

```
Is the part in purple correct?  What do you get from this command```
df -h
```
> 
I believe you want to see the smb.conf file in /etc/samba/smb.conf and the share folder permissions:

What you sent was the client machine's smb.conf.  The share is defined on the server.  Am I confused?
> 
```
tribble@Tribble:/media$ cd /media
tribble@Tribble:/media$ ls -l
total 4
drwxr-xr-x  1 tribble root       0 May 21 21:50 Hal
drwxr-x---+ 2 root    tribble 4096 Jun  8 05:38 tribble
tribble@Tribble:/media$ cd /media/Hal
tribble@Tribble:/media/Hal$ ls -l
total 394576
-rw-r--r-- 1 tribble root 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rw-r--r-- 1 tribble root 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxr-xr-x 1 tribble root         0 Dec 31 14:02 Accident
drwxr-xr-x 1 tribble root         0 Mar 15 05:39 Back-Ups
drwxr-xr-x 1 tribble   99         0 Mar 24 19:58 iTunes
drwxr-xr-x 1 tribble root         0 Mar 19 20:18 Mini Desktop
drwxr-xr-x 1 tribble   99         0 Mar 19 19:11 Movies
drwxr-xr-x 1 tribble root         0 Sep  8  2014 Partial transfer from old laptop
drwxr-xr-x 1 tribble   99         0 Apr  4 15:42 Pictures
-rw-r--r-- 1 tribble root     14336 Sep 21  2014 Reef Tank - 29.xls
-rw-r--r-- 1 tribble root   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxr-xr-x 1 tribble root         0 May 10 20:20 Shared
-rwxr-xr-x 1 tribble   99  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxr-xr-x 1 tribble root         0 Nov 29  2015 Stephen's Back-Up
drwxr-xr-x 1 tribble root         0 Dec 15  2013 Stephen's Biking Video
-rw-r--r-- 1 tribble root     15095 Feb 26 21:32 Tank Product Codes.odt
drwxr-xr-x 1 tribble   99         0 Mar  5  2014 Transfer from old laptop
drwxr-xr-x 1 tribble   99         0 May 15 06:14 TV Shows
drwxr-xr-x 1 tribble root         0 May 10 20:21 Users

```

Is this what you were looking for?
Why doesn't this match the updated fstab file.  You can remount everything with this command```

sudo mount -a
```

---

### Post by wazamoo on 2016-06-12
> **bab1 said:**
> Is the part in purple correct? 
Yes, I have only added the last line. The rest of the fstab is unchanged by me.
[QUOTE=bab1]What do you get from this command```
df -h
```[/QUOTE]

```
tribble@Tribble:~$ df -h
Filesystem          Size  Used Avail Use% Mounted on
udev                3.8G     0  3.8G   0% /dev
tmpfs               789M  9.8M  779M   2% /run
/dev/sda2            28G  4.8G   22G  19% /
tmpfs               3.9G  5.0M  3.9G   1% /dev/shm
tmpfs               5.0M  4.0K  5.0M   1% /run/lock
tmpfs               3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda5            46G  9.8G   34G  23% /home
/dev/sda1           226M  146M   65M  70% /boot
/dev/sdb1           7.3G  1.2G  5.8G  17% /var
/dev/sdb6           903G   44G  813G   6% /hdd
cgmfs               100K     0  100K   0% /run/cgmanager/fs
//192.168.1.1/Hal/  2.8T  1.5T  1.3T  54% /media/Hal
tmpfs               789M   56K  789M   1% /run/user/1000
tribble@Tribble:~$ 

```


[QUOTE=bab1]What you sent was the client machine's smb.conf.  The share is defined on the server.  Am I confused?[/QUOTE]
Sorry, no you're not confused. I do not see any config file on the server. There is only the router gui configuration which is all R/W.
[ATTACH=CONFIG]269535[/ATTACH]
[QUOTE=bab1]Why doesn't this match the updated fstab file.  You can remount everything with this command```

sudo mount -a
```[/QUOTE]
Sorry, I didn't realize I did this out of order this time. Here it is again after an update and restart.
```
tribble@Tribble:~$ sudo gedit /etc/fstab
[sudo] password for tribble: 


** (gedit:13863): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
tribble@Tribble:~$ sudo mount -a
tribble@Tribble:~$ cd /media
tribble@Tribble:/media$ ls -l
total 4
drwxr-xr-x  1 tribble tribble    0 May 21 21:50 Hal
drwxr-x---+ 2 root    tribble 4096 Jun  8 05:38 tribble
tribble@Tribble:/media$ cd /media/Hal
tribble@Tribble:/media/Hal$ cd /media/Hal
tribble@Tribble:/media/Hal$ ls -l
total 394576
-rw-r--r-- 1 tribble tribble 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rw-r--r-- 1 tribble tribble 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxr-xr-x 1 tribble tribble         0 Dec 31 14:02 Accident
drwxr-xr-x 1 tribble tribble         0 Mar 15 05:39 Back-Ups
drwxr-xr-x 1 tribble tribble         0 Mar 24 19:58 iTunes
drwxr-xr-x 1 tribble tribble         0 Mar 19 20:18 Mini Desktop
drwxr-xr-x 1 tribble tribble         0 Mar 19 19:11 Movies
drwxr-xr-x 1 tribble tribble         0 Sep  8  2014 Partial transfer from old laptop
drwxr-xr-x 1 tribble tribble         0 Apr  4 15:42 Pictures
-rw-r--r-- 1 tribble tribble     14336 Sep 21  2014 Reef Tank - 29.xls
-rw-r--r-- 1 tribble tribble   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxr-xr-x 1 tribble tribble         0 May 10 20:20 Shared
-rwxr-xr-x 1 tribble tribble  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxr-xr-x 1 tribble tribble         0 Nov 29  2015 Stephen's Back-Up
drwxr-xr-x 1 tribble tribble         0 Dec 15  2013 Stephen's Biking Video
-rw-r--r-- 1 tribble tribble     15095 Feb 26 21:32 Tank Product Codes.odt
drwxr-xr-x 1 tribble tribble         0 Mar  5  2014 Transfer from old laptop
drwxr-xr-x 1 tribble tribble         0 May 15 06:14 TV Shows
drwxr-xr-x 1 tribble tribble         0 May 10 20:21 Users
tribble@Tribble:/media/Hal$ 

```Now it all says tribble as owner, but when I tried to edit a file name in the gui, I got this saying I do not have permissions:
[ATTACH=CONFIG]269536[/ATTACH]
That does not seem right...

Edit:
Ok, I got something. I tried changing the permissions of all the files in Hal (NAS). This did not work since it said that I did not have the proper permissions (even though I was sudo). Since I first setup the NAS with a Mac, I went to my MBP and tried changing all the files on Hal to 777. This worked, it went through the full process. Now I can edit files on the NAS with tribble (Ubuntu computer). I know that 777 permissions is not a desirable state, but at least it is working. I'm thinking I have to somehow make the same group (GID) on all of the computers that will be using the NAS (in Ubuntu and Mac). I'll have to do some more research on GID's, but it seems like this is a large step in the right direction. Then maybe I could change the permissions back to something like 775. I will also have to make sure all files written to Hal have the same GID (no matter which computer). Would you agree with this train of thought?
```
tribble@Tribble:~$ cd /media/Hal
tribble@Tribble:/media/Hal$ ls -l
total 394576
-rwxrwxrwx 1 tribble tribble 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rwxrwxrwx 1 tribble tribble 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxrwxrwx 1 tribble tribble         0 Dec 31 14:02 Accident
drwxrwxrwx 1 tribble tribble         0 Mar 15 05:39 Back-Ups
drwxrwxrwx 1 tribble tribble         0 Mar 24 19:58 iTunes
drwxrwxrwx 1 tribble tribble         0 Mar 19 20:18 Mini Desktop
drwxrwxrwx 1 tribble tribble         0 Mar 19 19:11 Movies
drwxrwxrwx 1 tribble tribble         0 Sep  8  2014 Partial transfer from old laptop
drwxrwxrwx 1 tribble tribble         0 Apr  4 15:42 Pictures
-rwxrwxrwx 1 tribble tribble     14336 Sep 21  2014 Reef Tank - 29.xls
-rwxrwxrwx 1 tribble tribble   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxrwxrwx 1 tribble tribble         0 May 10 20:20 Shared
-rwxrwxrwx 1 tribble tribble  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxrwxrwx 1 tribble tribble         0 Nov 29  2015 Stephen's Back-Up
drwxrwxrwx 1 tribble tribble         0 Dec 15  2013 Stephen's Biking Video
-rwxrwxrwx 1 tribble tribble     15095 Feb 26 21:32 Tank Product Codes.odt
drwxrwxrwx 1 tribble tribble         0 Mar  5  2014 Transfer from old laptop
drwxrwxrwx 1 tribble tribble         0 May 15 06:14 TV Shows
drwxrwxrwx 1 tribble tribble         0 May 10 20:21 Users
tribble@Tribble:/media/Hal$ 

```

---

### Post by bab1 on 2016-06-12
> **wazamoo said:**
> ...Now it all says tribble as owner, but when I tried to edit a file name in the gui, I got this saying I do not have permissions:

That does not seem right...

Actually, it does seem right if the user name (uid) or group (gid) ownership is different than what you are logged in as.  It's easy to fix if you can set the parameters in the servers smb.conf file.  But since you can't you have to do what you discovered (below).  The user name (uid) or the group (gid) needs to be the same across all computers. 
> 
Edit:
Ok, I got something. I tried changing the permissions of all the files in Hal (NAS). This did not work since it said that I did not have the proper permissions (even though I was sudo). Since I first setup the NAS with a Mac, I went to my MBP and tried changing all the files on Hal to 777. This worked, it went through the full process. Now I can edit files on the NAS with tribble (Ubuntu computer). I know that 777 permissions is not a desirable state, but at least it is working. I'm thinking I have to somehow make the same group (GID) on all of the computers that will be using the NAS (in Ubuntu and Mac). I'll have to do some more research on GID's, but it seems like this is a large step in the right direction. Then maybe I could change the permissions back to something like 775. I will also have to make sure all files written to Hal have the same GID (no matter which computer). Would you agree with this train of thought?
```
tribble@Tribble:~$ cd /media/Hal
tribble@Tribble:/media/Hal$ ls -l
total 394576
-rwxrwxrwx 1 tribble tribble 246581284 Jun 12  2014 04 Beginner Yoga.m4v
-rwxrwxrwx 1 tribble tribble 139007220 Jun 12  2014 06 PM Yoga.m4v
drwxrwxrwx 1 tribble tribble         0 Dec 31 14:02 Accident
drwxrwxrwx 1 tribble tribble         0 Mar 15 05:39 Back-Ups
drwxrwxrwx 1 tribble tribble         0 Mar 24 19:58 iTunes
drwxrwxrwx 1 tribble tribble         0 Mar 19 20:18 Mini Desktop
drwxrwxrwx 1 tribble tribble         0 Mar 19 19:11 Movies
drwxrwxrwx 1 tribble tribble         0 Sep  8  2014 Partial transfer from old laptop
drwxrwxrwx 1 tribble tribble         0 Apr  4 15:42 Pictures
-rwxrwxrwx 1 tribble tribble     14336 Sep 21  2014 Reef Tank - 29.xls
-rwxrwxrwx 1 tribble tribble   1525760 Jun 21  2014 Reef Tank - 75.xls
drwxrwxrwx 1 tribble tribble         0 May 10 20:20 Shared
-rwxrwxrwx 1 tribble tribble  16888601 Jul 14  2011 SLR Camera Manual - D3100.pdf
drwxrwxrwx 1 tribble tribble         0 Nov 29  2015 Stephen's Back-Up
drwxrwxrwx 1 tribble tribble         0 Dec 15  2013 Stephen's Biking Video
-rwxrwxrwx 1 tribble tribble     15095 Feb 26 21:32 Tank Product Codes.odt
drwxrwxrwx 1 tribble tribble         0 Mar  5  2014 Transfer from old laptop
drwxrwxrwx 1 tribble tribble         0 May 15 06:14 TV Shows
drwxrwxrwx 1 tribble tribble         0 May 10 20:21 Users
tribble@Tribble:/media/Hal$ 

```

---

### Post by wazamoo on 2016-06-12
Thank you so much for your help with all this! It is very encouraging for my continued transition to Ubuntu.

---

### Post by bab1 on 2016-06-12
> **wazamoo said:**
> Thank you so much for your help with all this! It is very encouraging for my continued transition to Ubuntu.
I'm glad you have solved your problem.  I assume you set all machines user tribble to the same uid/gid.  Is that so?  Others that follow will want to know exactly what you did.

---

