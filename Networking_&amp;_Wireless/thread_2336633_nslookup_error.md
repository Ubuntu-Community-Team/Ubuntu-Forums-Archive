---
title: "nslookup error"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by yosoufe on 2016-09-09
Hi

I am trying to use nslookup command but I get the following error. 

```

$ nslookup google.com
nslookup: /opt/Xilinx/Vivado/2016.2/lib/lnx64.o/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /usr/lib/x86_64-linux-gnu/libicuuc.so.55)


```

What is wrong here? what does nslookup do with Xilinx vivado?

I have to say I am totaly new to linux (and also vivado)

I have added the followint lines to .bashrc to be able to run vivado. After commenting them it works fine. why?
```

# Add VIvado command to the shell
. /opt/Xilinx/Vivado/2016.2/settings64.sh

```

---

### Post by wildmanne39 on 2016-09-09
I ran the command and got:
```
nslookup google.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.3.206
```

This is what I found on Xilinx vivado
[https://en.wikipedia.org/wiki/Xilinx_Vivado](https://en.wikipedia.org/wiki/Xilinx_Vivado)

---

### Post by steeldriver on 2016-09-09
We'd need to see what's inside the /opt/Xilinx/Vivado/2016.2/settings64.sh file - at a guess, it messes with some library path variable(s)

---

