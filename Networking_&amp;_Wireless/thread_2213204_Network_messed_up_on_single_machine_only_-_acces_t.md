---
title: "Network messed up on single machine only - acces to router OK"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by RS_Hylleberg on 2014-03-25
Hi all

I've used ubuntu 12.04 for a while now and had no trouble accessing the internet via wife/cable until recently. I've search high and low for a solution to no avail.

I have several computers on my local network - all but one can acces the internet just fine trough our one router.
My ubuntu 12.04 has stopped working, regarding wifi and cable. For some time I was able to acces just by using chromium browser, not opera or firefox. I can ping 8.8.8.8 from a terminal, but not google.com. Now I have absolutely no acces to internet.
I get no error messages and my icons indicate everything should be fine.

I don't know where to start looking for "the error" - I hope someone can help me out

\RSH

---

### Post by TheFu on 2014-03-25
If you can ping by IP then it isn't a connectivity issue at all.
If you cannot determine the IP from the name - it is a DNS issue.
That is where you should be seeking a solution - the DNS settings.

---

### Post by RS_Hylleberg on 2014-03-26
Well ...
Even if i use the same DNS settings as my other machines (linux mint, lubuntu, xubuntu) I cant connect to the internet via browsers in ubuntu 12.04 LTS. I can only ping IP's from terminal.
I have no idea where to go from here. 
If i boot from a live CD/USB I get connected right out of the box, so I guess its not a hardware issue.

Im considering a reinstall of my system, but would really prefer to wait until the new LTS-release next month. Will I end up with the same system if i reinstall 12.04 now and make a dist upgrade later?

---

### Post by TheFu on 2014-03-26
So, let me understand.

You would rather reinstall the OS instead of tweaking DNS settings?
I don't run a desktop Ubuntu, so I cannot tell you how to solve this using a GUI, but of you post the /etc/resolv.conf and /etc/network/interfaces file, I may be able to help.

Any update from LTS-to-LTS can have issues .... or not. Always backup everything and know how to restore BEFORE beginning. There are no guaranties, just that Canonical tries to make this update path as painless as possible, but with millions of different configurations, it doesn't always work.  Plus, network settings will probably be carried forward - things like DNS, so ....

---

### Post by RS_Hylleberg on 2014-03-26
no, I would rather fix my internet/DNS - but I planned to reinstall when the new release is due in april, regardless of my present problems. 
I just don't know where to start fixing my DNS ...

All it says in "interfaces" is:

```
auto lo
iface lo inet loopback

```

"resolv.conf" is empty

---

### Post by TheFu on 2014-03-26
Well - I guess networking in desktops is completely different from servers.  "network manager" and DNS is what I'd search the forums for to find a solution.

Sorry I can't be more help.

Just to clarify - can you ping 8.8.8.8 or not?

---

### Post by steeldriver on 2014-03-26
First thing would be to check in the GUI connection editor IPv4 tab that you are either requesting DNS via DHCP ("Method: Automatic (DHCP)") or are specifying one or more DNS servers in the boxes provided (for "Method: Automatic (DHCP) addresses only" and/or "Method: Manual")

If that's correctly configured but /etc/resolv.conf is empty, you probably broke the resolvconf package - try

```
sudo dpkg-reconfigure resolvconf
```

It will present you with a question about preparing /etc/resolv.conf for dynamic  updates - answer "Yes". It may also present you with another question about temporarily appending your  existing config to the dynamic one - I suggest answeing "No" to that one.

---

### Post by varunendra on 2014-03-26
Wondering if it could be a b44+b43 case.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by RS_Hylleberg on 2014-03-26
Thanks to steeldriver I'm now online again!

My IPv4 settings are automatic and judged just by the look of settings in network manager it is exactly the same settings as my other PCs.
Your suggestion to reconfigure resolv.conf did the trick for me, now it says:

```

nameserver 127.0.0.1

```

and I got my internet connection up and running again

---

