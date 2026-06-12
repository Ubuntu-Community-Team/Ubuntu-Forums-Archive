---
title: "Access windows share windows NT (sic) machine on work network"
date: 2016-05-12
forum: Networking &amp; Wireless
---

### Post by uli9 on 2016-05-12
I am trying to access a windows NT machine on our work network with Ubuntu 16.04 machine. I can see it with nautilus. But if I am trying to connect like I do with the windows 7 machines it does not work. So, I thought I try to do it through terminal, as it usually gives you more info when something fails. I did some search as I don't know how to do it. Some instruction told me to use smbclient, which I installed, but I couldn't get it to work. Maybe because I don't know what to use as server name. Another site said to install samba. I check with Synaptic and it was also not installed. 
So, how can I connect to windows network shares with nautilus when both smbclient and samba were not installed. Was the documentation outdated? What would be the way to connect to network share in terminal the way it works with Nautillus?

---

### Post by bab1 on 2016-05-12
> **uli9 said:**
> I am trying to access a windows NT machine on our work network with Ubuntu 16.04 machine. I can see it with nautilus. But if I am trying to connect like I do with the windows 7 machines it does not work. So, I thought I try to do it through terminal, as it usually gives you more info when something fails. I did some search as I don't know how to do it. Some instruction told me to use smbclient, which I installed, but I couldn't get it to work. Maybe because I don't know what to use as server name. 

On Ubuntu Desktop the samba client software is installed by default.  What is it you see in Nautilus, that should be the server name.
> 
Another site said to install samba. I check with Synaptic and it was also not installed. 
So, how can I connect to windows network shares with nautilus when both smbclient and samba were not installed. Was the documentation outdated? What would be the way to connect to network share in terminal the way it works with Nautillus?As I said, you can always access another Windows (SMB) file server with Samba client software using Nautilus unless there is another problem.

The /etc/samba/smb.conf file should be there.  You should be able to use the command ```
smbtree 
```...to see the network shares.

---

### Post by uli9 on 2016-05-12
Ok, I don't now if the attachment worked, Haven't done that before. If it did, it shows what samba packages are installed.
I will check the command you suggested tomorrow at work.
One underlying question wasn't answered: Is it possible to connect to a windows NT (old) machine? I cannot in windows 7 and 10. I guess it is some sort of security thing, because it is not safe? With windows XP I can connect no problem.

---

### Post by bab1 on 2016-05-12
> **uli9 said:**
> Ok, I don't now if the attachment worked, Haven't done that before. If it did, it shows what samba packages are installed.

It may show it, But I can't use these for diagnosis.  The text version of that search would be this```
dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba
```
The results on my machine are this```
libsmbclient 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
libsmbclient-dev 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
libwbclient0 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
python-samba 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
samba 2:4.3.9+dfsg-0ubuntu0.14.04.1  install ok installed
samba-common 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
samba-common-bin 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
samba-dsdb-modules 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
samba-libs 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
samba-vfs-modules 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed
smbclient 2:4.3.9+dfsg-0ubuntu0.14.04.1 samba install ok installed

