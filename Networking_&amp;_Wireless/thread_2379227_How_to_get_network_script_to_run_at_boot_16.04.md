---
title: "How to get network script to run at boot 16.04"
date: 2017-12-02
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2017-12-02
I have a VPN service and I need to have local access for my ISP's mail server(The VPN IP is blocked). I found a script that does this in a very simple way:
```
#!/bin/bash
URL_LIST=("smtp.isp.net" "someplace.com" "otherplace.net")
GATEWAY="192.168.1.1"
 
IP_LIST=()
 
for url in $URL_LIST
  do
    ip=`dig +short $url`
    IP_LIST+=("$ip")
  done
  
for ips in $IP_LIST
  do
    ips=(`echo $ips | tr " " "\n"`)
    for ip in $ips
      do
        ip route add $ip via $GATEWAY
      done
  done
```
Tested and works!
But how do I get it to run at boot up? I have tried to put it in rc.local and have tried with the file in /etc/NetworkManager/dispatcher.d/ and neither get the desired results. Only after I run the command in terminal.

---

### Post by Hadaka on 2017-12-02
Hi, add this to your script and see if it helps.

```
[COLOR=#000000]#!/bin/bash[/COLOR]
PATH=$PATH:/sbin:/usr/sbin
```
how are you calling it in /etc/rc.local ?
may we see that code please.
Thanks.

@steeldriver...thanks.

---

### Post by steeldriver on 2017-12-02
... I would think 

```

PATH=$PATH:/sbin:/usr/sbin

```

would be nearer the mark, no?

---

### Post by Hadaka on 2017-12-02
steeldriver is correct.

@steeldriver...indeed
thank you i made the correction to my post.

---

### Post by lsutiger on 2017-12-02
Thanks for the reply!
How am I calling  it in rc.local?
```
sh '/bin/bpvpn.sh'
```
is in my rc.local file before exit 0

I checked out the syslog and found this
```
Dec  2 15:58:18 Aspire-R3-131T systemd[1]: Starting /etc/rc.local Compatibility...
Dec  2 15:58:18 Aspire-R3-131T rc.local[1074]: /bin/bpvpn.sh: 2: /bin/bpvpn.sh: Syntax error: "(" unexpected

```
So, it is trying to run it but I am not understanding why the "(" is unexpected.
Referring back to the script, this is what is in the 2nd line:
URL_LIST=("smtp.isp.net" "someplace.com" "otherplace.net")
When I run it manually, no error and it works. Hmmm.....
As per Bash arrays, it is defined: ARRAY=(value1 value2 ... valueN)

This is making me scratch my head!

---

### Post by steeldriver on 2017-12-02
... because sh is not bash: [DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

in particular, it doesn't support the (...) array syntax

---

### Post by lsutiger on 2017-12-03
I removed the sh from the command, but an now just getting a failed error
From syslog:
```
Dec  2 17:20:54 Aspire-R3-131T systemd[1]: Starting /etc/rc.local Compatibility...
Dec  2 17:20:54 Aspire-R3-131T systemd[1075]: rc-local.service: Failed at step EXEC spawning /etc/rc.local: Exec format error
Dec  2 17:20:54 Aspire-R3-131T systemd[1]: rc-local.service: Control process exited, code=exited status=203
Dec  2 17:20:54 Aspire-R3-131T systemd[1]: Failed to start /etc/rc.local Compatibility.
Dec  2 17:20:54 Aspire-R3-131T systemd[1]: rc-local.service: Unit entered failed state.
Dec  2 17:20:54 Aspire-R3-131T systemd[1]: rc-local.service: Failed with result 'exit-code'.

```
My bash script starts with #! /bin/bash, rc.local starts with !/bin/sh -e
Could this be causing the error? If so, how to fix?

---

### Post by lsutiger on 2017-12-03
Update - It is running but not getting the expected results.
Reason - It need internet connectivity in order to work. I am searching on how to nly run if there is connectivity, but notbeing sucessful.

---

### Post by lsutiger on 2017-12-03
I got it to work(somewhat - needs some more work, which I will post a new thread for), and how this make it work I have no idea.
I add a stderr and stdout command at the end of the command in rc.local:
/bin/byvpn.sh &> test

---

