---
title: "Zoom ADSL modem won't connect to internet"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by googlebytes on 2007-04-15
First, I have to say I am completely new to Ubuntu. I have been a Windows man. I have Edgy 6.1 installed. I am trying to configure my new Zoom X5v 5585 ADSL modem with an ethernet connection. I have followed the Zoom documentation and flashed the modem with both encapsulation settings (PPP) my DSL provider, Qwest, uses, but still cannot connect to the internet. I got the user name and password from Qwest and flashed with that. I followed the Zoom's manual instruction for DEBIAN to make sure the file "/etc/network/interfaces" contains the line: iface eth0 inet dhcp. My Edgy file already contained this line.

I also changed Firefox browser by typing "about:config" into the location bar and changing the default false setting of "network.dns.disableIPv6" to true. -- still no general internet connection, although it does seen to be able to communicate with the Zoom VOIP gateway console page.

My network setting is set for a wired connection with address DHCP. Is this right for PPP connection?
Please help. I'm sure I have some obscure setting incorrect somewhere.
Edit/Delete Message

---

### Post by googlebytes on 2007-04-15
Someone please help this NooB. So far the ethernet connection seems to at least allow me to communicate with the modem/router. If I connect my DSL line I get a solid Link light, and ADSL status is no longer down, but says Showtime - it is Showtime firmware version 3.52

The problem might be in the PPP status which is down. LAN status has an IP address and DHCP client has an IP address.

---

### Post by googlebytes on 2007-04-15
Maybe I need a driver for this modem?

I did the "sudo pppoeconf" command but it comes back with an apparent conflict with the pppoe process on the modem which I have set to one of Qwest's: PPPoA LLC. This modem is supposed to work with Debian, but so far I haven't found the secret. Can someone have mercy on this NooB? Maybe I have a conflict or something - I just don't know anything about Linux/Ubuntu.

---

### Post by googlebytes on 2007-04-16
Do I need a driver if I'm using a LAN connection? It also has USB capability, but I'm not using that. I have to imagine someone has had similar problems, but the help section has instructions for configuring Ubuntu, while this modem uses a gateway that is supposed to do most of the stuff the help section is talking about. Did I make a bad buy?  I really want to give Ubuntu a go, but I have to be able to access the internet in a reasonable fashion or I'll be off to  greener pastures. I can't spend days on stuff like this.

---

### Post by blackened on 2007-04-16
I'm sorry that no one has provided you any help so far, but please realize that not everyone checks this forum every day. It's only been 8 hours since your initial post, and it may take a few days or longer for someone with relevant knowledge to see your question and provide some direction. Unfortunately I am not that person, but I do want to emphasize the need for patience. You are not being ignored, your post is being read, and we all sympathize, especially considering that most of us have been in similar situations where hardware is concerned.

As to the problem at hand: is this an internal or external modem? I'm assuming it's external since you mentioned the status lights, but you never explicitly stated this.

---

### Post by googlebytes on 2007-04-16
Thanks for caring. Yeah, it's an external modem with VoiP. It has 4 LAN ports, and one 1.1 USB port, which I'm not planning on using - at least with Ubuntu. Obviously not wireless, which I figured would help. Has router, firewall, etc. I figured maybe someone will be able to help tomorrow.

---

### Post by kvonb on 2007-04-16
Does the modem do the ppp connection or does the computer have to do it?

If the modem has a username/password and a connect thing, then it will be the modem that connects and you simply connect through that.

Have a look at your ISP's instructions for connecting a Windows computer to their network, if it mentions that you have to create a dial-up connection, then you will need to setup pppoe.

It's quite easy, just open a terminal and type:

```
pppoeconf
```

It will search for your modem/router and if your ethernet connection is working properly it will tell you.

Just enter your username and password when asked, and if you want the connection to be on whenever you have your computer on, accept the option to activate at boot, otherwise you can install "Gpppon" afterwards, search for it in synaptic or type this in a terminal:

```
sudo apt-get install gpppon
```

That should have you up and running :)

---

### Post by googlebytes on 2007-04-16
The modem is supposed to be doing the connecting which is why I believe there might be a conflict or a missing setting somewhere. The help instructions here assume the computer is doing the connecting, but my modem is supposed to do it. It has a password input for it and all. But since I told Qwest it is not one of theirs - Actiontec - they won't help me with it -  they don't have the "tools".

Recap, Lan/ethernet connection seems to be good. DHCP seems to be good and has an assigned IP. PPP is down. I actually previously opened a terminal and typed  in pppoeconf, and Ubuntu told me to become  root before running this command. Sudo pppoeconf told me that pppoe process may already be running or couldn't be run for some reason I can't remember now. I assumed it was conflicting with the pppoe process on the modem. Now it seems I'm left with trying to work around the modem's pppoe or getting it to work.

---

### Post by kvonb on 2007-04-16
Can you access the modems config page?  If so then the basic connection between the computer and the modem would seem to be ok.

If you can, have a look to see if it has an IP, or maybe even a connection test page, most do.

Another thought I just had is your MTU.

Open a terminal and type:

ifconfig

See what the MTU is under eth0, it defaults to 1500, but it might need to be set lower.  Although this usually manifests in secure pages like hotmail.com, and prevents you from logging in.

Can you ping your modem?

If the IP of your computer is 192.168.0.2, then try pinging 192.168.0.1 or 192.168.0.255, the manual should tell you what port it defaults to.

Just work down the chain, first see if you can get to the modem from your computer, then see if you can get anywhere else, you can ring your ISP and ask them if you are connected, and if so, what your public IP is.

---

### Post by googlebytes on 2007-04-18
As I previously indicated, I can talk to the modem through the gateway. 

OK, I put the modem software on my XP machine, and I was online in practically 5 minutes. In fact I'm using the XP machine right now. So i know the PPP designation the Zoom manual gave me for Qwest is good, and that the password etc is good. The problem is in one of the settings on my Ubunu machine. Ubuntu will allow me to talk to the modem, but it is not set up correctly to go through to the internet - again the modem gateway says PPP is down.

Since no one seems to have the tools to help me with this problem, I am going to have to assume I need a driver or something I can't get - might have to abandon the Ubuntu machine.

---

### Post by googlebytes on 2007-04-19
How do you post resolved.

Well, for any of you following my toturous path, I am now visiting you on my Ubuntu machine.  YEAH!!!  It was apparently some kind of hardware initialization issue. After initializing the modem with my XP machine, I put my Ubuntu machine back on, and lo and behold, here I am!!!

Thanks to all who tried to help. I'm sure I'll be back again.... and again!

---

### Post by kvonb on 2007-04-19
>  OK, I put the modem software on my XP machine, and I was online in practically 5 minutes

Glad to hear you got online.

However, reading what you posted above makes me think that it's not a hardware or Linux issue.  If the modem doesn't work on Windows without installing that software, then I would say that the software is doing the connection.

Maybe try asking the modem manufacturer what that software does, and see if they can tell you how to connect from a Linux machine.

I still think that it is a PPPoE issue, and that software you install is the thing doing the actual connecting, like the Windows dial-up thing.

---

