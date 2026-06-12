---
title: "systemd-resolvosed: add DNS with custom port."
date: 2022-09-06
forum: Networking &amp; Wireless
---

### Post by dphusseini on 2022-09-06
[COLOR=#22231F][FONT=&quot]anyone here who can help me with systemd-revsoled configuration? 
I am trying to add a local DNS server with a custom port `30053`. 
I have added the server in [/FONT][/COLOR][COLOR=#22231F][FONT=monospace]`usr/local/lib/systemd/resolved.conf.d/myrpoject.conf`[/FONT][/COLOR][COLOR=#22231F][FONT=&quot] 

[/FONT][/COLOR]nameserver 127.0.0.1:30053


[Resolve]
DNS=127.0.0.1:30053


[COLOR=#22231F][FONT=&quot]
and it shows also in [/FONT][/COLOR][COLOR=#22231F][FONT=monospace]`resolvectl`[/FONT][/COLOR][COLOR=#22231F][FONT=&quot] on top under globals as [/FONT][/COLOR][COLOR=#22231F][FONT=monospace]`127.0.0.1:30053`[/FONT][/COLOR][COLOR=#22231F][FONT=&quot] 


[/FONT][/COLOR]Global
         Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
  resolv.conf mode: stub
Current DNS Server: 127.0.0.1:30053
       DNS Servers: 127.0.0.1:30053


[COLOR=#22231F][FONT=&quot]
but when I do a [/FONT][/COLOR][COLOR=#22231F][FONT=monospace]`nslookup myproject.local`[/FONT][/COLOR][COLOR=#22231F][FONT=&quot] the domain could not be found. 
[/FONT][/COLOR][COLOR=#22231F][FONT=monospace]`nslookup -port=30053 myproject.local 127.0.0.1`[/FONT][/COLOR][COLOR=#22231F][FONT=&quot] is successful.[/FONT][/COLOR]

---

