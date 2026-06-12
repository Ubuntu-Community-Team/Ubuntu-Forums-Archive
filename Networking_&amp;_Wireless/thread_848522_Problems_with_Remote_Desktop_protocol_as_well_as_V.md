---
title: "Problems with Remote Desktop protocol as well as VNC"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by employeeno5 on 2008-07-03
Hi there.

So I've got two separate remote desktop access issues.

I've got 8.04 dual booting with Vista. In Vista I remote desktop to my office. I need to do this and if I can get it working in Ubuntu, it's byebye Vista for good (rock!). 

The way we do it here is pretty typical. I establish a VPN connection to the office server. Then I login using Windows Remote Desktop client. 
All that is required to do this in Vista is giving it the name of my desktop on the sever and my user name and password. Presto! It's like I'm there.

Now, in Ubuntu I have no problem logging into the sever via VPN.
However I cannot get the terminal server client to ever connect to my desktop.

I'm giving it the same information as the Windows client. The computers name "W07.*******.local" and then my user name and password. I'm telling to use RDPv5.
However it never connects. I can see there are more fields below these first three, but I don't know what if I need to fill them in or what I would put in them...

Second issue: I would like to be able, while at work, to connect via VNC to Ubuntu at home.
So as I sit here at work, the computer is fired up and logged on at home with the remote desktop settings on to allow for viewing and control of the desktop. The port is set to 5900. 

Back here at work I've installed tightVNC viewer to connect to it. I put in "my ip address":5900 and it never connects. 
What gives? 


I get the impression it's likely in both cases that I'm missing something simple. Any guesses? 

Any help or advice would be great. 
I've been googling and reading posts and wikis for the past two days (slow at work) and have not found anything helpful. In fact,everything I've read would point to me doing everything correctly. So I'm left at a loss and hoping you can help.

Thanks!

ps
is VNC the best solution from work to home? If I'm logged onto the office sever via VPN at home already, is there an easier way for me to open my home desktop here?

---

### Post by pytheas22 on 2008-07-03
> Back here at work I've installed tightVNC viewer to connect to it. I put in "my ip address":5900 and it never connects.
What gives? 

Is your home computer behind a proxy, like a wireless router or a switch?  If so, you need to configure the proxy to forward vnc connections on port 5900 to your Ubuntu computer.  Otherwise the packets are just dying at your proxy.

As for the inability to remote from home to work: you may want to run a vnc server on your machine at work and see if you can remote in from home via vnc.  That way you'll know whether you're just having problems with RDP, or if it's some other sort of issue.

