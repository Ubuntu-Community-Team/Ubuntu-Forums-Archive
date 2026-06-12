---
title: "Slow ssh connection?"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by erikcw on 2006-09-14
Hi all,

Whenever I ssh into my Dapper box from my OS X laptop, it takes 30-60 seconds for the password prompt to appear.  I don't understand why it is taking so long to connect.

I can ssh to my webserver with no problems (very fast), but my LAN is so slow.  

Ping doesn't seem to have any latency, so I think the LAN is ok.  What could it be?

Thanks!

---

### Post by tbonius on 2006-09-14
Usually its an issue with reverse DNS.  Make sure your host is resolvable.. and make sure the SSH server can resolve itself as well.. even if you have to put an entry in /etc/hosts with its own IP address.

---

### Post by erikcw on 2006-09-14
Here is what I have in my hosts file.

> 
erik@turbo:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       turbo


The IP of my Ubuntu box (ssh server) is 192.168.15.100.  The ssh client is 192.168.15.105.  What do I need to add to my server hosts file?  I don't want to mess up the localhost...

Also - im not using hostnames for ssh.  I'm doing 
ssh 192.168.15.100 -l myuser

Does that make a difference?

Thanks!
Erik

---

### Post by Isoss on 2006-09-14
I am facing the same problem! slow ssh connection! I am pretty sure that my LAN is fine cuz before I could transfer files in GB between windows machines on the network! now that I am trying to do that with ssh or scp it only transfers few MB and then freezes the system! hope it's the same problem of yours Erik so I woudn't be deviating from the subject!

tbonius, I also would really know how what do I need to add to my server hosts file ... using IPs just like Erik's case.

Thanks

---

### Post by tbonius on 2006-09-14
What ErikCW is talking about is a long delay prompt between login and password when SSH'ing into the Linux server.  This is usually due to a reverse DNS timeout when trying to resolve itself.  If you are not running DNS on your internal network yourself.. then you can substitute this by adding the IP addresses of your hosts in /etc/hosts.  Try adding 192.168.15.100 to your hosts file:

turbo        192.168.15.100

And remove the 127.0.1.1 line.  You should only have one loopback entry.. 127.0.0.1.  After you do that.. you can even put the IP address of the client connecting to it into the hosts file.  Then try SSH'ing into your Ubuntu Server.

What Isoss is talking about is a different issue.  This could be a number of factors.  Bad network card.  Bad memory.  Bad processor.  Incorrect module loaded for the network card (though highly unlikely).

T

---

### Post by Isoss on 2006-09-19
Hey, I guess I know where's my problem, tbonius, would you please check this post [http://ubuntuforums.org/showthread.php?t=260303](http://ubuntuforums.org/showthread.php?t=260303)

---

