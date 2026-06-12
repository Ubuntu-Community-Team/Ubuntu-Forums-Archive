---
title: "OpenSSH, SFTP, and Ubuntu 8.10"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-03-22
I'm looking to set up my computer to be an SSH server, so I can SFTP from school or wherever and grab files off my computer securely.

I installed openssh-server, made a backup of the config file, then I made a few changes to the config file. I edited the banner which is located in /etc/issue.net

I also changed the listen port from 22 to an unused port. Then, I added the line AllowUsers (username is here without parentheses).

However, I'm not sure if the SSH server is accessible. How do I test this? Do I go to the terminal and do 'ssh username@localhost:: (port#)'?

Also, how do I set it up so that I can use this SSH server to SFTP and tunnel? Password protected of course. I tried doing this on Windows Vista with Cygwin and some other apps, but Ubuntu should be easier so I ditched that idea.

Thanks ;)

Edit: to connect I found out this works 'ssh -p PORT# localhost'

---

### Post by gibxam on 2009-03-22
Hey Lazy-buntu,

your going to have to use this command:
```
ssh -p (non-standard port #) username@localhost 
``` Also to access your computer from another computer on the Internet you will probably have to set up a 'port forward' with the specific port that you chose. Look around on the forums to find info about this, especially some of my recent threads :). Hope this helps

Max

one last thing that I forgot: make sure that you actually start the ssh server via this command: ```
sudo /etc/init.d/ssh start 
```

---

### Post by Lazy-buntu on 2009-03-22
I figured out the non-standard port syntax, but now it's asking for a password. How do I set up a password in the config file?

For example, I added the line:

AllowUser Lazy-buntu

I do: ssh -p XXXX Lazy-buntu@localhost

It displays my banner, and asks for a password for Lazy-buntu (or whatever my username is)

Edit: By the way, port-forwarding is already set.

---

### Post by MrWES on 2009-03-22
If you're forwarding port 22, or 2222 for sshd, I'd certainly install and configure DenyHosts.

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

Bill

---

### Post by Lazy-buntu on 2009-03-22
Figured out what the problem was. AllowUsers is not setting up a user/password for SSH. It limits who can ssh locally (so the User/Password is the same as the local account).


Anyway, how would I go about setting up SFTP and tunneling using this ssh server? And by setting up the SFTP, do I get to set up login credentials?

Edit: Another issue...if I do ssh -p XXXX username@my_public_ip_address it just sits there with the cursor blinking. I can do ssh -p XXXX username@localhost or ssh -p XXXX username@my_LAN_ip_address and it works fine.

---

### Post by Lazy-buntu on 2009-03-22
I am able to use WinSCP to SFTP to my computer either using localhost or my LAN ip address. However, if I try my home's public IP address it hangs. I set up port forwarding to my computer through my router like any other application that requires it. What could be going wrong? Maybe there's something I'm overlooking in the config file.

Off topic, but is there any security steps I need to perform? I've disabled the ability for root to login via SSH. What's the deal with public/private keys?

Also, how would I use my computer (ssh-server) to tunnel from another network?

One more thing: is there a linux application similar to WinSCP's SFTP interface? I tried putty, but it brought me to a terminal after logging in.

---

### Post by cfree220 on 2009-03-22
I don't really understand why you moved the SSH port to something other than 22... but ok.

If your SSH server is behind a router (chances are it is if you have a home network), you're going to need to do two or three things:

1. Set a static IP address for your computer. Chances are your router is setup to assign IP addresses via DHCP. To set a static IP, you need to edit /etc/network/interfaces :
```
Here is what my server, which has a non-expiring DHCP assigned address, looks like:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#       address 129.64.134.76
#       netmask 255.255.255.0
#       network 192.168.0.0
#       broadcast 192.168.0.255
#       gateway 129.64.134.1
~                                 
```
You want to change yours to look more like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
#       address 192.168.1.101
#       netmask 255.255.255.0
#       network 192.168.0.0
#       broadcast 192.168.0.255
#       gateway 129.168.1.1
                                 
