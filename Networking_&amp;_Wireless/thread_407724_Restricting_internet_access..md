---
title: "Restricting internet access."
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Revord on 2007-04-12
Is there a way to restrict internet access on just one account? I have 3 accounts on my ubuntu machine, and one of them needs to have a temporary internet restriction. I went into the users and groups, but didnt find any way to restrict that one group. I could restrict the whole computer through my router, but if possible, I would like to focus on the one account. Any ideas?
Revord

---

### Post by kidders on 2007-04-13
Hi there,

What you're describing can't really be done at a user management level, I'm afraid. You may have to resort to using an authenticating proxy. Of course, not all network-aware applications are happy to *use* proxies, so that could introduce new problems.

What kinds of restrictions are you thinking about?

---

### Post by dbott67 on 2007-04-13
A few options, depending on exactly what you want to achieve:

_**1. Total network denial (local & internet):**_

You could write a script that disables the network interface card and have it run after the user logs in (place it in **SYSTEM > ADMINISTRATION > SESSIONS**).
```
#!/bin/bash
sudo ifdown eth0
```_**2. Disable Internet Access Only:**_

You could go under **SYSTEM > PREFERENCES > NETWORK PROXY** and set the **PROXY CONFIGURATION to MANUAL**.  Use **[COLOR=Red]127.0.0.0[/COLOR]** as the IP Address and check the box that says: USE THE SAME PROXY FOR ALL PROTOCOLS.

You could also write a script that changes/replaces the proxy settings each time.  Basically, the proxy settings are stored in the user's home directory here:
```
/home/*username*/.gconf/system/http_proxy/%gconf.xml
```The program creates an XML file that you could just copy into the appropriate directory upon startup.

As an example, I configured a proxy for FTP on port 21 and this is what the XML file looks like after it was created:
```
$ ls
%gconf.xml  http_proxy  proxy
$ cd proxy
$ ls
%gconf.xml
$ cat %gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="ftp_port" mtime="1176481395" type="int" value="21">
        </entry>
        <entry name="ftp_host" mtime="1176481389" type="string">
                <stringvalue>127.0.0.1</stringvalue>
        </entry>
        <entry name="mode" mtime="1176481373" type="string">
                <stringvalue>manual</stringvalue>
        </entry>
</gconf>
$ 
```

If you wrote a script that inserted this file into the **/home/*username*/.gconf/system/http_proxy/%gconf.xml** directory (or 'proxy' folder, as the case may be), then the user would not be able to access HTTP, FTP or any other options you have selected.

Hopefully, this will give you a place to start.

-Dave

---

### Post by Revord on 2007-04-14
My intention is to restrict one person(account) from accessing the internet. Primarily as a punishment (grounding), however, not restricting all accounts. 

@ dbott67: Ill give that a try. Ill reply again if I have any other problems.
Revord

---

