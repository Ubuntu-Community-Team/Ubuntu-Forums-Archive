---
title: "Problem with remastersys installation in ubuntu 10.04."
date: 2010-09-21
forum: New to Ubuntu
---

### Post by raju50 on 2010-09-21
What should I write in sources.list file?
Should I write this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
or this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
or this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

This is related to what is written on the page [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)
It is written:
[LEFT][COLOR=#000099]**[SIZE=4]Where can I get remastersys?[/SIZE]**[/COLOR][/LEFT]
 The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

For Gutsy and Earlier - up to version 2.0.11-1
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/


For Hardy and Newer with original grub - version 2.0.12-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

How do I know if I have Gutsy and Earlier, or Harder and Newer or Karmic. I don't know what is 'Gutsy', 'Harder', 'Karmic'. Please help.

---

### Post by lkjoel on 2010-09-21
> **raju50 said:**
> What should I write in sources.list file?
Should I write this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
or this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
or this:
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

This is related to what is written on the page [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)
It is written:
[LEFT][COLOR=#000099]**[SIZE=4]Where can I get remastersys?[/SIZE]**[/COLOR][/LEFT]
 The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

For Gutsy and Earlier - up to version 2.0.11-1
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/


For Hardy and Newer with original grub - version 2.0.12-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

How do I know if I have Gutsy and Earlier, or Harder and Newer or Karmic. I don't know what is 'Gutsy', 'Harder', 'Karmic'. Please help.
Fiesty=7.04
Gutsy=7.10
Hardy=8.04
Intrepid=8.10
Jaunty=9.04
Karmic=9.10 (If no Lucid is available, take this one)
Lucid=10.04

So you want lucid.

---

### Post by raju50 on 2010-09-21
Thanks.

---

### Post by lkjoel on 2010-09-22
Do you want to mark this as solved?
Thread tools->Mark this thread as solved

---

### Post by vase070 on 2010-12-17
so this [COLOR=#0000EE]Remastersys Backup[/COLOR]  works for ubuntu 7.04 feisty fawn right :popcorn:

---

