---
title: "How to share a folder via hamachi? Hamachi ok, how to share?"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by neander on 2007-08-19
I have hamachi set up on 7.04, and have joined the hamachi network I use with windows boxes. I've never shared a folder under linux and my first attemp to map a drive to the linux box hamachi node like so failed:

\\5.12.23.453\testshare

testshare is a folder I created at /home/mylogin/testshare. Am I going about it correctly, and simply don't have the perms set up right so testshare would be available? The only perm I changed from the default for that dir was that hamachi group has folder perms set to create and delete files. The error when I try to map a drive to that address above is that the network path cannot be found.

I think this has little to do with hamachi and is all about me not knowing how to share a folder under linux.

---

### Post by jpkotta on 2007-08-19
Do you have Samba (server) installed?  If not, get that and Swat.  For a quick and dirty method, I would recommend an SSH server (Linux) and WinSCP (Windows).  Hamachi only creates a VPN, you still need a higher layer to do useful things.

---

### Post by neander on 2007-08-19
Thanks for posting. I don't have samba installed, and the nominal reason (besides the fact that I know little of it and am not much with network config) is that the linux box and the widows boxes use different ip address ranges. They are physically near each other but the linux box is in a sort of dmz, it's an http server to the net. My impression is that samba is good for LAN connectivity? Hamachi usually makes it simple to provide a vpn pipe between pcs that would otherwise be isolated.

Later I will have a linux server at a webhost that I was planning to remote into using hamachi and vnc.  

Do you still think I don't need hamachi?

Do I still need samba in order to get hamachi to work?

---

### Post by jpkotta on 2007-08-19
You probably don't need Hamachi.  You can probably just configure whatever is creating the DMZ to let Samba traffic through.  

I am going to assume that the Linux box is a web server and not much more, and you want a way occasionally upload files to it, not to turn it into a file server for your network.  In that case, put OpenSSH server on the Linux box and use WinSCP to copy files to it.  Even in the case of a remote host, you will not need Hamachi.  Use a free DNS service like No-IP and just use SSH (which is encrypted).

---

### Post by neander on 2007-08-20
The thing is, I understand hamachi, and don't really have a handle on dmz config. What will serve my very simple need is to be able to share a folder via hamachi.

I found that common-samba is installed, seems to have been by defualt with 7.04. Can someone tell me step by step how to share a folder?

---

### Post by neander on 2007-08-20
I found the system/administrate/shared folders menu item, and added shared folder support there for a specific folder:

/home/mylogin/shared01

Now with hamachi on I can at least hit the ubuntu box with the address //5.5.5.55/shared01. But I'm prompted to supply a login/pswd, none of the ones I'm aware of work. What step am I missing?

There is no samba menu item after it's installed? I've not seen one.

---

### Post by neander on 2007-08-20
Added a user to samba and it all works

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

---

### Post by motin on 2007-09-05
Can you share a printer over hamachi as well? I have been battling with this, but can't connect to the cups interface regardless if the hamachi client uses XP or Feisty... Would you mind trying this out? [Thread >>]("http://ubuntuforums.org/showthread.php?p=3313212#post3313212")

---

