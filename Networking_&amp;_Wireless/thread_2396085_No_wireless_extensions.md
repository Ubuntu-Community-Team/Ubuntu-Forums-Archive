---
title: "No wireless extensions"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by wseng92 on 2018-07-10
My pc cannot detect wifi! 

Below are the output when I type **iwconfig**

```
    virbr0    no wireless extensions.        enp7s0    no wireless extensions.        lo        no wireless extensions.
```

Output for [B]rfkill list all
[/B]
```
    0: hci0: Bluetooth        Soft blocked: no        Hard blocked: no
```

---

### Post by wildmanne39 on 2018-07-10
Is this in a virtual machine? that is what it looks like.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wseng92 on 2018-07-10
> **wildmanne39 said:**
> Is this in a virtual machine? that is what it looks like.
No, not virtual machine

---

### Post by wildmanne39 on 2018-07-11
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will probably be able to help you.

---

### Post by wseng92 on 2018-07-11
> **wildmanne39 said:**
> Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will probably be able to help you.
Alright, will get back to you soon

---

### Post by wseng92 on 2018-07-11
I used these two commands but unfortunately it did not work

```
sudo apt update
sudo apt dist-upgrade
```

After searching for several hours, I came across with this answer [https://askubuntu.com/a/1052418/642889](https://askubuntu.com/a/1052418/642889) and it works like charm !

Here the command I used

```
wget http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.3_amd64.deb
sudo dpkg -i bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.3_amd64.deb
```

---

