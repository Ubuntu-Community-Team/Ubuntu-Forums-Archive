---
title: "Create VPN without static IP"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-04
I want to create a VPN so that a specific computer (call it Computer A) can connect to my computer (call it Computer B). Specifically, I want Computer A to be able to mount a specific folder on Computer B.

I have ddclient set up so that when my computer moves to a different location, I have a URI to point to my new IP address.

I have worked through the VPN instructions, but it does have a problem: It requires a static local IP address (e.g. 192.168.1.10), which the router needs to forward to.

How can I set up a VPN such that it doesn't matter where my computer is and which Internet connection I'm using?

* EDIT * It doesn't have to be a VPN as such. I simply need Computer A to be able to see a specific folder on Computer B, securely.

---

### Post by Jeroensum on 2010-06-04
It seems that you are able to manage the router, so why aren't you able to manage the dhcp server? The easiest solution would be to tell the dhcp server to give the PC a static IP or to dismiss dhcp all together and set a static ip for that box.

---

### Post by Paddy Landau on 2010-06-04
> **Jeroensum said:**
> It seems that you are able to manage the router...
Yes, that's all fine when I'm at home.

But...

When I pick up my laptop (Computer B) and go to a different town, I'll connect via a completely different ISP.

That's the problem. I should have explained that in my first post. Sorry.

---

### Post by bodhi.zazen on 2010-06-04
You would need to use a DNS service, such as dyndns, and update your public IP.

You would then need to be able to forward ports from your new router to your private ipaddress, and you would unlikely be able to do that as the router is not under your control.

I think you need a dedicated server that you can ssh (sshfs) into.

---

### Post by Paddy Landau on 2010-06-04
> **bodhi.zazen said:**
> You would need to use a DNS service, such as dyndns, and update your public IP.
I have it.

> **bodhi.zazen said:**
>  You would then need to be able to forward ports from your new router to your private ipaddress, and you would unlikely be able to do that as the router is not under your control.
Well, there must be some type of option that tunnels through routers. I know this, because, for example, [LogMeIn]("http://logmein.com/") and [Yuuguu]("http://www.yuuguu.com/") do just that, although sadly they don't provide quite what I'm after.

---

### Post by The Cog on 2010-06-04
There is a protocol called UPnP (Universal Plug 'n' Play) that can request some makes of router to open incoming ports on the fly. I don't know if there's a Linux client though, and I know not all routers support it.

Does it have to be the fixed computer connecting to the mobile? Can't you have the mobile "call home" whenever it can, so the VPN is always available to connect back through?

---

### Post by keithweddell on 2010-06-04
I agree.  I think you are looking at this backwards.  You can ssh from Computer B back to your home base (Computer A), set up a ssh reverse tunnel and trigger whatever you want Computer A to do with the folder on Computer B.  Then you do not rely on Computer A knowing the ip address for Computer B.


Keith

---

### Post by Paddy Landau on 2010-06-04
Thank you for your ideas.

> **The Cog said:**
> There is a protocol called UPnP...
Hmm, I'm not always in places where I can control the router.

> **The Cog said:**
> Does it have to be the fixed computer connecting to the mobile? Can't you have the mobile "call home" whenever it can, so the VPN is always available to connect back through?
Well, it made sense to me like that, as the mobile computer is the server. But I'm willing to hear options.

> **keithweddell said:**
> You can ssh from Computer B back to your home base (Computer A), set up a ssh reverse tunnel and trigger whatever you want Computer A to do with the folder on Computer B.  Then you do not rely on Computer A knowing the ip address for Computer B.
Wow, now you're getting a bit more complex than I actually understand.

Here's how I see it, and it's in layman's terms because I'm not an expert.

Something like LogMeIn or Yuuguu has the server advertising its presence, even behind a router. The client simply looks for the correct name, and the computers link up.

Now, it's possible that behind the scenes they're doing what you explain.

So...

Is what you explain easy to do, or will I be tearing my hair out (I ask humbly)? I'm very willing to give it a try, but you'd have to use baby steps with me, because I don't understand about SSH reverse tunnels, or how to mount a folder through SSH (the only SSH I've used is connecting to my web host, and that's terminal only, no GUI).

---

### Post by The Cog on 2010-06-05
> **Paddy Landau said:**
> 
Well, it made sense to me like that, as the mobile computer is the server. But I'm willing to hear options.

What I'm thinking is that if you configure OpenVPN with your fixed (home or work?) computer as the VPN server and your laptop computer as the client and the VPN always running, then the laptop will connect to the fixed computer at every opportunity. The VPN will always be there, providing network connectivity between them. Apart from the odd keepalive packet, there's no traffic unless you actually start using the VPN.

With the VPN connectivity always there, you will be able to connect from the fixed computer to the service on the laptop whenever you want.

The only requirement you have at the places you leave the laptop is that their firewall must allow the VPN protocol out to the internet. OpenVPN can also connect through an HTTP proxy but requires site-specific configuration for this.

---

### Post by Paddy Landau on 2010-06-05
> **The Cog said:**
> What I'm thinking is that if you configure OpenVPN...
Thank you, I learn something every day.

