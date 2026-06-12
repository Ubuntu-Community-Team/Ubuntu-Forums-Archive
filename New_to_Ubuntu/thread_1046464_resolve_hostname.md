---
title: "resolve hostname"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by gv29847 on 2009-01-21
I have several pcs on a windows workgroup network. I have run live CD ubuntu 8.1 on one of them. If I look at "Computor" > "Network" on the ubuntu pc I see all the pcs on the net. I can select one - for example "asus" and see the folders and files. I can copy a file from asus and paste it on my ubuntu desktop, and vice versa.

However if I run a command like 
rsync -avz /home/ubuntu/desktop/*.* asus:c:\temp
I get a "could not resolve hostname asus: Name or service not known" error message.

How can I make asus visible to rsync?
Peter

---

### Post by taavikko on 2009-01-21
Use ip.address for the asus.
**man rsync** gives more info

I fail to see what you're trying to achieve?
copy content of Desktop to other machine, running windows?
Install ssh-server on it, and that should take care of it.
Samba doesn't cover rsync. at least what I'm aware of.

---

### Post by gv29847 on 2009-01-21
I have been looking at the rsync man but after my two hours hands on with linux, much of the manual is meaningless to me. I cant fing any mention of ip's in scanning through 3,400 lines of the manual, and I can't find a way of searching it. I tried just putting the ip where "asus" was and it just went into never never land and I had to CtrlC to get back.

The example is just suposed to be a simple begining with doing more complex transfers with rsync.

When you say "Install ssh-server on it" - by "it" do you mean the windows pc or the ubutu one?

---

### Post by taavikko on 2009-01-21
If asus is windows machine, install it on that one.
to push with rsync
```
rsync -avr /home/ubuntu/desktop/ ip.address.asus:destination
```

linux to windows needs a bit of working around (cygwin. or similar)
[http://www.gaztronics.net/rsync.php](http://www.gaztronics.net/rsync.php)
[http://www.linux.com/feature/113847](http://www.linux.com/feature/113847)

Hope that helps a bit.

---

