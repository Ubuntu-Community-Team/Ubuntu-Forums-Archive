---
title: "[Samba v2] Duplicate entries?"
date: 2021-01-31
forum: Networking &amp; Wireless
---

### Post by username2758 on 2021-01-31
Hiya!

I don't know much about Samba, but why do I see two entries of the same Samba Server on my local network?

Here I have two server machines, UBUNTU64 (Samba v1) and M75Q (Samba v2):

[[IMG]https://i.ibb.co/NCDQC0P/Screenshot-20210131-154845.jpg[/IMG]]("https://ibb.co/NCDQC0P")

Why two M75q?

---

### Post by CelticWarrior on 2021-01-31
Do you see the same in opther desktop/laptop computers in the network or just in that phone/tablet?

---

### Post by username2758 on 2021-01-31
Yes, I only see the duplicate on VLC software. I hadn't noticed before you asked.

Initially I thought it was a bug in Samba v2, because the other server is running Samba v1 instead.

BTW, is it possible to install Samba v1 on newer Ubuntu 20.04? I'm still running Ubuntu 16 LTS because of hardware compatibility issues.

---

### Post by username2758 on 2021-02-01
I have been experiencing yet another problem with Samba v2.

On the VLC player, whenever I try to access files from Samba v2 it keeps asking for login credentials each and every time I try and load a different file in the same server (or even the very same file repeatedly). This problem doesn't happen with Samba v1.

Note: I had to use "server min protocol = NT1" for the client to be able to access Samba v2.

---

### Post by rsteinmetz70112 on 2021-02-01
What is Samba v2?

---

### Post by username2758 on 2021-02-01
> **rsteinmetz70112 said:**
> What is Samba v2?

Version of Samba of course, or SMBv2. Come on... (:

So why is SMBv2 showing duplicates on VLC software? Also why is it asking for login credentials repeatedly?

If I remove the appended "server min protocol = NT1", the login bug disappears and I can access files just fine, but some clients won't connect to SMBv2.

---

### Post by rsteinmetz70112 on 2021-02-01
SMB2 is a protocol (Signal Message Block). SAMBA is a software suite that amoung other things impliments SMB2.
I have never seen it referred to as SAMBA v2 because the protocol is implemented in various other systems but originated in Windows.

I'd suggest you take your question to the SAMBA mailing list which the SAMBA team monitors and there is deep knowledge of SAMBA code and the protocols.

---

### Post by username2758 on 2021-02-02
> **rsteinmetz70112 said:**
> SMB2 is a protocol (Signal Message Block). SAMBA is a software suite that amoung other things impliments SMB2.
I have never seen it referred to as SAMBA v2 because the protocol is implemented in various other systems but originated in Windows.

I'd suggest you take your question to the SAMBA mailing list which the SAMBA team monitors and there is deep knowledge of SAMBA code and the protocols.

But my question is very simple, and I'm certainly not an expert in networking.

I just want to set up a simple working file-server at home with Linux is all.

I have had good experience with SMBv1, but no luck when it comes to SMBv2.

---

### Post by Morbius1 on 2021-02-02
I cannot figure out from the information presented here what operating system and what version of that operating system each of these servers is running:

UBUNTU64
M75Q

One of them appears ... maybe ... to be running Ubuntu 16.04 but which one I do not know.

---

### Post by username2758 on 2021-02-02
> **Morbius1 said:**
> I cannot figure out from the information presented here what operating system and what version of that operating system each of these servers is running:

UBUNTU64
M75Q

One of them appears ... maybe ... to be running Ubuntu 16.04 but which one I do not know.

My bad again,

- UBUNTU64 (Ubuntu 16.04 LTS)
- M75Q (Lubuntu 20.04 LTS)

That's it!

---

### Post by Morbius1 on 2021-02-02
The samba client and the server it is trying to connect to negotiate the correct smb dialect ( SMB1, SMB2, SMB3 ) to use between a min and max limit.

By default Samba ( Version 4.3.8 ) in Ubuntu 16.04 ( UBUNTU64 ) has the client run from pre-SMB1 to SMB1 ( NT1 ) and the server run from pre-SMB1 to SMB3.

By default Samba ( Version 4.11.6 ) in Ubuntu 20.04 ( M75Q ) has the client run from SMB2.02 to SMB3 and the server run from SMB2.02 to SMB3.

Ubuntu 16.04 cannot access the Ubuntu 20.04 machine because there is no SMB1 on the server. You can either:

Set client max protocol = SMB3 on the Ubuntu 16.04 machine but that will disable host discovery.

Or you can set server min protocol = NT1 on the Ubuntu 20.04 machine.

Either way a reboot is required.

You posted that you set the server min to NT1 - not sure on which machine - and you ended up with VLC asking for credentials when you access each file. I honestly have no idea what that is all about. Never seen that symptom.

As for the original question of duplicate hosts showing up. A modern samba server ( M75Q ) will announce its Samba server to the network 2 different ways: NetBIOS and mDNS ( Avahi ). You are seeing both. One should resolve to the hostname and the other to hostname.local. If it bothers you you can disable one or the other.

Ubuntu 16.04 did not have that implemented yet.

---

### Post by username2758 on 2021-02-02
> **Morbius1 said:**
> You posted that you set the server min to NT1 - not sure on which machine - and you ended up with VLC asking for credentials when you access each file. I honestly have no idea what that is all about. Never seen that symptom.

Thank you very much for the explanation!

I set the server min to NT1 on the newer Ubuntu 20.04 machine ( M75Q ) because not all of my devices are able to access the server without it. I never had that problem with SMBv1 ( UBUNTU64 ).

Now on the issue regarding the login credentials, it keeps asking for username and password indefinitely with NT1 ( M75Q ) without a single successful login. But if I disable server min to NT1 on that same server ( M75Q ), the client is able to log in successfully, but keeps asking for login credentials every and each time I try to access a different file on that server. This issue only occurs with older software, VLC version 3.2.12, think the latest version is 3.3.4 now. If I use VLC 3.3.4 (latest) to access the newer Ubuntu 20.04 machine ( M75Q ) without server min to NT1, it works flawlessly, just showing the duplicate hosts but that's fine.

---

### Post by rsteinmetz70112 on 2021-02-04
Samba negotiates the protocol to be used for any connection. This is controlled by the "client min", "client max", "server min" and "server max" parameter in the smb.conf file.
"protocol" and "max protocol" are synonymous with "server max protocol". "min protocol" is a synonym of "server min protocol"

I normally do not set these as the negotiation between the Samba server and client usually results in the highest protocol common to both, however Windows 10 will not connect at SMB1/CIFS protocols unless you enable it in Windows 10. This is sometimes necessary when connecting to older versions of Windows or possible some other clients.

> Understanding min and max protocol levels in smb.conf
client min protocol – This setting controls the minimum protocol version that the client will attempt to use.
client max protocol – The value of the parameter (a string) is the highest protocol level that will be supported by the client.

SMB2: Re-implementation of the SMB protocol. Used by Windows Vista and later versions of Windows. SMB2 has sub protocols available:
SMB2_02: The earliest SMB2 version.
SMB2_10: Windows 7 SMB2 version. (By default SMB2 selects the SMB2_10 variant.)
SMB2_22: Early Windows 8 SMB2 version.
SMB2_24: Windows 8 beta SMB2 version.
SMB3: The same as SMB2. Used by Windows 8. SMB3 has sub protocols available. SMB3 has sub protocols available:
SMB3_00: Windows 8 SMB3 version. (mostly the same as SMB2_24)
SMB3_02: Windows 8.1 SMB3 version.
SMB3_10: early Windows 10 technical preview SMB3 version.
SMB3_11: Windows 10 technical preview SMB3 version (maybe final). By default SMB3 selects the SMB3_11 variant.

> The "server min" and "server max" protocols control the
The value of the parameter (a string) is the highest protocol level that will be supported by the server.

Possible values are :

LANMAN1: First modern version of the protocol. Long filename support.
LANMAN2: Updates to Lanman1 protocol.
**NT1: Current up to date version of the protocol. Used by Windows NT. Known as CIFS.**
SMB2: Re-implementation of the SMB protocol. Used by Windows Vista and later versions of Windows. SMB2 has sub protocols available.
SMB2_02: The earliest SMB2 version.
SMB2_10: Windows 7 SMB2 version.
SMB2_22: Early Windows 8 SMB2 version.
SMB2_24: Windows 8 beta SMB2 version.
By default SMB2 selects the SMB2_10 variant.

SMB3: The same as SMB2. Used by Windows 8. 
SMB3 has sub protocols available.
SMB3_00: Windows 8 SMB3 version. (mostly the same as SMB2_24)
SMB3_02: Windows 8.1 SMB3 version.
SMB3_10: early Windows 10 technical preview SMB3 version.
SMB3_11: Windows 10 technical preview SMB3 version (maybe final).

By default SMB3 selects the SMB3_11 variant.

**Normally this option should not be set as the automatic negotiation phase in the SMB protocol takes care of choosing the appropriate protocol.**
Default: server max protocol = SMB3
Example: server max protocol = LANMAN1

Setting "server min protocol = NT1" limits the server, not the client. You need to look at the protocols each client will supports.

---

