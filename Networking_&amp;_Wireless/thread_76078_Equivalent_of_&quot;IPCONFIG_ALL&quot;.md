---
title: "Equivalent of &quot;IPCONFIG /ALL&quot;"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by Leigh on 2005-10-14
I'm trying to see what DNS server my Breezy PC is using. In the Windows command line I can type "IPCONFIG /ALL"

What's the linux equivalent? I tried "ifconfig" but it doesn't give me what I want.

---

### Post by transactionlogfiller on 2005-10-14
cat /etc/network/interfaces

---

### Post by Leigh on 2005-10-14
I tried that command but it doesn't list the DNS server(s) just the IP address, mask and gateway.

---

### Post by insitu on 2005-10-14
ifconfig -a gives you information on the interfaces 
what you want should be in /etc/resolv.conf 

yours

---

### Post by gotee12 on 2008-02-26
I know it's been a looonnggg time since anyone posted to this thread, but I had the same question and created my own little script to give this info in a single command. I know it's probably not the most elegant script. And I'm sure there's a thousand other ways to do it better, but it works for me! Hope this helps someone out there.

Just open your choice of text editor, copy/paste the text below and don't forget to give it an ".sh" extension when naming the file. For example, just for kicks and giggles I named mine "ipconfig.sh".

```
#! /bin/bash
ifconfig
echo
echo Gateway"               "Interface
route -n | awk '/UG/ {printf "%-21s %s\n",$2,$8}'
echo
echo DNS Servers
awk '/nameserver/ {print $2}' /etc/resolv.conf
echo
```

After you've created the script, navigate to the folder the script is located in and run:

```
sudo chmod +x *scriptname*.sh
```

That makes the script executable from the CLI. After that I copied the script into the /usr/local/bin folder. That way you're able to simply run the script from the CLI without having to reference the folder the script was originally located in.

What's really neat is that when I connect to work via an IPSEC VPN, the script catches all of the new settings and gives both gateways in use. Wasn't expecting that without some extra work, but what do I know?

---

### Post by A$h X on 2008-07-01
Thanks, this is exactly what I was looking for. But I can't copy it into my usr/local/bin folder. I don't even have a usr/local/bin folder, I have usr/local/sbin. I also have a usr/bin folder where all my scripts seem to be located. How would I copy into there to run from terminal when cut'n'paste is not allowed?

EDIT: Quick google gave me the answer, open terminal in the same folder you saved "scriptname.sh" and type:

> sudo cp scriptname.sh /usr/bin

Then you can run the script from anywhere! :)

---

### Post by gotee12 on 2008-07-02
Glad it worked out for you A$h X!

---

