---
title: "how-to network two computers"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by noob92 on 2010-05-06
ok i have one computer windows xp SP2 and one computer Ubuntu 10.4 and the windows box has the wireless adapter and i need to connect with RJ-45 from the window box to Linx box and be able to access the Internet with the linx box. how do i need to do this?

---

### Post by HarrisonNapper on 2010-05-06
Why don't you cable it to the router directly?

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

---

### Post by noob92 on 2010-05-06
> **HarrisonNapper said:**
> Why don't you cable it to the router directly?

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

the cable is not long enough

---

### Post by Shark_AtK12 on 2010-05-06
> **HarrisonNapper said:**
> Why don't you cable it to the router directly?

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

From what I understand he has a wireless adapter that is connected to the windows box and wants o share it with Linux. I am unsure but currently looking

---

### Post by noob92 on 2010-05-06
> **Shark_AtK12 said:**
> From what I understand he has a wireless adapter that is connected to the windows box and wants o share it with Linux. I am unsure but currently looking


yes that is correct

---

### Post by HarrisonNapper on 2010-05-06
> **Shark_AtK12 said:**
> From what I understand he has a wireless adapter that is connected to the windows box and wants o share it with Linux. I am unsure but currently looking

Doesn't seem like it would be possible to share the wireless adapter through an ethernet cable afaik. You might could have the windows box pass all network data through, but don't know how you would have it shared. 

You could do something like feed the data through telnet to the client machine from Windows, but I don't know enough about Windows to say definitively how that would be done.

---

### Post by spiky001 on 2010-05-06
just to verify the windows has the internet then linux is connected via etho cable, can you not in the windows machine select share network cable I,ve not got windows running at moment so cant check

---

### Post by Shark_AtK12 on 2010-05-06
I found [this]("http://www.linuxforums.org/forum/linux-networking/47591-windows-sharing-internet-connection-linux.html") and it seems like it will help you. One thing to remember is to make sure the cable you are connecting the two pcs together is a crossover cable. An easy way to tell is to look at the connectors and you should be able to see the colored pairs inside. The green/orange are swapped.

Enable Internet Connection Sharing in Windows->[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

### Post by Shark_AtK12 on 2010-05-06
> **HarrisonNapper said:**
> Doesn't seem like it would be possible to share the wireless adapter through an ethernet cable afaik. You might could have the windows box pass all network data through, but don't know how you would have it shared. 

You could do something like feed the data through telnet to the client machine from Windows, but I don't know enough about Windows to say definitively how that would be done.

Could he just bridge the wireless and ethernet adapters? I never messed with it but it let me do it on my laptop

---

### Post by spiky001 on 2010-05-06
if i remember there is a wizard that takes you through it and yes you select wirleess as internet then bridge it with lan

---

### Post by Palanthas on 2010-05-06
I think I may have done this before and sadly I can't recreate it now since I don't have a machine wireless and wired and WinXP we'll see if I remember correctly.

You should be able to go into Network Connections (where you see icons for Local area Network and Wireless area network) and select both the wireless and wired connections icon by selecting one connection then while holding the 'CTRL' select the other connection. Right click on one of the selected icons and choose "Bridge Connections".

I want to think that may do the trick, but its been a long time since I tried this so I may be wrong... If it doesn't work make sure you un-bridge the connection before moving on. Also, as Shark_AtK12 said, make sure you are using a cross-over cable between the computers.

---

### Post by pricetech on 2010-05-06
ICS or Internet Connection Sharing is probably your best bet.  Your windows box will serve as a router for your Linux box.

But do be sure to use a crossover cable between the two boxen.

---

