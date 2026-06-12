---
title: "Run script after connection to network"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Mars Thrax on 2008-05-11
Hey all,

I have sshfs configured so that I can connect to my desktop's home folder. I have added the appropriate sshfs entry to /etc/fstab, and if I manually run mount -a (or mount /mnt/Desktop, which is the mount point on my filesystem), everything is just peachy (ie, I can navigate the desktop's filesystem as expected).

The problem is that I am using a wireless card to connect my laptop to the network, and it doesn't connect until after log in (and thus, after my drives are mounted). So, my desktop's home folder is not mounting automatically on boot.

Since I can manually perform the mount without issue after logging in, I'm guessing I just need to configure my laptop to run the mount command after it connects to my wireless network.

Ideally, I'd also like to have a way of automounting once I establish a vpn connection into my home network.

Any ideas on how to do this stuff?

---

### Post by kevdog on 2008-05-11
How are you connecting to your wireless network?  If you are using the /etc/network/interfaces file, and if all your mounting commands are in a shell script file you can run the shell script under the network adapter something like:

auto wlan0
iface wlan0 inet dhcp
...
...
post-up /etc/shell_script.sh

Do you think something like that will work for you?

---

### Post by amingv on 2008-05-11
<kevdog posted the first bit of my answer, but heed the second bit>

However, **do consider it throughoutly** before editing the interfaces file, _specially_ with wireless interfaces; **if you use a network manager it may (most likely will) stop managing your network** and you may have to manually reconfigure your network.

---

### Post by kevdog on 2008-05-11
If you dump Network Manager, and switch to WICD, I know that it has the ability to run a custom script after login. Just an idea.

And what amingv stated about NM is true.

---

### Post by Mars Thrax on 2008-05-11
Hmm, I forgot that about wicd. I could try that. I would prefer a solution that would allow me to continue using network-manager though, simply because I am trying to come up with solutions that require the fewest programs and the least command-line possible (which, unless wicd supports openvpn, would require me to use the command line to connect). I don't personally have a problem with it, but I'm trying to find solutions for some friends, who are definitely more comfortable with GUIs.

---

