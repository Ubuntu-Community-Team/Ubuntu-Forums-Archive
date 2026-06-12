---
title: "rdesktop to a comp on Windows S.B.S. 2003 network"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by mmendez on 2007-05-03
Hi my situation is that I am trying to connect to a computer on a LAN that is connected to a Windows Small Business Server 2003. When I use rdesktop no matter what I have tried I dont get the results that I need.
Here are my trials:

1. Port forwarding from router to comp. then rdesktop #.#.#.#: port (port being the one setup @ router)
Results: No good rdesktop gives me this (Autoselected keyboard map en-us) then it just hangs there

2. I tried just the i.p. address to ensure rdesktop was ok
Results: I get the login screen for Server

3. I tried rdesktop -n FDESK1 #.#.#.# (FDESK1 being the comps name) (I also tried fdesk1)
Results: I get the login screen for the Server still

Any Ideas?

Thanks

---

### Post by dbott67 on 2007-05-03
I have successfully used tsclient (which is a GUI client for rdesktop, VNC, Citrix, etc.) to connect to my servers at work.

RDP uses TCP port 3389 by default, so make sure that your firewall/router is forwarding from the external interface to the internal IP of the device you wish to connect to.

Also, make sure any software firewalls are disabled.  The fact that you can connect from an internal computer indicates that this is likely not a problem.

Then, from Ubuntu, open the **Terminal Server Clien**t (Applications > Internet > Terminal Server Client).  Enter the external IP, port number & RDP protocol, as well as any other desired settings for resolution & colour depth, etc.

-Dave

---

### Post by mmendez on 2007-05-03
I tried it through the gui and get the same results:

The router has 3389 forwarded to the server, and I put 2867 to the computer that I want to connect to. 

When I type #.#.#.# it goes to the server because as you mentioned port 3389 is rdesktop's default and is forwarded to the server, that's ok but I don't need the server for now.
I need to get to the comp on port 2867 and heres what happens:

first two pics are to purposely connect to server, last 2 are the attempts at the computer the error comes back after about 60 secs or so.

Thanks for the help.

---

### Post by dbott67 on 2007-05-03
On the router, do you have port forwarding configured like this:

1. Port 3389 on external i/f of router ---> forward to IP address of server on port 3389
2. Port 2867 on external i/f of router ---> forward to IP address of other computer on port 3389

Then connect to IP of router on port 2867 (as above) and the router *should* forward to other computer on port 3389.

If you have access to the machine, you can verify if the RDP protocol is running.  From the computer, type the following:
```
C:\Documents and Settings\dbott.STCATHARINES>netstat -a -n | find "3389"

Active Connections

  **Proto  Local Address          Foreign Address        State**
  TCP    0.0.0.0:[COLOR=Red]3389[/COLOR]           0.0.0.0:0              [COLOR=Red]LISTENING[/COLOR] 
```

In this case, my computer is "listening" on port 3389.  Also, make sure any security software is disabled (Norton Firewall, McAfee, Windows Firewall, etc.).  Many software security suites come with AV, spyware and firewall software that can be a royal pain.

-Dave

---

### Post by mmendez on 2007-05-03
Almost got it but something is missing. I followed example number two and IT WORKED but with the server. I changed the server's port to 2688 external and 3389 internal with the router's "Virtual Server" settings. This worked when I tried ```
rdesktop #.#.#.#:2688
``` and when I did the same for the others I get nada. I tried to compare the server to the comp and everything seems the same. I tried with firewall disabled and everything else I could think of. Oh and btw I tried to execute the code you posted I ran a command prompt and from Documents and Settings I ran everything exactly as you typed and I got unknown command or something of the sort.

Really appreciating the help your giving.

---

### Post by dbott67 on 2007-05-03
The code is just:
```
netstat -a -n | find "3389"
```
What are the other machines?  Windows XP?  Make sure that RDP is enabled and that you have a valid user account to connect with:

[IMG]http://www.jakeludington.com/images/xp/rdc/rdc_system_properties.gif[/IMG]

Also, check  the Windows firewall (disable it altogether for testing purposes):

[IMG]http://www.thinsoftinc.com/images/support_firewall.jpg[/IMG]

-Dave

---

### Post by mmendez on 2007-05-03
You know sometimes I just feel like getting a rope and taking myself outback. Remote Desktop was not enabled!!!!! On behalf of my defense it was on the "exceptions list" in the firewall and so I thought no further on it.

Either way **A HUGE THANKS TO YOU** =D>  thanks for the help

---

### Post by dbott67 on 2007-05-03
Don't worry, we've all done it.

Glad you got it going!

-Dave

---

