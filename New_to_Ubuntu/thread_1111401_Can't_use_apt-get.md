---
title: "Can't use apt-get"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Django1200 on 2009-03-30
I have an ubuntu server running a web page with apache2. I usually log into it using ssh 2 from my laptop with putty. I only do this across the network and my router doesn't forward requests for ssh's port (only port 80 is forwarded to the server). I was trying to install proftpd with apt-get and found that I can't access the net. I can still see my web page and log in with putty but can't get anything out (firefox won't connect, either) I would greatly appreciate any help. Thanks.

---

### Post by bodhi.zazen on 2009-03-30
Are you running a firewall on the server ?

Are you running any type of proxy for internet access ?

---

### Post by Django1200 on 2009-03-30
No to both. Thanks for the quick reply. Maybe it is worth mentioning that, most recently, I was using the useradd command to prepare for setting up the ftp. When I did the first two accounts, it automatically added the ~ directory and copied files for both. After those, though, I had to use mkdir and chown seperately

---

### Post by bodhi.zazen on 2009-03-30
What then are your error messages ?

---

### Post by Django1200 on 2009-03-30
Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
-bash: Err: command not found
steven@Clowder:~$   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
-bash: Could: command not found
steven@Clowder:~$ Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

-bash: Err: command not found
steven@Clowder:~$   Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

-bash: Could: command not found
steven@Clowder:~$ Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
-bash: Err: command not found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Sorry about the length. This is from sudo apt-get update but it is much the same with proftpd

---

### Post by supersonicdarky on 2009-03-30
I could guess that either
a) router not letting it acces outside
b) or more likely, some dns configs are messed up
i) try pinging google.com
ii) try pinging 74.125.45.100 (google.com's ip)
iii) post the results

---

### Post by Coreigh on 2009-03-30
So you can access the server from inside the LAN using another computer, this 'other computer *can* access the internet but the server can not access the internet. Strange. The Network settings are obviously ok because you can access the server. Is you network segmented in some way? i.e. the server IP address range is a different subnet than the internet gateway. Is the server configured to allow access ONLY for the LAN? So http responses get ignored by the server even though the serve makes requests.

Did it ever work? When *exactly* did it last work? and What changes have you made between then and now? It seems unlikely that adding users and groups for ftp access would break this unless you somehow removed or denied access to the user being used. Incidentally does it work if you use sudo?

---

### Post by Django1200 on 2009-03-30
I tried both ping and mtr and both cycled endlessly. How do I get it to stop and give me results?

---

### Post by drs305 on 2009-03-30
> **Django1200 said:**
> I tried both ping and mtr and both cycled endlessly. How do I get it to stop and give me results?
If you are running ping from the command line you can stop it with CTRL-C. You can also add the "-c" switch to set the number of pings.
```
ping google.com -c 1
```

Added: As to the length of your earlier post, you can paste the content between 'code' or 'quote' tags. You get the 'code' tag by clicking on the # symbol at the top of the post while you are composing it.

---

### Post by Django1200 on 2009-03-30
$ ping google.com -c 1
ping: unknown host google.com
$ ping 74.125.45.100 -c 1
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=242 time=42.3 ms

--- 74.125.45.100 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 42.333/42.333/42.333/0.000 ms


Thanks for the advice about the quote and code tags

---

### Post by bodhi.zazen on 2009-03-30
Looks like your problem is with DNS.

I can not tell if you are blocking port 53 with a firewall of some kind or not.

What is in:

```
cat /etc/resolv.conf
```

---

### Post by Django1200 on 2009-03-30
# Generated by NetworkManager

was all that was in there

By the way, I went into firefox and entered google's ip in the address bar and it brought it up no problem, pretty much confirming that it is a DNS problem

---

### Post by bodhi.zazen on 2009-03-30
open that file and enter your routers ip address

Ex: 

> nameserver 192.168.0.1

---

### Post by Django1200 on 2009-03-30
Is nameserver a command or something I should be replacing with something specific to my computer? I just copied it in like this:```
nameserver 192.168.1.10
``` where that is the ip of my server. As is, it hasn't changed anything. I used ```
sudo netstat -plntu 
``` and 53 wasn't anywhere on the list

---

### Post by bodhi.zazen on 2009-03-30
no, you need to add the ipaddress of your router.

I am going to guess 192.168.1.1

so , /etc/resolv.conf should have one line :

```
nameserver 192.168.1.1
```

then all should work just fine.

---

### Post by Django1200 on 2009-03-30
Thank you. That worked perfectly. Any idea what happened that could have caused it to stop working so suddenly?

---

### Post by bodhi.zazen on 2009-03-30
Looks like network manager stuck again :)

Network manager can help sometimes, but it can be a nuisance as well.

Did you open network manager to change your settings ?

---

