---
title: "IP address"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by gabmuks on 2014-08-31
Hello and good day.
Am trying to network two Xubuntu PC's together to share files.

Am trying to follow instructions given in threads on these Ubuntu Forums.

The instructions require an IP address.
I have so far used ifconfig -a

But it did not produce anything that resembles an IP address at least from the examples I've seen on these forums.

The ifconfig -a command did give me a MAC address I think, but the networking instructions I've seen here ask for an IP address.

According to these forums an IP address looks like this: [LEFT][COLOR=#000000][FONT=Ubuntu Mono]192.168.0.100:8000
[/FONT][/COLOR][/LEFT]
But I cannot get that using ifconfig -a.

I went to a site called: What is MY IP Address and got 70.226.167.125 for my IP.

But I get the same IP for both computers when using that site.

Very confusing....any ideas from you all?

---

### Post by deadflowr on 2014-08-31
Post the full output of ifconfig...

---

### Post by Elfy on 2014-08-31
what DO you seen when running ifconfig?

```
eth0      Link encap:Ethernet  HWaddr 90:2b:34:62:06:29  
          **_inet addr:192.168.1.64_**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe62:629/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21708 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:23777809 (23.7 MB)  TX bytes:2892663 (2.8 MB)
```

---

### Post by sbnwl on 2014-08-31
Can you post the output of 
```
ifconfig -a | grep "inet addr"
```

---

### Post by Iowan on 2014-08-31
Are those the only two computers connected - or are they both on a network with a router, other machines, etc?
If they are connected only to each other (or a switch/hub) then you may need to manually assign an IP address to each machine.

---

### Post by ajgreeny on 2014-08-31
You LAN IP is the "inet addr" that is shown in the ifconfig output.  That is the one that your router has given your machine.  My router allows me to reserve IPs for each machine attached so they do not change.

The 70.226.167.125 that you get from the website, that I have also used before now, is your WAN IP address, and was assigned by your ISP at the time your router connected to the ISP.  If you turn off the router and then reboot it later you may find that the WAN IP has changed.

---

### Post by gabmuks on 2014-08-31
> **sbnwl said:**
> Can you post the output of 
```
ifconfig -a | grep "inet addr"
```

Thank you all for kind reply.

Here is results from terminal.

liz@ubuntu:~$ ifconfig -a | grep "inet addr"
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
liz@ubuntu:~$

Both computers connected to same router with cat5 cable.
Nothing else is connected to the router.

---

### Post by deadflowr on 2014-08-31
So 10.0.0.2 is the ip address.
Not typical, but still legit.

Also, which sharing method are you using?
(I guess that got lost in the ip issue)
May or may not have relevance.

---

### Post by gabmuks on 2014-08-31
> **deadflowr said:**
> So 10.0.0.2 is the ip address.
Not typical, but still legit.

Also, which sharing method are you using?
(I guess that got lost in the ip issue)
May or may not have relevance.
Yes. Thanks for reply. I do not know which sharing method to use. But the ones I have found on line so far, require an IP address.
My goal is to transfer all documents from storm damaged PC, (USB inputs are toasted), to a functional laptop. The files are to large and too many to email. What sharing method do you suggest? Thanks for your time.

---

### Post by ajgreeny on 2014-08-31
I have only seen that style IP address when running a virtual machine in VirtualBox.  Mine is then 10.0.2.15

 Can we check that this is not the case here as it will probably make some difference to the connection.

You could also try using **Transfer-on-lan** which is a simple java application and needs no installation.  Get it from [https://code.google.com/p/transfer-on-lan/downloads/detail?name=TransferOnLAN-0.6.1.tar.gz&can=2&q=](https://code.google.com/p/transfer-on-lan/downloads/detail?name=TransferOnLAN-0.6.1.tar.gz&can=2&q=) and simply run the TransferOnLAN.sh shell-script in the extracted archive to run the app.  You need to run the application on both machines, and you will then see both machines in the TOL windows.

---

### Post by gabmuks on 2014-08-31
> **ajgreeny said:**
> I have only seen that style IP address when running a virtual machine in VirtualBox.  Mine is then 10.0.2.15

 Can we check that this is not the case here as it will probably make some difference to the connection.

You could also try using **Transfer-on-lan** which is a simple java application and needs no installation.  Get it from [https://code.google.com/p/transfer-on-lan/downloads/detail?name=TransferOnLAN-0.6.1.tar.gz&can=2&q=](https://code.google.com/p/transfer-on-lan/downloads/detail?name=TransferOnLAN-0.6.1.tar.gz&can=2&q=) and simply run the TransferOnLAN.sh shell-script in the extracted archive to run the app.  You need to run the application on both machines, and you will then see both machines in the TOL windows.
Thanks much!
That is interesting what you said about virtual machine. How can I find out if that is happening? If it is so, It is not something I have caused. At least not intentionally. Could someone else have done this without my knowing it?

---

### Post by lisati on 2014-08-31
The 10.0.0.x style address isn't confined to virtual box. By default, my main router/modem hands out addresses in the 192.168.1.x range, and my spare router hands out addresses in the 10.0.0.x range.

---

### Post by ajgreeny on 2014-09-01
> **lisati said:**
> The 10.0.0.x style address isn't confined to virtual box. By default, my main router/modem hands out addresses in the 192.168.1.x range, and my spare router hands out addresses in the 10.0.0.x range.
Thanks for that info, I have never seen anything other than 192.168.#.# for IP addresses, so it is interesting to see your comment.

@ gabmuks

If you didn't install the OS as a VM in VirtualBox you can forget about my question; there is no way it could happen by mistake or without your knowledge.

---

