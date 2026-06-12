---
title: "Cisco SSL WebVPN  - Application launch fail"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by almibuntu on 2009-10-12
Hello all,

I am new with Linux and would like to check if anybody found this same problem...

I'm trying to connect with a Cisco VPN with the WebVPN and using Firefox in Ubuntu 9.04

I can get into the login screen, and once logged in it seems that it starts loading the application but then it fails. The error that i'm getting is:

"The installer was not able to start the Cisco SSL VPN Client."

My other attemps have been:
- Try to connect with AnyConnect but I get the following error: "AnyConnect package unavailable or corrupted. Contact your system administrator."
- Download IE for Linux and try to execute VPN from there, but not working either...

Any help is welcome! :)

---

### Post by yeats on 2009-10-12
I don't know if this will work for you, but it does for me... Go to the Synaptic Package Manager and install a program called vpnc.  Then open a terminal and type 'sudo vpnc-connect'.  You will get this dialog:

```
you@your-desktop:~$ sudo vpnc-connect
[sudo] password for you:
Enter IPSec gateway address: gate.example.org
Enter IPSec ID for gate.example.org: user1
Enter IPSec secret for user1@gate.example.org: *password*
Enter username for gate.example.org: user1
Enter password for user1@gate.example.org: *password*
VPNC started in background (pid: 6207)...

```

In my case, the IPSec ID/secret is the same as my username/password, but that will depend on how yours works.

Hope that helps.

---

### Post by casevh on 2009-10-17
A couple of suggestions.

The Cisco SSL WebVPN features require that the Sun Java plugin for Firefox is installed.

The sys admin must also have the Linux version of the AnyConnect client install on the remote access server.

casevh

---

