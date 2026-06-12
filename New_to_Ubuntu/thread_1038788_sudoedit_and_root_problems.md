---
title: "sudoedit and root problems"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by kyle.hall on 2009-01-13
Hello, I am trying to install eclipse from these instructions:

[http://www.ubuntued.com/?p=40](http://www.ubuntued.com/?p=40)

When I used the line sudoedit /usr/bin/eclipse my terminal freaked out.  Here is what I see:

lots of tildies (is that how you spell it?):
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/var/tmp/eclipse.XXU1gTUl" 0 lines, 0 characters

I can only close terminal window to exit terminal.  When I reopen terminal window and log in as superuser this happens:

kyle@kyle-tPadLaptop:~$ sudo su
sudo: unable to resolve host kyle-tPadLaptop
root@kyle-tPadLaptop:/home/kyle# 

I am not prompted for a password anymore but am logged in as root.  I think this is a security issue that I somehow created.  

Please suggest a way to fix this problem.  Thanks.

Kyle

P.S. How do I put code into a box on my posts to this forum?   I am very new to all of this!

---

### Post by iaculallad on 2009-01-13
Edit your /etc/hots file with:

```
gksudo gedit /etc/hosts
```

File output should be similar with:

> 127.0.0.1 localhost
127.0.1.1 **[COLOR="DarkRed"]gutsy-gibbon[/COLOR]**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Now, change gutsy-gibbon with:

> **kyle-tPadLaptop**

Save and Close the file. Retry the commands on the tutorial.

HTH.

---

### Post by Titan8990 on 2009-01-13
That guide is old. Eclipse is in Synaptic as eclipse-sdk. Just get it from there. But you do have other issues to solve...

---

### Post by kyle.hall on 2009-01-13
OK.  Part of the way there.  I had nothing in my /usr/hosts file.  I added the first two lines you suggested and now get this:

kyle@kyle-tPadLaptop:~$ sudo su
sudo: unable to resolve host kyle-tPadLaptop
[sudo] password for kyle: 
root@kyle-tPadLaptop:/home/kyle#

Can you explain what these commands did/do?  I assume they are port numbers?  What are all of the others you have listed below the fist two lines of the file hosts in your post?

Thank you for the reply.

Kyle

---

### Post by iaculallad on 2009-01-13
> **kyle.hall said:**
> OK.  Part of the way there.  I had nothing in my /usr/hosts file.  I added the first two lines you suggested and now get this:

kyle@kyle-tPadLaptop:~$ sudo su
sudo: unable to resolve host kyle-tPadLaptop
[sudo] password for kyle: 
root@kyle-tPadLaptop:/home/kyle#

Can you explain what these commands did/do?  I assume they are port numbers?  What are all of the others you have listed below the fist two lines of the file hosts in your post?

Thank you for the reply.

Kyle

That should be /etc/hosts file, not /usr/hosts.

---

### Post by kyle.hall on 2009-01-13
Still no luck.  I did some searching, should I be making these changes in safe mode?  Should I be rebooting or anything like that after making changes?

Kyle

---

