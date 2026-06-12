---
title: "how do i connect to a computer over internet threw ssh"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-08-26
Hello i built a computer for my granny and if i ever need to send her files i would like to be able to thew ssh if i have her ip how do i enable that on her computer

---

### Post by NetworkGuy on 2006-08-26
It's a complicated answer, but here is a good place to start..

Do you have a firewall/router between the Internet and your granny's PC?
If so, you will need to allow port forwarding from the router to the PC on port 22 (I think 22).

Minimum: You need to load the ssh server from synaptic.  You may want to configure it for higher security.

To transfer files you will need to learn how to copy over ssh. (scp from a terminal prompt)

Let me know if I can help you with anything else with this.

---

### Post by CameronCalver on 2006-08-26
ok ill be doing it later on today ill let you no how i went

---

### Post by steve.horsley on 2006-08-27
The package to install is **openssh-server**. Make sure she has a good passsword because there are lots of password-guessing bots out there. 

It is worth looking at extra security. 

If you know the IP address you will be calling from, you can configure it to only allow calls from that address.by adding the following line to /etc/hosts.allow (but use your IP address):
**sshd: 1.2.3.4**
and this line to /etc/hosts.deny:
**sshd: ALL**

Or you could even read up on using certificates for SSH authentication.

Or you could confgure ssh to only allow login to an account that you create with a really tough password.

You could also have SSH listen on a high port number rather than the standard 22, which should avoid the guessing bots.

---

### Post by CameronCalver on 2006-08-27
i have downloaded that but can you give me a step by step on what i have to do on the computer im connecting to and what i do on the computer i am connecting from becuase i dont really understand

---

### Post by steve.horsley on 2006-08-28
You installed that package on your granny's PC, yes? If so, it should be listening for incoming SSH connections. You need to know granny's IP address. You can get this by running the command **ifconfig | grep Bcast**. 

If that address starts 192.168 then you have a NAT router between the PC and the Interweb, so you need to set up port forwarding on that router. You also need to know the IP address of the router's WAN link because that's the address you will be connecting to from your PC. 

If it's some other address, then it's probably listening on the Interweb right now, and you can connect to it from your home PC.

The command to connect using SSH is **ssh user@address** where you replace user with the user name on granny's PC and address with the address of granny's PC, or the interweb address of the router.

---

### Post by CameronCalver on 2006-08-29
Ok i am beginning to think this is impossible ecuase granny's computer is a modem not broadband:(

---

### Post by tturrisi on 2006-08-29
> **CameronCalver said:**
> Ok i am beginning to think this is impossible ecuase granny's computer is a modem not broadband:(
Put a link on granny's desktop that she can click & reveal her ip address & auto email the address to you.  (or she can use phone).

---

### Post by CameronCalver on 2006-08-30
ok if i can get her ip what do i do next

---

### Post by tturrisi on 2006-08-30
Simplist method is to install openssh-server on her system.  Then use gftp (need to install openssh-client too) to upload (ssh2).  This is secure as well.   If you config the account in gftp for her server and use root & root pass then you can upload to any dir on her system.  The downside is that you will have to re-config the gftp bookmark to her current ip address each time it changes.

---

