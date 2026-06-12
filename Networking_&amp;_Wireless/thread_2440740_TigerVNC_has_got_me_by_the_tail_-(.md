---
title: "TigerVNC has got me by the tail :-("
date: 2020-04-14
forum: Networking &amp; Wireless
---

### Post by ken35 on 2020-04-14
I have been using various flavors of VNC for more than 20 years. I will be the first to admit that I really have no idea what I am doing. Creating a working ~/.vnc/startup script is always an adventure. The one created when a vnc server is first run NEVER works. I look at examples on-line, look at some which have worked for me in the past and eventually cob together something with runs.  That said...

I have been using vnc4server on Ubuntu Mate 18.04 and tigervnc-server on CentOS 7 with good results for a long time.  I just installed Ubuntu Mate 20.04 beta on a test machine.  It offers tigervnc-standalone-server from the repo as its VNC package. I installed it and configured it per a couple of instructions I found on-line.  Of course it did not work so I tweaked the xstartup file and now the vnc server is running. ```
!/vnc/xstartup
#!/bin/sh

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
xrdb $HOME/.Xresources
vncconfig -iconic &
mate-session &
mate-panel &

the server seems to be running

ken@ubuntu:vncserver -depth 24 -geometry 1600x1024

ken@ubuntu:~/Desktop$ vncserver -list
TigerVNC server sessions:
X DISPLAY #    RFB PORT #    PROCESS ID
:1        5901        4474

ken@ubuntu:~/Desktop$ netstat -tlnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:5901          0.0.0.0:*               LISTEN      4474/Xtigervnc      
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -                   
tcp6       0      0 ::1:5901                :::*                    LISTEN      4474/Xtigervnc      
tcp6       0      0 :::22                   :::*                    LISTEN      -                   
tcp6       0      0 ::1:631                 :::*                    LISTEN      -      

```So far, so good. Upon starting the vnc server I receive the message ```
xtigervncviewer -SecurityTypes VncAuth -passwd /home/ken/.vnc/passwd :1
```If I issue that command on the Ubuntu 20.04 machine I can access my Mate desktop FROM THE LOCAL MACHINE. However, I cannot connect to the vnc server from another computer. I have tried vinagre which I use for everything else and also the Tiger vnc viewer. It is not a firewall issue as I have the firewall disabled on the Ubuntu machine at the moment.

It looks like it is listening on port 5901 as X session :1.  I have tried connecting using 10.42.0.227:1 and 10.42.0.227:5901. vinagre tells me "Connection closed" and Tiger viewer tells me "unable connect to socket: Connection refused (111)" Frustrating ! I am probably overlooking something simple at this point. Any suggestons???

TIA,

Ken

---

### Post by Holger_Gehrke on 2020-04-15
Looks to me like it's only listening on the loop back interface (127.x.y.z for ip4 / ::1 for ip6). This is probably meant to be used with a ssh-tunnel to get a secure connection that's protected against man-in-the-middle attacks.

Holger

---

### Post by slickymaster on 2020-04-15
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2020-04-15
> **Holger_Gehrke said:**
> Looks to me like it's only listening on the loop back interface (127.x.y.z for ip4 / ::1 for ip6). This is probably meant to be used with a ssh-tunnel to get a secure connection that's protected against man-in-the-middle attacks.

and really bad, non-encrypted, network connections.

Any interest in a different tool, like x2go which is based on the NX protocol? NX uses ssh tunnels and feels faster than any VNC I've used.
[https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver) There's a client-side. x2go always "just works."  OSX, Windows, Linux clients exist. No iOS or Android, if you need those, however.  I've been using x2go almost daily for access to my main desktop running inside a VM since probably 2012-ish. The client has a nice GUI to tune the compression used which lets you choose the performance desired vs quality of the desktop image. You'll see.  x2go is pretty great.

---

### Post by ken35 on 2020-04-18
Thanks for the replies. I am having issues with my access to this site. I posted a detailed reply, I thought, but it did not seem to be saved.  I will look into x2go and into what is wrong with my account here.

Ken

---

### Post by TheFu on 2020-04-18
> **ken35 said:**
> Thanks for the replies. I am having issues with my access to this site. I posted a detailed reply, I thought, but it did not seem to be saved.  I will look into x2go and into what is wrong with my account here.

Ken

Everyone, including me, loses posts here from time to time.  Almost always, it is a browser cache or network problem on my side.  

In about 10 yrs here, I've only seen the forum server fail perhaps 4 times and 2 of those were major outages the admins needed after account data was stolen by hackers. They re-did the SSO and don't forward to any place anymore.  While I cannot rule out something specific to your account and I'm not an admin here, it is doubtful that's the issue.  Empty the browser cache, use a different browser or run another instance inside a **firejail --private** constrained sandbox.

I've gotten into the habit of copying my posts into the X/buffer before "submit" buttons are pressed on all forum sites.  Then if something bad happens, I can drop that into a text file somewhere, usually in /tmp/t and try again.

---

### Post by ken35 on 2020-04-18
Thank you TheFu !!!  I installed the x2go server on my newly installed Ubuntu Mate 19.10 machine, the client on my CentOS 7 workstation, dorked around in the client for a minute or so and CONNECTED!  That is how it should be.  The two issues I currently have with x11vnc (key number pad does not work in the remote machine, and copy/paste does not work) are not a problem with x2go. 

I do have to figure out a few things with operating the client. I am now connected to a full screen session (on my workstation, not the remote machine). The workstation has a larger monitor and the remote session fills it up and it looks great - proper aspect ratio etc. However, I cannot figure out how to disconnect other than doing a log on the remote machine. With a lower resolution I can click the close X on the upper right of the client window - and later reconnect to where I left off on the remote. There must be some sort of hot key - need to do some reading.

As to the forum - I had to chuckle when I read your comment about copying the message  before posting.  I often, but of course not always, do that as well :) I had to rebuild my profile in Firefox a couple of months ago. I had not yet "trusted" this site in NoScript. I changed that in mid-session and that probably hosed things. I am poking around in my profile to see if I can get notifications working (I assume they are available in these forums). Let me post this and then see what I can do to my profile.

