---
title: "trying to get my VPN working"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by chengmichael on 2010-04-24
i subscribed to Open VPN (ACE vpn) while using windows, and can't get it to work now that i'm using ubuntu.

i installed the network manager from the ubuntu software center, but the icon is not showing up in the system tray (upper right corner).

i also tried to type in "sudo su-" into the terminal, but after typing in my password, the terminal said "sudo: su-: command not found"

then i typed in "apt-get install network-manager-openvpn network-manager-pptp openvpn" for kicks and the terminal told me that i "could not open lock file"

i copied and pasted the terminal entried below:

chengmichael@chengmichael-laptop:~$ sudo su-
[sudo] password for chengmichael: 
sudo: su-: command not found
chengmichael@chengmichael-laptop:~$ apt-get install network-manager-openvpn network-manager-pptp openvpn
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chengmichael@chengmichael-laptop:~$ 

what can i do now?

---

### Post by P4man on 2010-04-24
Hi.

A few things. First of all, I dont think you need to install any software at all. In the top right, there is a network connection icon (or there should be). Right click it, edit connections, VPN, Add, follow instructions.

If you dont have the networking icon, then right click the top right panel, click add to panel, select the notification area.

For the record, "sudo su-" is not a valid command. "sudo su" is, but it just gives you root privileges in the terminal. Be careful what you do with that if you have no idea what you are doing.

As for the apt-get instructions; its to install packages from the commandline. It does require root privildges, so put " sudo" in front if you need to install anything, like this:

```
sudo apt-get install name-of-package
```

dont go around installing packages randomly though, and it doesnt work if you have a package manager open already, like synaptic or ubuntu software center, both of which are graphical programs to install packages or programs, like apt-get. only one package manager can be active at a time, so just close synaptic first, or use synaptic to install the package rather than the command line, which ever you prefer

Hope this helps.

---

### Post by P4man on 2010-04-24
update. seem you are following these instructions:
[http://www.acevpn.com/knowledge-base/installing-ace-vpn-on-linux/](http://www.acevpn.com/knowledge-base/installing-ace-vpn-on-linux/)

You may indeed need those package, but there seems to be a small typo in the instructions. That dash shouldnt be there. Try this instead:

```
sudo apt-get install network-manager-openvpn network-manager-pptp openvpn
```

Tip: select the above command, click it with middle mouse button (to copy), open a terminal and paste it there with middle mouse.

---

### Post by chengmichael on 2010-04-24
i think i'm almost there...

i typed in this line you told me to into the terminal. 

sudo apt-get install network-manager-openvpn network-manager-pptp openvpn

it seemed to install something. after it installed, i closed the terminal, and went into network manager to add a connection.

following these instructions, i added a vpn connection:

[LIST]
[*]Click on NetworkManager icon and choose VPN Connections… then Configure VPN
[*]Click on "Add" button
[*]For the "Gateway" choose one of the "remote" servers in the conf file
[*]For the "Type" Choose "Passwords with Certificates (TLS)"
[*]Enter your assigned username and password
[*]Choose the correct User Certificate, CA Certificate and Private Key (leave the Private Key Password empty)
[*]Click on the "Advanced…" button
[*] Under "General" choose Use Custom Gateway Port 443
[*] Check the "Use LZO data compression" box
[*]The Network Manager handles everything including swapping the DNS routers in /etc/resolv.conf
[/LIST]
then, when i left clicked the network manager icon, i went to vpn connection 1, and clicked it, but after 30 seconds, the connection timed out. 

is there something i forgot to do? or might i have copied and pasted the wrong gateway - i just picked the UK server, which looks like this:

remote 77.92.94.119 443        #UK

that's correct yes?

thanks so much for your prompt help so far...

michael

---

### Post by P4man on 2010-04-24
edit:
What did you enter exactly as gateway? Try entering only the IP address, like

77.92.94.119

or maybe

77.92.94.119:433

if that 433 is a port (i have no idea)

---

### Post by chengmichael on 2010-04-24
for the gateway, i typed in:

77.92.94.119

77.92.94.119:433

77.92.94.119 443        #UK

77.92.94.119 443

none of those seemed to work...

anything else i can do? maybe i should i contact ace vpn support...?

---

### Post by P4man on 2010-04-24
Maybe someone with more experience than me with VPNs can chime in?

Pending that, perhaps post the output in the syslog. Go to system > administration > log file viewer

Select syslog, and copy paste the lines that correspond with the time you tried setting up a connection. That might help someone else troubleshoot, but Im not sure it will help me help  you :)

---

### Post by chengmichael on 2010-04-24
thanks for all your help! i checked the syslog, and it seemed stuck (as you thought) at the gateway - 

for some reason, the uk server wasn't connecting, so i just used another server in the conf. file and it connected - 

thanks so much for all your prompt help!

---

### Post by P4man on 2010-04-25
Great, glad you figured it out! Please mark this thread as solved:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

