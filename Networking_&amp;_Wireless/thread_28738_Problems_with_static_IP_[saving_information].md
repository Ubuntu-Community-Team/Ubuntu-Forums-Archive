---
title: "Problems with static IP [saving information]"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by PiO on 2005-04-21
Hello everyone,

I have been haaving problems with setting my Static IP up, i have
followed all of the instructions on going into /etc/networking/ and
editing interfaces or at least tried to everytime i do it it gives me
a message that the file "interfaces" is write protected, so i tried
changing permissions to 777 and it tells me that i do not have
permissions to do that even though im logged in as root?

Any ideas would be very helpful...

Thank You
Peter

---

### Post by heimo on 2005-04-21
```
$ ls -l /etc/network/interfaces 
-rw-r--r--  1 root root 596 2005-04-18 18:54 /etc/network/interfaces

$ su
# chmod 644 /etc/network/interfaces
# ls -l /etc/network/interfaces 
-rw-r--r--  1 root root 596 2005-04-18 18:54 /etc/network/interfaces
# chown root:root /etc/network/interfaces
# touch /etc/network/interfaces
# ls -l /etc/network/interfaces
-rw-r--r--  1 root root 596 2005-04-21 19:51 /etc/network/interfaces
# echo '# this is test' >> /etc/network/interfaces
# tail -1 /etc/network/interfaces
[font=Courier New] # this is test[/font]

``` 
$ = user prompt
# = root prompt

Maybe it's just your  text editor declining to write, because of file lock? (try nano/pico/vim/joe/gedit/kedit/emacs)

---

### Post by PiO on 2005-04-21
Thank you i will try that once i get back home from work... 

Thank you again for fast responce...

Also one more thing before i try this out, i have been trying to log into
my box threw SSH client (telnet) threw the ip my DHCP gave me and
it would not connect, i know my box connects to the internet by
using the wget... is there a specific command i should run before
that starts working or is it because my network connection is not
configured with the static IP yet?

Thank you again,
Peter

---

### Post by heimo on 2005-04-21
Do you have ssh-server package installed? Check /etc/ssh/sshd_config and try to restart ssh daemon (/etc/init.d/ssh restart). Try port scanning that machine with
 ```
nmap -p 22 [ip-address-here]

``` 
You should see:
 ```
PORT   STATE SERVICE
22/tcp open  ssh

```

EDIT: If you don't have ssh-server or nmap installed, use Synaptic or apt-get:
 ```
sudo apt-get install ssh-server nmap

```

---

