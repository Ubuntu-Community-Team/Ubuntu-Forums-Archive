---
title: "Script for logging in to FON HOTSPOT automaticaly BT WIFI"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by markandrews08 on 2015-01-02
I'm wanting to create or find a script that will automatically authenticate a FON hotspot. Specifically a BT Wifi hotspot. 
 
My only internet access is through this particular hotspot but it is a  real pain having to pass the screen by doing it manually. 
   
Is there a script to authenticate the BT hotspot automatically for ubuntu/linux?

I'm planning on building a Pi home theatre, so this would be really handy to maintain the connection.
 
Your advice please.

---

### Post by jeremy31 on 2015-01-02
There should be the option in Network Manager, in the connection settings, to automatically connect when available

---

### Post by markandrews08 on 2015-01-02
Connecting to the AP is okay its just it has a web interface to login to the internet itself once connection to the AP has been made

---

### Post by Itay_Grudev on 2015-12-07
Check [this script]("https://gist.github.com/itay-grudev/d3d4eb0dc4e239d96c84") I wrote. There is an authentication script and an automatic re-authententication script if connection is lost.

It is really simple to use:
```

btauth --user USER_OR_EMAIL --pass PASSWORD # To Authenticate with the BT WiFi
btmaintain --user USER_OR_EMAIL --pass PASSWORD # To maintain a connection and re-authenticate automatically
nohup btmaintain --user USER_OR_EMAIL --pass PASSWORD 2>&1 >/dev/null & # Same as above but ran in background

```

---

