---
title: "Cannot ssh inside my network"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by cocotu on 2006-07-20
Hi guys, I was using ssh to connect to a LAMP server downstairs and it was working fine until yesterday after I came back from lunch. I was told to use nmap to scan for open ports. I only see that port 80 is open. Can I use this port for ssh. I keep getting the error: "Conection refused" I'm sorry if I don't make any sense, I'm new to this thing, but I want to learn!!

Thanks...

---

### Post by ArBaDaCarBa on 2006-07-20
Maybe the ssh server is down for some reason...

Port 80 is usually for http, ssh port is 22. You still might not see it open with nmap depending on your server firewall configuration.

Have you tried restarting the ssh server ?

What have you done yesterday ? Have you been modifying your server configuration ?

---

### Post by cocotu on 2006-07-20
No I did not modify anything yesterday. It was working fine and after I came back from an 1 hour lunch break I could not connect again. I left the connection open so when I came back I saw the message: "Connection time out" or something similar.

These are the steps I followed yesterday, answering some questions that somebody asked me to do:

1) Yes I can ping to the remote machine.
2) I spoke with the network administrator and he says that the configuration has NOT been change.

3) I tried the command: "ps -A | grep ssh" and I got no output, nothing

4) No I can NOT connect to the ssh server from any other machine.

5) I tried to connect to the server from the local machine by using the code:
   "ssh user@localhost -p portnumber" and I got: "Network error: Connection refused" 

6) I checked for changes in /etc/hosts.allow and /etc/hosts.deny and no changes have been made.

Thanks for your help

---

### Post by harisund on 2006-07-20
Ok do a couple of things. 

First, open /etc/ssh/sshd_config and look for the port directive. Next to that will be a number and that should be the port on which your server listens. By default it is 22, and I would suggest you leave it at that. 

Next start your SSH server. Execute ```
sudo invoke-rc.d ssh restart
``` and look at the output. Hopefully there should be no error. If there are any, post it out here. 

Now make sure that the server is indeed listening on that port. Do a ```
 sudo netstat -plant | grep LISTEN
``` on the machine and it will tell you all the ports that are open and that it is listening on. You should see the SSH port being open and it will also tell you what application is listening to it (in this case the SSHD daemon). 

If you have followed so far, your machine should be having a successful running SSH server. 

If you want, you can try and ssh into the same box by doing ```
ssh localhost
```, or if you have changed the port to something other than 22, ```
ssh -p port_number localhost
``` and see if you are able to login. 

Finally head over to your upstairs box and login to the server. If they are on the same subnet it should be fine. If not, you are going to have to open ports on whatever is in between the two boxes.

---

### Post by cocotu on 2006-07-20
No luck, now Putty stays frozen and nothing happens. I will give you the output of the "sudo netstat -plant | LISTEN" command in a few. We are closing now! Thanks

---

### Post by cocotu on 2006-07-21
Ok harisund, this is the output of the sudo netstat -plant | LISTEN command:

tcp   0   0  127.0.0.1:3306     0.0.0.0:*    LISTEN 5279/mysqld

tcp6  0   0  :::80              :::*         LISTEN 10057/apache2

What does this means??

---

### Post by harisund on 2006-07-21
This means your SSH server is not running in the first place. Only the web server and the database server are running.

Can you post the output of the command ```
sudo invoke-rc.d ssh restart
```?

---

### Post by cocotu on 2006-07-21
When I type: "sudo invoke-rc.d ssh restart" I get file not found. But if I type: etc/init.d/ssh start I get: Restarting OpenBSD Secure Shell server.....[OK]. Then I ran sudo netstat -plant | LISTEN" command and I got:

tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 5279/mysqld

tcp6 0 0 :::80 :::* LISTEN 10057/apache2

Bad luck for me!

---

### Post by harisund on 2006-07-24
Hmmm something seems seriously wrong here. 

Try starting from a scratch. Remove your SSH server and restart it. 

```
sudo aptitude purge openssh-server
sudo aptitude install openssh-server
```

followed by a netstat will tell you if the SSH server has been correctly installed or not. 

Can you try this once?

---

### Post by cocotu on 2006-07-24
Harisund, after 2 hours it finally worked. I falling asleep that I tried so many commands I got finally got it back working. The computer froze and I had to reboot the machine. After it rebooted I typed: "sudo netstat -plant | LISTEN" and ssh was running.  Thanks a lot Harisund for your help, now I have to study on how the configure Apache with MySql. We are having an Intranet web page. Do you now any good tutorials for this purpose?

Thanks again...

---

### Post by harisund on 2006-07-24
I have myself posted many times in these forums on how to get Apache-PHP-MySQL working. Search the forums for posts made by "harisund" containing "apache" etc .. 

Here's my latest

[http://ubuntuforums.org/showpost.php?p=1272499&postcount=9](http://ubuntuforums.org/showpost.php?p=1272499&postcount=9)

This was from the thread [http://ubuntuforums.org/showthread.php?t=218429](http://ubuntuforums.org/showthread.php?t=218429)

---

