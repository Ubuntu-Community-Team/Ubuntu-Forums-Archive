---
title: "[SOLVED] Help with sudo and sudoers"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by know-it-some on 2008-12-04
My understanding of sudo is that it is used to allow you to perform a task as if you were the root user.  So a file like this one:

-rw-r--r--  1 root root 20 Dec  3 18:27 /etc/resolv.conf

which has rw permissions for root only, if I wanted to modify that file I would need to do something like:

$ sudo echo 'nameserver 10.0.0.1' > resolv.conf

After which I would be prompted for my creds and I would be allowed to overwrite the file even though my user has no explicit permissions to do so.

Similarly, if I want to be able to do this non-interactively, say in a php script through apache, I need to have a line similar to this one in the sudoers file:

apache  ALL= NOPASSWD: /usr/sbin/netconfig, /bin/rm, /sbin/service, /bin/echo

This is my understanding anyway. The problem I am running into is that my php script is not working for the echo command. However, there are two undesirable work arounds I can do to make it work:

1. chown apache.apache /etc/resolv.conf

2. chmod 666 /etc/resolv.conf

I don't like either solution, although I have tested both work arounds and they do indeed mitigate the problem. I would rather get the sudo command working as it should.  Does anyone here have any suggestions?

---

### Post by djbushido on 2008-12-04
I'll  admit i don't _really_ understand what you are talking about, but all sudo does is grant root user priveleges, so I'm not completely sure how sudo can be "broken."

---

### Post by linux_tech on 2008-12-04
Fix Broken Sudo
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by know-it-some on 2008-12-04
> **djbushido said:**
> I'll  admit i don't _really_ understand what you are talking about, but all sudo does is grant root user priveleges, so I'm not completely sure how sudo can be "broken."

I am not saying that sudo is broken at all, but rather that it is not behaving as I expected it to.  I was asking for help looking at how I have it set up to see if there were any suggestions about how I can improve what I have set up so far.

---

### Post by eder.apt-get on 2008-12-04
Maybe the user Apache has to be on /etc/sudores as an admin.

---

### Post by Michael.Godawski on 2008-12-04
I am just working on a course dealing with root and sudo for the Education Focus Group see here:
[https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Proposals](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Proposals)

I do not know if I can help you right now but I have found a sudoers example file with many different settings:

First sketch is here:
[http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)

and the example file is here:
[http://www.gratisoft.us/sudo/sample.sudoers](http://www.gratisoft.us/sudo/sample.sudoers)

Perhaps by studying it you get on the right track...

I am not an expert myself yet, but working on it... ;)

---

### Post by sisco311 on 2008-12-04
> **know-it-some said:**
> 

$ sudo echo 'nameserver 10.0.0.1' > resolv.conf



```
echo 'nameserver 10.0.0.1' | sudo tee /etc/resolv.conf
```
or
```
echo 'nameserver 10.0.0.1' | sudo tee -a /etc/resolv.conf
```



[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
> Although for desktops the benefits of using sudo are great, there are possible issues which need to be noted: 

Redirecting the output of commands run with sudo requires a different approach. For instance consider **sudo ls > /root/somefile will not work** since it is the shell that tries to write to that file. You can use **ls | sudo tee -a /root/somefile **to append, or **ls | sudo tee /root/somefile** to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo sh -c "ls > /root/somefile".


---

### Post by know-it-some on 2008-12-04
Sisco311, that was exactly the info I was missing so thanks!  The script now functions correctly and I didn't have to chown or chmod resolv.conf which is what I was hoping to avoid.

---

### Post by sisco311 on 2008-12-04
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by bodhi.zazen on 2008-12-04
Just take care with that tee ;)

If you do not use the -a flag the entire file will be over written.

the -a == append, or adds to (at the end) rather then over writing.

---

