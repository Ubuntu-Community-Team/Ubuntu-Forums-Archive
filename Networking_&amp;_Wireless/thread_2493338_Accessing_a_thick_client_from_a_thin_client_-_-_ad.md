---
title: "Accessing a thick client from a thin client - - advice needed for a clamshell purchas"
date: 2023-12-11
forum: Networking &amp; Wireless
---

### Post by Drone4four on 2023-12-11
I was thinking of purchasing a thin client clamshell laptop with the intention of logging in remotely to use my thick client when I am not at home.

I have a number of questions. But I think it might be a good idea to share my current hardware specs and provide a background on my use case first.

Here I go - -

I have a Desktop PC (tower) with Ubuntu installed natively. It’s an Intel i5-13600K CPU with 64 GB of RAM and AMD RX 6600 XT 8GB GPU with 6+ terabytes NVMe, SSD, and HD storage in total spread across my root fs, home directory, and back up data directories. It’s a terrific workhorse.

In terms of my use case for this hardware configuration, I am in a seemingly perpetual state of research, writing works of non-fiction and social science in Google Docs in Chrome (dozens of tabs) and searching and reading similar topics also in Chrome (hundreds tabs). So on the one hand while I do academic and literary research, I am additionally learning data science and algorithmic software design. For this I use VS Code and seem to accrue hundreds of Chrome tabs to support these endeavors as well. I furthermore interact with my peers on various communities on Discord and Slack. Having said all of that, with all of these Java heavy and electron/chromium based apps I rely on, this is how I justify the need for 64 GBs of RAM. My system monitors tell me that I usually hover around the 40%-60% range on a busy day.

Now for my line of questioning:
[LIST=1]
[*]How realistic is it to remote into a thick client from a $400-500 thin client? Comments? What kind of user experience could I expect to run Gnome or Plasma on my home PC but through a secured ssh internet connection from a clamshell?
[*]I’ve used ssh to login from my Desktop PC into virtual private servers in the cloud in the past. But in that case I had a static IP and was able to set up a DNS so that is why ssh worked so easily. I gather that my ISP is forever leasing and re-assigning unique IP addresses on rotation, so it is never static. This makes it difficult to set up a consistent ssh connection. I’d have to reconfigure it manually every 2 weeks or whenever my ISP arbitrarily decides to change my IP address. What might the solution be to this issue?
[*]If I am able to establish a decent regular consistent ssh connection successfully, is it as easy as running `startx` from my shell to launch an X / Wayland wm session?
[*]What alternatives might there be to ssh to remote in?
[/LIST]
Some more rationale: Laptops with 64 GBs of RAM or even 32 GBs of RAM are prohibitively expensive. To me it doesn’t make sense to lug around a heavy ultra expensive laptop in a public place like the library where a thief and opportunist could take advantage of the situation and swipe it with all my data on it. While I could encrypt the storage, I’d rather be out $400 than $2,500+.

I don’t travel around the world so latency is not an issue.
&#8203;

---

### Post by TheFu on 2023-12-12
>     My rig:
    IBM Personal System/2 Model 30-286 - - Intel 80286 (16 bit) 10 Mhz - - 1MB DRAM - - Integrated VGA Display adapter
    1.44MB capacity Floppy Disk - - PS/2 keyboard (no mouse)

I don't think any supported version of Ubuntu will run on this hardware.  So sorry.  Even Debian needs at least an i686 to work.

---

### Post by TheFu on 2023-12-12
> **Drone4four said:**
> <snip background> ....
Now for my line of questioning:
[LIST=1]
[*]How realistic is it to remote into a thick client from a $400-500 thin client? Comments? What kind of user experience could I expect to run Gnome or Plasma on my home PC but through a secured ssh internet connection from a clamshell?
[*]I&#8217;ve used ssh to login from my Desktop PC into virtual private servers in the cloud in the past. But in that case I had a static IP and was able to set up a DNS so that is why ssh worked so easily. I gather that my ISP is forever leasing and re-assigning unique IP addresses on rotation, so it is never static. This makes it difficult to set up a consistent ssh connection. I&#8217;d have to reconfigure it manually every 2 weeks or whenever my ISP arbitrarily decides to change my IP address. What might the solution be to this issue?
[*]If I am able to establish a decent regular consistent ssh connection successfully, is it as easy as running `startx` from my shell to launch an X / Wayland wm session?
[*]What alternatives might there be to ssh to remote in?
[/LIST]
Some more rationale: Laptops with 64 GBs of RAM or even 32 GBs of RAM are prohibitively expensive. To me it doesn&#8217;t make sense to lug around a heavy ultra expensive laptop in a public place like the library where a thief and opportunist could take advantage of the situation and swipe it with all my data on it. While I could encrypt the storage, I&#8217;d rather be out $400 than $2,500+.

