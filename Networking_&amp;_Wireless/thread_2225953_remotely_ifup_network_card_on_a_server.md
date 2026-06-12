---
title: "remotely ifup network card on a server"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by kwN7kft on 2014-05-24
Hi there,

I would like to know if there is any way of getting eth0 bring up remotely.
I was on a machine where I cannot get there and made networking restart although the process hangs up and the network card cannot be online.
The idea is to make some way of doing ifup eth0 remotely.

Thanks to all who can help.

---

### Post by TheFu on 2014-05-24
Step back and think what you are asking.
You want to enable networking .... over a network.

So .... it ain't gonna' happen through eth0.

OTOH, if you have eth1, eth2m eth3 m eth1000 .... or some other network connection (perhaps wifi?) ... then there is hope.

The idea to use WoL (Wake on LAN) capabilities requires that the network interface be enabled already.

So ... the short answer is - "unlikely" - but not impossible.

---

### Post by kwN7kft on 2014-05-24
Thanks for the answer.

Is that you said that I was afraid, although the idea is that

The network card gone when I made /etc/networking restart it hangups and never could access to the remote server.

I thinking if I have a remote command to make the eth0 bring it up would be easier .

I think I got two solutions I wait impatiently till monday or tried to google it if there is anyway (i think the hope side talking)

Thanks

---

### Post by TheFu on 2014-05-24
For a remote ISP running a virtual machine for you, the thing you want to find is a "remote console"  ... console access doesn't require networking to be enabled inside the guest. Every virtual machine has a remote console.

If the machine is a physical server, then it might have a hardware remote console method too - IPMI (or is it IMPI?) ... which lets administrators remotely reboot servers, but watch the boot up process including the BIOS. Cool stuff, if it is available and connected.  [http://www.intel.com/content/www/us/en/servers/ipmi/ipmi-home.html](http://www.intel.com/content/www/us/en/servers/ipmi/ipmi-home.html)  Dell, HP, IBM all have add-on cards for their servers that do this too - DRAC, RIBLO, are the terms to search.

---

### Post by tgalati4 on 2014-05-24
Yes, IPMI is the way to go on server-grade hardware that supports it.  Another option is to create a cronjob that checks network status on the server and if the network is down, either issue an ifup or reboot or an rtcwake at an appointed time.  So if your machine is down at 3:30 pm, but you have an rtcwake set for 4 pm and you check the network at 4:05 pm and it is up, then you know it had a reboot cycle.

You could also enable rsyslog and send your server logs to another machine and monitor that machine.  If the logs show a network issue, then you can try to intervene before you are locked out.

For the OP, what are the circumstances that cause the machine to go offline?  I would work that problem rather than trying to perform a remote ifup.

---

### Post by kwN7kft on 2014-05-24
Hi there,

Thanks for the appointment, although I've tried and didn't work :(
I will try when accessing to the physical server implement rtcwake

Any opinion ..

Thanks in advanced.

---