Thanks again,

Ken

---

### Post by TheFu on 2020-04-18
Resolutions inside x2go are controlled using the normal xrandr/lxrandr/arandr settings on the remote system as though it was local.  I prefer lxrandr.
Resolutions from the client machine is controlled by the monitor settings there and connection settings for the x2go client.

Disconnecting x2go can be through a logoff, disconnect (X on the x2go-client), shutdown, reboot. From a different machine, when you attempt to re-connect, it will show current sessions for the userid. Normally, I connect to the existing session and pick up where I left off. All the windows and programs are running where I left off.

---

### Post by kentaylor2525 on 2020-04-20
Hello TheFu,

Sorry for the delay in posting a followup. My original UbuntuOne account is totally hosed since I updated my email address. I am still waiting fora followup on my request for assistance. I went ahead and created a new account and will deal with any fallout later.

I am getting a handle on x2go. I can manage the resolution from the client without resorting to any "technical" tweaking. So far I am impressed except for one thing. The x2go client interface is a ghastly wast of monitor real-estate. 

When I used the vinagre viewer on CentOS 6 I was presented with a list of bookmarked remote machines in a vertical list on the left side of the monitor. This took up about 5% of the screen width. Clicking on a listed bookmark would connect to that machine or switch to that machine if already connected. Clean and efficient.

vinagre on CentOS  has a drop down menu to select the bookmark and active connections are presented in a tabbed manner. Not bad but I hate cascading menus for things I access frequently. The gnome2/Mate panel is the best interface I have ever seen.

As to x2go... The "bookmark" for a session is as big as a fist. I can create a desktop launcher for a given remote machine - this is good as I can mover the launcher to the Mate panel. However, after launching, using and closing a remote session I am again back to the x2go client.  

Do you know of a way to make the client automatically close upon closing the remote connection? 

Thanks again,

Ken

p.s. I installed tightvncserver on an Ubuntu Mate 20.04 beta test machine. I can connect to it with vinagre right out of the box. NOTHING to tweak. Install server, set password and go.  I can use my same script to start the server with the desired resolution and color depth. I have never had VNC actually work without tweaking.

---

### Post by TheFu on 2020-04-20
> **kentaylor2525 said:**
> The x2go client interface is a ghastly wast of monitor real-estate. 

"ghastly" pretty much covers the entire x2go-client interface.  I spend 2 seconds in it every 2-3 weeks. The rest of the time, I'm connected to a remote desktop, fully screen, and completely forget it is a remote desktop almost always.

When traveling, I tend to use x2go only for email and spreadsheets. Everything else is probably over an ssh tunnel or VPN (for non-Linux-laptop clients).

> **kentaylor2525 said:**
> 
As to x2go... The "bookmark" for a session is as big as a fist. I can create a desktop launcher for a given remote machine - this is good as I can mover the launcher to the Mate panel. However, after launching, using and closing a remote session I am again back to the x2go client.  

