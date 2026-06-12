---
title: "cannot access SYSTEM CONFIGURATION---&gt;NETWORKING to change DNS please help"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Windoze Refugee on 2010-02-25
Ive installed Ubuntu 9.10
Ive connected my adsl router/modem (D-link DSL 504T ADSL Router)
And all is fine and dandy EXCEPT I need to alter the DNS settings and CANNOT get to them ....Arrgggghhhhhhhh!!!!

It wont let me log on as root and apparently this is the only means by which I can bring up
COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (as, so I hear, I will need to be superuser (root))

Ive tried using Sudo command to emulate root, but this only brings up a command line and doesnt let me navigate to NETWORKING where, legend has it, the hallowed DNS settings tab lives.

Please plase, for the love of god before I tear out my last few remaining hairs, somebody help!!

thank you

---

### Post by ScottinSoCal on 2010-02-25
> **Windoze Refugee said:**
> It wont let me log on as root and apparently this is the only means by which I can bring up
COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (as, so I hear, I will need to be superuser (root))

root is disabled by default (and it's safer that way). I'm not a *nix guru, but I'm using it on both my home and work computers, and I'm completely lost on the command path you're showing above. The only Computer I have listed in my 9.10 is in places, and it doesn't have an option for System Configuration. When I want to change networking, I right click on the networking icon on the right side of the upper panel, near the Logoff/Shut Down button. That gives me the option to Edit Connections. I change what I want, enter my password when prompted, and the changes are saved. Are you using Gnome, or KDE as a desktop? I've got Gnome - tried KDE, didn't care for it much, and went back to Gnome.

---

### Post by Windoze Refugee on 2010-02-25
Hi Scottish SoCal
Thanks for your reply
I have spent hours and hours and hours trying to find a way to replicate the (apparently sucessful) advice of Python here
[http://ubuntuforums.org/showthread.php?t=11544&highlight=python+d-link](http://ubuntuforums.org/showthread.php?t=11544&highlight=python+d-link)

 to make the bloody thing work!

I may just go and cry for a while

---

### Post by ScottinSoCal on 2010-02-25
> **Windoze Refugee said:**
> Hi Scottish SoCal
Thanks for your reply
I have spent hours and hours and hours trying to find a way to replicate the (apparently sucessful) advice of Python here
[http://ubuntuforums.org/showthread.php?t=11544&highlight=python+d-link](http://ubuntuforums.org/showthread.php?t=11544&highlight=python+d-link)


OK, that thread is from 2005, which in computer years means it was sometime just before they discovered fire. All the command paths are different these days. So, let's ignore what that thread says and just start with the basic issue.

You want to change your DNS setting - why? And how familiar are you with basic networking? I'm not being snide, I want to know how much (or how little) explanation to give. Do you know what DHCP is? What router are you using (brand/model)? Is it your router, or does it belong to your internet provider? Is this for a wired connection? Or is it for wireless?

---

### Post by xpod on 2010-02-25
> **Windoze Refugee said:**
> Ive installed Ubuntu 9.10
Ive connected my adsl router/modem (D-link DSL 504T ADSL Router)
And all is fine and dandy EXCEPT I need to alter the DNS settings and CANNOT get to them ....Arrgggghhhhhhhh!!!!

It wont let me log on as root and apparently this is the only means by which I can bring up
COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (as, so I hear, I will need to be superuser (root))

Ive tried using Sudo command to emulate root, but this only brings up a command line and doesnt let me navigate to NETWORKING where, legend has it, the hallowed DNS settings tab lives.

Please plase, for the love of god before I tear out my last few remaining hairs, somebody help!!

thank you

If you cant find the Network Utility in your System>Preferences menu you should still be able to run it as admin by opening either the Terminal or ALT-F2 and running the following command...
```
gksudo network-admin
```

You will be asked for your password regardless of which method you use.

You can also add your DNS entries manually by using the terminal or ALT-F2 again to open the resolv.conf file as admin.
```
gksudo gedit /etc/resolv.conf
```

Enter your password if still asked to then put your required DNS  into the opened file something like this....

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

### Post by ScottinSoCal on 2010-02-25
Before you do any of that above, can you tell me if you're trying to get a PPPoE connection to work? If so, the problem may not lie in your DNS settings.

---

### Post by Windoze Refugee on 2010-02-25
Hi folks
and thanks for your input

LOL - yes dragging around my cave here <S>

The modem is a D Link DSL 504T ADSL Router

Im trying to change the dns servers as the current ones are 192.168.blah.blah (default I guess) and my ISP (Onetel) uses 212.67.96.129 and 212.67.96.130

I have no idea which ppoe or ADHD im trying to configure, I just want to get online with my ubuntu as then all will be right with the world.

you are wonderful people

---

### Post by Windoze Refugee on 2010-02-25
OK
Still no luck, but I have some more info

when trying to configure this thing the options I have are these:

edit connection

TAB    wired MAC address 

TAB 802.1x security

TAB IPv4 settings

Method 
Automatic (DHCP)                                 requires DHCP client ID

Automatic (DHCP) adresses only            requires DNS servers
                                                           Search domains
                                                           DHCP client ID

Manual                                                requires address netmask gateway
                                                          DNS servers
                                                          Search domains
                                                          (and routes ?)

TAB IPv6 settings

Ignore

Automatic (and routes?)

Automatic, addresses only                    requires DNS servers
                                                          Search domains
                                                          (and routes?)

Manual                                              requires address prefix
                                                        DNS servers
                                                        Search domains
                                                        (and routes ?)



Active Network Connections

interface:            ethernet
Hardware address        00:0C:6E:45:AF:DD (dunno why theres a smiley here)
DRIVER                skge
Speed                100mbps
Security            none    

IP address            10.42.43.1
Broadcast address        10.42.43.255
Subnet Mask            255.255.255.0        


I have no clue which permutation of these options will get it to talk to the net or log me on.

Any help very very gratefully received

---

### Post by ScottinSoCal on 2010-02-25
> **Windoze Refugee said:**
> 
```

interface:            ethernet
Hardware address        00:0C:6E:45:AF:DD
DRIVER                skge
Speed                100mbps
Security            none    

IP address            10.42.43.1
Broadcast address        10.42.43.255
Subnet Mask            255.255.255.0        

```


OK, from this it looks like you're connected via a networking cable, not through wireless. Is that correct?

If so, right click on your network icon, up on the panel, and select Edit Connections. You should default into the Wired tab, if not, go there. Click on the connection listed, and it'll open a new window. On the new window, go to the IPv4 tab. There's a pull-down box there labeled Method: Click on that, and choose "Automatic (DHCP) addresses only". When you do that, the box for DNS servers and search domains will be editable. Enter the primary DNS into the first, and the domain (like "comcast.net") of your ISP into the second. If the DNS is your problem, you should be good to go.

---

### Post by Windoze Refugee on 2010-02-26
Hi Scott
Thats great thank you
Yes wired not wireless - sorry, should've mentioned that
I give this a try and let you know how I get on
Cheers
Jonathan

---

### Post by Windoze Refugee on 2010-02-28
I have in fact had some success in that ubuntu recognises the connection (assiging it its own IP address 192.168.1.3 (I think))
I've tried configuring it both manually and using "Automatic (DHCP) addresses only" and entering my DNS servers manually (Im with Onetel and their DNS Servers are 
212.67.96.129 & 212.67.96.130 apparently.

But no mater what permutation I use I cant seem to get them to connect or even in fact be able to ping this aaddress or indeed any other. Im guessing it has somehting to do with a gateway (?) and Ive never been prompted for a username or password - is this usual?

Im used to having a broadband modem which 'dials' in using username and password. Is the ethenet connection that radically different in the way it negotiates with the server?
 
what is DHCP btw? And how can I turn it on or off in the router?

Still lost, getting a bit nearer (I think) but no less determined
 
cheers

---

### Post by Windoze Refugee on 2010-02-28
I've got a little further:
 
by querying the setup in XP I discovered that the DNS servers Im accessing (through windoze anyway) wwere not the same as those listed.
Ive made the changes and the connection now looks like this:
 
ip address 192.168.1.3
 
broadcast address 192.168.1.255
 
subnet mask 255.255.255.0
 
default route 192.168.1.1
 
primary DNS 62.24.139.139
 
secondary DNS 62.24.139.7
 
 
 
for "editing Auto eth0"
on the IPv4 settings tab:
 
automatic (DHCP) adresses only
 
DNS servers 62.24.139.139
 
Search domains [should there be anything here?]
 
DHCP client ID {what, if anything, should be here?]
 
 
for the ROUTES (separate button) i've not entered anything.
 
What do you think?
 
Cheers
 
WR

---

### Post by 3rdalbum on 2010-02-28
Looks good to me (don't worry about those empty fields).

If you're ever unsure about your DNS you can always use OpenDNS; just put 208.67.222.222
into your DNS field.

Your ISP's own DNS is quicker, but if it has problems you can switch.

---

### Post by mechro on 2010-02-28
I'm probably missing something here but I set my DNS servers directly in my modem/router. For my netgear router I open a browser and go to [http://192.168.0.1](http://192.168.0.1), enter a username and password for the router (nothing to do with Ubuntu username and password) and set and tweak as required.

Your Dlink should have a similar system though not necessarily the same URL. Have you got a manual?

---

### Post by Windoze Refugee on 2010-03-03
> **mechro said:**
> I'm probably missing something here but I set my DNS servers directly in my modem/router. For my netgear router I open a browser and go to [http://192.168.0.1](http://192.168.0.1), enter a username and password for the router (nothing to do with Ubuntu username and password) and set and tweak as required.

Your Dlink should have a similar system though not necessarily the same URL. Have you got a manual?

Mechro you are a genius!! Thank you so much.
Bit of a dope me, I had completely overlooked that the router itself had to be configured as well.
Thank you so much
Solved, connected and Ubuntuing like a good un.
Cheers to you and everyone else who chipped in
WR

---

### Post by Iowan on 2010-03-03
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by isee on 2010-03-11
If I may ask here, I am looking for a similar answer but without using my DLink router.  If I unplug my DLink and plug directly in to my ISP's cable-modem DSL (my TV comes in through that box also), I cannot get an internet connection.  I can connect through my DLink as it automatically logs onto my ISP.

In XP I can use a Wizard which guides a process to "Connect to the Internet...using a broadband connetion that requires a username and password."

When I am connected to my DLink in XP I am on the Local Area Connection.  If I unplug the DLink and plug into my cable-modem, the Local Area Connetion gives a warning "little or no connectivitey" and I have to use the New Network Connection wizard to create a new connection, a PPPoE.

The username to log onto my ISP is [EMAIL="username@res1.mts.net"]username@res1.mts.net[/EMAIL].  How can I get Linux to find my cablebox and provide me with fields to enter my username and password?

Thanks!

---

