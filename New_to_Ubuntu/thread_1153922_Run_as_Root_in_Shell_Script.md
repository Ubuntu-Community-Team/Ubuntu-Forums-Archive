---
title: "Run as Root in Shell Script"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Frank_F on 2009-05-09
Hello

Just created a simple shellp that flushes the iptables -F. The issue is the script fails (return 1, instad of 0), cause it want me to Sudo and enter password to run when I type iptables -F

I tried to set the setuid to 4, but it still doesnt work. How do i prevent the prompt or automate it

Thanks

---

### Post by wizard10000 on 2009-05-09
> **Frank_F said:**
> Hello

Just created a simple shellp that flushes the iptables -F. The issue is the script fails (return 1, instad of 0), cause it want me to Sudo and enter password to run when I type iptables -F

I tried to set the setuid to 4, but it still doesnt work. How do i prevent the prompt or automate it

The easiest way to do it (or at least the easiest way I can think of) is to run it from /etc/crontab.

---

### Post by bodhi.zazen on 2009-05-09
You have to run the script using sudo.

You can configure sudo so that the script may be run without a password (see visudo and man sudoers).

Or you can as suggested by wizard10000 run it from cron

```
sudo crontab -e
```

be sure to use the full path in cron, /sbin/iptables -F

---

### Post by garyed on 2009-05-09
You can do this in your script but it's pretty unsecure:
```
echo "your-password"|sudo -S iptables -F 
```

I wrote a small C program to enter my password in a script to make it a little more secure.

---

### Post by hobo14 on 2009-05-09
Run sudo with the -u switch.

ie. sudo -u <username> <prognam>

The program will run with root priveleges, without prompting for a password.

---

### Post by bodhi.zazen on 2009-05-09
> **hobo14 said:**
> Run sudo with the -u switch.

ie. sudo -u <username> <prognam>

The program will run with root priveleges, without prompting for a password.

No it does not , lol

try it for yourself :

> #!/bin/bash

sleep 60 &

exit 0```
# run as a user

bodhi@entropy:~$ ./program                    
bodhi@entropy:~$ ps aux | grep sleep       
[COLOR=darkgreen]bodhi    12351  0.0  0.0   9444   812 pts/0    S    10:16   0:00 sleep 60[/COLOR]

# run with sudo

bodhi@entropy:~$ sudo ./program                       
[sudo] password for bodhi: 
bodhi@entropy:~$ ps aux | grep sleep                  
[COLOR=darkred]root     12484  0.0  0.0   9444   812 pts/0    S    10:17   0:00 sleep 60[/COLOR]


# run with sudo -u bodhi

bodhi@entropy:~$ sudo -k
bodhi@entropy:~$ sudo -u bodhi ./program 
bodhi@entropy:~$ ps aux | grep sleep                  05/09/09 10:18 AM
[COLOR=darkgreen]bodhi    12491  0.0  0.0   9444   812 pts/0    S    10:18   0:00 sleep 60[/COLOR]
```see man sudo ( and the -u flag )

:lolflag:


As an aside, you can not set suid on regular files, just binaries

```
sudo chown root ./program
sudo chmod +s ./program
ls -la

[COLOR=red]-rwsr-sr-x  1 root  bodhi    32 2009-05-09 10:26 program[/COLOR]

See how suid is set ^^

bodhi@entropy:~$ ./program      
bodhi@entropy:~$ ps aux | grep sleep 
[COLOR=green]bodhi    12732  0.0  0.0   9444   812 pts/0    S    10:26   0:00 sleep 60[/COLOR]
```but as you can see, sleep does not run as root.

You can only set the suid bit on binaries

```
sudo chmod +s /bin/sleep
bodhi@entropy:$/bin/sleep 60 &

bodhi@entropy:$ ps aux | grep sleep                  05/09/09 10:30 AM
[COLOR=red]root     13020  0.0  0.0   9444   816 pts/0    S    10:30   0:00 /bin/sleep 60[/COLOR]

See how the binary sleep can have a suid set and sleep now runs as root even if called as a user ?

sudo chmod -s /bin/sleep
```

---

### Post by durand on 2009-05-09
You can explicitly tell sudo to ignore password input for a particular program.
```
sudo visudo
```
Scroll to the end of the file with Page Down.
Press o and paste this line into the file:
> <your_username> ALL= NOPASSWD: /path/to/program


Press escape, and type :wq. Then you can just use sudo in your script and it won't ask for a password.

---

### Post by hobo14 on 2009-05-09
> **bodhi.zazen said:**
> No it does not , lol

try it for yourself :

```
# run as a user

bodhi@entropy:~$ ./program                    
bodhi@entropy:~$ ps aux | grep sleep       
[COLOR=darkgreen]bodhi    12351  0.0  0.0   9444   812 pts/0    S    10:16   0:00 sleep 60[/COLOR]

# run with sudo

bodhi@entropy:~$ sudo ./program                       
[sudo] password for bodhi: 
bodhi@entropy:~$ ps aux | grep sleep                  
[COLOR=darkred]root     12484  0.0  0.0   9444   812 pts/0    S    10:17   0:00 sleep 60[/COLOR]


# run with sudo -u bodhi

bodhi@entropy:~$ sudo -k
bodhi@entropy:~$ sudo -u bodhi ./program 
bodhi@entropy:~$ ps aux | grep sleep                  05/09/09 10:18 AM
[COLOR=darkgreen]bodhi    12491  0.0  0.0   9444   812 pts/0    S    10:18   0:00 sleep 60[/COLOR]
```see man sudo ( and the -u flag )

:lolflag:


As an aside, you can not set suid on regular files, just binaries

```
sudo chown root ./program
sudo chmod +s ./program
ls -la

[COLOR=red]-rwsr-sr-x  1 root  bodhi    32 2009-05-09 10:26 program[/COLOR]

See how suid is set ^^

bodhi@entropy:~$ ./program      
bodhi@entropy:~$ ps aux | grep sleep 
[COLOR=green]bodhi    12732  0.0  0.0   9444   812 pts/0    S    10:26   0:00 sleep 60[/COLOR]
```but as you can see, sleep does not run as root.

You can only set the suid bit on binaries

```
sudo chmod +s /bin/sleep
bodhi@entropy:$/bin/sleep 60 &

bodhi@entropy:$ ps aux | grep sleep                  05/09/09 10:30 AM
[COLOR=red]root     13020  0.0  0.0   9444   816 pts/0    S    10:30   0:00 /bin/sleep 60[/COLOR]

See how the binary sleep can have a suid set and sleep now runs as root even if called as a user ?

sudo chmod -s /bin/sleep
```

Whoa there bodhi, not everyone is a guru like you, some of us (me) are only just beginning.

I know using sudo -u doesn't actually make the process belong to root, but I thought it was a valid solution because it appeared to work for me recently (turns out it was something else that made the difference).

You could have got your message across nicely, without the laughing.

---

### Post by bodhi.zazen on 2009-05-09
> **hobo14 said:**
> Whoa there bodhi, not everyone is a guru like you, some of us (me) are only just beginning.

I know using sudo -u doesn't actually make the process belong to root, but I thought it was a valid solution because it appeared to work for me recently (turns out it was something else that made the difference).

You could have got your message across nicely, without the laughing.

So sorry, it was not my intention to be insulting and I apologize if my post came across that way.

My intention was educational and it appears as if you have learned, which is the important thing.

---

