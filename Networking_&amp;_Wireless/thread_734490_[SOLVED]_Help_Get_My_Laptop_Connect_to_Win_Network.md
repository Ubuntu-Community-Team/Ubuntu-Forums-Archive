---
title: "[SOLVED] Help Get My Laptop Connect to Win Network"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by rphil2008 on 2008-03-24
Hello guys. I've searched but I still cant get the answer to my problem. I hope you can help me out here or point me to the thread where this is resolved. 

Problem: I dont know how to connect my laptop to the local area network (company's windows network.) I want to browse the internet and update my Edubuntu on the laptop using this network.

Details.

1. I have an office laptop, Dell D410, where I successfully installed Edubuntu 7.1 dual boot with WinXP.
2. This laptop is not currently connected to our LAN (Windows network)
3. My desktop workstation, HP Pavilion 8853, is connected to the LAN. Using my desktop I can browse the network and the internet through a proxy-server on this network.
4. The desktop has a unique IP address assigned by our IT dept and I know where to find those LAN settings.
5. I log-on to my desktop (that is, the windows network) using my assigned username and password.
6. This is a wired connection through a LAN cable plugged at the LAN socket on my desktop
7. My laptop also has a LAN socket.

Questions:

1. Can I swap the desktop and the laptop on the LAN cable?
2. How do I configure my laptop to connect to the network and internet using Edubuntu?
3. Where in Edubuntu is the LAN configuration? I have the details on the LAN settings on the desktop but I dont know where in Edubuntu can I put them in.
4. I have heard abut Samba but I have no idea about it. At in any case, the laptop cant connect to the internet to download anything.

I have prepared two formal OpenOffice presentations on the laptop to be conducted on a professional capacity (in my line of work) a few days from now. This time, I wanted to use Edubuntu and not WinXP. But I really wished I could update my Edubuntu 7.1 first before the presentation as I might be missing important bug fixes which could pop up during my presentation.

Please help. Thanks for your time!

---

### Post by Eiríkr on 2008-03-25
Answers:
[list=1][*]Yes, you can swap the cable from the desktop to your laptop.  This very likely won't be very useful, though.
[*]I strongly suspect your login on your desktop does far more than just get you into the machine -- many corporate deployments involve all kinds of fun domain-level authentication behind the scenes to set up such things as department-wide shared disks, printers, and the like.  As such, I'd really recommend you talk to your IT department about setting you up.  You *might* be able to replicate the basic networking setup from your Windows desktop, but even so, without the proper passwords and connectivity on the software level (Active Directory, domain logons, etc), you probably won't be able to do anything, and you might even piss off IT as they'll probably be seeing all kinds of weirdness from your attempted connection (if they're doing their jobs ;)).  
[*]I don't know about Edubuntu in specific, but in Xubuntu, you'd click Applications -> System -> Network.  
[*]Again, even if you replicate your Winbox's network settings on your laptop, I doubt this will be sufficient to get you online.  [/list]

Good luck,

Eiríkr

---

### Post by rphil2008 on 2008-03-25
Thank you Eirikr for taking the time to write. You are correct in saying I may need our IT to help me setup but that's the problem. THEY ARE PARANOID MANIACS which I believe goes with the job=). I can imagine them turning my request down without any second thoughts and I may even be prohibited from using Linux in the first place.

So I spent several hours doing trial and error. To make the story short, I succeeded in connecting my Edubuntu laptop to the network and internet using a proxy server address. This was a big thing for me. Imagine my glee upon opening Firefox with Edubuntu! Hurray!

But now on to the next challenge. I cannot update Edubuntu either by synaptic or apt-get in the command line. I keep getting proxy errors like ISA server crap, authentication required, cannot resolve whatever... This is now my challenge.

For the moment, I was able to install sorely needed codecs to play my mp3s and dvds by installing the packges the loooong way: individually downloading the core package and its dependency packages. I am so happy to be able to play my multimedia files. I also installed these pacakges in my home pc which has Edubuntu but no internet connection.

My two OpenOffice presentations are ready and I will be conducting them on this laptop using Edubuntu.

---

### Post by rphil2008 on 2008-03-25
This thread's problem is SOLVED.

I copied the proxy settings and IP address from my XP desktop to the Edubuntu laptop. I transferred LAN cable from the desktop to the laptop. The trick is finding the correct dialog boxes in Edubuntu to put settings data in. They are---

1. System Administration> Network
2. Network Manager icon on the top of desktop> Manual configuration
3. Open Firefox> Preferences> Network 

You will need:
1. a working proxy address
2. a unique ip address
3. a username and password authenticated by windows network
4. subnet mask
5. gateway setting

---

### Post by Eiríkr on 2008-03-25
Good news then, good to read!  :D  Since your issue is resolved, please also mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

### Post by gkffjcs on 2008-03-25
just something you might not have considered, if you are making this presentation you'l probabily want to be connected to some sort of projector, or other similar device, test this first, because this might be a much more challenging problem to fix than the network. Also if there is no network connection on a system, then there really is no reason to worry about security updates anyway.

---

### Post by rphil2008 on 2008-03-26
Thanks for the head's up guys. Wil test that projector later. Presentation is 3 days from now and I have a backup plan if laptop-projector wont work. Now I know how to put SOLVED on this thread.

---