I don't disconnect and reconnect much and use ssh-keys for authentication.  I'm not much of a GUI user really. My main purpose for x2go is to get access to the correct network and launch 15 terminals to manage servers and systems.  Not much point-n-click.

> **kentaylor2525 said:**
> 
Do you know of a way to make the client automatically close upon closing the remote connection? 

Nope. You could automate it using xdotool, if you like.  Every few minutes, look for the running x2go remote window. IF it doesn't exist, let xdotool send the "close" event to the x2go-client window.
> **kentaylor2525 said:**
> 
p.s. I installed tightvncserver on an Ubuntu Mate 20.04 beta test machine. I can connect to it with vinagre right out of the box. NOTHING to tweak. Install server, set password and go.  I can use my same script to start the server with the desired resolution and color depth. I have never had VNC actually work without tweaking.
Did you solve the terrible security of all the VNC solutions?  VPN?  ssh-tunnel?  Those passwords are a joke.

---

### Post by kentaylor2525 on 2020-04-20
I use vnc ONLY on my home LAN, not accessible via the Internet so the password and other (lack of) security does not concern me too much. At least now I have some various options from a convenience standpoint.  I may look into tunneling over ssh. I tried that this morning - set up a tunnel to the tigervnc-standalone-server machine but I could not get the tigervnc client to connect. 

Time to take a break from vnc and see if I can compile gnome-commander for Ubuntu 20.04.

Ken

---

### Post by TheFu on 2020-04-20
Inside your home only?  Why not just use remote X11?  No need for all the image transfers. Use X/Windows!

---

