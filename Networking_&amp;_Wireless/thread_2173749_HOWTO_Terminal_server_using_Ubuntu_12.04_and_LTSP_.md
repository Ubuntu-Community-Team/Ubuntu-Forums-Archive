---
title: "HOWTO: Terminal server using Ubuntu 12.04 and LTSP in 15 minutes"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by Emblem Parade on 2013-09-11
***Note: This guide also applies to Ubuntu 14.04***

There's a lot of information about [LTSP]("http://www.ltsp.org/") (the Linux Terminal Server Project) out there, including quite a few guides, but nothing that really brought everything together well enough for me. In particular, they were bad at explaining the reasons for each step. So, here's my version!

Note that you do not need a dedicated Ubuntu server for this guide. I ran a terminal server just fine using Ubuntu 14.04 or 12.04 running inside VirtualBox. If you do so, just make sure the virtual machine is running with the network adapter in bridged mode, so that it is a full participant in the LAN.

**HOW DOES LTSP WORK?**

When it does work it seems like magic, but it's worth understanding what LTSP does, because it's actually a rather simple (but beautiful!) combination of existing technologies and products.

The thin client runs applications on the server using X forwarding, in fact not much differently from Unix terminals in pre-PC days. You can easily try this technology without LTSP by using "ssh -X", as long as you have X running on the client. What LTSP adds to this is the initial handshaking, the creation of the client/server session. You thus require specialized thin/fat clients that include support for logging into the LTSP server. After this handshake, LTSP actually plays no further role. So, all a client really needs is this LTSP session creator, and then X. (I'm simplifying this a bit: LTSP adds support for forwarding USB devices and sharing network drives, too, but that stuff is all done within the X forwarding framework.)

So how do you get that specialized LTSP session creator and X on the client? One way is to install it manually, assuming the client has some storage. That's how [BerryTerminal]("http://www.berryterminal.com/doku.php") works: it's a tiny operating system that includes only that bare minimum. When it boots up, it will look for the LTSP server and display the login screen (or login automatically if you have that configured on the server).

**NETWORK BOOT**

But obviously, many clients do not have storage. They can, however, automatically download their operating system over the network, using an technology called [PXE]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment"). PXE has been included in practically every network card controller since the past decade. PXE, in turn, relies on two services: a DHCP server provides the client with its initial IP address, DNS, and PXE boot information. The client then uses TFTP to download the operating system image and boot it. So, in fact you will need three things to make this work: 1) a DHCP server; 2) a TFTP server; 3) a client operating system image. The whole dance of getting an IP address, downloading the image and booting it doesn't take that long: within 30 seconds you should get a login screen, even for weak clients.

To complicate things, there is an important limitation: only a single DHCP server can exist on a LAN, and it's very likely that you already have one running on your router. If that's the case, you have two options: 1) you *might* be able to configure your router's DHCP server to send clients PXE information about your terminal server, an advanced option that unfortunately does not exist in cheap office routers; 2) you can use a PXE feature called "proxy DHCP", created exactly for this situation. It's very easy to set up, and indeed **that's what this guide is for**. (Note that some *very* old equipment does not have proxy DHCP support in its PXE, in which case you can't use this method. But that's very rare these days.)

(Actually, there is a third, more complicated option: you can create a special closed LAN just for your terminal server and clients. In this LAN, your terminal server will act as both the DHCP server and TFTP server. Remember: you don't need a router in this LAN, because clients--assuming they are thin and not fat--run all their software on the server. But this means that your terminal server likely has two network cards, one sitting on this client LAN, and the other sitting on your broader network, likely with access to the Internet. This is what the "ltsp-server-standalone" package is for, and where most guides for LTSP begin. [Here's an excellent one]("http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients") if that's your situation. So, to reiterate, this guide assumes that you already have a working DHCP server on your network.)

**LET'S DO IT!**

Let's install LTSP, a proxy DHCP server, and a TFTP server:

```
sudo apt-get install ltsp-server dnsmasq tftpd-hpa
```

