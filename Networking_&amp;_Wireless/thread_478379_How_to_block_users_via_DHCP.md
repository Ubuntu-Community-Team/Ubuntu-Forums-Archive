---
title: "How to block users via DHCP"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by jconnett on 2007-06-19
I run a small, 10 client XP workgroup with an Ubuntu server running Samba as a file server.   I'm also using the Ubuntu server to run a DHCP server.  From the logs, it would seem that someone is using their own laptop to simply plug into the network, get an address, and go onto the internet.  I would like to stop this activity.

I've looked on the gateway router and there is no feature to block MAC addresses (this would be the easy solution).

Is there anything that can be done with the DHCP router or network to block these users who are using the network to gain access to the internet?

I'm not concerned about unauthorized access to the fileserver because of the permissions set via Samba and security inherent to Ubunutu.....it's the unauthorized access to the internet that I want to stop...for obvious reasons.

Thanks!
--Jim

---

### Post by Austin_KW on 2007-06-19
Dhcp is not goint to help you as they can always get to the gateway using static IP. 

You may have to use your ubuntu box as a gateway so that all internet traffic goes through it and out another ethernet card to the router. Then you can configure your firewall to police the traffic. Or get a better router or build your own dedicated linux router gateway.

---

### Post by p_quarles on 2007-06-19
I can think of a couple things you could try. First, you could assign every legitimate machine a static IP address, and then use the router to restrict the range of DHCP assigned addresses to just those. In other words, for ten machines it would be something like range = 192.168.1.2 - 192.168.1.11

If you think this person is using a wireless connection, though, you could just institute an encryption policy. Good idea anyway.

---

### Post by p_quarles on 2007-06-19
> **Austin_KW said:**
> Dhcp is not goint to help you as they can always get to the gateway using static IP. 

You may have to use your ubuntu box as a gateway so that all internet traffic goes through it and out another ethernet card to the router. Then you can configure your firewall to police the traffic. Or get a better router or build your own dedicated linux router gateway.
Yeah, good point. Didn't think of that. I guess for static IPs to work you'd have to leave every client on all the time.

---

### Post by dreadlord_chris on 2007-06-19
> **p_quarles said:**
> I guess for static IPs to work you'd have to leave every client on all the time.

Why would that be?

---

### Post by p_quarles on 2007-06-19
> **dreadlord_chris said:**
> Why would that be?
I'm not sure, but i'm thinking that if you went with my idea of restricting the IP range to ten static addresses, the interloper would be able to log in as any machine that wasn't currently active. I'd be happy to know I'm wrong about this, though.

---

### Post by dreadlord_chris on 2007-06-19
> **jconnett said:**
> I run a small, 10 client XP workgroup with an Ubuntu server running Samba as a file server.   I'm also using the Ubuntu server to run a DHCP server.  From the logs, it would seem that someone is using their own laptop to simply plug into the network, get an address, and go onto the internet.  I would like to stop this activity.

I've looked on the gateway router and there is no feature to block MAC addresses (this would be the easy solution).

Is there anything that can be done with the DHCP router or network to block these users who are using the network to gain access to the internet?

I'm not concerned about unauthorized access to the fileserver because of the permissions set via Samba and security inherent to Ubunutu.....it's the unauthorized access to the internet that I want to stop...for obvious reasons.

Thanks!
--Jim

I do beleive that since you're using Ubuntu as your DHCP server you can use the **dhcp-client-identifier** option in the server config:
> 
option dhcp-client-identifier string;

          This option can be used to specify a DHCP client identifier in a host declaration,  so
          that dhcpd can find the host record by matching against the client identifier.


---

### Post by Austin_KW on 2007-06-19
There is no security if someone has physical access to the equipment.

Even leaving the clients on, someone can unplug a cable, stick it in his laptop.
And remember mac addresses can be spoofed.

---

### Post by arsenic23 on 2007-06-19
The easiest thing to do would be to completly disable DHCP, set your router to non standard numbers, and then set all of your machines up with static IPs.

So lets say you set your network to run in 192.168.23.x instead of 192.168.1.x.  Then you can set your router, modem, or whatever is your gateway to something like 192.168.23.99.  This won't make it impossible for this person to use your internet, but he'll have to either know what he's doing to get the IPs from your network, or he'll have to guess really well.

---

### Post by jconnett on 2007-06-19
> **arsenic23 said:**
> The easiest thing to do would be to completly disable DHCP, set your router to non standard numbers, and then set all of your machines up with static IPs.

