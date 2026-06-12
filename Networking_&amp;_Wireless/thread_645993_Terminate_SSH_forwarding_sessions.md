---
title: "Terminate SSH forwarding sessions"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by osx on 2007-12-20
I'm using SSH forwarding to talk to a mysql server. I have a bash script which establishes the forwarding and then executes the desired mysql commands. It works great, however, I would like an automated way of terminating the SSH forwarding when I am done with it. Any ideas are greatly appreciated.

Thanks.

---

### Post by strateg on 2008-03-13
check the PID in another terminal window and kill it:

ps aux | grep ssh
kill <PID>

/J

---

### Post by strateg on 2008-03-13
or maybe Fugu?
[http://rsug.itd.umich.edu/software/fugu/](http://rsug.itd.umich.edu/software/fugu/)

---

### Post by osx on 2008-03-13
I need a way for it to be fully automated from a bash script. I ended up using the sleep option with an amount of time set that is more than long enough. It's not really the ideal way to do it, in my opinion, but it is at least working.

Thanks for the suggestions.

Here's the command I am now using for anyone interested:

ssh -fg -L 10000:127.0.0.1:3306 username@192.168.0.9 sleep 500

---