I don&#8217;t travel around the world so latency is not an issue.
&#8203;

Assuming remote access means from outside the LAN, on the public internet, then ....

a) you cannot use Gnome or KDE Plasma.  You must use a light DE, perhaps XFCE, LXQt or Mate, assuming you even want any DE at all. A good WM, Window Manager, is sufficient, actually.  Gnome and KDE demand access directly to a GPU, and if you are remote, there isn't a GPU.  People fight this and fail every day.  Don't bother. Use a lighter DE and move on.

b) ssh is how Unix systems communicate securely.  Leverage this.  The good news is that the NX remote desktop protocol uses ssh for encrypted tunnels and authentication. Further, we know how to secure ssh, so all that standard ssh security for internet connections still applies.  Also, NX is based on a much more efficient VNC with tunable compression based on the upstream bandwidth.  There are a number of NX client/servers, however, they all have proprietary, non-standard, extensions, so they do not interoperate.  The good news is that x2go is F/LOSS and works well.  It is stable and fast, if tuned correctly.  I've used x2go from 5 continents with widely ranging connection bandwidth.  The worst was a 128Kbps connection from Patagonia.  The bandwidth wasn't THAT bad for reading and replying to email, but there were many dropped connections since everyone in the hotel was sharing the satellite internet link.  If you are somewhere with more stable and higher bandwidth, the tuning is easier. A 1Mbps connection from Nepal worked great.

c) Wayland isn't supported.  Use Xorg.

d) While using ssh -X to use a pure X/Windows client/server connection **can** be done, for over the internet, you really want the added performance that NX with compression provides.  It blows away RDP and VNC and normal remote X/Windows for usability+performance.  Don't expect to edit graphics files over x2go.  That image compression for each frame means limiting colors to 4K or less, which is fine for most work.  Also, don't expect to watch videos and be happy, thought they will play, if the video resolution is low enough.  Probably much better off using sshfs or a VPN like wireguard.

e) No static IP?  Well, you need to know the IP for your home.  There are dynamic DNS services (some are free for use) that can be automatically updated using ddclient or your router might have a setting to do it for specific services. You'd get a sub-domain off someone else's  .... so in 1998, I use DynDNS.org and they were giving 1 free dynamic DNS entry to anyone.  Think I used something like regulus.dyndns.org ... and setup a dd-client with my dyndns account login to update the current public IP whenever it changed.  I've had static IPs for a long time, so I don't know how people do it today.  For my needs, I actually run a $4/month VPS as a reverse proxy with a wireguard VPN between my VPS and the gateway system inside my public LAN DMZ at home.  This is a little nerdy for most people.  There are how-to guides for this.  

f) If you do need a full VPN, you could setup a mesh network using Nebula that would bridge your travel Linux computer with your home network.  I was unable to get Nebula working - turns out that my WAN router and firewall are too close to an enterprise solution and don't work with the way the Nebula tricks most other consumer firewalls into working.  There are other methods like running your own Wireguard peer-to-peer VPN, which can accomplish the same thing, but if you don't want to trust a middle man service like TailScale, then you'll need to setup a wireguard node on a VPS with the monthly charges for that.  Wireguard is very light and fast.

e) The remote laptop you take with you can be a used $75 Chromebook, provided it has a standard Linux and can run the x2go-client software. 2GB of RAM and a Celeron CPU from 2012 is fine.  I don't think/know if there is an NX or x2go client for chromeOS. I doubt it.  There are excellent clients for Linux, MacOS, and MS-Windows. I think they all need to be x86-64, so don't get an ARM-based system.

So, the next thing is to try it out.  x2go connects to a virtual desktop, not the one displayed. That means is isn't like RDP or VNC.  The remote system should be on, but you can be logged in or not when making remote access, unlike those other tools.  Also, the network security for both RDP and VNC are terrible, so using those requires either an ssh tunnel or full VPN anyway.  NX handles that for you with better compression, so better performance.  Get it working and if performance isn't snappy, come back and ask tuning questions.

---

