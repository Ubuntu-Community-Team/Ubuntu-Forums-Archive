---
title: "UFW usage on terminal"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by mentisafer on 2010-06-09
I just installed Ubuntu Lucid and read about the simple set up of firewall UFW. I just want to make sure I set it up right; here is what I did:

sudo ufw allow from 192.168.0.0/24
sudo ufw default DENY
sudo ufw enable

Honestly I don't understand too much but was just following instructions. Is the first command ok, or should I change it?
Thanks

---

### Post by Breambutt on 2010-06-09
You get an error message if your syntax is incorrect and *sudo ufw status* displays a list of rules that are currently activated.

If you don't feel like getting familiar with the syntax you can also install **gufw**, a graphical frontend for ufw. Will appear under System > Admin > Firewall.

Just for the record, "sudo ufw allow from 192.168.0.0/24" can be deleted with "sudo ufw delete allow from 192.168.0.0/24". I found this a little un-uncomplicated at first, or at least a tad unintuitive.

---

### Post by mentisafer on 2010-06-09
thanks for the reply; but what does that command do? Do I need it at all? To browse the internet and perform normal activities online? Or does it open unnecessary ports?

---

### Post by Breambutt on 2010-06-09
Uh, oh. Well, IF you're behind a router and IF your router uses the 192.168.x.x scheme (there's also others such as 10.0.x.x) it allows incoming traffic from your local network between the range 192.168.0.0-192.168.0.24.

Usually the gateway is 192.168.0.1 (if I remember correctly, I have one of those 10.0.0.2 setups), your first machine on the LAN is 192.168.0.2, the second 192.168.0.3 and so on.

If you only have one computer or don't need to access the computer from other machines in the network you don't need the example rule and can safely delete it.

Type *ifconfig -a* to see your network information. Mine says

[I]eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx 
          inet addr:**10.0.0.3**  Bcast:10.0.0.255  Mask:255.255.255.0[/I]

and the bold stuff is your IP.

The other two lines in your original post were fine. It sets the default behavior to block incoming connections and enables + automatically starts the ufw when you boot into Ubuntu.

---

### Post by Deadite81 on 2010-06-09
If you use a router those are all things you need to use the internet.  I'm behind a Linksys wireless router, and if I don't allow 192.168.1.x I cannot connect.  I notice you put a zero in there, which to my understanding is atypical.  If you aren't behind a router you do not need this setting.  Right clicking on the network monitor in your panel and selecting "Connection Information" will tell you your ip address etc., if you're not comfortable with the commandline.

I would do as Breambutt suggests and install "gufw" or, if you want a more Windows like firewall, "sudo apt-get install firestarter".  It gives you a graphical interface with lots of info and is simple to use.  I used it for the longest...just switched back to gufw.  It gives you real-time stats, whois lookups, a systray icon, etc.

You will also have to whitelist several other things probably...
port 443 (SSL, Gwibber doesn't work without it)
port 80 (If you're set to deny, no internet for you)
135,139,445/tcp ; 137;138/udp (Windows/Samba sharing ports)

That's a good basic setup that should be fine for a normal user.
Also, "192.168.0.0/24" is a range much larger than 0-24.
A cool tool to calculate ip ranges and then some is Gip IP Address Calculator, which you can get with "sudo apt-get install gip".

Hope this was helpful, good luck.

---

### Post by Breambutt on 2010-06-09
Oh yeah, just noticed that subnet thing. Funnily enough I couldn't have explained it correctly anyway. These uncomplicated things are a little too complicated for me, but have to try everything that's shipped in Ubuntu. Now I'm curious - can you even define a certain range that way? : instead of / or something.

---

### Post by Deadite81 on 2010-06-09
I'm far from an expert, believe me, but subnets and what not on the Linux firewalls I've used only accept "/" to denote a range.  A port range, on the other hand, can be ```
port:port
```I've never configured a firewall through files or the command line...unless BlockControl counts, and it only accepts "/".  I quit Windows cold turkey about 6 months ago, so learning Linux firewalls was quite a chore, on top of everything else!  I really miss the whitelisting by application feature of Windows' firewalls :(  

At one point I tried to learn how to calculate ip ranges myself, and apparently you have to be a master physicist to do so manually, so that last last bit was really just anecdotal.  The actual ip range of 192.168.0.0/24 is 192.168.0.0-192.168.0.255, assuming his subnet mask is 255.255.255.0.  To most people this is unknown, they just copy and paste.  Is it relevant?  No, not really. :)

(Had to put "port:port" in code tags because....awesome.)

---

### Post by Breambutt on 2010-06-09
Yeah. Well. Yeah. Something. I'm unable to produce anything constructive right now.

I got around to setting up a Debian server with iptables and at least for me configurations like this are a one-time thing and I may recycle them for years and even forget the basic syntax (which I'm not yet fluent in with ufw). The port range syntax I miraculously enough remembered, but IP ranges are a blank. Would have to dust the iptables manual as well, but... oh well, don't really need them on this machine anyway.

It's a good thing "human beings" don't really have to worry about these things, for curiosity kills even a seasoned nolife chump like me on a daily basis.

---

