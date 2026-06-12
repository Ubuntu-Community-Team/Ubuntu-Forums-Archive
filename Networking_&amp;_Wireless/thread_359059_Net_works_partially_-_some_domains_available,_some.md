---
title: "Net works partially - some domains available, some not"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Tachyon_ on 2007-02-11
Hi,
I can't understand why my laptops kubuntu stopped loading some domain names. This is really confusing and hasn't occured before. I might have done upgrade or something before this problem occured, now I cant upgrade with apt-get anymore. Problems exist even if I disable iptables firewall and try with firefox or konqueror. All other computers connected trought same ADSL-device work.

Some domains, like google.com, slashdot.org kde.org and ubuntuforums.org work fine, but some like ubuntu.com, kubuntu.org, cnet.com etc. and almost all random links in google, just don't load. I get message:

"An error occurred while loading [http://www.ubuntu.com:](http://www.ubuntu.com:)
Unknown host www.ubuntu.com" with konqueror (cache, cookies etc. cleared).

Torrent works, apt-get doesn't.

I have win XP just for gaming, but it displays all domains just fine, so it isn't the hardware. I really don't have any idea what could cause this?

---

### Post by Tachyon_ on 2007-02-12
Okay, I came thinking that maybe it was ipv6 after very much googling, but no, disabling it didn't help. Then I found out that my etc/resolv.conf was different from any other machines. it pointed nameserver to somewhere ... and had search verkkotieto.fi (provider) when all other machines had nameserver 192.168.1.1 (router).

I changed it and now it works, it tookt some time however.

(Two replies in one thread so this seems answered)

---

### Post by kot7k on 2007-02-12
hi, i have exactly the same problem as you, some internet domains work but some other not, i also tried to disable the ipv6 and now surffing seems to be faster, but some domains like [www.bugmenot.com](www.bugmenot.com) or loggin into a hotmail account seems to dont work (they work on windows xp). I also tried to put opendns into /etc/resolv.conf and tried everything on this topic " Internet works sorta?" but is still the same, its very annoying that you just cant visit some pages that you know you should can. I hope somebody can help me im tired of searching and trying thigs without any result :/.
```

resolv.conf
search mshome.net
nameserver 192.168.0.1
```

Can please somebody try to help me?


EDIT: by the way i forgot to say that im not connected directly to internet, im on a lan and the main server have a windows xp os (192.168.0.1), dont know if it matters.

---

### Post by kot7k on 2007-02-16
Any idea?

---

### Post by Floppyjoe on 2007-02-16
I copied this from the OpenDNS site:
> Using OpenDNS with DHCP

If you assign your computer's IP with DHCP, it probably overwrites your /etc/resolv.conf. Here's how to fix that:

   1.

      Run: sudo gedit /etc/dhcp3/dhclient.conf
   2.

      Change the prepend line to read:

      prepend domain-name-servers 208.67.222.222, 208.67.220.220;

      This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.
   3.

      Run: sudo /etc/init.d/networking restart
   4. Using Ubuntu? Check "Networking" to see if the changes applied correctly.
      Go to "System –> Administration –> Networking" and click the DNS tab.


---

### Post by chili555 on 2007-02-16
I would take everything out of resolv.conf...everything, except:```
nameserver 192.168.0.1
```

Then try again and let us know.

---

### Post by handy on 2007-02-17
resolve.conf get's rewritten it is not the place to set up your DNS addresses.

Have a look at the DNS section of [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034"), it should get you out of trouble.

---

### Post by kot7k on 2007-02-19
Still the same problem :/, i cant access webpages like [www.bugmenot.com](www.bugmenot.com) or log into a hotmail account :(. But i can enter this page for example, google, an a lot of more :/

Finally fixed thanks to this post:

> **Karris said:**
> Woohoo! Solved it!

I found a fix, seeming with most SiS190 type integrated network chips.

What I did was:

```
sudo ifconfig eth0 mtu 1492

sudo /etc/init.d/networking restart
```

And that's it!

I can't say I know what I did technically, but it sure worked. :D

Thanks you very much :D

---

