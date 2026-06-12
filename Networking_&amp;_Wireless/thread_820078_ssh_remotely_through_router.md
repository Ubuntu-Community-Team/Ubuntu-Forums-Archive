---
title: "ssh remotely through router"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by pondochris on 2008-06-05
okay, I have an old pc running Ubuntu.  I am using this as a file server for miscellaneous stuff but that's not important.  I have everything running exactly as I want and can ssh and vnc into it when connected to my LAN but, I would like to connect via the internet when away from home.  I have searched the web and the forums for an answer but it seems to be in in another language as I am a beginner.  Everything else that I have found tells me what I already know(how to connect via LAN)
"ssh username@ip" then password 

I have port 22 forwarded on the machine and router

the command I use when at home is 
"ssh 192.168.2.4 -l chris"
it then prompts me for my password.  I can then administer and do what I want and stuff.

What is the simplest way to ssh into my machine from work or somewhere else?  I am pretty well versed in commands, editing config files and all kinds of linux admin stuff...but am just starting to learn about networking and remote access.

I am not really interested in security at this point I just want to access it, for now.

I have tried a few ways to connect but not much. here are my feeble attempts to ssh:

"ssh 192.168.2.4@myip -l chris"

"ssh chris@desktop@myip"

see...I have no clue

Thanks for your help

---

### Post by dmizer on 2008-06-06
```
ssh chris@yourip
```

that's it.

the trick will be setting up your router to [forward port 22](http://portforward.com/routers.htm) to your server.

---

### Post by kevdog on 2008-06-06
Might want to register the server's ip address with noip.com if the IP address has a possibility of changing.  This will asssociate your current IP address with a domain name.  With the dynamic updater client installed, everytime your server's IP address would change, this would be reflected and sent to noip's DNS servers.  This way, your domain name would always be reflective of the current IP address.

To connect you would do:

ssh chris@<domain_name>

which in reality is the same as:

ssh chris@<ip_address>

The advantage of the first method is only if ip_address would change (and for memmory purposes).

Also port forward the ssh port (22 as the default) from your router to your home computer in the LAN.  As a suggestion, you should probably change port 22 to some other port number for security reasons.

---

### Post by jalirious on 2013-02-22
I wasn't able to easily set a static ip address, so I came up with this.

All I want to do is ssh into my home laptop on occasion. This works when I know the ip, but it is dynamic & changes from time to time.

So that I always know the current ip to ssh into, I did this

gedit send_ip.sh &
copy in "cat <(date) <(curl icanhazip.com)> /home/me/Dropbox/current_ip.txt" without the quotes
save, close.
chmod +x send_ip.sh

crontab -e

*/5 * * * * /bin/bash cat <(date) <(curl icanhazip.com)> /path_to_it/send_ip.sh

[(all one line), close & save]

Now the current_ip.txt is updated by cron every 5 minutes, so I know where to ssh to.

---

### Post by wildmanne39 on 2013-02-22
Thanks for sharing! Old thread closed.

---

