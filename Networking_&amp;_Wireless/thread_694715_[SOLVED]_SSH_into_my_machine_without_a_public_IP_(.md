---
title: "[SOLVED] SSH into my machine without a public IP (By email?)"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by benpage26 on 2008-02-12
I while ago when I was looking into using Linux I saw a tip that allowed you to send an email to your computer at home that then triggers the computer to initiate a SSH tunnel to your workplace (or possibly vice versa).  I do not remember the advice and I cannot find it on Google either.  
*[SIZE="1"](Sorry if this post is long, but I want to give you all the information).[/SIZE]*

I am a student living in halls, my ISP's security is quite tight.  I was not able to use SSH to connect to my laptop from my university, but I can SSH from home to the campus.  I guessed it was an ISP issue so I emailed their tech support and they told me they do not give me a public/external IP address unless I pay for the platinum package.  This upgrade package is too expensive for me, as it overkill for the simple need of using SSH.  I am assuming that my connection goes through a router or proxy of some sort, so everyone in the residence has the same IP as visible to the internet.  And i guess port forwarding is out of the question (if that would be a soloution) because they are in control of the router not me.

As I said at the start, I found a blog or website somewhere where a man had a similar problem, he could connect to home from work, but not to work from home.  As a solution, he used an email (sent from home) triggered script to start a connection from his work computer to his home computer, then somehow he used that connection in reverse to start another connection that would work from home to the work servers.

Can anyone point me in the right direction, or tell me how this is possible.
Sorry again for the masses of writing.

Ben.

---

### Post by lespaul_rentals on 2008-02-12
That is a load of horse****; every computer has an IP address and your ISP has no right to keep it from you.  Sounds like a plan so they can make money off people who are ignorant about computers.  Go to [www.whatismyip.com](www.whatismyip.com) and it will give you your IP address.

As for the reverse connect, I'm sorry but I'm not aware of anything email-based.  It seems that you would need to set up an SMTP server on the computer you would send an email to, but I'm sure both your University and your ISP block port 25.  You could always get a dynamic hostname and get an application that would continually attempt to reverse connect to the hostname.  That'd probably be your best bet.

---

### Post by mike.123850 on 2008-02-12
True every computer does have an IP address. However, if the ISP's (campus) network is setup for DHCP and uses a NAT firewall those computers behind it may not be accessible from the outside world. For example, use the IP address from whatismyip.com, then take that number and enter it into [http://www.arin.net/whois/](http://www.arin.net/whois/) Chances are it is not your actual computer, rather it is the IP of your Internet Service Provider (campus network).


In that case, you would need to get the static IP address to do what you want. You might get away with something like Gotomypc.com, but I have never used something like that and don't know if it would work with Ubuntu or any Linux distro. I also don't know how secure it would be. But it might be worth looking into.

A free alternative is [https://secure.logmein.com/home.asp?lang=en](https://secure.logmein.com/home.asp?lang=en)  Again, I have no firsthand information on either of these, so use at your own risk,

Good luck,
Mike

---

### Post by lespaul_rentals on 2008-02-12
> **mike.123850 said:**
> True every computer does have an IP address. However, if the ISP's (campus) network is setup for DHCP and uses a NAT firewall those computers behind it may not be accessible from the outside world. For example, use the IP address from whatismyip.com, then take that number and enter it into [http://www.arin.net/whois/](http://www.arin.net/whois/) Chances are it is not your actual computer, rather it is the IP of your Internet Service Provider (campus network).

Oh, my bad.  I thought he meant the IP address of his home computer!  Yes, you are totally right; the university has him behind a NAT.

If you are trying to take control of a Windows computer, there's always NuclearRAT.  Yes, I know it's a "Trojan" but it has legitimate uses.  It can use reverse connection, if that helps.

---

### Post by benpage26 on 2008-02-14
Thanks for your replies!

I looked up the whois data and it is the ip of the ISP not of me.

Both Uni and Home are Linux machines, and the function was 'email triggered' by a feature in Thunderbird that allows you to run a script.
could i put a script that would start a connection from the home computer (maybe just a ```
ssh user@host -password
```) and then trigger it by email.  And then use that connection to locate my computer and connect the other way to grab/place files.

The grabbing and placing of files is the main thing that i want to do.

---

### Post by jetsam on 2008-02-14
A setup like [this]("http://www.vdomck.org/2005/11/21/reversing-an-ssh-connection/"), except you'll need to write the script to replace "Pete."

---

### Post by benpage26 on 2008-02-16
Thanks,

That looks like the solution I was looking for.  I don't have time to implement it right now, a project just came up :(.

But I'll mark this thread as solved, thanks for the help forum members! :)

edit: 
also found this
[http://www.vdomck.org/2005/11/21/reversing-an-ssh-connection/](http://www.vdomck.org/2005/11/21/reversing-an-ssh-connection/)

---