### Post by kentaylor2525 on 2020-04-21
Thank you again TheFu. Remote X11 looks interesting.  I remember MANY years ago we had a product at work called Hummingbird (or perhaps that was the vendor's name) which we used for mainframe 3270 remote access. It could also be configured for access to HPUX servers. It did something like this if I recall correctly. Too many options :P

If I may ask a conceptual question about x2go... I have found a lot of easy to follow setup pages from various universities. I guess it is popular for the education world. However, none of them seem to answer the question and my testing seems to point to an answer which I do not like...

Do I really have to invoke the x2go client each time I wish to connect an additional session?  I created a second user account on my test machine. I created an x2go session for user "bob", launched it in the x2go client just fine.  I see my session listed in the client but I cannot launch it. If I call up a second instance of the x2go client I CAN launch my session.

I need to redecorate my home office. Perhaps I will purchase 6 more monitors and nail the to the walls. One for each of my 3 data servers, one for my gateway, firewall, dhcp, vpn sharing box, one for my BitTorrent box and one for my Usenet leaching box.  Then I can get 6 wireless keyboards and mice and some spray paint and color code each :biggrin:

Ken

---

### Post by TheFu on 2020-04-21
> **kentaylor2525 said:**
> Thank you again TheFu. Remote X11 looks interesting.  I remember MANY years ago we had a product at work called Hummingbird (or perhaps that was the vendor's name) which we used for mainframe 3270 remote access. It could also be configured for access to HPUX servers. It did something like this if I recall correctly. Too many options :P

Hummingbird X/Server was for Windows. These days, you aren't still using Windows, are you?  Use X11 between workstations on LANs or even fast WAN connections. No need for x2go, VNC at all. None.
```
ssh -X userid@server command
```
20 yrs and you haven't been using that all this time?  I would cry, were I you.  The lack of good X/Servers is what moved me to use a Linux VM back in 1998.

The only reason I have to use a remote desktop is for over-internet stuff or from Windows. If I'm on the same LAN, I use the X/Windows client/server architecture. 1000x better than any remote desktop, easily.

> **kentaylor2525 said:**
> If I may ask a conceptual question about x2go... I have found a lot of easy to follow setup pages from various universities. I guess it is popular for the education world. However, none of them seem to answer the question and my testing seems to point to an answer which I do not like...
I only run 1 x2go session to get into a Linux system with a desktop. From there, I use remote X11 to anything else on the same LAN.  That's kinda the point.

> **kentaylor2525 said:**
> Do I really have to invoke the x2go client each time I wish to connect an additional session?  I created a second user account on my test machine. I created an x2go session for user "bob", launched it in the x2go client just fine.  I see my session listed in the client but I cannot launch it. If I call up a second instance of the x2go client I CAN launch my session.

Why does this matter? Perhaps looking at how you work would lead to efficiencies?  If there isn't some funky network firewalls happening between the remote systems, I'd trust those servers more than I'd trust any desktop OS.

> **kentaylor2525 said:**
> I need to redecorate my home office. Perhaps I will purchase 6 more monitors and nail the to the walls. One for each of my 3 data servers, one for my gateway, firewall, dhcp, vpn sharing box, one for my BitTorrent box and one for my Usenet leaching box.  Then I can get 6 wireless keyboards and mice and some spray paint and color code each :biggrin:

Ken

Or just use a dual 24inch monitor setup with a KVM switch?  KVM switches used to be costly in in the 1990s, but now they are really, really, cheap.  I'm still using one from 2002 - a Belkin Omni-Cube 4port KVM.  [https://blog.jdpfu.com/2012/01/03/home-nerd-station-setup-for-servers-and-network-devices](https://blog.jdpfu.com/2012/01/03/home-nerd-station-setup-for-servers-and-network-devices) has a picture of my "data center" from about 10 yrs ago. It basically looks the same since I reuse parts almost always, but the compute power is probably 3x what it was back then and I've added another disk array.  All the disks in the other systems have probably been swapped from 320G to 2TB or larger.  A $70 wheeled bread rack from Costco does wonders for access to the back of the systems.
Basically, there are 3 wires into the rack - 2 that power UPSes and 1 for the internet coax.  There are a few ethernet cables OUT, going to the wiring closet switch for the rest of the house and wifi AP (mounted centrally). The wifi-AP sits on the "guest" network, outside any of my systems. Wifi systems have to use a VPN to access LAN systems. I've considered wifi as "internet traffic" since designing a huge deployment in 2005-2007 for a client with over a thousand locations. Never trust wifi and definitely never trust bluetooth. EVER.

Around 2008, I jumped into virtualization BIG TIME at home. In 2005, at work, deploying on VMs was the default for all applications unless there was a failure to work or it was obvious that it wouldn't work.  Some vendors wouldn't certify the config, so we'd just sit on the contract for a quarter until they did. The company was huge, spending more than many countries spend, so we had plenty of market power, usually. I can think of only about 5 companies who refused out of thousands. Apple, Microsoft, Oracle.  HP and IBM were all on with running stuff in VMs. SAP was too.  Nobody can get MSFT to do anything, that has always been the rule. Anyway, I'd been using VMs a little since around 1998, but from 2008 on, most of my "systems" have been virtual.  At one point, I had 30 VM systems supporting 3 clients.  I've scaled that back and I'm down to 10 systems now that I'm semi-retired, though I've been bringing up a few LXD containers recently that do internal DNS + ad blocking and an email gateway.  The gateway isn't in production now, but running as a backup MX server.
My main desktop runs inside a VM and can be accessed from almost anywhere in the connected world with either ssh or x2go.  ;)

Anyway - use VMs rather than physical machines. If you have more raspberry pis than you have TVs, why?  I do insist that my WAN router is a separate HW box, but for internal routing between subnets, I have virtual machines doing the routing and firewalls.

Did I miss anything? ;)

---

### Post by kentaylor2525 on 2020-04-21
I did the KVM thing many years ago. I am currently running virtual machines as well. I guess I could get one BIG computer and run most everything as VMs. However, that takes a lot of (electrical) power. My data servers are only powered up when I need to access files on them or to archive files.  The machines which run  all the time - the gateway and the BitTorrent client - are low power machines. They were Pi 3B+ units but as I do not see much future for them - 1GB of RAM will NOT run a 64 bit OS etc. I replaced them with low end Intel NUCs just last week. 

Let me get some pictures of my data center and I will PM you with links.  I have to get my vehicles safety inspected this afternoon etc. but I will get you some pics soon.

Ken

---

### Post by TheFu on 2020-04-21
> **kentaylor2525 said:**
> I did the KVM thing many years ago. I am currently running virtual machines as well. I guess I could get one BIG computer and run most everything as VMs. However, that takes a lot of (electrical) power. My data servers are only powered up when I need to access files on them or to archive files.  The machines which run  all the time - the gateway and the BitTorrent client - are low power machines. They were Pi 3B+ units but as I do not see much future for them - 1GB of RAM will NOT run a 64 bit OS etc. I replaced them with low end Intel NUCs just last week. 

Let me get some pictures of my data center and I will PM you with links.  I have to get my vehicles safety inspected this afternoon etc. but I will get you some pics soon.

Ken

A 65W Ryzen can easily handle 20 VMs. A Ryzen 1600 AF goes for $80.

