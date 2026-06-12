---
title: "Please help me configure my network"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by herbster on 2007-09-19
I have a XP box and a Feisty box on a home network, with a Linksys router. I'd like to be able to remote desktop into my Feisty box from anywhere (specifically my sister's Vista laptop), and be able to transfer files to and from, etc.

How would I exactly do this? I have downloaded Tight VNC to the Vista laptop and the XP box, but the main thing is I have no idea how to connect to my Feisty box, as the router IP is of course 192.168.1.101.

What IP do I use? I have googled on static IPs and read some on the dyndns service, but I gotta be honest-- it's making no sense to me in a step-by-step way, I don't know exactly how to do it.

TIA :)

---

### Post by kevdog on 2007-09-19
Hmm, 

Lets just talk about what you want to do exactly. If all you want to do is transfer files, then I wouldnt recommend TightVNC or VNC -- a lot of extra overhead, is a graphic utility, and is very slow.  It does give you the ability however to control the remote desktop.  If this is what you are after then maybe this is the solution.

If you just want to transfer files, is this going to be from within the same local network, or from a distant location (out in the world).  Options for local network include samba.  If you want to access the computer from a remote location (different local network), then options could consist of ftp, ssh).

---

### Post by herbster on 2007-09-19
kevdog,

Thank you, that is a good point. I do not require a GUI/remote desktop after all, as all I really do want to do is transfer files. I have no problem currently doing this on the network as I transfer stuff from the XP share all the time over to my Feisty box. Yes, I want to enable it so that I can login via SSH or FTP into my Feisty box from out in the world, like this Vista laptop I'm on or a library or anything.

I have setup SSH that I use regularly in terminal on the Feisty box to get onto my website, but how do I set it up to use with my actual Feisty machine and/or partitions on the Feisty? ie., I'd love to login from the Vista laptop at my office and see all the partitions on my Feisty box, and be able to do whatever I need (make dirs, delete, move, copy, download from, etc.).

---

### Post by herbster on 2007-09-23
Help? :)

I got WinSCP going and just used it to copy over some files from Feisty to the XP box on my network, just testing. Works great.

Now I need to get static IPs or what have you so I can get to these home PCs from outside :)

---

### Post by wheredidrealitygo on 2007-09-23
No-ip.com offers an excellent dynamic dns utility, you sign up for a free account, download the updater, and it sits there and does it's thing on it's own, giving you a dynamic dns, such as example.example.org)

The windows utility you probably won't need any help with, but no-ip.com offers an awesome walkthrough for configuring the linux version.

---

### Post by herbster on 2007-09-23
Thanks, I downloaded and installed the program and checked their help page on configuring your router, but I'm confused now.

I set up an account at no-ip.com, and set up to redirect to me.whatever.com, but in my account it's using my IP, as in my real IP not the 192.168.x.x network IPs (Of course I couldn't put that in there). So when I hit up me.whatever.com in a web browser, it just sits there saying "Connecting to" and nothing happens. I don't think I've set it up right and am befuddled at this moment :D I don't know which port it would be using, either, but in my Linksys web-based config tool I added ports 22 (which worked in putty and winscp) and 80 to be forwarded, still nothing :(

---

### Post by wheredidrealitygo on 2007-09-23
are you ssh/vnc'ing into the feisty box from the outside, or remote desktop'ing into the windows box from the outside.

you can just use any terminal to ssh into a feisty box, just make sure port 22 is forward, and that the port is open in the firewall on the feisty box. 

you need a vnc client to vnc into it (on the computer you're going from), such as ultra/tight/realvnc.

windows has it's own remote desktop client, but only works with the rdp protocol going to other windows boxes.

---

### Post by herbster on 2007-09-23
I am trying to use WinSCP which uses SCP to copy files from my Feisty to a windows machine outside (ie., my Vista laptop at my office).

I know I can use the redirect of me.whatever.com from no-ip.com, but I can't set it up properly, the whole DNS redirect process.

---

### Post by wheredidrealitygo on 2007-09-24
[http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

This provides a step by step walkthrough for configuring the linux dynamic update client.

just configure that and you're all set, it'll automatically do the dynamic updating for you, then you can point your ssh terminal to your address, and it should connect.

---

### Post by herbster on 2007-10-17
> **wheredidrealitygo said:**
> [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

This provides a step by step walkthrough for configuring the linux dynamic update client.

just configure that and you're all set, it'll automatically do the dynamic updating for you, then you can point your ssh terminal to your address, and it should connect.

I have finally got some time to set this up right, and I've got the no-ip.com client running, but I have no redirect or anything. It's the only thing I've done, following that guide. My network is still 192.168.x.x, nothing else is different.

That's what I don't understand how to do-- how to actually redirect and/or change my home network IP ???

EDIT: What's the very first step to configuring my network itself-- do I set a static IP? How exactly? Then what?  Right now I'm stuck here at the very beginning.

---

### Post by Almumin on 2007-10-17
Herbster,

There is a GUI tool that you can add that will allow you to remote into the Ubuntu PC. It is Gnome-RDP. 

On the** Menu -> Applications -> Add Remove Open Applications**

Type in **gnome-rdp** (make sure that you have All available applications selected under "show")

Apply the changes and then install the utility.

I don't recommend using the computer name. Use the IP of the machine. Make sure it is RDP and enjoy!

Make sure that you remote connection settings in your Windows box will allow you to remote connect to your sisters computer.

Good luck! Now I have to find out how to setup a share to my dag on Buffalo Linkstation gigabit server!

Almumin

---

### Post by herbster on 2007-10-17
Almumin,

Thank you but I already use terminal server client to get into my XP machine on the network. My aim is to have access to this Feisty machine from anywhere by typing in for example herbster.mysite.com and then using scp or sftp to transfer over and manage files. Nothing more.

I have just set a static IP address and opened up a port, but don't know how to get the outside world to see my box by hitting up herbster.mysite.com. How exactly do I connect the domain to my network IP???

---

