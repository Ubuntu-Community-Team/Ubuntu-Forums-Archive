---
title: "Connecting to a LAN HDD"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by winjeel on 2010-08-01
We have an I-O Data (that's the brandname, it's quite popular in Japan) external hard disk drive on our home LAN network. I've noticed that sometimes I could access it, and sometimes I couldn't. Now I've realised the reason. From Ubuntu 10.04 connect either LAN cable or Wifi, I need my wife's Windows computer to be switched on before my computer can recognise the LAN HDD. Or, my own computer on Windows (I run a dual boot system), and so my mini-laptop (on 10.04) can connect to the LAN HDD. 

How can I set up by Ubuntu 10.04's to connect to my home LAN external hard disc drive without being depended on a Windows computer being present?

Thanks in advance for the help.

---

### Post by cherva on 2010-08-01
Where and how is this HDD connected and shared ?

---

### Post by winjeel on 2010-08-01
> **cherva said:**
> Where and how is this HDD connected and shared ?

On a Wifi hub, but connected via lan cable, shared with two computers (one dual boot, one Windows), and a printer. Also, other devices are occasionally connected via Wifi.

---

### Post by winjeel on 2010-08-02
help?

---

### Post by jerenept on 2010-08-02
Try Places>Connect to server.
select "Windows Share" and ebter the details (IP address, folders, username etc.)

and, use an ethernet cable over wifi. it is faster and usually more reliable.

---

### Post by winjeel on 2010-08-04
Thanks. I've tried this a few times, and variations of it, and it does not work. However, I can access (read-only) via Firefox.

---

### Post by lukeiamyourfather on 2010-08-04
What protocol is used to share the drive? FTP, CIFS, NFS? This information is necessary and probably on the manufacturer's site. Once you know how the drive is shared then you can properly connect to it. Without knowing how the drive is shared its all just guessing.

---

### Post by winjeel on 2010-08-04
> **lukeiamyourfather said:**
> What protocol is used to share the drive? FTP, CIFS, NFS? This information is necessary and probably on the manufacturer's site. Once you know how the drive is shared then you can properly connect to it. Without knowing how the drive is shared its all just guessing.

The connection uses smb://

---

### Post by winjeel on 2010-08-05
Any ideas?

---

### Post by varunendra on 2010-08-05
> **winjeel said:**
> Thanks. I've tried this a few times, and variations of it, and it does not work. However, I can access (read-only) via Firefox.

Can you please deliberate the variations you have tried?
What is the message you get in Ubuntu after failing to connect? Is it something like "Cannot find windows share list..." or something similar?

If it can be directly connected to LAN then it must have an IP address of its own. Have you tried smb://xxx.xxx.xxx.xxx ?
(where xxx.xxx.xxx.xxx would be replaced by the drive's IP.)

If it does not work, please provide the model no. of the drive so that we can try to find out its specs. from the manufacturer's website.

---