Built an ITX system for about 50% cost of a NUC, though about 2x the size, but that is still fairly small.  This week, I've seen Core i5/8G+120G SSD mini-Desktops come off-lease for $130-$150 on eBay.

A number of my friends have multiple Dell R710 and larger systems in their basements. They never want to talk about the house power bill.  Staring at mine that just arrived - $61.03 for March. That's for a 2900 sqft home where we work from home full-time the last 12+ yrs.  If I were living in an RV/camper, then I'd worry more about size and getting power down below 20W peak for each.

---

### Post by ken35 on 2020-04-21
It seems I cannot send you a PM so let me share some pics of my home data center here.  They are stored on my Mega account and can be accessed by the links provided.  I had a free account on the riginal Megaupload although I never stored anything important there. I signed up for a free account on the new(er) Mega although I do not store anything important there - but is 50 GB free space! I am afraid Mega will make you download the pictures. I do not seem to be able to embed them in the thread.

I need a wide angle lens but here is most of it [https://mega.nz/file/A19jBZRA#QvMJrKPnpos1honpvUKkwZCQF1PvEVjcuHe9lfcZbD4](https://mega.nz/file/A19jBZRA#QvMJrKPnpos1honpvUKkwZCQF1PvEVjcuHe9lfcZbD4) From left to right top level

My ancient Brother MFC240c color inkjet printer, scanner, fax and copier.
Two 24" Dell UltraSharp monitors
Dell Precision T3620 workstation, i7-860, 32 GB RAM, 2 M.2 PCIE drives, 3 spinning rust drives, CentOS 7, VNWare Player and a bunch of VMs. One CentOS 7 VM always resides on the visible workspace on the right monitor.
My network "stack" and a test PC - Dell Inspiron 3050 Micro

Lower level - on a shelf with casters so I can roll it out for service
My old Dell Studio XPS 8000 PC - not connected - used for testing on occasion
Dell T20, T130 and T30 servers wired together via the hub on top of the T30 and connected via the umbilical seen behind the Studio PC. 64 TB of storage on 12 drives. Configured as 32 TB mirrored.

Here is a detail of the network stack [https://mega.nz/file/o9lRXJgD#7F2J97LmWzL7O5l4C4xxjIsexdHy_1SXuDv_54tudHk](https://mega.nz/file/o9lRXJgD#7F2J97LmWzL7O5l4C4xxjIsexdHy_1SXuDv_54tudHk)

DSL modem with fan on top left, hub to feed "dirty" connection from ISP (yellow patch cords) to 

Bottom NUC - gateway, firewall VPN sharing box - green patch cord feeds VPNed signal to the two 8 port hubs for LAN
Top Nuc - my BitTorrent client - makes connection to peer to peer enabled ProtonVPN server
Dell 3050 on top of stack - my Usenet leecher. It uses a VPN from my Usenet provider.
The empty shelf above the hubs used to contain 2 Raspberry Pi3B+ boxes which performed the rolls of the NUNs

This is a Pi3B+ on my test desk [https://mega.nz/file/IoMklIAZ#HA_1E0SB6kUN6p_2Up5LVgQnw9Iqo8Ke51YENRoerCI](https://mega.nz/file/IoMklIAZ#HA_1E0SB6kUN6p_2Up5LVgQnw9Iqo8Ke51YENRoerCI)  Laser printer to the left.

Here is a shot of my gateway etc. running on a Pi Zero. It had potential but as I had to run Raspbian it was rather flaky. It seemed to rename the network connections at random. Hard to manage a firewall etc.  when the names keep changing.  [https://mega.nz/file/gw9gVYKQ#AFIV21kLTxUGPjDSrfyxEKf5OO9BNyhmYN_pQkz_CzI](https://mega.nz/file/gw9gVYKQ#AFIV21kLTxUGPjDSrfyxEKf5OO9BNyhmYN_pQkz_CzI)

Finally, here is my original gateway/firewall. I did not have the color code for patch cords decided at that time
[https://mega.nz/file/84UBXKpJ#bjWeCOQbBTiNtJ45vQxrvu9AV9se6nSBkIgYa6bn49g](https://mega.nz/file/84UBXKpJ#bjWeCOQbBTiNtJ45vQxrvu9AV9se6nSBkIgYa6bn49g)

And to think I do this for a hobby. Actually the hobby turned into a real job in 1987 during a corporate reorganization.  My actual background is nuclear plant chemistry and radiation protection. I played at IT for 18 years before taking a premature early retirement in 2005. Back to hobby IT :P

Ken

---

