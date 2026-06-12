---
title: "spawn: not found"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by drao on 2008-11-04
Hello,

I am trying to run a script to reboot the broadband router. I am getting the following error. Thanks in advance.

adsl: 1: &#65279;#!/usr/bin/expect: not found
adsl: 19: spawn: not found
couldn't read file "Login:": no such file or directory
adsl: 23: send: not found
couldn't read file "Password:": no such file or directory
adsl: 25: send: not found
couldn't read file " -&gt; ": no such file or directory
adsl: 29: send: not found
couldn't read file "# ": no such file or directory
adsl: 33: send: not found
adsl: 35: send: not found

Code::
#!/usr/bin/expect -f


set timeout 20

# router user name
set name "xxxxx"

# router password
set pass "yyyyyyy"

# router IP address
set routerip "xx.xx.xx.xx"

# Read command as arg to this script
set routercmd [lindex $argv 0]

# start telnet
spawn telnet $routerip

# send username &amp; password
expect "Login:"
send -- "$name\r"
expect "Password:"
send -- "$pass\r"

# get out of ISP's  Stupid menu program, go to shell
expect " -&gt; "
send --  "sh\r"

# execute command
expect "# "
send -- "$routercmd\r"
# exit
send -- "^D"

---

### Post by puppywhacker on 2008-11-04
Hi,

start with the first error message, expect not found. since your script is an "expect" script and not a regular shell script

sudo apt-get install expect

goodluck

---

### Post by drao on 2008-11-07
i have installed expect. There is no improvement and am getting same error. Please help how to make it work.Thanks

---

