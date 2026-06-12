---
title: "Creating an authentication script"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Nulifier on 2007-09-11
My university requires me to authenticate via ssh to their proxy in order to access the internet.

I am trying to get it to autorun an ssh session (for authentication) when I connect to this network (over wireless). I only want it to run when it detects that I am connected to this network (the name is always constant).

I am currently using network-manager and it detects and connects to this network automatically. I am wondering if there is a script that is run when it connects to a network that I can add a simple if then statement to (to check if it is the right network).

I think this should be possible and that maybe it has something to do with if-up/if-down.

If possible I would like it to disconnect once the network is closed but this is not required as I could just kill all ssh sessions in my hibernate script

Thanks for any help

---

### Post by kevdog on 2007-09-11
I dont know if network manager has such functionality, but I know WICD does - or has the ability to run a script after logging into a network.  The only other way I could think to do what you are describing is to bring your network up manually in a script, and then after making the connection, run the ssh script.  This of course would not use network manager.

---

### Post by robert_pectol on 2007-09-11
Well, here's a little code snippet that I threw together for you that might help you get there:
```

#!/bin/sh
if [ `iwconfig 2>/dev/null | grep ESSID | cut -d ':' -f2 | sed 's/"//g'` = "school-essid" ]; then
    echo "yes"
else
    echo "no"
fi
exit 0

```
That should at least give you the logic to determine if you are connected to the right network or not.  Obviously you need to replace, "school-essid" with the essid of the access point you connect to at school.  Running this in it's current form will return a, "yes" if you are connected to the school-essid, else it will return a, "no".  Add the appropriate call to your ssh command/script in place of the, "echo yes."  Hope that helps.

---

### Post by Nulifier on 2007-09-11
thanks for the fast reply

I just tried wicd but it does not want to connect to my other network (home with wep) so it is not a viable solution

there is also a big problem with getting the ssh to auto authenticate as public/private keys are not an option (no access to files on proxy) so I may just have to login each and every time...

---

### Post by Nulifier on 2007-09-11
I tried an expect script 
```
#!/usr/bin/expect -f
# Expect script to supply root/admin password for remote ssh server 
# and execute command.
# This script needs three argument to(s) connect to remote server:
# password = Password of remote UNIX server, for root user.
# ipaddr = IP Addreess of remote UNIX server, no hostname
# scriptname = Path to remote script which will execute on remote server
# For example:
#  ./sshlogin.exp password 192.168.1.11 who 
# ------------------------------------------------------------------------
# Copyright (c) 2004 nixCraft project <http://cyberciti.biz/fb/>
# This script is licensed under GNU GPL version 2.0 or above
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit http://bash.cyberciti.biz/ for more information.
# ----------------------------------------------------------------------
# set Variables
set password [lrange $argv 0 0] 
set ipaddr [lrange $argv 1 1]   
set scriptname [lrange $argv 2 2] 
set arg1 [lrange $argv 3 3] 
set timeout -1   
# now connect to remote UNIX box (ipaddr) with given script to execute
spawn ssh root@$ipaddr $scriptname $arg1
match_max 100000
# Look for passwod prompt
expect "*?assword:*"
# Send password aka $password 
send -- "$password\r"
# send blank line (\r) to make sure we get back to gui
send -- "\r"
expect eof
```
 however it is does not appear to connect to the network when I test it on my own server (through who)
it would appear that this script is made for executing a command rather than keeping a session alive though I know there is no shell given at the other side just a blurb telling you to close this window when finished (it is designed for putty)

---

