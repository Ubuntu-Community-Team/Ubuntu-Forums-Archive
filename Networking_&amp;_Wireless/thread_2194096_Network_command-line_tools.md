---
title: "Network command-line tools"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by Jonathan Precise on 2013-12-16
Hello all!

Yes, I'm back, as I was busy for a long time. But that's another story.

I'm working on a network troubleshooting program, and want to learn some commands to try to fix common network issues. For example:


[LIST=1]
[*]Renew the IP adress [Achieved in the second step (I think)]
[*]Reset wireless network adapter [SOLVED - Thank you!]
[s]Restart(, reset, or reboot) the router[/s]
[*]Purge the DNS resolver cache [SOLVED - Thank you!]
[s]Restart, reset, or reboot the modem (optional)[/s]
[/LIST]


What are the commands to do those tasks?

Thanks in advance!

PS. If I posted in the wrong section, send me a [message]("http://ubuntuforums.org/private.php?do=newpm").

---

### Post by tgalati4 on 2013-12-16
To see what tools are already on your system:

```
apropos dhcp
apropos network
```

There are many tools that handle the tasks above.  *nm-tool* is one.  *nmcli* is another.  Dig into the source code for the tools that do the stuff that you want to see the low-level commands.

---

### Post by Jonathan Precise on 2013-12-16
> **tgalati4 said:**
> There are many tools that handle the tasks above.  *nm-tool* is one.  *nmcli* is another.

I have dug deep into those you mentioned. Unfortunately, I can only find how to deactivate the interface wlan0. [EDIT: The help page shows to run:
> Usage: nmcli device { COMMAND | help }

  COMMAND := { status | list | disconnect | wifi }

  status
  list [iface <iface>]
  disconnect iface <iface> [--nowait] [--timeout <timeout>]

Yet it outputs:
> Unknown parameter: disconnect
So I don't know what to do here]

However, I need to see one that can reset ANY wireless/wired network card, as this program would be published to the world, and I can't take the risk that some people have another iface than wlan0.

Any other ideas? Anyone?

PS. I'm still looking at the manual pages of the programs the 2 commands outputted. I'll reply if I find anything.

---

### Post by iebo on 2013-12-16
hope this could help u

- dns flush

sudo /etc/init.d/nscd restart

-new ip

sudo ifconfig wlan0 192.168.1.98 netmask 255.255.255.0 broadcast 192.168.1.255


- change mac address

macchanger --mac 00:00:00:00:00:00 wlan0

---

### Post by tgalati4 on 2013-12-16
You are correct.  Disconnect feature was either removed or not implemented.  You would have to examine the source code (and any notes contained within) to find out why.

*rfkill* is a more generalized tool for shutting off (blocking) wireless devices.

---

### Post by Jonathan Precise on 2013-12-16
> **iebo said:**
> sudo /etc/init.d/nscd restart

sudo: /etc/init.d/nscd: command not found.

> **iebo said:**
> sudo ifconfig wlan0 192.168.1.98 netmask 255.255.255.0 broadcast 192.168.1.255

This just ruined my internet connection! Re-connecting fixed this.

> **iebo said:**
> macchanger --mac 00:00:00:00:00:00 wlan0

I think that would just totally mess up everything in my connection.

---

### Post by iebo on 2013-12-16
> **Jonathan Precise said:**
> sudo: /etc/init.d/nscd: command not found.



This just ruined my internet connection! Re-connecting fixed this.



I think that would just totally mess up everything in my connection.

ofc this command will disconnect u  :) how come u want new ip without destroying ur current connection ? 

macchanger --mac 00:00:00:00:00:00 wlan0  

 mac changer is helpful i use it when i'm looking to have new mac address (not original )

---

### Post by Jonathan Precise on 2013-12-16
> **iebo said:**
> ofc this command will disconnect u  :) how come u want new ip without destroying ur current connection ? 

I put **_RENEW_** the IP address, not destroy the IP address. Anyways, this was solved by rfkill. Thanks anyways.

-----------------------------------------------------

@tgalati4, Thank you!!!!!!!!!!!!!

---

### Post by Jonathan Precise on 2013-12-16
Just need #3 and optionally #5. Thanks in advance.

---

### Post by steeldriver on 2013-12-16
Are you actually running an Ubuntu box as a router (or modem ?!) - or are you talking about rebooting an external device? If the latter, then you will need to refer to the device's user / API documentation. For most consumer grade routers that would be a web interface - you might be able to access it using curl. Some modems provide a telnet interface.

---

