---
title: "How to get ubuntu online via second pc and winmobile?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by piergen on 2011-01-12
I am currently without dsl line at home. 
How can I share internet connections from windows xp laptop onto my xubuntu box?
They  are both on my home network.  But as I have no dsl line at the moment I  need to get the ubuntu box online to update ang get some depandancies  for samba to work correct. The switch act as DHCP and delivers IP addresses to all computers on network also the win xp when I have that one connected. When I click on properties for local area connection for the windows mobile I know I can share internet connection if I mark that in the advanced tab. Thing is when I try to share internet connection I get this error:

> 
A LAN connection is already configured
with the IP address that is required for automatic IP addressing[Googling that error message ]("http://www.google.com/search?client=firefox-a&rls=org.mozilla%3Anb-NO%3Aofficial&channel=s&hl=en&source=hp&q=A+LAN+connection+is+already+configured+with+the+IP+address+that+is+required+for+automatic+IP+addressing&btnG=Google+Search")I learn this:

>  **Explanation:** 
Internet connection sharing configures the LAN connection of the home network or small office network with a static address. There is another network adapter in the system that is configured with the same address.
**User Action:** 
Change the static address of the network adapter before enabling Internet connection sharing.I also see this:


> To use ICS, change the wired network to a different address range,
such as 192.168.1.x.

That mask simply means that IP
addresses that are the same in the first three numbers are in the same
subnet. For example:

192.168.0.1 and 192.168.0.10 are in the same subnet
192.168.0.1 and 192.168.1.1 are in different subnets And how can I assign different subnet at all when all IP's are given from the netgear switch?
Do I need crossed cables and direct pc to pc connection to fix this? (course I do not have crossed cables at all at home) Or is there maybe a smart trick that might help? 



Can  I curcumvent this issue in any ways if I also use a router and place  the router somewhere? Maybe if the router is connected to switch, then  ubuntu is connected to switch and windows laptop connectes directly to  router. Will this work?


I  am thinking router will give ip in one subnet to laptop and switch in  different subnet to switch? But will all gates be closed by firewall in  the router???

[U][B]
Possible to use windows mobile cell phone directly on the ubuntu and get ubuntu to connect via windows mobile?




[/B][/U]

---

### Post by d3ngar on 2011-01-12
Erm, to be honest I didn't read all of it carefully, but I think where you went wrong is here: When you share the computer's internet connection you effectively turn it into a DHCP server.

Where does the winXP machine get the internet from? Is there a USB modem or something?

Do this:

Plug out the switch from the laptop > connect to the net > share the internet as before > connect the laptop to the **uplink** socket of your switch > connect the other xubuntu 'box'. 
This should in theory work...

Otherwise a crosslink cable should do the work.

---

### Post by piergen on 2011-01-12
Hmm still not working here. Guess there is no way around it. Got to shell out money for crossed cable.

---

### Post by d3ngar on 2011-01-14
what kind of switch is it? Do you have any control over it's settings, is there a web interface that tells you what the settings are?

The switch needs to get it's IP address from your windows machine...

---

### Post by piergen on 2011-01-14
The switch is netgear gs 605. A simple not managed switch. So it is not possible to turn off DHCP.

I come acreoss another thread that might help me: [get your ubuntu online via windows mobile 6 device connected via usb cable.]("http://ubuntuforums.org/showthread.php?t=869229")

But as always lately I run into dependencies hell. If I find a way to get subversion (svn) installed on the ubuntu box I will be online. Do you know if there is a terminal command to use to check if I allready have svn, and if so what version?

Or if womeone have great tips to how I can get subversion installed manually without internet conection for the ubuntu? 

I am aware of the [http://packages.ubuntu.com/hardy/subversion](http://packages.ubuntu.com/hardy/subversion) but as there is so many dependencies manual install is near impossible.

Any smart tricks to resolve this would be highly appriciated.

---

### Post by piergen on 2011-01-14
duplicate post

---

### Post by piergen on 2011-01-14
> **d3ngar said:**
> what kind of switch is it? Do you have any control over it's settings, is there a web interface that tells you what the settings are?

The switch needs to get it's IP address from your windows machine...

The switch is netgear gs 605. A simple unmanaged switch. So it is not possible to turn off DHCP.

I come acreoss another thread that might help me: [get your ubuntu online via windows mobile 6 device connected via usb cable.]("http://ubuntuforums.org/showthread.php?t=869229")

But as always lately I run into dependencies hell. If I find a way to  get subversion (svn) installed on the ubuntu box I will be online. Do  you know if there is a terminal command to use to check if I allready  have svn, and if so what version?

Or if someone have great tips to how I can get subversion installed manually without internet conection for the ubuntu? 

I am aware of the [http://packages.ubuntu.com/hardy/subversion](http://packages.ubuntu.com/hardy/subversion)  but as there is so many dependencies manual install is near impossible.  Does anyone know what those Virtual packages are? Are they complete?  What I mean is that are they put togheter in a smart way so I dont need  to worry about dependecies maybe?

Any smart tricks to resolve this would be highly appriciated.

---

### Post by piergen on 2011-01-15
Ok I have dropped the switch and are now using a Linksys WRT54 GL router with dd-wrt firmware v24.

I now have the windowspc and the ubuntu on different subnet.
Here is my ```
 sudo dhclient
```> Listening on LPF/eth0/00:1d:60:88:23:81
Sending on   LPF/eth0/00:1d:60:88:23:81
Listening on LPF/vmnet8/00:50:56:c0:00:08
Sending on   LPF/vmnet8/00:50:56:c0:00:08
Listening on LPF/vmnet1/00:50:56:c0:00:01
Sending on   LPF/vmnet1/00:50:56:c0:00:01
Sending on   Socket/fallback
DHCPDISCOVER on vmnet8 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.130.129 from 192.168.130.254
DHCPREQUEST of 192.168.130.129 on vmnet8 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPACK of 192.168.130.129 from 192.168.130.254
bound to 192.168.130.129 -- renewal in 780 seconds.[B] 

_Ipconfig on windows give this result:_[/B]


**This is the part for the usb cable connection between windows mobile cellphone and windowspc:**

> Ethernet adapter Local Area Connection 6:

        Connection-specific DNS Suffix  . : xxx.xxx.xx
        IP Address. . . . . . . . . . . . : 192.168.0.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1


[B]And this is for the wired lan connection via Linksys router:


[/B] > Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.215.200
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :


Clearly the two connections are now on different subnets, right?

In theory there should be no reasson for the same error message anymore as the two connections are on different subnets.

Why can I still not get xubuntu online?

---

### Post by piergen on 2011-01-16
Is there anything else I might need to supply of information in order to get help?
If I have forgotten any information pls ask and I will submit asap.

Hope someone have ideas cause I am fresh out now.

---

### Post by piergen on 2011-01-16
For days I have been struggling with this problems. And guess what? Not one person has stopped by to give me tips. I dont know if me description of the problems is inadequate or if I am that kind of person people dont feel like like helping in general.

Is the community effort dissolving? Or is this just seen thru the eyes of an old beaten man who has struggled for close to 2 weeks with pc trouble without being able to fix it?

---

### Post by piergen on 2011-01-16
Really, 4 days now and no replies from anyone........is it something wrong with my ability to adequatly desribe the problems or could it be I have personality that people hate?

Fell free to post even if you are not sure how to solve this. As long as you have a theory or can think of things I can try out I will gladly try it out. So what if that might not work? My ubuntu box sure does not work for me right now anyway so I will try anything.

---

