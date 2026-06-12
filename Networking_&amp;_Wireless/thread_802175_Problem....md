---
title: "Problem..."
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Nikolasr on 2008-05-21
Hello i have cable internet and i have allow only to view local sites,why i like to see and public sites like [http://www.google.com](http://www.google.com)

But it's says server not found

I have modem motorola SB5101

Thanks
Nikolasr

---

### Post by chili555 on 2008-05-21
May we please see the result of a terminal command:```
cat /etc/resolv.conf
```Thanks.

---

### Post by Nikolasr on 2008-05-21
I will try if not i will post again if yes i will sloved the theard

Thanks anyway

---

### Post by chili555 on 2008-05-21
This command is not going to solve your problem, it's going to tell us if you have useful DNS servers in your */etc/resolv.conf* file, or if the file exists at all. 

DNS nameservers are the mechanism by which 'www.google.com' gets translated to '74.125.47.147' which is what the internet needs.

If your */etc/resolv.conf* file doesn't exist or has no nameserver listed or is, in some way, malformed, we'll fix it together. In order to know what, if anything, needs to be fixed, we need to see it.

---

### Post by Nikolasr on 2008-05-21
I know the dns server and are 89.185.223.66 it's one server default gateway 89.185.192.1 my ip are 89.185.193.153

---

### Post by chili555 on 2008-05-21
In any case, may we please see the */etc/resolv.conf* file?

---

### Post by Francewhoa on 2008-12-27
Rebooting the cable modem worked for me. [Details and more solutions can be found here.]("http://ubuntuforums.org/showpost.php?p=6443197&postcount=3")

---

### Post by Nikolasr on 2009-01-28
Hello guys...here i'm...i have finally installed ubuntu..i will try commands now and solutions if is working i will edit this post

---

### Post by Nikolasr on 2009-01-28
> **chili555 said:**
> May we please see the result of a terminal command:```
cat /etc/resolv.conf
```Thanks.
I have got no permission to do that command

---

### Post by Nikolasr on 2009-01-28
Anyone help..i have also tryed to restart my cable modem, i have restarted but no effect

---

