---
title: "Iptables and VPN PPTP"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by saffolino on 2008-05-20
I've set a VPN and it works fine.But it does only when I shutdown Firestarter, so it's rules issue.I connect this host to internet through wlan0+ppp0 (pppoeconf). I need to set a rule for allowing IN/OUT IP GRE to a destination XXX and allowing TCP OUT 1723 to a destination XXX.How do I configure iptables? And how do I save my custom rules forever because they will be deleted on the next reboot?

---

### Post by SpaceTeddy on 2008-05-20
I must mention at the very start - i don't like firestarter. But that may well be the case because i can pretty much speak iptables. That off my chest - here is how you save your firestarter iptables rules, how you can edit them and how to make them permanent. However i fear that you will need to unstall firestarter with this setup... as firestarter will most likely overwrite the boot settings :(

first, load firestarter. That should initialize your iptables configuration as you are used to it. Once that is done, save the iptables configuration into a custom file (i usually use the one from webmin - but you can use any... really) with this command
```
sudo "iptables-save > /etc/iptables.up.rules"
```
that will create a file called iptables.up.rules in your /etc directory which will hold the EXACT same rules as firestarter did. No difference at all.

Next - load those rules during startup. You can do that via the /etc/rc.local file. just put in the following line to load the file on boot:
> /sbin/iptables-restore < /etc/iptables.up.rules
be sure to but that line BEFORE the exit 0.
You can edit that file with this command:
```
gksu gedit /etc/rc.local
```

Now your rules will always be loaded upon reboot, regardless if firestarter is installed or running. they are now permanent. 

Next, adding a rule for the GRE protocoll. i do not know how firestarter handles the connection, so i will only give you the plain iptables commands
```
sudo iptables -A INPUT -p gre -j ACCEPT
sudo iptables -A OUTPUT -p gre -j ACCEPT
```

that will allow the gre protocoll to pass through your filter chains (assuming that the firestarter rules do not get it first)

last, add the tcp 1723 port. same drill as before, commands look like this
```
sudo iptables -A INPUT -p tcp --sport 1723 -s XX.XX.XX.XX -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 1723 -d XX.XX.XX.XX -j ACCEPT
```
The XX.XX.XX.XX is the IP of your vpn server.

now with these rules your vpn should be able to connect. But the rules you have put in are only temporary, as they have NOT been written to the file that is loaded at boottime yet. Check that everything works, and then commit the new iptables filter to the with the initial command you ran at the start - this one
```
sudo "iptables-save > /etc/iptables.up.rules"
```
voila - all done :)

hope it helps :)

PS: if you ever put in a rule that messes something up - you can also restore your old configuration (assuming you have not done a save yet) with this command
```
sudo iptables-restore < /etc/iptables.up.rules
```

---

### Post by saffolino on 2008-05-21
Thanks! It works. I love you :D

---

### Post by saffolino on 2008-05-21
Ah! I forgot. For disable iptables? (firestarter had the button STOP)

---

### Post by SpaceTeddy on 2008-05-21
yes, but it will reenable after the next reboot... i had installed one and found that button too. But it keeps restarting upon boot... 

or so it behaved for me

---

