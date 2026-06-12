---
title: "Bridged Network. Laptop and Xbox 360"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-07-28
Hello all, 

I am looking to share my internet from my laptop to my xbox 360.

Right, what I would like is:

Xbox 360 connected to my Laptop through Ethernet, then the laptop's wireless card connected to my Wireless router. 

I want the Xbox 360 to be able to have internet access, through the Laptop's Wireless card.

How would I do this?
Where do I start?
My wireless card is works. But not perfectly. But works :)

Please point me in the right direction.

Thanks :)
Tom

---

### Post by dmizer on 2008-07-29
It's not bridging, but this will work: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Edit:
"will" = "should" ;)

---

### Post by Tom--d on 2008-07-29
Thanks :)
I thought i got it wrong.

But can I still use Wifi-radar for my wireless/internet connection and have the ethernet plugged in from the 360. I dont want firestarter installed either. I have no reason for a firewall, at all.

---

### Post by dmizer on 2008-07-29
> **Tom--d said:**
> Thanks :)
I thought i got it wrong.

But can I still use Wifi-radar for my wireless/internet connection and have the ethernet plugged in from the 360. I dont want firestarter installed either. I have no reason for a firewall, at all.

Yes, you can still use wifi-radar for your wireless internet connection.  In the howto, simply replace eth0 with your wireless connection.

Firestarter is not a firewall.  Firestarter is a GUI frontend for Ubuntu's firewall called IPtables.  And yes, you do need a firewall to configure internet connection sharing.  Fortunately, but using the howto I linked, you are only changing the part required for sharing your internet connection.

---

### Post by Tom--d on 2008-07-29
I see. 
I have now done what I need with Firestarter but really, I dont want that. Its old. Hasn't been updated in a long time. its dead etc. 
I can work UFW tho. Thats simple but I dont know how it would handle Internet connection sharing. 
Is there any other CLI or GUI for iptables, which support internet sharing? Of course, would be great if it was in the repo :D

Many thanks!

---

### Post by Tom--d on 2008-07-29
Also, 
How do I clear all my settings in iptables and ufw? I mean all.

---

### Post by dmizer on 2008-07-29
to clear all iptables rules:
```
sudo iptables -F
```

---

### Post by Tom--d on 2008-07-29
Thanks :)

Right, Well I can give my 360 access to the internet through Firestarter.
I dont really want to do that, as explained before. Its old. Dead etc etc

Whats the alternative way? (dont really want to directaly fiddle with the iptalbes.)
Something with a gui maybe?

---

### Post by dmizer on 2008-07-29
The best and easiest way is to modify iptables directly.  According to the howto I linked in my second post, it's only three lines:
```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
```
Where:
eth0 = the network card connected to the internet (in your case, it's wireless)
eth1 = the network card that your 360 attaches to.
192.168.0.0/24 = a subnet other than what your wireless card is on.

That's it.

---

### Post by Tom--d on 2008-07-30
Right I see

but if i put those in /etc/rc.local would the rules unitil i restart? as I need ifconfig eth0 up at the start as its otherwise down. 


Also,
192.168.0.0/24 
Is that the ip up to 24?

So 192.168.0.1-24?

---

### Post by dmizer on 2008-07-30
> **Tom--d said:**
> Right I see

but if i put those in /etc/rc.local would the rules unitil i restart? as I need ifconfig eth0 up at the start as its otherwise down.
Save the configuration with this command:
```
sudo iptables-save
sudo sh -c "iptables-save > /etc/iptables.rules"
```
That should be enough to make the change permanent. You can check that your settings are active with this command:
```
cat /etc/iptables.rules
```

> **Tom--d said:**
> Also,
192.168.0.0/24 
Is that the ip up to 24?

So 192.168.0.1-24?
No, the /24 means a 24 bit subnet mask, or 255.255.255.0, or all ip addresses from 192.168.0.1 to 192.168.0.254.

---

### Post by Tom--d on 2008-07-30
> **dmizer said:**
> Save the configuration with this command:

No, the /24 means a 24 bit subnet mask, or 255.255.255.0, or all ip addresses from 192.168.0.1 to 192.168.0.254.

Right, I'm understanding now :)

So, 
What would I need to put in my 360 for the default router? (192.168.0.1 or 192.168.0.0?)

And what does a subnet mask do? 255.255.255.0 I mean. As that is what I use? I mean. It doesn't change (for me).

And, 
If I have those rules saved in Iptables. Will the firewall be up and running all the time? Would I need to put in more rules for allowing port 80 and etc etc through? Or is that not needed and why?

Sorry for asking all these questions. Is just I want to know what's going on. What am I doing to iptables etc.
And, how will I know the firewall is up and running?. What command do I need?
Can I have UFW up. As that's easy to understand :) 
But if I have ufw enabled, would that mean the rules I put in iptables not to be used?

Thank you :)

---

### Post by dmizer on 2008-07-30
your xbox 360 can have any address between 192.168.0.1 and 192.168.0.254.  It does not matter WHICH address you pick, just that you know which one it is.

However, the ip address on the xbox should not be the same as the wired ethernet card on your ubuntu machine.

Once you've saved the firewall rules, they are active.  There should not be any more need for enabling/configuring the firewall once it has been configured properly.

---

### Post by Tom--d on 2008-07-30
> **dmizer said:**
> your xbox 360 can have any address between 192.168.0.1 and 192.168.0.254.  It does not matter WHICH address you pick, just that you know which one it is.

However, the ip address on the xbox should not be the same as the wired ethernet card on your ubuntu machine.

Once you've saved the firewall rules, they are active.  There should not be any more need for enabling/configuring the firewall once it has been configured properly.

Thanks :)
Now I've done the iptables. Saved it. 

How will I know iptables is up and running?

Also,
With ifconfig eth0 up
do I need to do, 
```
ifconfig eth0 192.168.0.1
```
as well?

---

