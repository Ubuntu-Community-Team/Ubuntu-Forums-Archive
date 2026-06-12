---
title: "[SOLVED] Need Help Remote Accessing a Mac from Ubuntu"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by crazy_lazy_bear on 2008-12-09
I would like to remote access a Mac from Ubuntu.  Here are the steps I have taken (found at [http://howto.diveintomark.org/remote-mac/):](http://howto.diveintomark.org/remote-mac/):)

In Windows
1. Using PuTTYgen, generate an SSH key pair (private and public).
2. Copy public key to the Mac.

On the Mac
3. Create .ssh directory
4. Set proper permissions for the .ssh directory using “chmod 700 .ssh”.
5. Set proper permissions for the public key file using “chmod 600 publickey.txt”.
6. Rename publickey.txt to “authorized_keys”.
7. Move authorized_keys to .ssh directory.
8. In sshd_config, uncomment “AllowTCPForwading yes”, PasswordAuthentication no”, and “UsePAM no”.
9. In terminal, enter “ssh-keygen –l –f /etc/ssh_host_rsa_key.pub”.
10. In my router, forward port 22 to the Mac.
11. Enable “Remote Login” in System Preferences &#8594; Sharing.
12. Using OSXvnc 1.01, enable “Only allow local connections (require SSH)”.
13. Click on the “Configure Startup Item” button.

     Here is where I get stuck.  I have configured PuTTY in ubuntu as I have in Windows with no success.  I don't know if it should be the same configuration; or which would be the preferred VNC viewer in ubuntu.  Here's what I do to access the Mac from a PC:

In Windows
1. Add privatekey.ppk to Pageant.
2. Using PuTTY, enter my home external ip address as the Host Name.
3. Using PuTTY, under Connection &#8594; Data, enter my OS X short name as the Auto-login username.
4. Using Putty, under Connection &#8594; SSH &#8594; Auth, click browse to select privatekey.ppk.
5. Using Putty, under Connection &#8594; SSH &#8594; Tunnels, add “5900” to Source port and “localhost:5900” to Destination.
6. In UltraVNC Viewer, enter “localhost” as the VNC server.

     I have searched the threads on the ubuntu forums, and tried finding a solution through google; however I have yet to find a satisfactory resolution.  Any help is greatly appreciated.  Thanks.

---

### Post by handydan918 on 2008-12-09
> **crazy_lazy_bear said:**
> I would like to remote access a Mac from Ubuntu.  Here are the steps I have taken (found at [http://howto.diveintomark.org/remote-mac/):](http://howto.diveintomark.org/remote-mac/):)

In Windows
1. Using PuTTYgen, generate an SSH key pair (private and public).
2. Copy public key to the Mac.

On the Mac
3. Create .ssh directory
4. Set proper permissions for the .ssh directory using “chmod 700 .ssh”.
5. Set proper permissions for the public key file using “chmod 600 publickey.txt”.
6. Rename publickey.txt to “authorized_keys”.
7. Move authorized_keys to .ssh directory.
8. In sshd_config, uncomment “AllowTCPForwading yes”, PasswordAuthentication no”, and “UsePAM no”.
9. In terminal, enter “ssh-keygen –l –f /etc/ssh_host_rsa_key.pub”.
10. In my router, forward port 22 to the Mac.
11. Enable “Remote Login” in System Preferences &#8594; Sharing.
12. Using OSXvnc 1.01, enable “Only allow local connections (require SSH)”.
13. Click on the “Configure Startup Item” button.

     Here is where I get stuck.  I have configured PuTTY in ubuntu as I have in Windows with no success.  I don't know if it should be the same configuration; or which would be the preferred VNC viewer in ubuntu.  Here's what I do to access the Mac from a PC:

In Windows
1. Add privatekey.ppk to Pageant.
2. Using PuTTY, enter my home external ip address as the Host Name.
3. Using PuTTY, under Connection &#8594; Data, enter my OS X short name as the Auto-login username.
4. Using Putty, under Connection &#8594; SSH &#8594; Auth, click browse to select privatekey.ppk.
5. Using Putty, under Connection &#8594; SSH &#8594; Tunnels, add “5900” to Source port and “localhost:5900” to Destination.
6. In UltraVNC Viewer, enter “localhost” as the VNC server.

     I have searched the threads on the ubuntu forums, and tried finding a solution through google; however I have yet to find a satisfactory resolution.  Any help is greatly appreciated.  Thanks.

You don't need puTTY in linux as it supports ssh natively. you can do this at the cli like ```
ssh <local_ip_address>
```
See man ssh for further options.

---

### Post by crazy_lazy_bear on 2008-12-09
> **handydan918 said:**
> You don't need puTTY in linux as it supports ssh natively. you can do this at the cli like ```
ssh <local_ip_address>
```
See man ssh for further options.

Thank you for the prompt reply.  For <local_ip_address>, I assume that should be the external ip address of the Mac location (home).  I tried ssh <local_ip_address> twice.  The first time I received a message asking me if I wanted to authenticate.  When I entered "yes", I received a message about adding <local_ip_address> to trusted hosts.  I did not receive those messages the second time I tried ssh <local_ip_address>.  However, both times I received the following message:

Permission denied (publickey,gssapi-keyex,gssapi-with-mic,keyboard-interactive).

I read the information in man ssh.  It seems as if the switches -A, -L and/or -p would be useful.  The information about host-based authentication and public key authentication is very useful.  However, I don't understand if those are steps I have already taken on the Mac, or if I need to edit ssh config files in ubuntu.  If I need to edit the ssh config files in ubuntu, I don't know which edits are necessary.

I apologize for being so ignorant about all of this.  I am new to remote access and even newer to Linux.  For that reason, I posted in Absolute Beginner Talk.

Off topic:  I see that unbuntuforums counts the # of "Thanks" sent to each user.  How do I send you a "Thanks"?

---

### Post by crazy_lazy_bear on 2008-12-10
I upgraded from Hardy to Intrepid.  I entered ssh <local_ip_address> again (<local_ip_address> being the external ip of the Mac location [home]).  I still received the "Permission denied" message.  I appreciate any suggestions sent.  Thank you.

---

### Post by Titan8990 on 2008-12-10
Are you properly forwarding port 22 to the MAC?

---

### Post by crazy_lazy_bear on 2008-12-10
> **Titan8990 said:**
> Are you properly forwarding port 22 to the MAC?

Thank you for the reply.  I am properly forwarding port 22 to the Mac.  I can remote access it from a PC.  I am just ignorant when it comes to the Ubuntu (client) side of things.

---

### Post by Titan8990 on 2008-12-10
Ah, I see what the first helper left off. Try specifying your username:


ssh <your username>@<ip addy of MAC>

---

### Post by crazy_lazy_bear on 2008-12-10
Thank you again.  However, I was unsuccessful.  I tried both my Mac username and my Mac short name.

---

### Post by Titan8990 on 2008-12-10
And you are getting "access denied" and not "connection refused"?

---

### Post by crazy_lazy_bear on 2008-12-10
The message I receive is this: "Permission denied (publickey,gssapi-keyex,gssapi-with-mic,keyboard-interactive)."

---

### Post by crazy_lazy_bear on 2008-12-10
I am assuming that the public/private key pair I created must come into play at some point.  In Windows, PuTTY (Pageant) asks me for the location of the private key.  I don't know at which point in Ubuntu I would add the private key.  Thank you.

---

### Post by capn_hector on 2008-12-10
your right about the key pair make a new one on the ubuntu machine run ssh-keygen on your ubuntu machine and copy the .pub to your mac and add the key to the authorized keys file on the mac.  that should get you up and running.  now when you connect with putty to the ip it asks for a user name thats the name you use with ssh <username>@<ipyourtryingtogetto>

---

### Post by crazy_lazy_bear on 2008-12-10
> **capn_hector said:**
> that should get you up and running.  

OK.  I understand how that would get me up and running.  I don't mean to sound paranoid, but is it safe using only a public key instead of a key pair?  On the client (Windows) machine, I like the extra step (but don't know if its necessary) of having to enter a passphrase to unlock the private key.  Thank you for the suggestion.

---

### Post by jamesrl on 2008-12-10
To connect to a machine through ssh there are in general two methods.  One is the normal method, where you just give your username and your login password and connect.  If you have an ssh-server (eg openssh-server) installed on the machine you are trying to connect to, and openssh-client on the ubuntu machine you have no key management to worry about.  

For the key method, say you have two machines LOCAL and REMOTE.  You want to access REMOTE from LOCAL.  On LOCAL you run ssh-keygen which creates a keypair, consisting of a private key (which optionally has a passphrase associated with it ... for security you should have the passphrase) and a public key.  You then transfer your public key to the REMOTE machine, adding it to the authorized keys list.  An analogy would be  the public key being instructions on how to build a lock, and the private key is something that can open a lock built for its public key.  So you don't want others to be able to access your private key (because they could get into areas that are designed for just you), but you don't mind anyone having access to your public key (as hey if someone wants to put locks up that you know how to open thats just fine with you).

Your public key will be in a file called ~/.ssh/id_rsa.pub  (or id_dsa if you used dsa instead of rsa authentication)
and your private key will be in file called ~/.ssh/id_rsa
To be safe you want your private key to begin like this:
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
with the encrypted part present (indicating you need to enter a passphrase before you can use your private key).  Otherwise anyone who can access your system and read the file ~/.ssh/id_rsa can get your (unencrypted) private key and then has access to any system you have access to.


I've slightly over simplified things, by skipping over the part of the ssh protocol where you verify that the host you want to connect to, is the host that you are thinking of.  So each machine (in addition to user) has private and public keys that identify it as a host, in the /etc/ssh directory.  When you connect to a new machine for the first time, the public key of the host gets put on your .ssh/known_hosts file.  With this public key, you then can create a challenge (analog to a 'lock') that only the host's private key can answer, so you can be sure on your next logins that it is the same machine.  This helps you know that you if someone has changed the machine that you think you are connecting to (which may not now be a trustworthy machine anymore, or it may just be that the host admin reinstalled the OS or regenerated the host key due to a security threat).  By default you shouldn't have to worry about configuring these keys.  But that's why you got the message the first time you connected  [The private host key needs to be unencrypted so it can automatically verify, though only root should have read/write access to it.]

---

### Post by capn_hector on 2008-12-10
> **crazy_lazy_bear said:**
> OK.  I understand how that would get me up and running.  I don't mean to sound paranoid, but is it safe using only a public key instead of a key pair?  On the client (Windows) machine, I like the extra step (but don't know if its necessary) of having to enter a passphrase to unlock the private key.  Thank you for the suggestion.

i was not totaly clear, when you do an ssh-keygen it makes 2 keys the public and private and puts them in .ssh (default) when you move the public key to the mac you leave the private key in the .ssh folder where openssh pulls keys from by defaut.

---

### Post by crazy_lazy_bear on 2008-12-10
OK.  Thank you both.  This is making much more sense.  I copied the public key to the authorized_keys file on the Mac.  (Interestingly the key ends in "== <username>@<computer_name>".  The first key I generated [for use with Windows] ends in "= rsa-key-2008-10-30".  I don't know if the double equals sign makes a difference.)  Now, when I enter <username>@<local_ip_address>, I receive the message "ssh: connect to host <local_ip_address> port 22: Connection refused."  However, I am now trying to connect from within my home network.  (I don't know if that makes a difference.)  Even still, I don't know how to add the private key so that it asks for the passphrase.  I'll try it again from work tomorrow.  Thank you.

---

### Post by capn_hector on 2008-12-10
connecting from your home network is no problem you just take out the step with the dyndns so its <username>@<ip>

---

### Post by jamesrl on 2008-12-11
When you run ssh-keygen I believe by default it prompts you for passphrase.  Type one in and you have an encrypted private key.

```
[<user>@<machine> ~]$ ssh-keygen -b 4096 -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/<user>/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
```

---

### Post by jamesrl on 2008-12-11
Have you looked in the the ssh settings on the mac?
/etc/ssh/sshd_config
For me on ubuntu it is (by default):
> 
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes


I suspect that  you have 
#PasswordAuthentication yes
set as 
PasswordAuthentication no
and that is preventing you from logging in without public/private keys.  You should be able to do
ssh mac_username@mac_ipaddress
and be able to login after changing that line.  [You can change it back and try getting it working with private/public keys if you want as well, by just making sure all your public keys are in the authorized_keys list (each on there own line).]

---

### Post by crazy_lazy_bear on 2008-12-11
Thank you all very much for all your help.  I believe I am making progress.  I discovered "ssh-add" to add the private key.  I now have the ssh tunnel working properly (from home.  I was too busy at work today to play around.  I'll try again tomorrow.)  In terminal, I see the Mac prompt.  

The problem I have now is with vinagre.  When I try to connect to <local_ip_address>, I receive the message "Connection to host <local_ip_address>:5900 was closed".  This happens when I set PasswordAuthentication to either "yes" or "no" in sshd_config on the Mac.  It also happens whether I use <local_ip_address> or <internal_ip_address_of_mac> (since I am on the same router at home).  Again any suggestions are greatly appreciated.

---

### Post by capn_hector on 2008-12-11
[http://bobpeers.com/linux/vnc_ssh.php](http://bobpeers.com/linux/vnc_ssh.php) theres a good website which goes through the vnc over ssh config  you can jump to the setting up client section  and here is a good site to set up the mac for vnc if you have not gotten that done [http://www.macminicolo.net/Mac_VNC_tutor.html](http://www.macminicolo.net/Mac_VNC_tutor.html)

and any vnc viewer will work thats what i like about open protocols so many choices for clients and servers

---

### Post by crazy_lazy_bear on 2008-12-16
The ice storm in the northeast knocked me out of commission for the past several days.  Thank you very much for the links.  They gave me a better understanding of port 5900 vs 5901.  With some more investigation, I found the answer at this thread: [http://ubuntuforums.org/showthread.php?p=4833902](http://ubuntuforums.org/showthread.php?p=4833902).

After adding the private key with "ssh-add id_rsa", instead of simply typing "ssh <username>@<local_ip_address>" (which opened the ssh tunnel, but lacked the permissions to connect to the VNC server), what worked for me was the syntax "ssh -L 5900:localhost:5900 <username>@<local_ip_address>".  In a separate terminal window, typing "vinagre localhost:0" successfully connected to the VNC server.

Thank you for all your help.

---

