---
title: "proxy authentication and sudo apt-get install !!!! help :(("
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by mono.maryam on 2008-03-24
Hi,
My internet connection is via a proxy that needs authentication ! using firefox, I have no problem as it prompts for username and passwrd !
but when using synpatic package manager or "sudo apt-get install" It can not find packages which are available via Internet ! I tried adding the following code to apt.conf
 Acquire::http::Proxy "http://myusername:mypassword@Proxy:Proxyport"; 
and then using "sudo apt-get update" but I get error 407 Proxy Authentication Required !!!!

I also tried 
export http_proxy=http://user:pass@proxy:pot/
but I get the same error !

I'm confused, what shall I do ?! Maybe It worth mentioning that my proxy username contains a dot character in it ! Does it cause any trouble ?

---

### Post by cuby on 2008-03-24
Hello, did you configure the system->preferences->network proxy?

;)
Bye

---

### Post by bapoumba on 2008-03-24
Is this an ISA proxy ?
@ cuby: apt-get uses its own config file for proxy settings (/etc/apt/apt.conf) or can acquire from bash command line.

---

### Post by Mustard on 2008-03-24
This link contains the information that you have already tried, but it may contain something that you may have overlooked in the process.

[https://help.ubuntu.com/community/AptGetHowto#head-09fab4df311ef78d0376d13547043811307c49fa](https://help.ubuntu.com/community/AptGetHowto#head-09fab4df311ef78d0376d13547043811307c49fa)

---

### Post by mono.maryam on 2008-03-30
Hi, I do not know if it is a ISA proxy, does it matter ? If It is an ISA, what shall I do ?!
And I also tried the system ->prefernces -> network proxy , It seems that It does not work at all !

---

### Post by bapoumba on 2008-03-30
> **mono.maryam said:**
> Hi, I do not know if it is a ISA proxy, does it matter ? If It is an ISA, what shall I do ?!
And I also tried the system ->prefernces -> network proxy , It seems that It does not work at all !
Please see [here]("http://ubuntuforums.org/showthread.php?t=589854"). An ISA proxy is a Microsoft proxy. There is a quoted thread that has other infos as well.

---

