---
title: "[SOLVED] Help sharing internet with xp please!!!!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by lewbram on 2008-12-16
Hi,
I have been at this for days and still cannot figure it out. I have a desktop running ubuntu and a laptop on xp. I wish to share files and Internet with the laptop. 

I have everything plugged in and xp is saying,
" network did not assign a network address to the computer"

can anybody please help me with this???

I am very new to linux!

---

### Post by Michael.Godawski on 2008-12-16
hi lewbram,
you need the application samba to share files with a windows machine.
Have a look at:

[LIST]
[*][https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[/LIST]
and report back when you hit the wall:p.

---

### Post by Tatty on 2008-12-16
How are you connecting your network?  Do you have a router that you are connecting all your devices to?

---

### Post by lewbram on 2008-12-16
hey thanks for replying, 
I have installed samba and to be honest I think i am getting inti a bit of mess with this. The problem is i don't even know if the computers are networked properly?

How do i know if ubuntu can see xp and vice verser?

---

### Post by lewbram on 2008-12-16
hey, 
yep I have a router internet goes into the router and then from there to each computer

---

### Post by Tatty on 2008-12-16
> **lewbram said:**
> I have everything plugged in and xp is saying,
" network did not assign a network address to the computer"

When are you getting this message in XP?  It sounds like a problem with XP rather than Ubuntu.

In windows open a command prompt and run ipconfig - see if you have been assigned an ip address.  It will probably be something like 192.168.X.X

---

### Post by lewbram on 2008-12-16
it says autoconfiguration ip address 169.254.29.41

---

### Post by BUNAC on 2008-12-16
If XP says it has not been assigned a network address then it is looking for one but not found one.

You either need to...

1. Assign IP addresses automatically using DHCP on your Unix box

or

2. Manually enter static IP addresses into all of the systems involved.

Try this....

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables))

Hope that helps.

---

### Post by Tatty on 2008-12-16
> **BUNAC said:**
> If XP says it has not been assigned a network address then it is looking for one but not found one.

You either need to...

1. Assign IP addresses automatically using DHCP on your Unix box

or

2. Manually enter static IP addresses into all of the systems involved.

Try this....

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables))

Hope that helps.

His router should be dealing with the DHCP.

Try requesting a new IP address in XP. i dont have a windows machine to hand to check, but you need to right click on an icon somewhere which represents your connection and then get it to reconnect.  Or something like that, sorry i cant be more specific.

---

### Post by lewbram on 2008-12-16
I have tried to request another ip by going repair connection but get the same message.   

am i right to have the internet from the cable modem going stright into the router or should that go to the desk top ?

---

### Post by clive littlewood on 2008-12-16
Hi

Try creating a file in your documents to use for shareing.

Right click on this file and click shared file option

If you have samba installed then the file will be given shared status, if not it will offer to install Samba for you.

Go into XP and click on networks, your Ubuntu comp. should now be showing.

Before any transfers can be made you have to enter your user name and or password.

Hope that does it

Clive

---

### Post by lewbram on 2008-12-16
hey thanks I have just tried what you said but nothing, I think that the two computers do not see each other, do you know how i can test this?

---

### Post by stevoo on 2008-12-16
we need to fix you internet first. 

If you can look behind windowz, the ethernet port should be lighting some light on the xp machine and on your router. Are those there ? 

Try shutting down both machines, and start up only xp. See if you get another ip different from 169. . . . ( means you do not get an ip ) 

If still it is 169 shut down and connect the ethernet wire that goes into your laptop. Startup you machine and see if you get an ip then. 

Report back when you have done this.


We need to make your xp to get internet first !

---

### Post by lewbram on 2008-12-16
hey just tried that I canget internet on the  xp lap top if it plugged directly into internet and internet works through the router on the ubuntu. 

lap top wont connect through the router though!

---

### Post by redseventyseven on 2008-12-16
> **lewbram said:**
> I have tried to request another ip by going repair connection but get the same message.   

am i right to have the internet from the cable modem going stright into the router or should that go to the desk top ?

Ah. I think this might be your problem.

The way that modems and routers interact with each other is not standardized. You need to have the right type of router to take a connection to the internet from a cable modem and distribute it to your pc's.

I speak from experience - when I moved house I changed from having an ADSL connection to cable, and had to buy new hardware because my ADSL modem/router didn't work with the cable connection.

You might be ok though - on the back of your router box, is there a specific socket designated for "Cable modem input" (or something similar), or are you plugging the modem into one of the regular ethernet sockets? If it's the former, try resetting the cable modem. If it's the latter, then you have problems.

Most ISPs only allow you to have one IP address connected directly to the internet at any one time. What the router does is essentially act as a middleman. It's basically a tiny computer with one specific job to do. It takes the internet connection from your ISP, so that as far as the ISP is concerned, it's only allocating one IP address through your connection. The router then assigns a different set of IP addresses to the individual computers connected to it (either wired or wirelessly).

