---
title: "Log into Windows Server"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by antw on 2007-05-15
I have recently installed ubuntu onto a Dell 1501 laptop and am wondering how do I log into a windows server. The situation is that my kids would take normally log into the school network using the schools laptops. The laptops have windows XP professional installed and they just enter their username, password and the domain is already selected. 

Now they have the option to use their own computer which has ubuntu installed. First, are they able to log into the network? Second, how?

Currently the ubuntu computer sees the network and connects but she is unable to see her "home" drive. Also she does not have internet access through the network.

thanks for any help.

---

### Post by ghostboy on 2007-05-15
> **antw said:**
> I have recently installed ubuntu onto a Dell 1501 laptop and am wondering how do I log into a windows server. The situation is that my kids would take normally log into the school network using the schools laptops. The laptops have windows XP professional installed and they just enter their username, password and the domain is already selected. 
 
Now they have the option to use their own computer which has ubuntu installed. First, are they able to log into the network? Second, how?
 
Currently the ubuntu computer sees the network and connects but she is unable to see her "home" drive. Also she does not have internet access through the network.
 
thanks for any help.
 
To answer your question, yes they can log into the server using Ubuntu. The best part is that there is a way to log in without having to use WINE or any other emulators. 
 
Applications>System Tools (I think, Im writing this at work on my XP Box)>Krdc.
 
Krdc is the open-source version of Windows Remote Desktop Connection. Click Krdc, input the information. Username, password, domain, etc. Then you should be able to log in, and see the home folder. Let me know if this helps. I will edit this post when I get home, if Im missing any info and double check the path to Krdc. Hope this helps, at least a little.

---

### Post by david_kt on 2007-05-15
[QUOTE=antw;2657688]
Now they have the option to use their own computer which has ubuntu installed. First, are they able to log into the network? Second, how?

Currently the ubuntu computer sees the network and connects but she is unable to see her "home" drive. Also she does not have internet access through the network.

thanks for any help.[/QUOTE

To log in to network is easy. In dapper,just go to 

```
 places> network server > windows network
```

 and then it will ask for username, domain, and password. Key in the usual username and password. For my case, domain is not neccesary to key in, but if you are unable to login, key in the right domain.

As for internet access, if opening firefox does not prompt you for password and you could not browse, may be they use MS ISA to manage internet connection. In this case, you will need to installed NTLMAPS:

```
sudo apt-get install ntlmaps
```

Make sure universe resp is selected, otherwise it will not find it. You will need detail MS ISA configuration to configure ntlmaps (what I remembere are proxy server, port and domain name). User name and password would be the usual windows' ones.

After that, you should configure internet connection in firefox to use:

proxyserver: localhost
Port: 5865 (or any port you choose during ntlmaps configuration).

Please see [here]("http://ntlmaps.sourceforge.net/") for more details.

DK

---

