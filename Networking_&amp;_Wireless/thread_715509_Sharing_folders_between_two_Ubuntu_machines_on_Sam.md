---
title: "Sharing folders between two Ubuntu machines on Same network."
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by xl_cheese on 2008-03-04
I must be an idiot.  I can't seem to do it.

Two Gutsy machines.  One LAN and one a wireless laptop.
Both have shared folders.

Neither one can see the other shared folder.  There's some network junk from a previous setup that worked.

I've tried the unix shared folder AND the windows shared folders.  

It's ridiculous I've spent so much time trying to do this.  Both computers are sitting in front of me inches apart.  They can ping each other.](*,)

---

### Post by coolbrook on 2008-03-04
Try hard booting both again.

---

### Post by dedmonds on 2008-03-04
If you have set each up as a Windows (SMB) share, I believe you should be able to enter ```
smb://computername/path_to_folder
``` in the Location bar in Nautilus (with the appropriate computer name or IP address and path) to get to the shared folder on the other computer. I've had trouble in the past navigating to find a computer with a shared folder, but this has worked for me.

---

### Post by xl_cheese on 2008-03-04
Thanks guys, but on both computers I get this error message:

"Sorry, couldn't display all the contents of "Windows Network: dork-mobile"."

where dork-mobile is the name of my laptop.  It's actually capitalized, but gets defaulted to lower case.

---

### Post by jblackthorne on 2008-03-05
To Test Samba:

1. Open Nautilus
2. Enter: smb://<ip address of the other computer>

The above test eliminates DNS/hostname issues and will confirm definitively if you have Samba setup correctly.  If that does not work, the re-check your samba config.

With that said, I personally really prefer the build in SSH protocol myself.  Plus, it is really easy to setup.

1. Open Synaptic Package manager and install the following packages:

ssh
ssh-askpass-gnome
openssh-server
openssh-client

start the sshd service:
sudo /etc/init.d/sshd start

Test the new service:
1 Open Nautilus
2. Enter the following address format: ssh://192.168.0.1 (with the IP address being the IP of a target machine).

Note: Run both tests with IP addresses at first.  Once IP addresses prove the connectivity is good, then move on to hostnames from DNS or hostmames.

Note2: I also suggest setting up SSH security using /etc/hosts.deny and /etc/hosts.allow.  There are tons of howto docs on the net about both of these.

Any way, there are two very easy remote connectivity methods you can test. Good luck!

---

### Post by Eiríkr on 2008-03-05
Ditto to jblackthorne's advice -- ssh-based browsing in Nautilus or Konqueror is secure, easy, quick.  Samba is probably the *worst* possibility for easy Lin - Lin sharing networks; I suspect it shows up so much simply because a lot of us have to deal with Windows (myself included), but for Unixy file sharing, it's really a dog.  

Cheers,

Eiríkr

---

### Post by xl_cheese on 2008-03-05
> **jblackthorne said:**
> To Test Samba:

1. Open Nautilus
2. Enter: smb://<ip address of the other computer>

The above test eliminates DNS/hostname issues and will confirm definitively if you have Samba setup correctly.  If that does not work, the re-check your samba config.

With that said, I personally really prefer the build in SSH protocol myself.  Plus, it is really easy to setup.

1. Open Synaptic Package manager and install the following packages:

ssh
ssh-askpass-gnome
openssh-server
openssh-client

start the sshd service:
sudo /etc/init.d/sshd start

Test the new service:
1 Open Nautilus
2. Enter the following address format: ssh://192.168.0.1 (with the IP address being the IP of a target machine).

Note: Run both tests with IP addresses at first.  Once IP addresses prove the connectivity is good, then move on to hostnames from DNS or hostmames.

Note2: I also suggest setting up SSH security using /etc/hosts.deny and /etc/hosts.allow.  There are tons of howto docs on the net about both of these.

Any way, there are two very easy remote connectivity methods you can test. Good luck!


Thanks.  Both methods work with the direct ip address call, but neither computer or protocols work with the host name.

My laptop is called "Dork-mobile" and my main computer is called "Dork".

Dunno.  I'll just set up a link with the ip address in there and be done with it.

---

### Post by Eiríkr on 2008-03-05
This might sound obvious or stupid to say, but host names only work when they're known.  ;)  In Ubuntu terms, this means you need at least one of:
[list][*]a fully populated /etc/hosts file (on each machine!) listing all the hostnames and relevant IP addresses you want to use on your network (easy, but inelegant if anything changes, and you need to know the IP addresses beforehand)
[*]a properly configured DNS server somewhere on your network, with the individual network configs for each machine pointing to that DNS server (more difficult, and also a pain if anything changes)
[*]some sort of zeroconf setup (most elegant, and no worries if anything changes, but it's also the newest option and therefore hardest to find info / assistance for)[/list]

Windows machines are incredibly chatty, which makes some things very convenient -- unfortunately, also for the bad guys.  This is partly why Windows machines are crazy silly to crack.  Ubuntu, on the other hand, is configured by default to *not* broadcast its presence, social security number, luggage combination, and passport bar code to all and sundry.  This means that simply having a hostname assigned on a particular machine won't necessarily mean anything to any other machine on the network.  Zeroconf is an attempt (spearheaded by Apple, if memory serves) to implement some of the Windows convenience in a way that is at least a bit more security conscious.  The Linux daemon for zeroconf functionality is called Avahi, and there's a package available for Ubunutu.  I use it to simplify NFS sharing to my iBook ([post=4387032]described here[/post] if you're interested), but from what I've read there are also ways of using Avahi / zeroconf to implement a hybrid DHCP / DNS solution, so you can have dynamic IP addresses within a home network that are still translated to findable hostnames.  Once I can get a bit more time for fun projects like this, I plan on figuring this one out.  :)

Cheers,

Eiríkr

---

### Post by Jgonick on 2008-03-11
I'm new to this also, but I finally got mine working.  Check these to be sure.  

In system/administration/ shared folders/ general tab/ make sure the domain/workgroup is correct.
in system/administration/ network/ general tab /  make sure the domain is correct.

Also Ubuntu likes to add desktop to your computer name.  Try " smb://Dork-desktop" 

All of this might be irrelevant, but Mine finally started working.

Hope it works for you..

---