(Though [Dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html") can do both DHCP and TFTP, I've found it has a crucial bug when functioning as a TFTP server specifically with Ubuntu 14.04, so we'll be using tftpd-hpa instead for that.)

**Warning:** do *not* install "ltsp-server-standalone" package as is suggested by other guides, because that assumes that you want your terminal server to be a *full* DHCP server.

Now we need a client operating system image. As stated earlier, for thin clients all we need the is the LTSP session creator and X. Of course, we also need a kernel (Linux), basic drivers for keyboard, mouse, video card, audio, etc. It's still an operating system! Marvelously, LTSP on Ubuntu comes with a tool to automatically create such an image for you, based, of course, on Ubuntu. But it should be emphasized that this client operating system is nothing like the regular full-blown Ubuntu desktop distribution: it is stripped down and highly specialized to work purely as an LTSP client. Indeed, for thin clients its total size is less than 300 mb.

LTSP on Ubuntu gives you many options for customizing the client image, but the defaults should work just fine. (Customization would be necessary in case the default image doesn't support your thin clients' hardware for some reason. In that case, you might need to install additional drivers on your image.)

This is going to take a while, so sit back and relax:

Ubuntu 14.04:

```
sudo ltsp-build-client
```

Ubuntu 12.04:

(We'll assume in this guide that our thin clients are 32-bit x86 machines, which is most common. You can also build 64-bit x86 images, assuming you have clients that could support it, though there would be no serious advantage to it unless they are fat clients running heavy software. More commonly useful, perhaps, are images for ARM architecture clients. Simply replace the "i386" in this guide with the client architecture you are using, as long as it's supported by Ubuntu.)

```
sudo ltsp-build-client --arch i386
```

The command will download all packages for this stripped-down Ubuntu-based client operating system and install them under: /opt/ltsp/i386/. It will then compress this into /opt/ltsp/images/i386.img, the actual image to be sent to the client.

(Note that this image will be based on your *current* Ubuntu version, at the *current* state of packages in its repositories. Since this is merely a thin client operating system, it shouldn't really matter if the image is stays "old", as long as it works. Remember, the software is actually running on your server, not the client. However, it is possible to upgrade this image to latest Ubuntu packages, something you might want to do once in a while, especially if security is important. This guide won't cover that.)

Actually, we need to stop and explain one more aspect of the network booting process for LTSP on Ubuntu: it happens in two stages. In order to download, decompress and boot into the i386.img, we need a network operating system bootloader. This is provided by [PXELINUX]("http://www.syslinux.org/wiki/index.php/PXELINUX"), a tiny Linux-based bootloader (really, a mini operating system) designed exactly for this use case. If you're used to desktop Ubuntu, consider that PXELINUX is similar to GRUB, but designed around network boot. The "ltsp-build-client" created it for us under /var/lib/tftpboot/ltsp/i386/. It is less than 15 mb in size. So, the client gets this pxelinux directly over TFTP and runs it, and PXELINUX then downloads i386.img, decompresses it into a RAM drive, and boots.

The configuration file for our PXELINUX is under /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default. Unfortunately, in the version of LTSP included in Ubuntu 14.04 and 12.04, it is generated without support for proxy DHCP by default. To fix this, you must run:

Ubuntu 14.04:

```
sudo sed -i 's/ipappend 2/ipappend 3/g' /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
```

Ubuntu 12.04:

```
(cat <<EOF
ipappend 3
EOF
) | sudo tee -a /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
```

If you update your client image in the future (with "ltsp-update-image") then you will need to run this command again.

(Documentation for the "ipappend" can be found [here]("http://www.syslinux.org/wiki/index.php/SYSLINUX#IPAPPEND_flag_val_.5BPXELINUX_only.5D"). The value "3" is the logical OR of "1" and "2".)

OK! Now it's time to configure Dnsmasq. Edit /etc/dnsmasq.d/ltsp.conf (the file isn't there, you must create it) and put something like this:

```
#
# Dnsmasq running as a proxy DHCP and TFTP server
#
# See: http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html
#

#
# TFTP
#

# This might work instead of tftpd-hpa:
#enable-tftp
#tftp-root=/var/lib/tftpboot

#
# DHCP
#

# DHCP proxy on this network
dhcp-range=192.168.1.0,proxy

# Tell PXE clients not to use multicast discovery
# See section 3.2.3.1 in http://tools.ietf.org/html/draft-henry-remote-boot-protocol-00
dhcp-option=vendor:PXEClient,6,2b

# Better support for old or broken DHCP clients
dhcp-no-override

# Enable this for better debugging
#log-dhcp

#
# PXE
#

# Note the file paths are relative to our "tftp-root" and that ".0" will be appended

pxe-prompt="Press F8 for boot menu", 3
pxe-service=x86PC, "Boot from network", /ltsp/i386/pxelinux
pxe-service=x86PC, "Boot from local hard disk"

```

You will need to change "dhcp-range" to the subnetwork of your LAN. Also change "i386" and "x86PC" to something else if you are using a different client architecture image. Now, restart dnsmasq:

```
sudo service dnsmasq restart
```

Note that on Ubuntu 14.04, there is currently a bug with tftpd-hpa, with [this solution](https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509/comments/40).

And ... you should be good to go. Start your clients with network boot: they should get an IP address from your router's DHCP server, then get PXE information from your proxy DHCP server (Dnsmasq), then boot PXELINUX from your TFTP server (also Dnsmasq), then download and boot into the i386.img stipped-down-Ubuntu-based client operating system, and then display the login screen.

**EXTRAS**

By default, LTSP on Ubuntu uses an ssh tunnel for secure X forwarding, but you can switch to "direct X" mode for better scalability and performance, at the expense of reduced security on the LAN. Edit /var/lib/tftpboot/ltsp/i386/lts.conf (the file will not exist, but it's OK to create it) and put this:

```
[Default]
LDM_DIRECTX = True
```

Now we need to regenerate the image and not forget to fix the proxy DHCP issue:

Ubuntu 14.04:

```
sudo ltsp-update-image
sudo sed -i 's/ipappend 2/ipappend 3/g' /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
```

Ubuntu 12.04:

```
sudo ltsp-update-image --arch=i386
(cat <<EOF
ipappend 3
EOF
) | sudo tee -a /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
```

The next time clients boot, they will be using this new image.

**NEED GUEST USERS FOR A PUBLIC LAB?**

I've created a [separate guide]("http://ubuntuforums.org/showthread.php?t=2177959") for doing that.

---

### Post by robin.peters on 2013-11-29
Hi - nice HowTo, but can you make one for the configuration with a i386 terminal server and Raspberry Pi (armhf architecture)? I use Ubuntu Server and U-Boot (RasPi), but I have no idea what I'm doing wrong.

Thanks - Robin

---

### Post by Emblem Parade on 2013-11-29
The setup is identical for an i386 terminal server: there should be no difference on the server side.

However, Raspberry Pi introduces a special limitation: you cannot create an Ubuntu-based client image for it (for the same reason Ubuntu won't run on a Raspberry).

The solution is to install [BerryTerminal]("http://www.berryterminal.com/") on your Raspberries. It's a very minimal image that could work on small, cheap SD cards. With it, the Raspberry would boot straight into the LTSP logon. Simple!

---

### Post by Grugs on 2014-03-02
Hi,

Thanks for the great how-to.

I've just now tried to work my way through it, but unfortunately, I didn't quite end up where I thought I would.

[indent]In short, upon starting the machine that I want to use as a thin client, I got:

```

PXE-E53: No boot filename received

PXE-M0F: Exiting Intel PXE ROM.

```
[/indent]

My situation is this:

I have two computers, one running Linux the other Windows 7.  Both are connected to a home-network router through which they share an internet connection.  Both computers are plugged into the router with an ethernet cable (and both also have a wireless connection to the router, though I can't remember why - but I digress).  Suffice to say: the router is acting as the LAN's DHCP server.

For the sake of science (proof-of-concept), I want to turn the Linux machine into an LTSP terminal server and the Windows 7 machine into a thin client.

Following your instructions, I've done this:

[list=1]
[*]On the Linux machine,
[font=courier]sudo apt-get install ltsp-server dnsmasq[/font]
[br].[/br]
[*][font=courier]sudo ltsp-build-client --arch i386[/font]
[br].[/br]
[*][font=courier](cat <<EOF
ipappend 3
EOF
) | sudo tee -a /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default[/font]

This step I don't fully understand except that it is necessary because in "the version of LTSP included in Ubuntu 12.04, [the configuration file for our PXELINUX] is generated without support for proxy DHCP."

How, though, does just the appending of [font=courier]ipappend 3[/font] to end of the file linked to by the soft link at [font=courier]/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default[/font]  ensure I'll be provided with a functioning "network operating system bootloader", ie,  PXELINUX?  Given that, using "a PXE feature called 'proxy DHCP', [is] **what this guide is for**", could you please expand on this seemingly vital step? 

For the moment, I will have faith.

Next step.
[br].[/br]
[*]"Edit [font=courier]/etc/dnsmasq.d/ltsp.conf[/font]"

You wrote "edit".  Is that to say that this file should have been created by the [font=courier]apt-get install[/font] or [font=courier]ltsp-build-client[/font] commands and we need just to change it?  For me, at this point, there was no such file at that location.

So I created a file named [font=courier]ltsp.conf[/font] in the [font=courier]/etc/dnsmasq.d[/font] directory and put into it what you have in your post.

However, for the [font=courier]dhcp-range[/font] line, you suggest that we change it to the "subnetwork of your LAN".  I'm not entirely clear on how to figure out what the subnetwork of my LAN is, but my guess is this: to get to my router's user interface, I open [font=courier]http://192.168.0.1[/font] in a web browser; therein, I can find that my router's IP address on the LAN is [font=courier]192.168.0.1[/font]; so I'm guessing the "subnetwork of your LAN" is  [font=courier]192.168.0[/font] and so I made the [font=courier]dhcp-range[/font] line look like this:

 [font=courier]dhcp-range=192.168.**0**.0[/font]

Is that what you mean by "change 'dhcp-range' to the subnetwork of your LAN" ?
[br].[/br]
[*] [font=courier]sudo service dnsmasq restart[/font]

The response was 

[font=courier][ ok ] Restarting DNS forwarder and DHCP server: dnsmasq.[/font]

Moreover, when I then ran

[font=courier]sudo /etc/init.d/dnsmasq status[/font]

I got 

[font=courier][ ok ] Checking DNS forwarder and DHCP server: dnsmasq[....] (running).[/font]

So it looks like I'm ready for the next step.
[br].[/br]
[*] "Start your clients with network boot"

Assuming that I've got everything right so far, this is where I could most use your help.

I did this:

I turned on the Windows 7 (thin-client-to-be) machine and repeatedly pressed F2 to enter its [font=courier]BIOS SETUP UTILITY[/font].  Went  to its [font=courier]Boot[/font] screen and there, guessing completely, made two changes: (A) For [font=courier]Boot Device Priority[/font], I moved [font=courier][Network:Atheros Bo][/font] from last place to first place: and (B), for good measure, I [font=courier][Enabled][/font] something called [font=courier]OnBoard LAN Boot ROM[/font] (which had until then been [font=courier][Disabled][/font], upon then saving and exiting, I saw the machine seemingly try to [not boot Windows as per usual], but that effort ended with

```

PXE-E53: No boot filename received

PXE-M0F: Exiting Intel PXE ROM.

```

That message then disappeared and Windows 7 started up.

So close and yet so far?
[/list]

---

### Post by Emblem Parade on 2014-03-02
It seems like you did things correctly. On the client, you should be seeing the menu we defined in ltsp.conf ("Press F8 for boot menu", etc.)

There is a chance that your "Windows 7 computer" has an NIC with firmware that does not support newer features of PXE, such as ProxyDHCP. If it's possible at all, try putting other computers on your LAN and having them boot from the network. Laptops should be fine! The newer the computer, the more likely it will work.

To answer your question in #3: I learned about it [here]("https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP"), but you'll see the solution repeated in many other guides, too. If you're really, really curious, the documentation for this option is [here]("http://www.syslinux.org/wiki/index.php/SYSLINUX#IPAPPEND_flag_val_.5BPXELINUX_only.5D"). (Why 3? It is a bitwise OR of both options 1 and 2, which we both want enabled.)

---

### Post by Grugs on 2014-03-03
Hi,

Thanks for writing . . .

> **Emblem Parade said:**
> (Why 3? It is a bitwise OR of both options 1 and 2, which we both want enabled.)

. . . which gives peace-of-mind that [font=courier]3[/font] is not just some arbitrarily chosen number.

But thank you even more for writing . . .

> **Emblem Parade said:**
> On the client, you should be seeing the menu we defined in ltsp.conf ("Press F8 for boot menu", etc.)

. . . which brought to my attention that the [font=courier]ltsp.conf[/font] file should not end with . . .

```
# Better support for old or broken DHCP clients
dhcp-no-override
```

. . . but rather with . . .

```
# Better support for old or broken DHCP clients
dhcp-no-override

# Enable this for better debugging
#log-dhcp

#
# PXE
#

# Note the file paths are relative to our "tftp-root" and that ".0" will be appended

pxe-prompt="Press F8 for boot menu", 3
pxe-service=x86PC, "Boot from network", /ltsp/i386/pxelinux
pxe-service=x86PC, "Boot from local hard disk"
```

. . . damn near-invisible scroll bar!  Or maybe I just have tunnel vision.  But I digress.

So having put *all* of what you suggested for [font=courier]ltsp.conf[/font] into it and re-running [font=courier]service dnsmasq restart[/font], I returned to the thin client machine.

Turned it on.  It booted Windows 7.  Turn it off and on again, all the while connected to router via ethernet cable, re-entered the BIOS setup, left all as it was (still set to boot from the network), exited from the BIOS set up and got this on the screen instead of Windows 7:

```

Intel UNDI, PXE 2.1 (build 082)
Copyright (C) 1997-2000  Intel Corporation 

For Atheros PCIE Ethernet Controller v1.0.0.5(01/22/09)

CLIENT MAC ADDR: <thin_client_computer_ethernet_nic_mac_addr> GUID: <a_guid>
CLIENT IP: <thin_client_computer_ip_address> MASK: 255.255.255.0
DHCP IP: <router_lan_ip_address> PROXY IP: <terminal_server_computer_ip_address>
GATEWAY IP: <router_lan_ip_address>

Auto-select:
     Boot from network

BOOT SERVER IP: <terminal_server_computer_ip_address>
!PXE entry point found (we hope) at 9CC4:0106 via plan A
UNDI code segment at 9CC4 len 2E9E
UNDI data segment at 9475 len 84F0
Getting cached packet 01 02 03
My IP address seems to be <thin_client_computer_ip_address>
ip=<thin_client_computer_ip_address>:<terminal_server_computer_ip_address>:<router_lan_ip_address>:255.255.255.0
BOOTIF=<a_hypen_separated_number>
SYSUUID=<the_same_guid_as_above_but_with_lower_case_letters>
TFTP prefix: /ltsp/i386
Trying to load: pxelinux.cfg/default                 ok

Decompressing Linux... Parsing ELF... No relocation needed... done.
Booting the kernel.
Loading, please wait...
```

then all that disappeared and was replaced with

```
connect: Connection refused
read: Connection refused
read: Connection refused
read: Connection refused
read: Connection refused
```

ad nauseum, until 

```
NFS over TCP not available from <router_lan_ip_address>
connect: Connection refused
```

Googled that and have, therefore, started to think that it is related to something that showed up when I ran 

[font=courier]sudo apt-get install ltsp-server dnsmasq[/font]

specifically this big [font=courier]** WARNING **[/font]:

```
Unpacking ltsp-server (5.5.0-1) ...
Processing triggers for man-db (2.6.6-1) ...
Setting up nbd-server (1:3.7-1) ...

Creating config file /etc/nbd-server/config with new version

** (process:14414): WARNING **: Could not parse config file: The config file does not specify any exports
** Message: No configured exports; quitting.
 nbd-server.
Setting up nfs-kernel-server (1:1.2.8-6) ...

Creating config file /etc/exports with new version

Creating config file /etc/default/nfs-kernel-server with new version
[warn] Not starting NFS kernel daemon: no exports. ... (warning).
Setting up squashfs-tools (1:4.2+20130409-2) ...
Setting up ltsp-server (5.5.0-1) ...
```

I was reminded of the above when, guessing, I ran

[font=courier]/etc/init.d/nfs-kernel-server restart[/font]

and got in response:

```
[ ok ] Stopping NFS kernel daemon: mountd nfsd.
[ ok ] Unexporting directories for NFS kernel daemon....
[warn] Not starting NFS kernel daemon: no exports. ... (warning).
```


I mention all this on the chance that it might be immediately obvious to you what the problem is.

---

### Post by Emblem Parade on 2014-03-04
You've definitely moved forward!

The error message suggests that somewhere else you may have not copy-pasted a complete config file.

My suggestion to you is to start from scratch with a clean installation of Ubuntu 12.04 and follow the instructions here to the letter. I'll note that you do not have to install Ubuntu on "metal," but instead can install it inside a virtual machine. That way, it's easy to simply delete the VM if it doesn't work and start over. Great for experimentation. I recommend using VirtualBox: it's especially easy to use.

In case you're worried: I did test this guide using a VM, too. (Actually, you can even run the LTSP client in a VM! The Virtualbox BIOS support PXE boot.)

---

### Post by felix10 on 2014-04-25
Hi, nice tutorial.  I ran into a situation.  I already have a Windows DHCP server.  Do I need to tweak anything on the Windows DHCP?  I didn't get the LTS to work that's the reason I'm asking the question.  Also, my LTS is on Virtual server.  Does that make any different? 
Oh, and how about
# DHCP proxy on this network
dhcp-range=192.168.1.0,proxy

Is the the IP of the Windows DHCP or the LTS-server?  Thanks!

---

### Post by Emblem Parade on 2014-04-26
Yes, it should work: the guide is exactly for situations where you already have a DHCP server existing on the LAN.

And it should work fine in a virtual machine, **as long as the VM's network card is in bridged mode**. You absolutely need the terminal server on the same LAN as the DHCP server and the terminals.

Then the dhcp-range would exactly be the range of the LAN as provided by the Windows DHCP server and used by the terminal server.

---

### Post by felix10 on 2014-05-07
I'm absolutely did something wrong with my configuration.  I have my Ubuntu 14.04 LTS on network 192.168.110.0 and Windows DHCP on 192.168.101.0 and my pxe client are on the same as the LTS.  How would I configure the ltsp.conf:
here's mine:
[COLOR=#800000][I]
#Dnsmasq running as a proxy DHCP and TFTP server
#
#see: [http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html](http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html)
#

#
#TFTP
#

enable-tftp
tftp-root=/var/lib/tftpboot

#
#DHCP
#
#set port to 0 so that dnsmasq knows its not being used as dns server
#port=0
#log-dhcp

#DHCP proxy on this network
dhcp-range=192.168.110.0,proxy

#Tell PXE clients not to use multicast discovery
#See section 3.2.3.1 in [https://tools.ietf.org/html/draft-henry-remote-boot-protocol-00](https://tools.ietf.org/html/draft-henry-remote-boot-protocol-00)
dhcp-option=vendor:PXEClient,6,2b

#Better support for old or broken DHCP clients
dhcp-no-overide

#Enable this fore better debugging
#log-dhcp
[/I][/COLOR]
Service dnsmasq restart = fail.. what do i need to change?

---

### Post by Emblem Parade on 2014-05-07
I would suggest looking at the logs of dnsmasq, perhaps it has information about what's causing it to fail. I imagine it is failing because there is a typo somewhere in the configuration, although I can't see it.

Also, all parts of this network -- the DHCP server, the LTSP server, the terminal clients -- should be on the same IP network. You mention both 192.168.110 and 192.168.101, but perhaps that is also a typo.

---

### Post by Emblem Parade on 2014-06-19
Hey everyone,

I've just edited the original post with an important fix for Ubuntu 14.04.

Dnsmasq has an issue with 14.04: if you restart your machine, the internal TFTP server will stop working. You can fix this by manually restarting dnsmasq, but obviously that's not a good solution.

So now I am recommending using tftpd-hpa as the TFTP server. *However*, incredibly that package suffers from the same issue in Ubuntu 14.04! There is, however, [a solution]("https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509/comments/40") which I also linked to.

In summary: I recommend using tftpd-hpa with the fix. The guide has been updated to reflect all of that.

---

### Post by nix_weasel on 2014-08-16
> **Configure tftpd-hpa**

[COLOR=#333333][FONT=Ubuntu]You'll need to tell tftpd-hpa to start its daemon (which it doesn't by default). To do this, edit the /etc/default/tftpd-hpa file, and make sure that it looks something like this:[/FONT][/COLOR]
#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
[COLOR=#333333][FONT=Ubuntu]Then, run the startup script to actually start the daemon[/FONT][/COLOR]
/etc/init.d/tftpd-hpa restart
(referenced from [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer))

 
saw this and thought it might be be helpful for the tftpd problems ta mate excellent guide

update: simply adding the above to the /etc/default/tftpd-hpa file works fine

---

### Post by BlackChart on 2014-08-31
I've been following this thread to test LTSP.

Installed the server in VirtualBox without issues.
I've then made a client, in VirtualBox too, but it won't boot.

The VBox client fails with the following error: pxe-e74 bad or missing pxe menu

I've tried a thin client too, same error.
I've tried a laptop on PXE, same error.

When Wiresharking the net, I can see the dnsmasq server replying to DHCP requests, alon side of the normal DHCP.

What could be the issue?

---

### Post by BlackChart on 2014-08-31
A bit more testing shows, when switching server and client from bridged networking to host-only, everything works flawless :/

---

### Post by rwmarch on 2014-10-30
Emblem Parade,
Thank you for a very nicely done Howto.  Following your instructions for 14.04, after first purging the existing ltsp-server package, a thin client booted right away.
I had done a dist-upgrade from 10.04 to 12.04 to 14.04 in one "sitting".  Then I found that the thin clients would not boot.  Appeared to be an nbd-server issue (was never able to pinpoint the cause) and every effort I made to boot had ended in failure.
Thank you for giving of your expertise.

---

### Post by dinhduy3110 on 2015-01-25
Hello, first of all, thank you your great TUT.

I have problem with LTSP and LDAP, please help. When I log in to LTSP with LDAP user, no GUI apear, it just blank desktop like below. thank you. 

[ATTACH=CONFIG]259503[/ATTACH]

---

### Post by Daniel_Vernall on 2015-02-04
Hello,

Thanks for the guide.

I'm am trying to set up on Zorin 9 (Based on Ubuntu 14.04) but am having problems.

I'm having problems with the second step.
    sudo ltsp-build-client

I get this when running with --debug:

DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/001-load-configuration-file

...

DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
/usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts: line 3: /opt/ltsp/amd64/etc/hosts: No such file or directory
error: LTSP client installation ended abnormally

I have tried uninstalling ltsp-server and reinstalling. But the same error occurs.

Simply running the build client script again gives:

NOTE: Root directory /opt/ltsp/amd64 already exists, this will lead to problems, please remove it before trying again. Exiting.
error: LTSP client installation ended abnormally

Which when I do returns me to the original error as above.

Any advice?

Thank you

---

### Post by alexandra2 on 2015-03-13
Thank you for the tutorial. I feel like I am **almost** there.

I am running two VM's on ESXi: the Ubuntu Server 14.04, and a thin client VM. I installed the xfce desktop environment (xubuntu-desktop) on the server. The server VM is 64-bit, as are the client build and the client VM. Both VM's are on the main network (no NAT).

The PXE boot works, but when I go to log in, the desktop never appears. If I switch to the command line interface to log in, authentication fails--even for the server admin account. Could someone please help me move forward?

Thanks,
Alexandra

---

### Post by felix_vang on 2015-03-15
I'm curious, how do you get configure the Windows Server?  this is what I have but somehow I didn't get it work at all.  
Server Options:
017 Root path: /opt/ltsp/i386
060 PXEClient: PXEClient
066 Boot Server Host Name: LTSP IP address
067 Bootfile Name: /ltsp/i386/pxelinux.0

save and restart dhcp service.  did I have it setup correctly?

---

### Post by felix_vang on 2015-03-15
oh, this is how the client response: on the vmclient, it said PXE:51: No DHCP or proxyDHCP offers were received.
on the physical machine it said: ProxyDHCP service did not reply to request on port 4011.

thanks..

---

### Post by paul196 on 2015-03-24
Hi I'm running through this guide and am pausing at the DHCP configuration point because I want to be sure of implications.

I wanted to implement an LTSP system on my existing corporate network, but do NOT want to interfere with existing DHCP, or other, services. I know you mentioned that this configuration is specifically for implementing on networks that already have DHCP running.. but I really want to be sure here. 

I have a SINGLE NIC setup.. are these instructions for a SINGLE NIC??

so.. if my corporate network is issuing 10.10.10 addresses, what am I putting in the "dhcp-range" field? I want thin clients to be able to boot on the corporate network, then connect to this LTSP server.. but I don't want to affect other normal systems.

Thanks,
Paul

---

### Post by YenPao on 2015-04-02
> **felix_vang said:**
> oh, this is how the client response: on the vmclient, it said PXE:51: No DHCP or proxyDHCP offers were received.
on the physical machine it said: ProxyDHCP service did not reply to request on port 4011.

thanks..
Anyone.. I have the same issue with the NoDHCP offers were received with port 4011.  I'm using vm host.

---

### Post by aravinda2 on 2015-05-09
Hi 
I did exactly as described.. [http://ubuntuforums.org/showthread.php?t=2277522](http://ubuntuforums.org/showthread.php?t=2277522)
yet im receiving a blank screen, after login ... 

[IMG]http://i.stack.imgur.com/X5OEe.png[/IMG]


How can i get this thing fixed please?

---

### Post by vktr2000 on 2015-06-05
Me too

---

### Post by UnhappyGhost on 2015-06-24
> **aravinda2 said:**
> Hi 
I did exactly as described.. [http://ubuntuforums.org/showthread.php?t=2277522](http://ubuntuforums.org/showthread.php?t=2277522)
yet im receiving a blank screen, after login ... 
How can i get this thing fixed please?



Here is a Sample lts.conf file in case you need to edit anything. Look at the lines that are bold and uncomment the line for gnome-fallback and see if it loads the gnome-fallback in the clients.


unhappyghost@unhappyghost:$ sudo nano /var/lib/tftpboot/ltsp/i386/lts.conf


[default]
# X_COLOR_DEPTH = 24        # to set the color depth on display
# LOCALDEV = True            # use local hardware on clients
# SOUND = True            # use sound drivers on clients
# NBD_SWAP = Y            # use swap to be set on server
# SYSLOG_HOST = server    # use server as syslog_server
# XKBLAYOUT= en            # keyboard default to en
# SCREEN_07 = rdesktop
# RDP_OPTIONS = "-a 16"
# RDP_SERVER = 192.168.5.99    # IP Address of the Windows Terminal Server with AD
# LDM_ALLOW_GUEST = True # enable guest logins, for old edubuntu
# LDM_GUESTLOGIN = True # enable guest logins, for newer edubuntu
# LDM_THEME = edubuntu # set theme folder - edubuntu, ltsp, default
LANG = en_US.UTF-8         
LANGUAGE = en_US.UTF-8
LDM_LANGUAGE = en_US.UTF-8
**# LDM_SESSION = "gnome-session --session=gnome-fallback" #For Ubuntu Gnome Desktop!!!**
**# LDM_REMOTECMD = /usr/bin/startkde             #For Ubuntu Unity UI Desktop!!!**




ctrl+O to save the changes
ctrl+X to exit nano editor

after the changes to the lts.conf file you have to issue the below mentioned ltsp-update commands after every change
Also you mentioned that it authenticates but the desktop doesn't load, so the sshkeys may be the problem.


unhappyghost@unhappyghost:$   sudo ltsp-update-kernels
unhappyghost@unhappyghost:$   sudo ltsp-update-sshkeys
unhappyghost@unhappyghost:$   sudo ltsp-update-image

---

### Post by UnhappyGhost on 2015-06-24
> **vktr2000 said:**
> Me too



Here is a Sample lts.conf file in case you need to edit anything. Look at the lines that are bold and uncomment the line for gnome-fallback and see if it loads the gnome-fallback in the clients.


unhappyghost@unhappyghost:$ sudo nano /var/lib/tftpboot/ltsp/i386/lts.conf


[default]
# X_COLOR_DEPTH = 24        # to set the color depth on display
# LOCALDEV = True            # use local hardware on clients
# SOUND = True            # use sound drivers on clients
# NBD_SWAP = Y            # use swap to be set on server
# SYSLOG_HOST = server    # use server as syslog_server
# XKBLAYOUT= en            # keyboard default to en
# SCREEN_07 = rdesktop
# RDP_OPTIONS = "-a 16"
# RDP_SERVER = 192.168.5.99    # IP Address of the Windows Terminal Server with AD
# LDM_ALLOW_GUEST = True # enable guest logins, for old edubuntu
# LDM_GUESTLOGIN = True # enable guest logins, for newer edubuntu
# LDM_THEME = edubuntu # set theme folder - edubuntu, ltsp, default
LANG = en_US.UTF-8         
LANGUAGE = en_US.UTF-8
LDM_LANGUAGE = en_US.UTF-8
**# LDM_SESSION = "gnome-session --session=gnome-fallback" #For Ubuntu Gnome Desktop!!!**
**# LDM_REMOTECMD = /usr/bin/startkde             #For Ubuntu Unity UI Desktop!!!**




ctrl+O to save the changes
ctrl+X to exit nano editor

after the changes to the lts.conf file you have to issue the below mentioned ltsp-update commands after every change
Also you mentioned that it authenticates but the desktop doesn't load, so the sshkeys may be the problem.


unhappyghost@unhappyghost:$   sudo ltsp-update-kernels
unhappyghost@unhappyghost:$   sudo ltsp-update-sshkeys
unhappyghost@unhappyghost:$   sudo ltsp-update-image

---

### Post by UnhappyGhost on 2015-06-24
Followed the instructions exactly in the post, but surprisingly there's no such file generated as pxelinux.0 and thats why ltsp-clients cannot find the needed file to start the PXE boot. 
Am using Ubuntu server x64 15.04 inside vmware and the ltsp-client is also inside vmware and both are able to communicate. Do I need to use a desktop version of Ubuntu may be for the pxelinux.0 file to be generated ?

---

