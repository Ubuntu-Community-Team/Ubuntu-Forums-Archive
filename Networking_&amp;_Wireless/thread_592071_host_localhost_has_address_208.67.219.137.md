---
title: "host localhost has address 208.67.219.137"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by petersfreeman on 2007-10-26
When I enter the command:

      [FONT="Courier New"]host $record localhost[/FONT]

 I get:

     [FONT="Courier New"]host localhost has address 208.67.219.137[/FONT]

It appears that this is in a confuraton file somewhere and it needs to be changed.  How do I fix this problem?

Thank you,

Peter Freeman

---

### Post by conjur3r on 2007-10-26
What's the $record bit doing there?

Anyway, you want to look into **/etc/hosts** and find the entry for localhost.

---

### Post by petersfreeman on 2007-10-26
Hi Conjur3r,

The $record part is what the instructions for BIND9 gave me at:
[FONT="Courier New"]
     [FONT="Courier New"]
[https://help.ubuntu.com/community/BIND9ServerHowto?](https://help.ubuntu.com/community/BIND9ServerHowto?)[/FONT]

It is near the bottom of the document:


[FONT="Courier New"]Status

To check the status of your BIND9 installation:

$ host $record localhost

or

$ dig $record @localhost

(where localhost is the system you are setting BIND9 up on. If not localhost, use the appropriate IP number.) [/FONT]

Here is my /etc/hosts file:

127.0.0.1	localhost
127.0.1.1	seanix

192.168.241.61	Office
192.168.241.31	muskrat.net


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/FONT]

I don't see that IP Address there, do you know what else it could be?

Thanks!

Peter

---

### Post by petersfreeman on 2007-10-26
Hi conjur3r,

I ran grep to search for that address in the /etc directory and its subdirectories and it gave me this result:

[FONT="Courier New"]modprobe.d/aliases:alias char-major-208-* ussp
resolv.conf:nameserver 208.67.222.222
resolv.conf:nameserver 208.67.220.220
[/FONT]

I looked for a file called modprobe.d/aliases but couldn't find it.  Any clues?

Thanks!

Peter

---

### Post by petersfreeman on 2007-10-26
Hi conjur3r,

Sorry, false alarm.  I just did a grep for '208' not the whole address.  So I'm a bit stumped.

Peter

---

### Post by petersfreeman on 2007-10-26
Hi conjur3r,

I restarted my server and I noticed this when the services were starting:

* Starting web server (apache2)...
apache2: Could not reliably determine the server's fully qualified domain name using 127.0.1.1 for ServerName

This suggests that there is a file that I need to modify to fix this.  But where?

Thanks,

Peter

---

### Post by conjur3r on 2007-10-26
First up, I believe the $record is a variable copy and pasted from a script without properly taken out.  For both host and dig, you do not need $record.  It will still work of course because it will evaluate to nothing as $record has not been set to anything.  The howto should be updated.  Thanks for highlighting it out.

Secondly, what is in your **/etc/resolv.conf** file?  I am assuming it is pointing to your ISP's DNS servers.  If you want to test your DNS server, make sure it has the IP address of your DNS server in there.  Or to test from the terminal beforehand (assuming you are on the DNS server):

# dig localhost @127.0.0.1

And finally, the apache warning is because there is no global ServerName definition in **/etc/apache2/apache2.conf**.  You can easily fix this by adding **ServerName localhost** to the file and restarting.

---

### Post by petersfreeman on 2007-10-27
Thanks conjur3r,

I noticed that there are two files very close in name:  resolv.conf and resolve.conf   I don't understand the purpose of either other than they must have something to do with pointing to DNS servers to resolve domain names into IP Addresses.  Here are their contents:

**[resolv.conf]**

[FONT="Courier New"]nameserver 192.168.241.31
nameserver 64.59.160.13
nameserver 64.59.160.15
[/FONT]

**[resolve.conf]**

[FONT="Courier New"]search muskrat.net
nameserver 127.0.0.1
nameserver 192.168.241.31
nameserver 64.59.160.13
nameserver 64.59.160.15[/FONT]


What is the difference (other than efficiency) to using 127.0.0.1 instead of 192.168.241.31 or vica versa?

What is the difference between 127.0.0.1 and 127.0.1.1?

With these files the way they are shown, I tried:

[FONT="Courier New"]host local host[/FONT]

and I get this message:

[FONT="Courier New"]Host localhost not found: 3(NXDOMAIN)[/FONT]

By the way, your suggestion helped me fix the apache problem

Thanks!

Peter

---

### Post by conjur3r on 2007-10-27
The real file is resolv.conf (no e).  This contains the DNS servers your system will use.  The other file is not standard.

Try changing your /etc/resolv.conf file to

nameserver IPADDRESS

replacing with 127.0.0.1 or 192.168.241.31 (whichever you prefer).  Do not have the other nameservers in there.  Then try host or dig again.

Edit, there is no speed difference in using 127... or 192...  In your case, they should both refer to the same server which is the server you've installed BIND on.

---

