---
title: "Samba min protocol SMB3, nmap report SMBV1"
date: 2021-05-27
forum: Networking &amp; Wireless
---

### Post by linuxlion2 on 2021-05-27
A Linux system uses Ubuntu 18.04.5
De file /etc/samba/smb.conf contains the rules "client min protocol = SMB3" and "smb encrypt = required"

The command "nmap -p445 -Pn -vvv --script smb-protocols" on that Ubuntu 18 system give (between others) the output rows:
   Host script results:
  | smb-protocols: 
  |   dialects: 
  |     NT LM 0.12 (SMBv1) [dangerous, but default]
  |     2.02
  |     2.10
  |     3.00
  |     3.02
  |_    3.11

Is that in contrast to each other?
In Samba it is set that the minimum SMB protocol is 3.
Nmap reports the dangerous SMBv1 protocol anyway.
Can the Ubuntu system still be accessed with SMBv1?

---

### Post by TheFu on 2021-05-27
My understanding is that there are 2 client min settings in the smb.conf file.  One for the client side and one for the server side.
```
; This is for the smb server; 
   min protocol = SMB2
; This is for the smb/cifs client connecting to Windows
   client min protocol = SMB2
```

Which returns: 
```
Host script results:
| smb-protocols: 
|   dialects: 
|     2.10
|     3.00
|     3.02
|_    3.11
```

Don't forget to restart the smbd service.

---

### Post by rsteinmetz70112 on 2021-05-27
Samba attempts to negotiate the protocol based on a number of different settings. 

There are a number of "protocol" statements that control this interaction

client min protocol
client max protocol

server min protocol
server max protocol

max protocol = synonym for server max protocol
min protocol = synonym for server min protocol

protocol  = synonym for server max protocol

I believe the protocol  statements can be implemented on a per share basis or in the global section if so a share specific option could override the global statement and allow other protocols to be used. 
If you want to prevent any connection below a specific level protocol I think** server min protocol** in the global section is probably your best bet.

---

### Post by TheFu on 2021-05-27
rsteinmetz70112 is correct again!  He's on a roll.

If we go to the manpage for smb.conf and find the section were "max protocol" starts, there is a huge amount of information which explains which protocol version goes with each version of Windows.  For example:
```

                  ·   SMB3: The same as SMB2. Used by Windows 8. SMB3
                      has sub protocols available.
...
       **min protocol**

           This parameter is a synonym for server min protocol.

       **server min protocol** (G)

           This setting controls the minimum protocol version that the
           server will allow the client to use.

           Normally this option should not be set as the automatic
           negotiation phase in the SMB protocol takes care of choosing
           the appropriate protocol.

           See Related command: server max protocol for a full list of
           available protocols.
```
So, it appears that *server min protocol* can only be used in the "Global" section - there is a (G) next to it. Yep, in the "Parameters" part of the manpage, it says:
```
       The letter G in
       parentheses indicates that a parameter is specific to the
       [global] section. The letter **S** indicates that a parameter can be
       specified in a service specific section. All S parameters can
       also be specified in the [global] section - in which case they
       will define the default behavior for all services.

```

It is a very dense manpage, full of information, tidbits, and caveats.

---

