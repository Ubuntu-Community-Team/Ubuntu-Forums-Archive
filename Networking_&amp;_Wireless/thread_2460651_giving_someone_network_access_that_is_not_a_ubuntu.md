---
title: "giving someone network access that is not a ubuntu question"
date: 2021-04-15
forum: Networking &amp; Wireless
---

### Post by josephchrzempiec on 2021-04-15
hello I'm setting up a ubuntu server for someone i work with. I know this is not a ubuntu question but maybe someone can help me out Sense I have 5 static ip addres I setup a second router with a static ip address on it and a ubuntu server. The problem is that the second router uses a 192.168.x.x address and my local network uses a 10.1.x.x address. When i go onto the second router that is the 192.168.x.x router and type in 10.1.x.x to my local router i can see my local router webpage to login and i can login. So my question is how can i stop someone from logging into or seeing my local router is there a way?


Joseph


Edit: My local router is comcast. My second router is Tenda.

---

### Post by TheFu on 2021-04-15
Inner routers and systems will necessarily have access to outer routers/systems.
Sounds like you are on a business comcast setup.  I've never heard of tenda network equipment. I use OPNSense which let's me have different subnets on either the same LAN port or different LAN ports.  I use the Comcast router only in bridge mode so all 5 public IPs are passed into my OPNSense router which provided enterprise class firewall support and continuous patching for the router OS. 

The only things directly connected to the Comcast router is 
a) opnsense router under my control
b) IoS stuff like android devices, IP cameras, gaming systems 
c) all wifi stuff - never trust wifi on your wired network without using a self-hosted VPN.

"a" has stuff I care about and servers on different subnets.  Internet servers are split by risks; desktops and servers don't share the same subnet. Firewalls on the systems AND on the router allow specific access as needed, no more.  Yes, it is a hassle.  That's the price of running public services at home.
"b" and "c" have things I don't expect to ever be secure.  The FBI recommends keeping all IoS devices on a separate, firewalled, subnet. [https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/](https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/) has more about that.

Might be best to get your friends server placed onto a $5/month VPS.  This will drastically improve your HOME security, especially when you aren't solid on network security.

In the meantime, know that Comcast does allow us to change the login password from the default, h............d, to something 20 characters or less.  I spent about 3 hrs on the phone with level-3 support to figure out the rules for those passwords.  22 characters are not allowed. The Comcast firewall is pretty substandard too. Don't think I'd trust it to do much besides what a home user needs who doesn't run any public services.

If you don't want people to login on the comcast router, setup a complex, random password that is as long as allowed. Have your password manager generate it. No special characters, I'm sad to say.

---

### Post by josephchrzempiec on 2021-04-15
Hello, Thank you for the response back. I do have a different password from the Default Password that comcast comes up with. 
I do also have a pfsense router I been learning how to program. I been looking into maybe looking into that making it into a middle man. Not sure if that will help. 
I'm trying to setup one router for my brother so he can have a minecraft server. Also Setup one router for my friend with a backup server that is on ubuntu. 
Comcast said to put the modem in bridge mode then use whatever router i like.


Joseph

---

### Post by TheFu on 2021-04-15
> **josephchrzempiec said:**
> Hello, Thank you for the response back. I do have a different password from the Default Password that comcast comes up with. 
I do also have a pfsense router I been learning how to program. I been looking into maybe looking into that making it into a middle man. Not sure if that will help. 
I'm trying to setup one router for my brother so he can have a minecraft server. Also Setup one router for my friend with a backup server that is on ubuntu. 
Comcast said to put the modem in bridge mode then use whatever router i like.

Comcast doesn't care about your LAN security at all.  They think everything outside their plant is dangerous. They have to think that way.  I worked at an ISP with over 50M customer locations.  We assumed every custom's location was compromised. We patched the router firmware whenever there were updates AND after we'd tested it, but we did that in stages. Most people would block all inbound connections, but some of their other habits were appalling. Lots of people would run a play server at home, on the same LAN as their other stuff, leaving it open to the world and thing that wasn't a springboard into the rest of their network. You know it is.

For what you are providing for your friends, either insist on only using VPN connections where you run the server (openvpn or wireguard) OR provide them with ssh-keys and don't allow any password-based ssh connections.  Regardless, block 99.9999% of the internet from even connecting to the VPN and ssh ports you select - do NOT use the default ports. Do not enable any other inbound connections.

With ssh, you can force only 1 specific command to be allowed for the connections for the login you provide.  That's covered in the ssh book from O'Reily.  That's how github works, BTW.

Mindcraft servers get hacked every day - thousands of them.  Be certain you lock it down so only allow connections from your internal LAN, where the VPN exit node is located.

If you aren't too far into pfsense, may want to switch to opnsense for ... reasons.  You can look those up yourself. I ran pfsense for about a decade before switching to OPNSense about a year ago. No regrets with that choice.  With pfsense or opnsense, you can setup different subnets on each LAN port. Do that. Don't setup any routing between the subnets and do some testing/hacking to see what you can see between them.

I assume you are running these servers as virtual machines of some sort?  If they share the same bridge, then the separation isn't complete.  I'm not even certain that with 2 physical, separate, NICs, each assigned to different VMs using PCI-passthru, that would be sufficient security.  The hostOS would still need a 3rd NIC, BTW.

And .... one more thing.  Don't put the VPN onto the pfsense router.  Routers should run the router software and the edge firewall, nothing else.  It should go without saying - use a real hardware router, do not put your WAN router inside a virtual machine.  Please don't be one of those people that sees a feature and enables it because it is there.

---

### Post by josephchrzempiec on 2021-04-16
Hell TheFu, Thank you for rehsponding back and for the information. Both servers are on there own system no VM at all. Each server has it's own router with it's own Static external ip address. 
As Far as routers go. I'm looking into opensense. I been looking over pfsense a little more. And I think i figure out a way to make all this work. However looking more into opensense and that might solve all my problems. I will return in a few days with a update. I thank you for the help. I'm a little confuse on somethings because I'm not a software person at all. My skills are in hardware. I can do pretty much anything just programming wasn't for me. But I'm trying.


Joseph

---