I'll mull this over. Both computers are laptops (Computer A is my wife's, Computer B mine), so it's possible that we'll both be out-and-about at the same time. That's why I wanted this requirement.

Maybe I'll just have to accept that one of us has to be home for this to work.

I hear what you say about the firewall, and that's something I'll have to accept.

---

### Post by Jeroensum on 2010-06-05
> **Paddy Landau said:**
> 
Something like LogMeIn or Yuuguu has the server advertising its presence, even behind a router. The client simply looks for the correct name, and the computers link up.


That's not really how it works. You make use of the servers @ logmein or yuuguu to get this to work. When you start your client it sets up a connection to the logmein server and so does the computer of your counterpart on the other side of the web. The server(s) at logmein effectivly broker the connection and setup a reverse tunnel from computer A trough B to C
A = you
B = logmein
C = your counterpart

There is no other way that this could work otherwise. :)

To get back to your problem, if I understand correctly you have a router but no PC at home and you and your wife both have laptops that are at different locations (both not at home) ?

If this is the case and you really want to setup the connections yourself then you need one of two things:
-Control of one of the routers at whichever location
or
-A pc at home (or get an virtual hosted server for a small price each month) with an ssh server and a port forwarded from your router at home to this server.

With the first option you could set a port forward on the router and check the external IP and setup an SSH connection.

With the second option you could let one of the laptops(C) connect to your ssh server at home and setup a reverse port forward, this will create a reverse connection back trough the ssh encrypted connection) to the laptop with a shell, which you could manage from the ssh server at home.
With the second laptop you would connect to the forwarded port at the server at home and get shell access to the other laptop.

The how's I can teach you if you can tell me if one of the above is an option. If none of the above are an option then you're stuck with Logmein or one of it's variants.

---

### Post by Paddy Landau on 2010-06-06
@Jeroensum

Wow, that makes things very clear. Thank you for this explanation.

Thinking about it, I suppose that's how similar connecting programs such as Skype work?

I think the solution will be more complicated than I'm willing to go, mainly because I don't have an always-on computer at home.

Unfortunately, neither LogMeIn nor Yuuguu provide what I want, so I'm going to search the 'net to see if I can find a commercial solution that does work.

I think that I'll mark this as "Solved", because you've given the outlines of what needs to be done. If I find a commercial solution, I'll post it here.

Thanks again to everyone who contributed to this thread. My understanding is much greater now.

---

### Post by Paddy Landau on 2010-06-07
> **Jeroensum said:**
> The how's I can teach you...
I have been thinking about this a lot.

I had a sudden realisation that I can access my web host through SSH.

Would that allow me to set up what you suggested?

If so, I'd love to give it a try.

---

### Post by zaphod777 on 2010-06-07
I think the easiest solution would be to use a service like dropbox then you can have the same folder synced and shared across multiple computers and users. Otherwise you can setup an at home server suing an old pc or a shiva plug and setup a vpn or ssh connection to the files that each pc needs to access.

---

### Post by Paddy Landau on 2010-06-07
> **zaphod777 said:**
> ... a service like dropbox
Cool, that looks good. Can you access it just like another folder? That's what I need.

Thinking about it, what about the new Ubuntu One? Does that do something similar, too?

* EDIT * Are they secure?

---

### Post by Paddy Landau on 2010-06-09
@Jeroensum - I thought that I'd try out your suggested method of having some type of intermediate computer with reverse ports (as per your [previous post]("http://ubuntuforums.org/showthread.php?p=9416719#post9416719")).

I've Googled and read and tried and, unfortunately, I remain quite bewildered. I haven't managed to make progress.

As the go-between, I've been trying my web host, which I can access through SSH. It may be that the web host has firewalls or something that prevents it, but I'd like to try.

Do you think you'd be able to walk me through setting it up please? Or, point me to some helpful tutorial on the Internet?

---

### Post by zaphod777 on 2010-06-09
> **Paddy Landau said:**
> Cool, that looks good. Can you access it just like another folder? That's what I need.

Thinking about it, what about the new Ubuntu One? Does that do something similar, too?

* EDIT * Are they secure?

Yes they are both secure Ubuntu One is only for Ubuntu Dropbox can be used on all platforms even your iphone or Android phone. 

I personally like dropbox because I can easily share a folder with another drobox user by entering their email address under the dropbox folder sharing option. 

It integrates pretty nicely into nautilus.

with your webhost you can do a portscan on your domain to see what ports are open. Most likely 80 (web), 443 (SSL), 21 (FTP) I would be surprised if there was anything else. 

You could use FTP but that is very insecure as FTP usernames and PW are not encrypted and anyone with a packet sniffer can see it plain as day. IF you have root access to the host server you may be able to remap a port for SSH but in the long run I think t will cause management problems for your web host. 

I think dropbox is really the way to go.

You can even logon to the website and upload and download files as needed from a public PC. 

[https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by Paddy Landau on 2010-06-09
@zaphod777:

Thank you, I signed onto Dropbox, and installed it on both the computers.

I see that it does everything I need, and more.

It really does work well, though strangely I had to reboot both computers twice to get it working.

Thanks for the advice, everyone.

---

### Post by zaphod777 on 2010-06-09
Great glad it works for you.

---