If you don't have the right sort of router, then essentially the modem connection is bypassing the small computer inside the router, and connecting directly to the first computer it sees - which will be the first computer you plugged into the router box (which I'm guessing is your Ubuntu machine). The ISP assigns the IP address to that machine, and not to the router. When another computer (in your case your XP machine) is plugged in, and starts asking the ISP for a second IP address, the ISP complains and the address is not assigned.

You can test to see if this is happening by following these instructions:

1. Turn off the computer for which the connection is working, and unplug its cable from the router. Turn off the other computer but leave its ethernet cable plugged in.

2. Reset the cable modem (there may be a reset button on it, or you might have to switch it off and on again at the mains). This should make it "lose its memory" as to which computer it had assigned an IP address to.

3. Once the cable modem has been reset, turn the computer which wasn't able to connect to the internet back on. Try to connect now.

4. If that succeeds, plug the ethernet cable from the computer that was originally connected to the internet back into the router. Try to connect to the internet from this computer now.

If you can effectively change which machine is able to connect, then I'd suggest going out and buying the right hardware. Sounds like your sharing issues are nothing to do with Ubuntu (or XP for that matter) - you'd see the same effect regardless of what OS's were on what computers.

---

### Post by lewbram on 2008-12-16
Thanks for that explaination, I really think i understand it a little better, I will give it ago now. The router is an old freebie! and it does not state anything about cable connections just 5 identical prots at the back. I will try resetting it now! 

back in ten!!!!!!

thanks again

---

### Post by redseventyseven on 2008-12-16
No problem.

Unfortunately it sounds (from the description) like you haven't got the right sort of router.

What's the manufacturer and model number of the router? Can you google it and post a link to the tech-specs (either from the manufacturer's website or from a shop)?

Fortunately, routers are not as pricey as they once were and you can probably pick one up for around £20. Just make sure to read the tech-specs and ensure that it's the right sort!

---

### Post by stevoo on 2008-12-16
or call your ISP.. 

mine used to allow only one computer to be connected on there router. The rest wouldnt work. 

If you can call them and confirm that the router can act as a router then the problem would lie with in XP

---

### Post by lewbram on 2008-12-16
it is a netgear GS605

could you recommend a router to use? 

maybe santa will bring me one!

---

### Post by stevoo on 2008-12-16
Well, you should be ok with that given router.

I dont think you need a new one. 

CAre you sure that the XP machine has a working ethernet card ? 
Maybe the problem lies there !

---

### Post by lewbram on 2008-12-16
the internet works fine straight into the laptop and works through the router when the modem is reset?

what would you suggest?

---

### Post by stevoo on 2008-12-16
so does it work on both now ? 

Or still no internet on XP

---

### Post by lewbram on 2008-12-16
nope not working

internet on ubuntu fine but xp says limited or no connectivity still

---

### Post by stevoo on 2008-12-16
two possibilities .... 
1 ) Either there is something wrong with the router and you cant share internet.
2 ) Something is wrong in the setting on Xp and doesnt give you an ip.

...... 
*bump* ... cant really tell from here. 
My best guess get a friedn with a laptop and try and connect him with a wire and see if he working :) 
That will rule or enforce possibility 1.

---

### Post by lewbram on 2008-12-16
cheers I will give it a go, can't afford anymore time on it today but I will let you know how it goes!

Thanks again

---

### Post by redseventyseven on 2008-12-17
> **stevoo said:**
> Well, you should be ok with that given router.

I dont think you need a new one. 

CAre you sure that the XP machine has a working ethernet card ? 
Maybe the problem lies there !

Sorry to contradict you, stevoo, but I've just looked up a Netgear GS605 ([http://www.netgear.co.uk/ethernet_network_switch_gs605.php](http://www.netgear.co.uk/ethernet_network_switch_gs605.php)) and I'm certain that it *is not* an internet router. It's a network switch box. Unfortunately it can be confusing because they both look similar on the outside. The difference is on the inside of the box.

The difference is that a network switch box doesn't have that tiny computer inside which acts as middleman (see post #15 for an explanation). It's simply a device for physically connecting ethernet cables together, with no clever device on the inside for handling the incoming internet connection and distributing it properly. So your connection from your ISP is going straight to the first machine it sees, and the ISP complains when a second computer asks it for an IP address.

I'm guessing (as your profile says you're from London, and you're using cable internet) that your ISP is Virgin Media - it's the same as the one I use. I can confirm that they only allow one computer to be connected directly to the modem at once ([http://www.virginmedia.com/help/broadband/using/connect-new.php](http://www.virginmedia.com/help/broadband/using/connect-new.php)). As I said before, I had the same problem when I first started using Virgin Media, and buying a proper router was unfortunately the only way of solving the problem.

Hope this helps!

---

