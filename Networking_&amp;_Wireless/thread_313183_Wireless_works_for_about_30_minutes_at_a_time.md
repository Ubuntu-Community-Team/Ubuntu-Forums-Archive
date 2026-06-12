---
title: "Wireless works for about 30 minutes at a time"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2006-12-05
I have been using Ubuntu for about a year or more as my primary operating system on my laptop at home.  After upgrading to Edgy it took me a while but I was able to get wireless working with the fwcutter script.

(the exact same script and driver I used with Dapper)

Wireless works just fine after I run "sudo dhclient" a few times, possibly with a few "sudo ifconfig eth1 down" and "sudo ifconfig eth1 up"'s thrown in.

30 minutes to an hour later, and it's time for a reboot.  (No amount of dhclient and bringing the network down and up will revive the connection.)

This becomes even less reliable when using a non-encrypted network.  (Open networks are insanely difficult for me to join and involve bringing the interface down and up quite a few times, and running dhclient for sometimes close to 5 minutes or longer.)

The unsecured wireless networks never worked well for me in Ubuntu, but I was always on the network when I was at home on my WEP encrypted network.

Any tips to get this up and running?  Any log files I can keep track of or command line results I can post here to help diagnose?

---

### Post by caricc on 2006-12-05
What is your wireless nic? Do you have the latest driver update. also you may need to have the windows wireless drivers installed under system/administration.

---

### Post by OneSeventeen on 2006-12-06
I've narrowed down the issue at home, I don't get DNS records or something, because I can ping external IP's, but not domain names.

any tips on having it refresh this automagically?

---

### Post by james957 on 2006-12-06
I am having a similar problem in Dapper.  I'm using ndiswrapper for a Broadcom card.  
The strange thing is that it worked for about a month, then I started seeing problems.
Any ideas?

Thanks,
James

---

### Post by OneSeventeen on 2006-12-07
Well, I finally figured it out!!!

For some reason Ubuntu likes to choose a random IP for DNS that doesn't work.  Then it overwrites my /etc/resolv.conf

All I do is clear the contents of /etc/resolv.conf then take my wireless down, then up, then I re-enter my essid and key (just to be sure) and run dhclient.

It usually then finds the proper DNS server and re-discovers the internet.

There are also times that it just decides not to reach the outside world, but pulling the network down and up again seems to do the trick.

This is the script I wrote:```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "allyourbase"
sudo iwconfig eth1 key "mypasswordgoeshere"
sudo dhclient
```

I can't figure out how to clear the contents of /etc/resolv.conf from the command line... (sudo echo "">/etc/resolv.conf just gives a permissions error)

If anyone knows how to avoid jumping through so many hoops just to get on the network, I'd really appreciate the tips, otherwise I'm at least able to get on the internet and re-connect each time it messes up.  (now it only wastes about 5 minutes for every 30 minutes I'm working, rather than wasting about 30 minutes for every 45 minutes I'm working.)

Oops, I was wrong... it only randomly picked up on the proper DNS server, so I had to manually restore it to my ISP's DNS server to get it to work... clearing out /etc/resolv.conf doesn't work...

(I found this out because when I hit "submit reply" my laptop had already lost its DNS records and wouldn't post, so I tried clearing out the resolv.conf file and it found an IP address for DNS that doesn't work and has never worked for me, yet it seems to be the default...)

man this is weird.

---

### Post by Iowan on 2006-12-08
Have you edited **dhclient.conf** to keep it from retrieving the DNS server? (Or you could prepend the one you want.)
[http://www.ubuntuforums.org/showthread.php?t=282034]("http://www.ubuntuforums.org/showthread.php?t=282034")

---

### Post by OneSeventeen on 2006-12-13
I found that late last night, and followed those instructions, and it was doing well until I turned on the laptop today.

Yesterday cat /etc/resolv.conf returned:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Today cat /etc/resolv.conf returned:```
search localdomain
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.136.2
```

So I commented out search localdomain and nameserver 192.168.136.2, then about thirty minutes later they were uncommented again.

When I go to System>Administration>Networking it is no longer set to my "Home" profile, but the profile is blank and it has added localdomain to the search domains and 192.168.136.2 to the DNS servers. 

How do I make it stay where I set it rather than automatically adding configuration settings.

My router is set to the OpenDNS IP's DNS servers as well. but can I still force OpenDNS servers when I go places whose routers are not configured for OpenDNS servers?

Oh, and even when it had the OpenDNS IP's along with the extras I could not ping google.com until I removed the extra nameserver and extra search domain.  Now that the extra search domain and name server have added themselves back, I can still browse the web.

Between the time that I started typing this and now it has already added the extras back...  (now the new IP address is 172.16.10.1 which I cannot ping.  Then again, I could ping Google's IP earlier, but not OpenDNS's DNS IPs... this is all so weird to me)

---