### Post by Jonathan Precise on 2013-12-16
@steeldriver, it's the latter. However, I found that in windows Network Magic it had a feature that it could reboot a router (external device). Just hoped there was something like that achievable here. :(.

---

### Post by Jonathan Precise on 2013-12-17
Anyone?

I really need some help.

---

### Post by SeijiSensei on 2013-12-17
The answers to #3 and #5 will depend on the router and modem in use and whether they expose any interfaces that Linux can talk to.  Most residential routers use a web-based interface which is hard to program for.  If it is running a Linux-based router OS like dd-wrt or Tomato, you might be able to script a command-based solution that talks to the router over SSH.

As for the modem, I think that is probably a hopeless quest.

One blunt solution is to connect both devices to an electrical strip controlled by an [X10 device]("http://www.dummies.com/how-to/content/controlling-your-linux-smart-home-with-x10.html").  Then you could tell the X10 device to shut off the power.

---

### Post by Jonathan Precise on 2013-12-17
So it's going to be very hard to work that out?

---

### Post by steeldriver on 2013-12-17
Here's something to get you started --> [http://lmgtfy.com/?q=curl+post+router+reset](http://lmgtfy.com/?q=curl+post+router+reset)

For information specific to your router, add the router vendor name and/or model number to the query

---

### Post by tgalati4 on 2013-12-17
I would guess that the Windows Network Magic tool sends "magic packets" to routers with proprietary operating systems which allows them to reboot remotely.  It would be difficult to write a generalized tool to reset a router or modem because there are so many different brands with different firmware.  

As *steeldriver* has suggested, for a Netgear router, you would create a script using information from this tutorial:

[http://www.makionv.com/2011/05/how-to-reboot-your-netgear-via-command.html](http://www.makionv.com/2011/05/how-to-reboot-your-netgear-via-command.html)

Each router has a different way navigating through the admin web page to get to the reset button.

How many routers do you have to support?  Why are we rebooting routers?  Why am I asking so many questions?

---

### Post by Jonathan Precise on 2013-12-20
> **tgalati4 said:**
> How many routers do you have to support?

I have to support at least Linksys, Cisco, and NetGear (theoretically 2, as Cisco and Linksys are made by the same company).

[HR][/HR]
> **tgalati4 said:**
> Why are we rebooting routers?

That's one of the features of network magic: in the auto repair mode, it resets the router. I wanted to implement that feature in my network repair program.

[HR][/HR]
> **tgalati4 said:**
> Why am I asking so many questions?

I probably didn't explain myself properly. I'm working on a basic network troubleshooter, and I liked the "Router Reset feature" it had. Just wanted to implement it here.

[HR][/HR]
Also: is there any command to _purge the DNS resolver cache_, as that question hasn't been answered yet?

---

### Post by Jonathan Precise on 2013-12-20
Anyone?

---

### Post by steeldriver on 2013-12-20
What dns resolver cache? if you are referring to dnsmasq, then I *think* that in the standard invocation (at least in 12.04) it forwards queries and does not actually cache - for example, if you run a query from the command line such as

```

dig google.com

```

and then disconnect your network interface and try it again you should see it query dnsmasq on localhost (e.g. 127.0.0.1:53) again but return no records.

Again in the standard (desktop) 12.04 configuration, dnsmasq runs under network-manager

```

$ pstree -s $(pidof dnsmasq)
init&#9472;&#9472;&#9472;NetworkManager&#9472;&#9472;&#9472;dnsmasq

```

so restarting the network-manager service should clear it if it *is* actually caching. It should also be possible to do it directly via DBUS (method ClearCache ??).

Be aware that the configurations of networkmanager / resolvconf / dnsmasq have changed somewhat over recent Ubuntu versions so you will need to do your homework to decide how to make whatever method you chose robust / maintainable - I hope this at least gets you started

---

### Post by Jonathan Precise on 2013-12-25
Thank you! I'm using "initctl" to restart the network manager.

Edit: Anyone know the solution for the router reboot?

---

### Post by Jonathan Precise on 2013-12-30
Anyone?

Please?

---

### Post by steeldriver on 2013-12-30
If you are still looking for help in rebooting a router remotely, then I don't think anyone will be able to help you with the specifics until you provide details about the router(s). 

Depending on the hardware / firmware / software the answer will likely vary from

[LIST]
[*]can be done with a simple curl command 
[*]can be done via telnet 
[*]can be done via telnet, but only after modification to the router's software and/or firmware to enable the telnet service 
[*]can be done after completely replacing the router OS e.g. with tomato or DD-WRT 
[*]can't be done 
[/LIST]

---

### Post by Jonathan Precise on 2013-12-31
Ok. Shall mark as solved.

---