It may also help for you to give RDP the IP address of your computer at work (if it's static) instead of the hostname.  Maybe there's some problem resolving it.

As for the p.s.: vnc is probably best.  ssh is safer and faster if you only want to connect to your home computer over the command-line, but it's not so good if you want to have the whole graphical desktop (ssh can do that, but it will be much slower than vnc, and possibly unbearably slow unless you have really fast speeds on both ends of the connection).

---

### Post by employeeno5 on 2008-07-04
Hello!

Thanks for the input.
I am using a wireless router here at home. I'll get into the admin page and see about configuring it forward the port. Thanks for that!

I'll try if I can get the VNC working, I'll see if that can work into the office as well.

Well, it the 4th, and I'm not planning on going back into the office anytime this weekend to try any of this out, but I'll let you know on Monday if I've had any luck.

Thanks so much again!

---

### Post by employeeno5 on 2008-07-09
Hello again!

I now have VNC running fine from my XP work computer so I can remotely use the Ubuntu rig back at my home. The issue was indeed simply setting my router to forward the ports to my computer.
Thank you again!

However, I still have no RDP working correctly from home to work. Again, the VPN connection to the server is fine, but I cannot get the terminal sever client to "resolve the host".
The computer's "full name" clearly isn't working. I tried your suggestion of using my computers ip, but the only one I can find is the server's ip. Every computer in the office spits up the same ip. If I have a more specific one for my desktop below the server's I cannot find where/how to determine it. 

I do have access to the server downstairs. Not exactly high security on the physical end. Browsing through it, all the information I can find relating back my desktop is just regarding my username on the network and the computer's workstation name. Nothing regarding another ip address

If anyone has any more ideas to help get that working, I'd be oh so grateful.

---

### Post by pytheas22 on 2008-07-09
I'm glad you got at least half of the problem solved.

Your computer at work must have a unique (unique on your network, at least) IP address; I don't know of any way that it could connect to the Internet otherwise.  If you type in Windows:
```

ipconfig
```

it should tell you what IP is assigned to the computer.  See if you can figure it out that way.  If the IP is local, however (e.g. 192.168.x.x or 10.0.x.x), it won't work.  But if each machine in your office has a unique IP on the Internet, it might help.

Also, did you get a chance to see if you can VNC from home to work?

---

### Post by inteluser on 2008-07-09
If you've successfuly set up a VPN connection to work, a local IP address to your work computer might in fact work; it's certainly worth a try.

---

### Post by pytheas22 on 2008-07-09
> If you've successfuly set up a VPN connection to work, a local IP address to your work computer might in fact work; it's certainly worth a try.

Yes, that's right; I wasn't imagining things correctly when I said it wouldn't.  Since you're connecting to a VPN first, it would work--I was forgetting the VPN part and thinking you were going directly to your work computer.

---

### Post by employeeno5 on 2008-07-09
Thank you for the "ipconfig" command.

It did in fact bring up my local ip. However I still cannot connect with the local ip when connected via VPN.
Now however, instead of saying it cannot resolve host, it is saying "no route to host".

I have not yet successfully managed VNC from home to work, however I have not yet tried. I keep forgetting to run a VNC server at work some night to try logging on.

Still no problems with the VPN though. 

Everything is still up and running fine in theory over at the office; I can still log right on through the remote desktop viewer in Windows.

Well. I give up for the evening unless anyone else has any new ideas. 
I'll try to remember to leave a VNC server running at work tomorrow and we'll see how that works.

Thanks again!

---

### Post by bushda on 2008-07-09
I'd be very cautious about using VNC in a corporate environment as it may violate your corporate security policy. VNC is a clear-text protocol, and using it could potentially allow some hacker in the middle to intercept anything you type. Passwords, usernames, sensitive information, etc. is all up for grabs by a hacker in the right place with tools like tcpdump or wireshark. This is less of a problem if you're traveling over a VPN from home to work, but if you're communicating from work to home over the public internet you're just asking for your info to be intercepted and used against you.

Instead I would suggest that you consider alternatives like the freenx server. That would tunnel your connection over ssh, which is a secure medium. I don't see the freenx server listed as an available package, so you'd need to Google for "NX server ubuntu hardy". That should point you in the right direction. 

As for your work to home connection, I assume that you can remote desktop from your home system to the work system fine in Windows. Is this true? If so, that eliminates the port being blocked on the firewall as a possibility. 

How do you know the vpn to work is functioning properly? Can you access other things on the work network by some other means? (Corporate intranet page via Firefox, corporate mail server, pinging devices on the other side, etc) If you can do that, then you have verified that your VPN is working. 

Did you try connecting to the remote system using the IP address instead of the name? In other words, if you go to my.system.local while you're at work and run ipconfig, it'll tell you what the ip for that system is. When you're at home, you can try connecting to that IP instead of my.system.local. If you find you can connect to the IP and not the address, then DNS is not working properly. This isn't the end of the world if you memorize the IP's you need to access. 

If you can answer those questions it'll help me further diagnose your problems.

---

### Post by employeeno5 on 2008-07-09
> As for your work to home connection, I assume that you can remote desktop from your home system to the work system fine in Windows. Is this true? If so, that eliminates the port being blocked on the firewall as a possibility.


Yes. The remote desktop works fine from Windows. 

> How do you know the vpn to work is functioning properly? Can you access other things on the work network by some other means? (Corporate intranet page via Firefox, corporate mail server, pinging devices on the other side, etc) If you can do that, then you have verified that your VPN is working.


The only way I've managed to tell it's working fine is that going to [http://192.168.100.1/](http://192.168.100.1/) takes me the page for the modem at work rather than the web admin. for my home router. We don't have any intranet pages or web apps at my company. Just databases for Quickbooks and Paradox. I'm not sure how I'd test my connection is working otherwise. Any advice there would be helpful.

> Did you try connecting to the remote system using the IP address instead of the name? In other words, if you go to my.system.local while you're at work and run ipconfig, it'll tell you what the ip for that system is. When you're at home, you can try connecting to that IP instead of my.system.local. If you find you can connect to the IP and not the address, then DNS is not working properly. This isn't the end of the world if you memorize the IP's you need to access.

I used "ipconfig" at work to bring up the local IP address of the computer. I've been trying that now instead of the computer's name. I still cannot connect, however it does respond differently. When it fails to connect using the computer's name is tells me that it "cannot resolve host". When I try using the IP it outputs "no route to host". 

I hope that's helpful. Thank you for the advice regarding VNC.

Because remoting to the office works in Windows it's not the end of the world. However, I would love to have it working in Linux. It's one of the only reasons I boot into Windows at all still, and certainly the only necessary reason. I'd love to get it off my back.

---

### Post by pytheas22 on 2008-07-09
> NC is a clear-text protocol, and using it could potentially allow some hacker in the middle to intercept anything you type.

There are plenty of well-known exploits against RDP too.  ssh and its extensions are pretty safe (provided you're patched up from the Debian ssh key fiasco a couple months back), but they're slowwwww in my experience for forwarding more than just a command prompt.  Is freenx fast enough to forward the whole desktop session at an acceptable speed?

In any case, if you only run a vnc session for a couple of seconds just to see if it works, the risk is pretty minimal.

I agree that if you can connect from home to work using Windows, then there are obviously no ports being blocked.  But I think it still wouldn't hurt to make sure that VNC works too, just to rule out other factors.  If VNC works, then it nails the problem down to the way that Ubuntu handles RDP, not a broader problem with Ubuntu.

Also, another test that would help isolate the source of the problem would be to try to connect over the terminal server client to a different Windows computer, like one in your house, if possible.  If that works, then you'd rule out bugs with the terminal server client in Ubuntu.

It may also help to try a different program to connect, like Gnome RDP, or to compile rdesktop (the backend to these programs, I think) from the latest stable source, in case there's a bug there that's preventing the connection.

By the way, couldn't you remote from work to home, and then over that connection, test home to work?  No need to remember to leave VNC running overnight :)

---

### Post by employeeno5 on 2008-07-09
I tried out Gnome RDP with identical results.
I might consider trying to compile rdesktop, but the current repositories do seem to work fine for most everyone, not to mention the fact every time I've attempted to compile anything from source I've completely failed (I still don't know what I've ever done wrong there; I followed instructions very carefully). 

I suppose I could VNC home and then VNC through there back to work just to check it out. I'll try it tomorrow. After that though I won't continue to use it.
The remoting home to Ubuntu is completely unnecessary. I just wanted to try it out. It is awfully fun to watch the girlfriend with the webcam and then scare the crap out of her by using Festival to make the computer talk to her.However, I don't need it; just wanted to check it out. 

It's the home to work telecommute I really need to use. 

Trying to get onto another Windows computer, particularly one on the same LAN sounds worth trying; however, I'm the only Windows computer in the house. I'll see if I can't arrange trying that somewhere else sometime soon though.

---

### Post by bushda on 2008-07-09
> **employeeno5 said:**
> 
The only way I've managed to tell it's working fine is that going to [http://192.168.100.1/](http://192.168.100.1/) takes me the page for the modem at work rather than the web admin. for my home router. We don't have any intranet pages or web apps at my company. Just databases for Quickbooks and Paradox. I'm not sure how I'd test my connection is working otherwise. Any advice there would be helpful.

Okay - there's a command that may work here, and it may not. It's called ping. The idea is that a packet is sent out and the remote machine replies to it. (Think of every movie you've ever watched with a submarine and how they sent out a ping and listened for the reply.) If no reply is received, then one of two things is happening: it's either being blocked by a firewall rule (fairly common) or it did not reach its intended destination. 

You can ping either by IP address or by hostname. Either way it's easy. Just type 

     ping *hostname*

Here's an example. I'm going to use ping with the -c switch to ping my router 5 times:

xxxxxx@yyyyyy:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.73 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.48 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.06 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 1.447/1.640/2.066/0.237 ms
xxxxxx@yyyyyy:~$ 

The results you see above indicates that it reached my remote router and the router replied. The time at the end indicates how long it took from the time my system sent the ping until it heard the reply back. 

> **employeeno5 said:**
> 
I used "ipconfig" at work to bring up the local IP address of the computer. I've been trying that now instead of the computer's name. I still cannot connect, however it does respond differently. When it fails to connect using the computer's name is tells me that it "cannot resolve host". When I try using the IP it outputs "no route to host". 


That's indicative of your system not being able to reach the remote system. 

Are you routing everything through your work network when you are connected via VPN, or only specific networks? Assuming you're using Network Manager to control your VPN, edit your VPN configuration and go to the last tab for Routing. Look to see if the box for Only Use VPN Connection For These Addresses is checked. If it is, are you routing the networks you have at work? If so, are you sure that the network blocks are correct? (When in doubt, ask "the network guy" at work for this info.)

I should also caution you that if your home network range is the same as the one you're connecting to at work, it could cause problems. For example, if you do an ifconfig at a command prompt in Ubuntu and see that your computer is using 192.168.1.101 and an ipconfig on the system at work shows that it is using 192.168.1.55, they're probably going to have issues getting to each other because they're both using the same network addressing. 

> **employeeno5 said:**
> 
I hope that's helpful. Thank you for the advice regarding VNC.


It is, and I hope the info I'm passing along helps you out too. 

No problem on the advice about VNC. I've got a masters in network security, and I work for a network security company. I have more than a few colleagues that'd beat me senseless if I advocated a clear text protocol for sensitive information like that. 

> **employeeno5 said:**
> Because remoting to the office works in Windows it's not the end of the world. However, I would love to have it working in Linux. It's one of the only reasons I boot into Windows at all still, and certainly the only necessary reason. I'd love to get it off my back.

Hang in there. We'll get you through it. :)

---

### Post by bushda on 2008-07-09
> **pytheas22 said:**
> Is freenx fast enough to forward the whole desktop session at an acceptable speed?

In my infrequent use of it, it's surprisingly fast. I wouldn't be watching videos over it, but I did try that to see how badly it'd fail. There's no 30 frames per second response from it, but when I connected from my desktop at work to my home system on a cable modem connection I was shocked at how quick the response was. 

> **pytheas22 said:**
> But I think it still wouldn't hurt to make sure that VNC works too, just to rule out other factors.


Again, while it may be a good test I strongly caution you to check with your corporate policies to make sure that running VNC (or telnet, or ftp, or any other clear text protocol) does not violate your corporate security policy. I have a very large former marine who is head of security at work. I hate to think what he'd do to me if I was caught with VNC, telnet, or ftp running on my system. 

...and whether you know it or not, there's a chance that your PC at work is scanned for this stuff regularly. Nessus is a great tool, and I know that every vlan we have at work, and every device on those vlans, is scanned regularly to make sure we're up to date on patches as well as scanned for rogue services like VNC. Be *VERY* careful there guys.

---

### Post by bushda on 2008-07-09
> **employeeno5 said:**
> It is awfully fun to watch the girlfriend with the webcam and then scare the crap out of her by using Festival to make the computer talk to her.

It's amusing how many of us have had that idea and executed it. 

If that's all you want to do, set up apache and a web cam app to view the webcam, and then ssh into the command line and use festival from there. I did that exact same thing years ago, and my wife would suddenly hear the computer talking dirty to her. Always amusing to watch her reaction.

---

### Post by employeeno5 on 2008-07-10
OK, so let's see where we're at today.

I'm pinging the work server just fine when connected via VPN.
No packages lost.



> Are you routing everything through your work network when you are connected via VPN, or only specific networks? Assuming you're using Network Manager to control your VPN, edit your VPN configuration and go to the last tab for Routing. Look to see if the box for Only Use VPN Connection For These Addresses is checked. If it is, are you routing the networks you have at work? If so, are you sure that the network blocks are correct? (When in doubt, ask "the network guy" at work for this info.)

I should also caution you that if your home network range is the same as the one you're connecting to at work, it could cause problems. For example, if you do an ifconfig at a command prompt in Ubuntu and see that your computer is using 192.168.1.101 and an ipconfig on the system at work shows that it is using 192.168.1.55, they're probably going to have issues getting to each other because they're both using the same network addressing.

Now as far as the VPN settings go, I do not have the option you're speaking of checked off and I do not know what to put in there. We don't have a network guy at work. We have a company with a guy on call for when we have problems and he does a monthly check in. About six months ago while he was fixing something with the virus software on my desktop, I mentioned that I had started using Linux at home as my desktop operating system. He made a face that I can only describe as a sneer and said, "Why would you do that?"
So, I don't know how much help I'm going to get from him on this front. When I first started remoting in I asked him what I needed to do to get it running and rather than explaining it to me or sending me some instructions he insisted it was best if I just bring in my laptop and let him do it (on Windows that is, naturally, or we wouldn't be having this conversation). 
He also was terribly upset to find that I'd moved the shortcuts in my start menu into a sane hierarchy (i.e., instead of having separate folders for Firefox, ie, pidgin, etc. I moved all of their folders under one called "internet". Apparently this fit of rational organization through him off his game.)
All of that said. I have full physical access to the server and there is no security policy to violate. In fact, I've had to get in there myself more than once and use a little Google, the little I already know, and trial and error to get certain things working again when our "network guy" wasn't available. 
Also, my father own the company. He owns the server. I have permission. So if it doesn't make a security experts head spin too much, I can hop on the server and locate this information with a little guidance, and you need not worry about the moral implications of it, just the practical ones. 
Of the twenty five people at the company I know the most about computers in general (I'm also by far the youngest, surprise surprise) so even though this thread exposes a large amount of ignorance on my part regarding anything network related, everyone else in the company looks at me to be "computer guy" when real computer guy isn't around.

So, anything I learn here is probably good for the company in general what with Crabby McWindows frequently unavailable.  

Regarding complications that could arise from the local IPs of the two machines being similar; you may also be onto sometime there. My machine's individual IP under the home server is only one number different from my workstation's local IP under the office server in the exact same manner you presented in your above example. Forgive me if my terminology is wrong or misleading. I'm don't know the correct terms and I'm not sure how to make myself more clear.

So, that's where I'm at. I've got solid pings, no clue what network blocks are (but access to them), similar IP addresses on both machines, a cranky once-a-month-IT-guy who doesn't like Linux and a girlfriend who is now afraid to be alone in the room with my talking laptop. 

Thanks again. Though I'm not connecting yet, I'm learning a lot and enjoying the conversation. It's very much appreciated. 


These forums are the best.

---

### Post by bushda on 2008-07-12
> **employeeno5 said:**
> OK, so let's see where we're at today.

First off - sorry to take a few days to get back to you. I'm traveling for business and this fell through the cracks. You have my most sincere apologies for my leaving you hanging. 

> **employeeno5 said:**
> 
I'm pinging the work server just fine when connected via VPN.
No packages lost.


That's good! That means that your system can get to the remote server when your VPN is connected. I have to admit that I'm surprised though because before your messages about no route to host indicated to me that it wasn't that. 

 > **employeeno5 said:**
> Now as far as the VPN settings go, I do not have the option you're speaking of checked off and I do not know what to put in there. 


When in doubt, leave it unchecked. What happens in that case is that all traffic is routed through the remote connection instead of just select traffic based on the networks you define. The benefit is all traffic should get to where it needs to go on your work network. The bad news is that ANYTHING you check out on the internet now goes through your work connection. In other words, if you wouldn't look at it on your PC at work, don't look at it when connected through work. 

> **employeeno5 said:**
> We don't have a network guy at work. We have a company with a guy on call for when we have problems and he does a monthly check in. About six months ago while he was fixing something with the virus software on my desktop, I mentioned that I had started using Linux at home as my desktop operating system. He made a face that I can only describe as a sneer and said, "Why would you do that?"


Some people aren't open minded and have decided to keep shoveling their hard earned dollars to Microsoft and other software companies. Personally I prefer Linux. To each their own. 

> **employeeno5 said:**
> He also was terribly upset to find that I'd moved the shortcuts in my start menu into a sane hierarchy (i.e., instead of having separate folders for Firefox, ie, pidgin, etc. I moved all of their folders under one called "internet". Apparently this fit of rational organization through him off his game.)


Good luck. Sounds like you're better off asking in forums like this for help than running to him. I know his kind well. 

> **employeeno5 said:**
>  All of that said. I have full physical access to the server and there is no security policy to violate. In fact, I've had to get in there myself more than once and use a little Google, the little I already know, and trial and error to get certain things working again when our "network guy" wasn't available. 


Okay. Sounds like you'll have access to do whatever is necessary to make this work then. 

> **employeeno5 said:**
> Also, my father own the company. He owns the server. I have permission. So if it doesn't make a security experts head spin too much, I can hop on the server and locate this information with a little guidance, and you need not worry about the moral implications of it, just the practical ones. 


In that case, it might be time to consider using VNC to see if it works using that approach. I would specifically recommend TightVNC because the compression will improve the speed at which it will work over a remote connection. [http://www.tightvnc.com/](http://www.tightvnc.com/)

Obviously you should never, ever expose that externally. If you do that you're asking for trouble. 

> **employeeno5 said:**
>  Of the twenty five people at the company I know the most about computers in general (I'm also by far the youngest, surprise surprise) so even though this thread exposes a large amount of ignorance on my part regarding anything network related, everyone else in the company looks at me to be "computer guy" when real computer guy isn't around.


In my experience it's been those that thought they knew something and forged ahead that have made my life miserable. Those that know their limitations and are not afraid to ask for guidance, like yourself, I hold in high esteem. You're a rare breed my friend. :)

> **employeeno5 said:**
>  Regarding complications that could arise from the local IPs of the two machines being similar; you may also be onto sometime there. My machine's individual IP under the home server is only one number different from my workstation's local IP under the office server in the exact same manner you presented in your above example. Forgive me if my terminology is wrong or misleading. I'm don't know the correct terms and I'm not sure how to make myself more clear.


Okay, so at home you're using something like 192.168.1.101 for your PC and at work you're using something like 192.168.1.102 for your PC? That could be a problem, but with routing all traffic through the VPN it shouldn't be a problem. Still, changing your local IP range on your home PC network might be beneficial. If you can give me examples of each I can guide you on what to replace them with. (Feel free to private message me if you don't want to post them here.) 

> **employeeno5 said:**
>  So, that's where I'm at. I've got solid pings, no clue what network blocks are (but access to them), similar IP addresses on both machines, a cranky once-a-month-IT-guy who doesn't like Linux and a girlfriend who is now afraid to be alone in the room with my talking laptop. 

Thanks again. Though I'm not connecting yet, I'm learning a lot and enjoying the conversation. It's very much appreciated. 


The fact that you're scaring your girlfriend by messing with festival is a good sign. I enjoy how Linux let's me tinker with things, and that's a lot of my attraction to it. Keep that curiosity going. 

> **employeeno5 said:**
> 
These forums are the best.

Glad you feel that way, and I'm glad to help. I still feel guilty that I took a few days to get back to you though.

---