```
> 
I will check the command you suggested tomorrow at work.
One underlying question wasn't answered: Is it possible to connect to a windows NT (old) machine? I cannot in windows 7 and 10. I guess it is some sort of security thing, because it is not safe? With windows XP I can connect no problem.
It's not safe or unsafe.  The configuration may need some tweaking.  I run an instance of XP as a VM and can access  shares hosted by the latest version of Samba and Windows 10.

---

### Post by uli9 on 2016-05-12
libsmbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
libwbclient0 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
python-samba 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common-bin 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-libs 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
smbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
vlc-plugin-samba 2.2.2-5 vlc install ok installed

Why do you also say machine, as other people call it a box? Maybe I don't speak the correct lingo?

The strange thing about the Nautilus connection is that it shows a windows network folder and some computers with their network name on the same "level", so it doesn't really tell me the "server" name for samba. Is it "Windows Network" or "Workgroup", which it usually seems to be. Or is it the domain name used by windows. Like I said: I can connect to windows 7 machines through Nautilus no problem, but the NT machine doesn't work.
(BTW, have you ever been in the town of Machine? (It's not so great a place if you are from Cleveland, or make flowers from paper ...)

---

### Post by bab1 on 2016-05-13
> **uli9 said:**
> libsmbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
libwbclient0 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
python-samba 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common-bin 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-libs 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
smbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
vlc-plugin-samba 2.2.2-5 vlc install ok installed

Why do you also say machine, as other people call it a box? Maybe I don't speak the correct lingo?

Box is a popularized term.  The machine I refer to is the real machine (the OS running on physical hardware).  A virtual machine (VM) is the OS running on virtual hardware.  I use the terms I have been using for 20+ years as a professional.  Amongst my peers if you use the term "box" everyone would understand that you are most likely self taught.  You asked so I answered.  ;-)
> 
The strange thing about the Nautilus connection is that it shows a windows network folder and some computers with their network name on the same "level", so it doesn't really tell me the "server" name for samba. Is it "Windows Network" or "Workgroup", which it usually seems to be. Or is it the domain name used by windows. Like I said: I can connect to windows 7 machines through Nautilus no problem, but the NT machine doesn't work.

The SMB protocol does not use hostnames or domain names (as in DNS).  The SMB resource is the COMPUTER NAME (NETBIOS name) and the share name (i.e. //NETBIOS_NAME/share_name.  Nautilus parses the names to show the NETBIOS name in the same pane (level) as the "Windows Network" icon.  Drilling down using either the NETBIOS icon or the "Windows Network" icon will get you to the same place; a listing of the shares.  If you show the NETBIOS name that means that the name has been advertised and Nautilus can see it.  At this point, if don't see the share we really know where the problem is.

---

### Post by uli9 on 2016-05-13
(BTW, the other footnote was from the movie Dead Man with Johnny Depp, which I think is pretty good....)
Ok, so I open Nautilus and click on 'Network'. I see some computers by network name and a folder 'Windows Network'. In the 'Windows Network' folder there are 2 more folders (or directories). One is called '<our domain name>' and one 'Workgroup'. The NT machine shows up in the first 'level' by network name and also in the Workgroup folder.
With 'smbtree' I can see basically what I see in Nautilus.
So, what command do I use to access the said machine in the terminal? And what would be the 'server name' - 'Workgroup', that's where it showed up under?

---

### Post by bab1 on 2016-05-13
> **uli9 said:**
> (BTW, the other footnote was from the movie Dead Man with Johnny Depp, which I think is pretty good....)
Ok, so I open Nautilus and click on 'Network'. I see some computers by network name and a folder 'Windows Network'. In the 'Windows Network' folder there are 2 more folders (or directories). One is called '<our domain name>' and one 'Workgroup'. The NT machine shows up in the first 'level' by network name and also in the Workgroup folder.
With 'smbtree' I can see basically what I see in Nautilus.
So, what command do I use to access the said machine in the terminal? And what would be the 'server name' - 'Workgroup', that's where it showed up under?
Please post the output of ***smbtree -d3*** using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon and pasting the text between the blocks.

---

### Post by uli9 on 2016-05-13
> **bab1 said:**
> Please post the output of ***smbtree -d3*** using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon and pasting the text between the blocks.

```
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\ROBOT WORLD            
resolve_lmhosts: Attempting lmhosts lookup for name ROBOT WORLD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ROBOT WORLD<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROBOT WORLD<0x20>
resolve_hosts: getaddrinfo failed for name ROBOT WORLD [Temporary failure in name resolution]
name_resolve_bcast: Attempting broadcast lookup for name ROBOT WORLD<0x20>
Got a positive name query response from 192.168.45.47 ( 192.168.45.47 )
Connecting to 192.168.45.47 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=18 destlen=16 - 'UM-ASPIRE-R5-471T'
Connecting to 192.168.45.47 at port 139
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
        \\ROBOT WORLD\TEMP               
        \\ROBOT WORLD\Daves_old_C        
        \\ROBOT WORLD\ORCADWIN           
        \\ROBOT WORLD\C$                 Default share
        \\ROBOT WORLD\IPC$               Remote IPC
        \\ROBOT WORLD\ADMIN$             Remote Admin
        \\ROBOT WORLD\winzip 

```

I don't want to post the whole output, ROBOT WORLD is the machine.

---

### Post by bab1 on 2016-05-13
> **uli9 said:**
> ```
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
    \\ROBOT WORLD            
resolve_lmhosts: Attempting lmhosts lookup for name ROBOT WORLD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ROBOT WORLD<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROBOT WORLD<0x20>
resolve_hosts: getaddrinfo failed for name ROBOT WORLD [Temporary failure in name resolution]
name_resolve_bcast: Attempting broadcast lookup for name ROBOT WORLD<0x20>
Got a positive name query response from 192.168.45.47 ( 192.168.45.47 )
Connecting to 192.168.45.47 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=18 destlen=16 - 'UM-ASPIRE-R5-471T'
Connecting to 192.168.45.47 at port 139
[COLOR="#FF0000"]**Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'**[/COLOR]
        \\ROBOT WORLD\TEMP               
        \\ROBOT WORLD\Daves_old_C        
        \\ROBOT WORLD\ORCADWIN           
        \\ROBOT WORLD\C$                 Default share
        \\ROBOT WORLD\IPC$               Remote IPC
        \\ROBOT WORLD\ADMIN$             Remote Admin
        \\ROBOT WORLD\winzip 

```

I don't want to post the whole output, ROBOT WORLD is the machine.
No guarantees then as I can't see all the data.  For sure *this* server uses outdated security (see red above).  The Samba client expects that enhanced security will be used.  The only options are to install a current Windows version or to degrade the client's security.  You can degrade the security of the client with this```
client use spnego = no
client ntlmv2 auth = no
```
These need to be added to the */etc/samba/smb.conf *file in the [global] section of the Ubuntu client.  This will affect all of the client security when authenticating with any server, so who knows what problems you will encounter down the line.  You will need to use sudo to edit the* /etc/samba/smb.conf * file as only the root user has read/write permissions.

After you edit the file post the output again of this```
 smbtree -d3
```

Of course the correct thing to do is to leave the Samba client alone and upgrade the Windows machine.

---

### Post by uli9 on 2016-05-14
Thank you for the information BAB1! I was just trying to understand what was going on. It looks like the security settings in Ubuntu are similar to windows (forgive me). So, you cannot connect to older machines.

---

### Post by bab1 on 2016-05-14
> **uli9 said:**
> Thank you for the information BAB1! I was just trying to understand what was going on. It looks like the security settings in Ubuntu are similar to windows (forgive me). So, you cannot connect to older machines.
The security settings are Samba not Ubuntu.  The current version of Samba uses security settings that are pretty close to what Windows10 uses.  The NT host does not use these EXTENDED_SECURITY settings.  That's what the error message in red above states.

---

