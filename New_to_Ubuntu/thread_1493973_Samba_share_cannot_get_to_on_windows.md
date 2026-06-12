---
title: "Samba share cannot get to on windows"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by 0xCAFEFACE on 2010-05-26
Hi all,

So I have set up a samba server within my windows domain group, I have access to read LDAP users, I've joined the domain, I can do things like

$ smbclient '\\devbox\username' -U username

And I can explore around in the share using that command, I can see all shares and such using things like 

$ smbclient -L devbox

HOWEVER, when I open up MS Windows explorer on another networked machine, I cannot gain access into the devbox shares. Please note that I am working in a domain not a workgroup.

Logins such as:
User: username
Pass: password 

These do not authenticate and I receive an error that says I don't have access. Now, when I try to login with something such as:

User: DOMAIN\username
Pass: password 

I get an "unsuccessful login" alert (different from previous error).

Now I'm not sure what the problem is here, I have a few theories but I'm new to samba.

[LIST=1]
[*] I need to use the smbpasswd command -- I keep getting the error "Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE"
[*] Something to do with firewalls, but I'm positive I don't have those installed yet, unless something was defaulted.
[*] I think I played with PAM once to set up the passwords (I don't understand how PAM works), but I'm unsure (this was months ago). I'm afraid this may have messed things up for myself.
[/LIST]

Version of Ubuntu: 2.6.31-20-server #58-Ubuntu SMP x86_64 GNU/Linux

---

### Post by -humanaut- on 2010-05-26
Here's how I accessed a Samba share from my network. I would go to Places --> Network
then hit ctrl+l type: smb://windows.ip.address 

For some reason thats always worked for me and I've never got the more conventional ways to work for some reason but I have really tried either. Make sure the windows machine is scanning for your system.

---

### Post by 0xCAFEFACE on 2010-05-26
Not sure what I've done using smbpasswd but it works now :). I'll document this better when I'm trying to move into production so we get the knowledge into the public.

> **-humanaut- said:**
> Here's how I accessed a Samba share from my network. I would go to Places --> Network
then hit ctrl+l type: smb://windows.ip.address 

For some reason thats always worked for me and I've never got the more conventional ways to work for some reason but I have really tried either. Make sure the windows machine is scanning for your system.

Sorry I'm not using any GUI. There's no reason to run a GUI on a server when all the commands are available on the CLI.

---

