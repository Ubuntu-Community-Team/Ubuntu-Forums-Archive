---
title: "Pass PID to openvpn up script"
date: 2017-02-07
forum: Networking &amp; Wireless
---

### Post by m-dw on 2017-02-07
Hi

I already have an openvpn up script which sets up some firewall rules when the tunnel interface (identified by the variable $1) is created. I was wondering if there was any way to pass the PID of the openVPN client process to the up script, for use in a renice command.

I've been looking for documentation showing what environment variables are passed by the init-script but no luck.

Is the PID passed as an environment variable, or just stored in the pidfile?

---

### Post by SeijiSensei on 2017-02-07
You could grab the PID in the script like this:
```
PID=$(pidof openvpn)
```

---

### Post by m-dw on 2017-02-07
Unfortunately, this isn't the answer, because unfortunately I have an OpenVPN server running on the same box.

I did find the answer, however. I used my up script to dump all the variables to a file which revealed that the variable is $daemon_pid.

I now have another problem, for which a new thread is needed.

---