So lets say you set your network to run in 192.168.23.x instead of 192.168.1.x.  Then you can set your router, modem, or whatever is your gateway to something like 192.168.23.99.  This won't make it impossible for this person to use your internet, but he'll have to either know what he's doing to get the IPs from your network, or he'll have to guess really well.

Well, the problem with that is that it's quite easy for someone to gain access to another machine and discover whatever non-standard non-routable IP address we were using, then apply that number to their own laptop, and voila, their on.

---

### Post by jconnett on 2007-06-19
> **Austin_KW said:**
> There is no security if someone has physical access to the equipment.

Even leaving the clients on, someone can unplug a cable, stick it in his laptop.
And remember mac addresses can be spoofed.

Exactly...that's what has been happening...wire out of authorized machine and into the unauthorized machine...and out onto the internet.

The person we're suspecting doing this is not savvy enough to spoof MAC addresses, so I don't suspect (at this time) that that would be a hole that needs to be plugged.

---

### Post by jconnett on 2007-06-19
> **dreadlord_chris said:**
> I do beleive that since you're using Ubuntu as your DHCP server you can use the **dhcp-client-identifier** option in the server config:

Now THIS may be a possibility...I'll do a search on this and give it a try!  Thanks.

---

### Post by jconnett on 2007-06-19
If you think this person is using a wireless connection, though, you could just institute an encryption policy. Good idea anyway.[/QUOTE]

The wireless is not an issue as we are already filtering by MAC addresses and we are also using a 63bit WPA2 key.  The problem exists when someone connects with a hard wire.  I have no way of stopping them from getting access to the gateway.

---

### Post by jconnett on 2007-06-19
> **Austin_KW said:**
> Or get a better router or build your own dedicated linux router gateway.

You know...this has crossed my mind many times...I'm considering turning off DHCP on the Ubuntu server and putting Smoothwall between the gateway and the switch.  Smoothwall would also provide many other services I probably would be interested in, too.

Thanks for the reply...:)

---

### Post by Catsworth on 2007-06-19
I'm assuming that this is a corporate environment, and that the person concerned is employed by the company?

If they are then you need to do the following:

1.  Explain to the senior management that this constitutes a serious risk to the company, both in terms of financial losses and reputational losses.  This person's actions directly compromise the security of the network, and their access (as it is unmonitored/unregulated) could be used for illegal/immoral purposes for which the company would then be liable.

2.  Having convinced senior management of the above, you implement a company-wide policy expressly forbidding the connection of any un-authorised devices.  Stating (very clearly) that anybody caught doing so will be subject to disciplinary action.

3.  You now wait for them to do it again (because they *will*), this time you use a camera/monitoring software to gain proof.

4.  Now you kick their *** out of the company, and make sure the door hits them on the way out!

---

### Post by dreadlord_chris on 2007-06-19
> **p_quarles said:**
> I'm not sure, but i'm thinking that if you went with my idea of restricting the IP range to ten static addresses, the interloper would be able to log in as any machine that wasn't currently active. I'd be happy to know I'm wrong about this, though.

it just seemed rather silly to assign all legit boxes static IPs, then leave DHCP on. What are you going to use it for? If all the legitimate machines have static network info - then only ones that would use DHCP, by definition, would be illegitimate users.

---

### Post by jconnett on 2007-06-19
> **Catsworth said:**
> I'm assuming that this is a corporate environment, and that the person concerned is employed by the company?

Your assumption is wrong...and actually, that makes what I'm addressing that much more of an issue as I'm trying to make sure that the network is as secure as possible, and out of the way of those who are authorized to use it and its resources.

It would be much easier if it WAS an employee, because those policies are in place as you noted, and the results would be...well...as you noted!

Fortunately, through router logs, I'm closing in on a name associated with the unauthorized user because I'd much rather talk to them personally, rather than play a cat-and-mouse game.

---

### Post by arsenic23 on 2007-06-19
I obviously misunderstood the situation here.  Is your network outdoors ??  I'm kind of curious now about what kind of person would walk up to someone's physical network and just plug into it.

---

### Post by Mr. C. on 2007-06-19
The best you will be able to do at this level is MAC address rejection via iptables.

A better solution would be a managed or semi-managed switch that provides authentication.

There are other techniques such as captive portals that allow authentication before using the net.  This is more complex to setup, and requires a more thorough understanding of TCP/IP networking.

MrC

---