```
Your actual values will vary depending on your router. 192.168.1.1 is the gateway for Linksys routers. When choosing an IP for the server address, I would recommend choosing something higher than 101. If you have other computers on the network, you do not want the IP of your server to get assigned to that IP (e.g. if the server was off, and another computer was booted and joined the network. If your server was using .101, and was off (thus .101 is free) the router will assign that. When you start the server, it wants .101. You now have an internal error).

The second thing you need to do is set up port forwarding through the router. I don't know what hardware you have, so I would recommend googling [router model] + port forwarding. You will then want to forward your SSH port to the IP of the server.

To connect to the server over SFTP (FTP with SSH encryption on the command channel), I'd recommend Filezilla.

---

### Post by cfree220 on 2009-03-22
hmmm... you sniped my post with new information :-P

As for your last question... Ubuntu comes built with the ability to access your files securely. Go to places ==> connect to server. From the drop down menu, choose SSH, then enter in the information into the fields and connect. You will be able to navigate your folders and files as though they were local (much nicer than the Filezilla interface).

---

### Post by Lazy-buntu on 2009-03-22
> I am able to use WinSCP to SFTP to my computer either using localhost or my LAN ip address. However, if I try my home's public IP address it hangs. I set up port forwarding to my computer through my router like any other application that requires it. What could be going wrong? Maybe there's something I'm overlooking in the config file.

Off topic, but is there any security steps I need to perform? I've disabled the ability for root to login via SSH. What's the deal with public/private keys?

Also, how would I use my computer (ssh-server) to tunnel from another network?

I figured setting the port to something other than the default port 22 would add a layer of protection.

I've got my router to port forward to my computer's MAC address, so I don't think I need to worry about static vs dynamic ip address in the LAN.

That connect to a server works great by the way :)

---

### Post by Lazy-buntu on 2009-03-22
By changing it from port 22 to another port help prevent less intelligent intrusion attempts?

By the way, I'm using 8.10 desktop edition not server edition. Do I need a software firewall for Ubuntu?

And still need some input regarding:
> I am able to SFTP to my computer either using localhost or my LAN ip address. However, if I try my home's public IP address it hangs. I set up port forwarding to my computer through my router like any other application that requires it. What could be going wrong? Maybe there's something I'm overlooking in the config file.

Off topic, but is there any security steps I need to perform? I've disabled the ability for root to login via SSH. What's the deal with public/private keys?

---

### Post by Bachstelze on 2009-03-22
Whether or not changing the port SSH listens to increases security is subject to debate. Personally, I think it does not in most cases, or more accurately, that the level of additional security it provides is unsignificant compared to that of having strong password or using key-based authentication. However, if you're running a highly critical server and really need all the additional security you can get, then it might make sense, but remember that it is definitely not a replacement for sane security practices.

Whether or not you need a firewall mostly depends on your environment. Do you have a lot of untrusted users on your system, that might run possibly harmful network services? If you do, a firewall is certainly the best way to prevent that. If you don't, it's mostly useless since you're going to allow the services you're running anyway.

> However, if I try my home's public IP address it hangs. I set up port forwarding to my computer through my router like any other application that requires it. What could be going wrong? Maybe there's something I'm overlooking in the config file.

Are you trying to connect to your server from a machine inside your LAN or from outside? Some routers won't allow you to connect to a machine on your LAN using your public address (what's the point of doing so anyway?).

```
Off topic, but is there any security steps I need to perform? I've disabled the ability for root to login via SSH. What's the deal with public/private keys?
```

Key-based authentication on SSH is a deep subject, I'm sure your friend Google know lots about it. ;) What I personally do on my server is

1) Disable all password-based authentication, users can only authenticate using key-based authentication

2) Allow only an explicitly defined list of users to login (You've done that already using the AllowUsers directive).

3) Move the authorized-keys files outside the users' home directories, so they can't add arbitrary keys to the file.

---

### Post by Lazy-buntu on 2009-03-22
I was trying to access the server from inside the LAN using my public address to see if it would work from the outside. I.E. would I be able to connect to my SSH server from the university computers if need be. So maybe I'll try to SFTP from my school tomorrow.

I'm the only user of this computer, so I'm guessing I won't need a software firewall for Ubuntu.

I'm confused by key-based authentification though. I've found a lot of things through google about it, but I'm not seeing the difference between a password and a key.

For file encryption, like TrueCrypt, there's an option for a password and a key file. The key file can be any file that you use like a key to open the encrypted container, is this similar to key-based authentification? What's the difference between public and private?

---

### Post by cfree220 on 2009-03-22
mmmmm.....
When I first set up my SSH server, I also tried changing the port with similar intent. Didn't have any luck and changed it back. You might be having problems with your firewall not accepting connections on that port.

Public/Private keys are a method of using SSH without entering username or password. It can help increase protection against brute force attacks if, and only if, you disable all other methods of logon (so, you would only be able to login using this method). The private key is a file stored on the local or client computer. The public key is the file stored on the server. You need both to authenticate and complete the connection. Check out this link for more information on configuring your SSH server/client for this type of authentication.
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by Lazy-buntu on 2009-03-22
So if I wanted to connect to my home ssh server from school, I'd need my private key file on my flash drive to connect basically?

---

### Post by Bachstelze on 2009-03-22
> **Lazy-buntu said:**
> So if I wanted to connect to my home ssh server from school, I'd need my private key file on my flash drive to connect basically?

Yes. And don't believe people who say it's fine to have a SSH key without a passphrase. It is not. It is like having a file on your Flash drive that says "STEAL ME! THEN YOU CAN CONNECT TO ALL MY SERVERS!". You know how small Flash drives are nowadays, anything can happen. Do assign a passphase to your key, and a strong one.

---

### Post by cfree220 on 2009-03-22
Yes. I think most SFTP/SSH clients allow for the use of keyfiles. When I need to connect to my server from a school computer, I use the portable version of Filezilla. It runs right off your flashdrive and does not require any installation. You can get this and other portable applications at [http://www.portableapps.com](http://www.portableapps.com)
I know you said something about using WinSCP... I'm pretty sure there is a portable version of that available as well.

---

### Post by Lazy-buntu on 2009-03-22
Thanks everyone, you've been a great help. I think I should be able to pursue the rest on my own, like VNC and tunneling.

I'll test out my server on someone else's computer or a school computer soon to see if it's accessible.

Score one for linux and its community!:guitar:

---

