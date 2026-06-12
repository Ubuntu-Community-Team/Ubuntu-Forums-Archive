---
title: "Can't access just github.com via browser - on Windows it works"
date: 2022-11-28
forum: Networking &amp; Wireless
---

### Post by vjekobalas on 2022-11-28
I have Ubuntu desktop 22.4 installed in Virtualbox on a  Windows10 host pc.
My local network subnet is 192.168.X.X but the Ubuntu Desktop VM shows 10.X.X.X in the settings.

Could someone please explain :
(a)How is it that I can access internet from the Ubuntu VM (I'm writing from the VM now) if it is not
in the same subnet as the router ?
(b)If the Ubuntu VM should have an ip address in the same subnet as the rest of the devices on
my network, how do I set the VM to use dhcp (I can set a static ip address for the VM on the router
or let the router allocate an aviailable ip address)?
(c)A weird one - if I open Firefox on the VM, I can watch youtube videos, open search results for GitHub BUT
can't access GitHub web page ([www.github.com]("http://www.github.com")). If I open Firefox on the Win10 host, it opens GitHub
web page without problems.

---

### Post by ian-weisser on 2022-11-28
a) Your Windows Virtualbox application is acting as a router, connecting your 19.168.X.X real-life LAN with a 10.X.X.X subnet that connects the Guest VMs.

b) Go into your Windows Virtualbox settings. The default Network Adapter is set to NAT. Change it to "Bridged Adapter"

---

### Post by TheFu on 2022-11-28
ian-weisser is right. A bridged network (set in the virtualbox VM Network settings), is how to make a VM use the network DHCP server to get an IP or if you want a static IP for it, set that static IP inside the guest VM in the normal way for the distro. Regardless, "bridged model" in the vbox network for that VM is required.

There are other networking options for virtualbox.  Chapter 6 of the vbox manual does a good job explaining the options.
[https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)

---

### Post by vjekobalas on 2022-11-30
Much appreciated, that clarifies and resolves the ip issue but I still can't access github.com via Firefox in
the Ubuntu VM in Virtualbox although I can access other web sites.

---

### Post by TheFu on 2022-11-30
> **vjekobalas said:**
> Much appreciated, that clarifies and resolves the ip issue but I still can't access github.com via Firefox in
the Ubuntu VM in Virtualbox although I can access other web sites.

There are websites that will check websites from multiple places around the world to see if it is just you or everyone else who is down.  Start with that, next time it happens.  Also, beware that some govts block access to sites with a history of supporting things they don't like.  github is one of those from time to time for *certain* countries.

But the  first things to check are:
- can you 'ping' the website by name or IP?
- can you resolve the host - use 'dig'

Websites go down all the time for a number of reasons.  Heck, mine go offline for about 20 seconds every night while I'm doing backups.  If anyone does notice, by the time they try again, it is back up.  A few weeks ago, my ISP had a 2-3 hr outage, so any dynamic parts of my internet stuff wasn't available, including email.  A few times over the decades, I've misconfigured things and didn't notice since it all worked for me, but nobody outside could see anything. Oooops.

---

### Post by vjekobalas on 2022-12-01
I'm newbie surprised - it was the DNS server. Once I changed the ISP DNS servers on the router to Google 8.8.8.8 and 8.8.4.4
I could access github.com on the Ubuntu VM in Virtualbox also. I missed looking at the basics because I could
access github.com from the host Windows 10,so neglected to check the name resolution on the VM. I don't know
what is the best practice regarding DNS server- should it be defined only on the router or on each host/OS on the pcs in
the network.

Thanks for teaching me something ! I wanted to acknowledge your answers but I can't see the star or medal that is 
talked about that should be near your avatars.

---

### Post by TheFu on 2022-12-01
Thanks for the thought, but actually the best thing you can do is what you've done.  Say what you finally determined the issue to be and that it is corrected.

But to help even more, please use the "Thread Tools" link near the top of the page and mark this thread as "SOLVED".  That way people seeking answers know it contains the solution.  The thread title does sorta suck - would be better if the specific problem were concisely listed.  Also, marking it "SOLVED" prevents people who'd like to help from wasting time.

---

