---
title: "ssh error &quot;X11 forwarding request failed on channel&quot;"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by cyclingchap on 2014-03-29
I am having real problems getting GUI programs to run on a remote 'client' computer after logging into a server. Both client and server are running ubuntu 12.04.

The client is a 32 bit netbook and the server a 64 bit laptop.

After trying everything, I eventually simply tried ssh logging into the server computer from a terminal IN the server computer itself. I STILL get the "X11 forwarding request failed on channel" and "Error: Can't open display:" when trying to run a GUI like xclock!

I have in my sshd_config file:

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
PermitRootLogin no
AllowTcpForwarding yes
X11UseLocalhost yes
AddressFamily inet

and in my ssh_config file
#   ForwardAgent no
ForwardX11 yes
# X11DisplayOffset 10
ForwardX11Trusted yes
XAuthLocation /usr/bin/xauth

I'm logging in either using ssh -X -v user@ipaddress or ssh -Y -v user@ipaddress.

I cant get the X11 to forward.

I have tried everything in these wiki's:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Forwarding](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Forwarding)
[https://wiki.archlinux.org/index.php/Ssh#X11_Forwarding](https://wiki.archlinux.org/index.php/Ssh#X11_Forwarding)

I'm kind of new at setting up ssh, so what am I doing wrong? :(

---

### Post by houstonbofh on 2014-03-29
I do this often, and I have never had to configure anything from within X to make it work.

So, start with the basics.  Is X client installed on your server?  How was it installed?

Is there any firewall or filtering between you?

Are you doing anything with sudo?  (Sudo can brake pipes...)

---

### Post by cyclingchap on 2014-03-29
Thanks for helping.

So I don't know if X client is installed. Could you explain this to me?

The only things I have installed in this regard (beyond what comes packaged with a standard Ubuntu 12.0.4 install)  are openssh-server.

I have the same issue whether ufw on the server is switched off or on. When ufw is on I have set up a rule to allow communication on channel 22.

But even with ufw switched off on both client and server machines I have the same problem.

I have done nothing with sudo other than install the openssh-server.

Port 22 is open on both machines, if it wasn't I'm guessing I wouldn't be able to log in via ssh at all (which I can, just no GUI/X11 forwarding).

---

### Post by SeijiSensei on 2014-03-30
Sounds like the server doesn't have the X infrastructure installed which is standard for Ubuntu Server.  See if running "sudo apt-get install xorg" on the server solves the problem.

---

### Post by cyclingchap on 2014-03-30
I think that was it. I already had that installed, but just reinstalled it, and that seems to have dome the trick.

Thanks.

---

### Post by houstonbofh on 2014-03-30
I actually install a minimum X server with "apt-get install synaptic" or "apt-get install system-config-printer" since it will install the bare minimum to make those X apps run.  But it does not install all of gnome, or nautlius, so it may not fit your needs.  If you install the entire desktop, make sure you "apt-get purge lightdm" to keep the server in text only mode.

---

