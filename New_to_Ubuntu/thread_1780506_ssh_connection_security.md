---
title: "ssh connection security"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-12
I have a trouble with ssh connection security.

The other day when I was setting up ssh on my server, I got a (man-in-the-middle attack)! statement instantly. 

Right away, I denied 22/tcp on the gufw.  I also closed port 22 on the router.

However, I havent done "rm ~/.ssh/known_hosts" or "ssh-keygen -R hostname" on the server yet.  I didnt even remove/purge openssh on the server.

Is it possible for intruder to connect to the server? even if port 22 is closed on the router? Does the intruder still have access to my server????

---

### Post by yeats on 2011-06-12
> The other day when I was setting up ssh on my server, I got a (man-in-the-middle attack)! statement instantly.

This just means that the ssh key for this server in ~/.ssh/known_hosts doesn't match the key on the server.  Within that message about the "man-in-the-middle attack" you should see "offending key in ~/.ssh/known_hosts:*XX*" where *XX* is the line number in the ~/.ssh/known_hosts file.  Open ~/.ssh/known_hosts in a text editor, delete that line and try again.

---

### Post by webofunni on 2011-06-12
Did you recently re-installed the OS where ssh server is installed, in that case that message will come.

---

### Post by 007casper on 2011-06-12
> Did you recently re-installed the OS where ssh server is installed, in that case that message will come.

no I didnt re-installed the OS.  However, I re-installed openssh-server, and client before I did ssh localhost.
> 
This just means that the ssh key for this server in ~/.ssh/known_hosts doesn't match the key on the server. Within that message about the "man-in-the-middle attack" you should see "offending key in ~/.ssh/known_hosts:XX" where XX is the line number in the ~/.ssh/known_hosts file. Open ~/.ssh/known_hosts in a text editor, delete that line and try again.

there wasn't a key in ~/.ssh

there werent any files in ~/.ssh at all. I  removed the files in that folder before I tried ssh localhost.  Only /etc/ssh had files.

---

### Post by 007casper on 2011-06-12
The reason why I ask is that today I was able to access my laptop on a lan, even after I enabled the firewall all the way, and removed known hosts on the laptop.  I couldnt believe I was able to create files on the laptop, even after removing ~/.ssh/known_hosts, and enabling the firewall.

Here is what happened.
I wanted to practice seting up ssh and test connecting to the laptop from the desktop computer locally without opening any ports on the router.  I wanted to practice before I tackle the remote server again.

on the laptop...
I had the ufw enabled.  I also denied incoming, and allowed outgoing. Then, allowed 22 tcp on the ufw.  I was able to connect between computers without a problem.

Then, in the middle of the connection, I decided to deny 22 tcp on the laptop's firewall.  However, the desktop computer didnt lose connection to the laptop. I was still able to create text files and folders on the laptop from the other computer.

Then, I decided to deny incoming and outgoing on the laptop altogether. I was still able to create files.

Laptop's firewall didnt do anything.  

Then, I deleted the ~/ssh/known_hosts on the laptop, and it still worked.  

I removed openssh-server, and openssh-client on the laptop.  I was still able to create files on the laptop from the other computer.

Only when I reboot the laptop, desktop computer lost the connection.

This really surprised me and got me worried about the remote server since I didnt reboot after the intrusion on the server.

Is my local test with closed ports on the router same as the server intrustion with open port 22?  
Because, the router that is connected to the server had port 22 open at the time of the intrusion, however, my lan test had router port 22 closed.

I was surprised that I was able access the laptop, even after I deleted the files.  This might be a stupid question... however, I wonder... 
Can the intruder access the server after the intrusion even if I block or delete port 22 on the router?

---

### Post by yeats on 2011-06-13
Can you post the full text of the "man-in-the-middle" message here?

---

### Post by jramshu on 2011-06-13
> Then, in the middle of the connection, I decided to deny 22 tcp on the laptop's firewall. However, the desktop computer didnt lose connection to the laptop. I was still able to create text files and folders on the laptop from the other computer.

This is normal until you log off, once you're in you're in.

As far as the man in the middle attack, this is normal when you reinstall openssh, especially when you have removed known hosts. It's letting you know that there has been a change in the key and it's "possible" that a man in the middle attack has occurred. Except in your case you actually are the one who has changed it.

I went through the same kind of stuff when setting my server up.

---

### Post by compmodder26 on 2011-06-13
> **007casper said:**
> Then, in the middle of the connection, I decided to deny 22 tcp on the laptop's firewall.  However, the desktop computer didnt lose connection to the laptop. I was still able to create text files and folders on the laptop from the other computer.

As has been said before, this is normal until you log out and try to log back in.  I'm not familiar with how ufw constructs its firewall rules.  But generally when firewall rules are created there is a rule to allow already established connections to continue.

Nothing you have written sounds suspicious.  The man in the middle message happened because you re-installed ssh on the server and it didn't match the signature that you had on your client.  And I explained above why you were still able to stay connected after closing 22 on your firewall.

---

### Post by webofunni on 2011-06-13
Yes, the firewall will not do anything on the connections that is already established. You need to restart the service to which established the connection to block them. In this case you need to restart open-ssh server after you blocked port 22. 

It process sshd may continue to run, if there is a connection. Even though you uninstalled it.

---

