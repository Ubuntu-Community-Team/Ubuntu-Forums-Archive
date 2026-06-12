---
title: "going for update got an error message"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by republic74 on 2009-05-12
Hello,

Since I'm a newbie I decided to put this here if that is ok.  My issue is that I received the following error message.

"Failed to Check for installed and available applications.  This is a major failure of your software management system. Please check for broken packages w/synaptic. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software info with: 'sudo apt-get update' and 'sudo apt-get install -f'. 

I could just re-install the OS but figured I would see if I could fix it through the command line.  How do I do what they say above? 

Thanks for any help.  So far I have really enjoyed Linux I can see why people like it.

---

### Post by spiderbatdad on 2009-05-12
```
ls -l /etc/apt/sources.list
```will show your permissions of the file. They should look like this:
```
-rw-r--r-- 1 root root 2687 2009-04-29 18:52 /etc/apt/sources.list

```

To fix broken packages:
```
sudo apt-get install -f
```
Also open synaptic package manager and click the Edit menu. Choose "fix broken."

---

