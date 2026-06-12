---
title: "Need help (freeradius &lt;--&gt; 2nd router)"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by denbagoos on 2014-03-19
[COLOR=#000000][FONT=verdana]need help here...i wanna use freeradius for my hotspot, i use two mikrotik for my router and i have a problem connecting my 2nd mikrotik to freeradius[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]here is my topology
[/FONT][/COLOR][IMG]http://s4.postimg.org/6c6ax5f99/Screenshot.png[/IMG]

[COLOR=#000000][FONT=verdana]when i test on LAN connection its working fine but when i use it for my RB433 user cannot login...[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]this is what i get from freeradius -X
[/FONT][/COLOR]```
rad_recv: Access-Request packet from host 192.168.1.2 port 59092, id=26, length=193        NAS-Port-Type = Wireless-802.11
        Calling-Station-Id = "A4:17:31:41:CB:B6"
        Called-Station-Id = "hotspot3"
        NAS-Port-Id = "bullet"
        User-Name = "test"
        NAS-Port = 2152726618
        Acct-Session-Id = "8050005a"
        Framed-IP-Address = 192.168.10.183
        Mikrotik-Host-IP = 192.168.10.183
        CHAP-Challenge = 0xf1fb74cf86fcb8d3dd4bf34451c2f96c
        CHAP-Password = 0x18622df4a39f1dc321153f4223329159d5
        Service-Type = Login-User
        WISPr-Logoff-URL = "http://192.168.10.1/logout"
        NAS-Identifier = "RB433"
        NAS-IP-Address = 192.168.1.2
# Executing section authorize from file /etc/freeradius/sites-enabled/default
+- entering group authorize {...}
[am-authorize]  expand: %u -> test
[am-authorize]  expand: %n -> 192.168.1.2
Exec-Program output:
Exec-Program: returned: 0
++[am-authorize] returns ok
++[preprocess] returns ok
[chap] Setting 'Auth-Type := CHAP'
++[chap] returns ok
++[mschap] returns noop
++[digest] returns noop
[suffix] No '@' in User-Name = "test", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] No EAP-Message, not doing EAP
++[eap] returns noop
++[files] returns noop
[sql]   expand: %{User-Name} -> test
[sql] sql_set_user escaped user --> 'test'
rlm_sql (sql): Reserving sql socket id: 3
[sql]   expand: SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radcheck           WHERE username = 'test'           ORDER BY id
[sql] User found in radcheck table
[sql]   expand: SELECT id, username, attribute, value, op           FROM radreply           WHERE username = '%{SQL-User-Name}'           ORDER BY id -> SELECT id, username, attribute, value, op           FROM radreply           WHERE username = 'test'           ORDER BY id
rlm_sql: Failed to create the pair: Invalid octet string "0" for attribute name "Mikrotik-Total-Limit"
rlm_sql (sql): Error getting data from database
[sql] SQL query error; rejecting user
rlm_sql (sql): Released sql socket id: 3
++[sql] returns fail
Using Post-Auth-Type Reject
# Executing group from file /etc/freeradius/sites-enabled/default
+- entering group REJECT {...}
[attr_filter.access_reject]     expand: %{User-Name} -> test
 attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 0 for 1 seconds
Going to the next request
Waking up in 0.8 seconds.
Sending delayed reject for request 0
Sending Access-Reject of id 26 to 192.168.1.2 port 59092
Waking up in 4.9 seconds.
Cleaning up request 0 ID 26 with timestamp +8
Ready to process requests.

```

[COLOR=#000000][FONT=verdana]thanks for all your help.....[/FONT][/COLOR]

---

