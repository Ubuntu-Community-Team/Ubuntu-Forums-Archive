---
title: "Connect Network printer between 2 Ubuntu computers"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by marty757 on 2007-06-07
I am running two desktops with Ubuntu Fiesty 7.04. I have a HP Deskjet 3520 printer and a Epson Stylus Photo R200 printer. Both printers work on the PC that they are connected to, but I am unable to connect either printer via the network.

When I try to print I get this error message: Paused: /usr/lib/cups/backend/lpd failed

Both computers connect OK via the network and I can share files.

---

### Post by carolinason on 2007-06-07
I would set up a samba share. Use swat for administration.

---

### Post by marty757 on 2007-06-13
Thanks.
I finally changed the host name to the IP address and it worked. However, I have swat installed and could not access according the the swat man. [http://localhost:901/](http://localhost:901/)  Is there another way to access it?

---

### Post by carolinason on 2007-06-17
Well I had no idea SWAT was like this in Ubuntu. In Debian you simply install it and it runs. It's a service that must be cut on. I'll fix it on my test machine and post the process.

---

### Post by carolinason on 2007-06-17
Here is how to enable swat in Ubuntu in 3 easy steps:

/* Pre-note
I logged into the command line terminal and created a password for root. 

$>sudo passwd

follow the prompts, then

$>su
*enter the new root password*
*/

**1) Install xinetd with either apt or synaptic**

enter in the command line terminal
#>apt-get install xinetd
**or**
#>synaptic
and search for xinetd by the name field, mark it to install and apply, close synaptic.

**2) create a text file and call it swat and save in the /etc/xinetd.d/ directory**

If you prefer vi, paste the below text into 
#>vi /etc/xinetd.d/swat
**or** if you prefer gedit type
#gedit
paste the below text into gedit and and save it as swat into /etc/xinetd.d/. Close gedit.

# description: SAMBA SWAT
service swat
{
disable = no
socket_type = stream
protocol = tcp
#should use a more limited user here
user = root
wait = no
server = /usr/sbin/swat
}

**3) restart the xinetd service at the command line terminal**

#>dpkg-reconfigure xinetd 

you'll hopefully see

Stopping internet superserver: xinetd.
Stopping internet superserver: xinetd.
Leaving `diversion of /etc/init.d/inetd to /etc/init.d/inetd.real by xinetd'
Starting internet superserver: xinetd.

/* Post-note
exit root in the command line terminal 
#>exit
**or**
key combination ctrl-d
*/

go to your web browser and try localhost:901 again
log in as root to swat

Easy as pie, but harder than Debian, okay!

---

