---
title: "Remote access Windows XP from Ubuntu"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by itsols on 2010-06-08
Hello everyone!

I'd like to know if it is possible to access my office computer from home using my laptop.

Here's what I have (and don't have) :)

1. Home:Ubuntu 10.04 LTS

2. Office: Windows XP Professional.

3. Neither of these machines have fixed EXTERNAL IPs.

4. Both use static IPs on the local LANs.

Any advice is highly valued.
Thank you!

---

### Post by Sef on 2010-06-08
If you are working for a company, do you have permission to access Windows remotely?

---

### Post by itsols on 2010-06-08
Yes, Sef, I do have permission. In fact It's the college which I teach in. Here's more info of my requirement.

At school we have a LAN.
I have also setup an Ubuntu 8.04 server in it.
I need to get to the Windows box so that I can run FF and access phpmyadmin on the server.

So today I tried (while at work) running Remote desktop on Windows and it created some sort of file and stated I should mail it to the one making the remote access (I believe it's me). But I got home and retrieved that file and it contains some lines with some IP numbers, XML, etc... Makes no sense to me.

So the bottom line - I need to access the work machine, mainly Windows XP, and then get to my server from it, while staying at home.

Once again, my home unit is Ubuntu 10.04.

Thank you for your time!

---

### Post by mbzn on 2010-06-08
I don't know much about networking but i think you should look into VPN, as far as i know, if set up correctly the pc's is as good as next to each other on a home network.

Hope this helps

---

### Post by BbUiDgZ on 2010-06-08
The file you were asked to send was a "remote assistance" file. You want to use remote desktop via terminal services. You might want to look the [window xp documentation for that](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)


I do exactly what your looking for.
I connect to our pptp server using the gnome network manaager's pptp applet and then use the terminal services client to "RDP" into my works machine (did have winxp now has win7 both work fine)

you will need some sort of access to your works lan from outside
permission to use RDP on your works system. Most MS domain enviroments will have this disabled via group policy. I happen to be lucky (or unlucky depending how u look at it) as i set the policies for our MS domain and implemented our pptp VPN. I would think your domain admin will have a pptp server running and would think the domain admin would give you access if you have a case for it.

---

### Post by itsols on 2010-06-08
Thank you everyone for all your suggestions and especially BbUiDgZ for sharing your last experiences. I hope you understand that this is my situation:

1. Neither work place nor home has static external IP. So how can I connect from home to the remote network?

2. I don't have a Win network at work. It's just a single Ubuntu box. And the WinXP box is on the work LAN.

3. Of course they have static IPs for internal use.

So to start, how do I make the first connection either to the XP box or to the remote Ubuntu server?

Thank you!

---

### Post by Paddy Landau on 2010-06-08
I access my father's Windows XP and Vista machines from Ubuntu using the excellent [LogMeIn]("http://www.logmein.com/").

For simple use (and it really is good), LogMeIn is completely free.

If you need the fancier features, you can get its inexpensive paid-for version.

---

### Post by rockoprem on 2010-06-08
The solution lies in leaving your office computer on and noting down its ip address for that session and then connecting to it with vnc or ssh from home. A detailed description is given in the following link.

[http://ask-leo.com/how_can_i_connect_to_my_home_computer_from_work.html](http://ask-leo.com/how_can_i_connect_to_my_home_computer_from_work.html)

---

### Post by Paddy Landau on 2010-06-08
> **rockoprem said:**
> The solution lies in leaving your office computer on and noting down its ip address for that session and then connecting to it with vnc or ssh from home.
The IP address would be a local one behind the company's router. That won't work. (I know, I've tried!) You need something that will punch through the router and firewall, and applications like [LogMeIn]("http://www.logmein.com/") or [Yuuguu]("http://www.yuuguu.com/") will do that (unless the company's firewall is extremely restrictive).

I recommend LogMeIn, because it's highly flexible and can even wake up a sleeping remote computer if the BIOS and router both allow.

---

### Post by rockoprem on 2010-06-08
Hmmm... I would simply open up port 3389 (I think this is what Windows uses for Remote Desktop:confused:) or some other and connect to it via the router's ip. 
LogMein sounds really cool, but is it an open source software? Also, which protocol do they use? I didn't get any information on their site.

---

### Post by itsols on 2010-06-08
Yes rockoprem, LEO's article seems pretty clear and comprehensive. I ought to try out his port forwarding thing. I just have some other concerns too:

1. Forwarding the port - is it safe?
2. About LogMeIn, can it be trusted?

I've also worked once with TeamViewer but that meant Windows. But I'm on Ubuntu at home.

Should try out all these things.

Thank you all!

---

### Post by Paddy Landau on 2010-06-08
> **rockoprem said:**
> LogMein sounds really cool, but is it an open source software? Also, which protocol do they use?
Yes, it is cool. I've been so impressed by it. It has let me easily support my father, who lives on a different continent 6,000 miles away.

No, it's proprietary. For the features it offers, it needs to be; it must have cost a packet to develop.

I wouldn't have the foggiest idea about protocols, sorry. Email LogMeIn and ask, if it's important to you.

---

### Post by Paddy Landau on 2010-06-08
> **itsols said:**
> 1. Forwarding the port - is it safe?
Not sure. Would your college allow you to, though?
> **itsols said:**
>  2. About LogMeIn, can it be trusted?
Why not? Its income depends on its reputation. What would it do... spy on millions of users in case one of them is dealing in state secrets that it could sell to rogue countries? :lol: The manpower would be too great and too expensive.

BTW, please mark the thread as solved if you've found your answer.

---

### Post by rockoprem on 2010-06-08
Yes, port forwarding is a safe option. It is safer, in fact, if you open the non-conventional ports. Eg: Windows uses 3389 as default remote desktop port. So, if you open 3390 or 3391, it is much better. Also, if you have a firewall on your office Windows computer, make sure you allow these ports to remote desktop. As long as you have a strong password, opening the ports is a safe option. I would also suggest you to open a normal user (non administrator) account on your windows computer and remote desktop by logging into this account only and not to the administrator account. 
For personal purposes, I would probably use LogmeIn, but not to remote desktop to my office. I am not much bothered about them going through my files (which I think they do not), but I also don't want a log file or  a comment in all my files which says "This file has been accessed with LogmeIn (c)2010". Nevertheless, nice to know about possible options. :p

---

### Post by itsols on 2010-06-08
Yes, I think I'm pretty convinced that opening the port and forwarding it to my home PC is kind of safe.

I've also heard of XRDP on Ubuntu. Would you folks happen to know about it compared to RDP?

---

### Post by rockoprem on 2010-06-08
They are essentially the same. xrdp provides a graphical interface. Remote desktop*ing* from ubuntu is really easy. You just need to install rdesktop by typing ```
sudo apt-get install rdesktop
```

You then just run the remote desktop from Applications-Internet.

---

### Post by YesWeCan on 2010-06-08
If you want to do Network Neighbourhood and other Microsoft networking things with the XP machine you may want to consider openVPN. All free.

[http://www.openvpn.net/index.php/open-source/documentation.html](http://www.openvpn.net/index.php/open-source/documentation.html)

I have a Ubuntu server connected to a Windows network. I can remotely connect to the server via an encrypted VPN tunnel. All the Microsoft networking stuff works. Rock solid.

You would need to:
Install openVPN on the Ubuntu machine and run a tap tunnel, bridged with the LAN the XP PC is on. This is very easy.
Install openVPN on your home machine (can be Windows) and run a tap client.

There are a couple of more details but its pretty easy. 
Email me if you want more info.
Brian

---

