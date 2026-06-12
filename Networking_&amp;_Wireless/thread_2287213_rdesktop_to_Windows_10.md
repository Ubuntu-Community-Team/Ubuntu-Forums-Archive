---
title: "rdesktop to Windows 10"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by eoin-houston on 2015-07-17
I have been trialling Windows 10.0 (build 10240) and could not remote desktop in to the test machine from an Ubuntu 12.04.2 machine on the local network.

```
eoin@HOSTNAME:~$ rdesktop XX.XX.XX.XX
Autoselected keyboard map en-gb
ERROR: recv: Connection reset by peer
```

After various unhelpful attempts to change settings on the Windows machine and upgrading to newer builds through the "insider program" I eventually found a registry tweak was required on the target machine.

With reference to:
[https://cyberarms.net/security-insights/security-lab/important-windows-2012-remote-desktop.aspx](https://cyberarms.net/security-insights/security-lab/important-windows-2012-remote-desktop.aspx)

I changed the registry key
*\HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp\SecurityLayer*[COLOR=#575656]

[FONT=Arial]from DWORD Hex '**2**' to a value of '**1**'[/FONT]

[FONT=Arial]This reduces the security resilience of the windows machine but allows older software to remote in.[/FONT][/COLOR]

---

### Post by fabioxxxx on 2015-08-12
Thanks  Eoin : )

---

### Post by luca43 on 2015-11-17
Worked fine for me as well. Amazing

---

### Post by cerien on 2016-01-15
Many thanks - worked for me as well with xrdesktop 1.7.1 - what bugs me is that it worked with another identical computer (but hdd crashed, so I cant truly compare) without this setting !

-- edit
I've upgraded to 1.8.3 and same issue - I really wonder why, of two computers running mint 17.2, one could connect and not the other

---

### Post by stoian on 2016-12-14
Well, in my case it was not the NLA authentication setting on the server. What has changed -- the operating system on the server was re-installed and so the fingerprint (or the host key) has changed. The freerdp on linux stored the previous fingerprint in a file under your home folder ~/.freerdp/known_hosts.

The error comes from the fact that the server IP address is the same but the fingerprints don't match.

The solution is to clear or delete the ~/.freerdp/known_hosts file on the linux guest.

---

