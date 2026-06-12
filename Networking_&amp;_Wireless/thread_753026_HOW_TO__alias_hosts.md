---
title: "HOW TO : alias hosts"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2008-04-12
Hello,

searching the forums I didn't find a how to on this so I decided to write one myself.
What we want to do:
We want to add hosts to a specific file so every time we want to connect to a host, instead of typing ssh ... , to type only ssh "host_name" and connect right away (after giving our password of cource).

In order to do so we have to do the following:
```
cd .ssh
```
```
vim config
```
With the last command we create inside .ssh (mind the dot) a file named config. FYI in some ubuntu distros this file already exists. Then for every host we have to type this:

#First Host
Host "host_name" "IP address"
HostName "host_name"
User "name_of_the_user_of_the_machine_we_want_to_connect"
Compression yes
Protocol 2
Port 22 

#Second Host
...

Host *
ForwardAgent yes
ForwardX11 yes

Notes:
[LIST]
[*]everything inside " " will be from the machine we want to connect.
[*]in order to find the hostname of the machine we want to connect we type in **that** machine ```
hostname
```
[*]in order to find out the ip address we type ```
ifconfig
``` in inet address we find out the ip, yet if we are behind a rooter we have to see it via [http://www.whatismyip.com](http://www.whatismyip.com)
[*]with ```
whoami
``` we can find out as which name we connect
[*]in case we have changed the port then we have to give that number and not the default which is 22
[*]EDIT: With the *ForwardX11 yes* option we do not have to type *-Y* in order to enable trusted X11 forwarding.
[/LIST]

Then we have to do:

```
sudo vim /etc/hosts 
```
and add in the end this line per host:
"ip address" "host_name"

Now every time we type ```
ssh "host_name" (without the " ")
``` we will connect.
We have to give the password, which will be the one of the machine we connect. The messages that we will see about keys and hosts are normal and we do not have to worry about them.
In case we want to open a browser while we have done ssh we can type:
```
ssh -Y "host_name"
```

In case you type ssh with the usual way:

```
ssh -Y -l "user_name" "ip_address" (-p "port_number" if necessary)
```
and you are not able to submit your password, you might have typed something wrong with host_names. Just FYI.

Regards!

---

