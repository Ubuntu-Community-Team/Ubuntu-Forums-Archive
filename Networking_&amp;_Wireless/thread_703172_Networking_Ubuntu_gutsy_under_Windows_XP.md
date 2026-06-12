---
title: "Networking Ubuntu gutsy under Windows XP?"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Stephen Winters on 2008-02-21
[SIZE="2"]Hi,
I have been searching the Internet and searching the UbuntuForums and haven't been able to find easy to use instructions of setting up a network between Ubuntu 7.10 and Windows XP. 

I'm trying to network a 700 Mhz Celeron computer running Ubuntu 7.10 to a 1.8 Gig computer running Windows XP home edition. The windows computer is our main computer. I've been using computers since 1986, but I'm a new Ubuntu/linux user. I've only been using Ubuntu for less than a month. I"ve never used Linux before this. I'm really please with Ubuntu, but I have a lot to learn, especially about networking.

The windows computer has our printer and internet hooked up to it. I want to use the Windows XP computer as the Internet gateway. All the other computers will be hooked up to the router (Have a Linksys  model BEFSR41 Etherfast Cabel/DSL Router with 4 port switch.), and then will go through the Windows XP computer to the Internet.

This is what I want to be able to do with the network:
[LIST=1]
[*]Share files between all  the computers
[*]All the computers would use the printer hooked up to the Windows XP Computer
[*]All computers would be able to connect to the Internet through the Windows XP computers, using Internet connection sharing
[/LIST]
I realize that I could hook up the Internet directly to the router and then all the computers would be hooked up directly to the the Internet. However, the Networking instructions of the Windows XP don't recommend this way because it would exposes all my files to anyone on the Internet. I certainly don't want that to happen, so I don't want to do that.

After I get the network working between these two computers, I have a couple other computers I want to add to the network. (One will be Windows 98 SE, and the others will be either Win 98, or Xubuntu.)

**_Could someone give me baby-steps_** of how to set up this network, or tell me where to find a good tutorial on this? I've never set up a network before.[/SIZE]

Thanks for any help,

Best Wishes,
Stephen
**Winters Sewing**
[http://www.winterssewing.com]("http://www.winterssewing.com")

---

### Post by HereInOz on 2008-02-21
Hi Stephen,

Have you checked out this:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

or this:

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

Personally I think it is a bad idea to use the XP machine as the Internet gateway.  If the Linksys can connect you to the Internet, then let it do so and put all your computers through it.  The simple fact that the Linksys router will use NAT to connect your machines to the Internet gives you a high level of security in any case, because no one can see the computers behind the router unless you open ports to allow it.  

Frankly, I would rather have a Linksys router facing the internet than an XP box, but maybe that is just me.

---

### Post by Stephen Winters on 2008-02-21
> **HereInOz said:**
> Hi Stephen,
Have you checked out this:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
or this:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)


Hi HereInOz,
   Thank you for giving me these links. I had seen the top one, but don't think I've see the bottom one. These are quite a bit for me to wade through, but I"m trying.

> **HereInOz said:**
> 
Personally I think it is a bad idea to use the XP machine as the Internet gateway.

The reason I'm using the XP machine for the Internet gateway is because the computer is 2 1/2 time faster than the Ubuntu computer. 

> **HereInOz said:**
> 
 If the Linksys can connect you to the Internet, then let it do so and put all your computers through it.  The simple fact that the Linksys router will use NAT to connect your machines to the Internet gives you a high level of security in any case, because no one can see the computers behind the router unless you open ports to allow it.  

What is NAT? I don't know or understand what this is or how to use it?

If I connected all the computers directly to the Internet through the Linksys router, how would I share files and share printers between my computers without opening up all my files to be accessible to anyone on the Internet? The Windows XP help system caution against this setup because, it says, all my files would be accessible to anyone on the Internet.

I don't know enough about networking to know what else to do.

> **HereInOz said:**
>  Frankly, I would rather have a Linksys router facing the internet than an XP box
I don't dispute you opinion, I am no expert on computer systems or Networking. I'm just very cautious (I'm made more than my share of mistakes in the past). 

Thanks for your advice. I'll see what I can do in following the instructions (if I can understand them) on the links you provided to me.:p

Best Wishes,
Stephen

---

### Post by freebeer on 2008-02-21
Ok.. Windows help isn't being completely true.  They're assuming that you don't have a router when they're saying your network will be exposed.  With a router, your internal network has a different IP address than your Internet Address.  This, essentially is what NAT (Network Address Translation) is.  Your router acts as a hardware firewall and is far more reliable, IMHO, than Window's firewall.

By connecting your two boxes directly to the router you will have a LAN.  If your printer also supports connection via LAN, that's how I would set it up.  A direct connection will also be faster, since you don't need to tap into the XP box's CPU, memory and LAN card in order for your Ubuntu box to communicate with the world (or your printer, if you can set it up as I've suggested above.

A thing to take note about XP Home version, when you're setting up Samba on the Ubuntu box (I think it's already installed in 7.10, btw) is that XP Home cannot join a domain.  It's been deliberately disabled so that folks who do need to connect to a domain have to buy the more expensive Pro version.

That is NOT to say that XP Home can't share data on the Ubuntu box.  It can (I have such a setup at home) but it does make it harder for you to setup/use in my experience.  (You have to log in after every reboot, etc.  Niggly stuff, but annoying just the same.

---

### Post by Stephen Winters on 2008-02-23
Hi Freebeer,
   Thank you so much for taking the time to explain some things to me. I'm very new to Linux, and I also know very little about networking.  You response has helped me to understand a few things a little better. I do have some questions.

> **freebeer said:**
> Ok.. Windows help isn't being completely true.  They're assuming that you don't have a router when they're saying your network will be exposed.  With a router, your internal network has a different IP address than your Internet Address.  This, essentially is what NAT (Network Address Translation) is. Your router acts as a hardware firewall and is far more reliable, IMHO, than Window's firewall. 

Could you point me to someplace where this is explained in more detail? I had never heard about this before (which isn't surprising since I have looked into this before). The part I'd really like to see in writing is where it talks about the router having a different IP address than my internet address, and how that would protect my computers better.....

For the time being I've connected both computers to the router, which is connected directly to the Internet. But they are not yet networked together. At this point the router is acting like a dual plugin so that both computers can share the same internet connection. That is all I know how to do at the moment.

If your way works better, I'm OK, with it, it's just a new thought for me and, because it seems to go against the Windows XP network instructions. I need some professional verification to put my mind at ease. It could very well be that I'm not understanding this well enough. I just don't want to open up my computer


> **freebeer said:**
>  By connecting your two boxes directly to the router you will have a LAN.  If your printer also supports connection via LAN, that's how I would set it up.

I don't know to to create the LAN, but will look more into it as time allows. Since my last message I have spent hours searching on the Internet, experimenting, trying to set up a network. I've also read through and tried to follow the instructions to Samba that you linked to, , but to this point, haven't been successful. However, I think I've found some useful information, see below.

 > **freebeer said:**
> A direct connection will also be faster, since you don't need to tap into the XP box's CPU, memory and LAN card in order for your Ubuntu box to communicate with the world (or your printer, if you can set it up as I've suggested above.

Thanks for the info.  

> **freebeer said:**
>  A thing to take note about XP Home version, when you're setting up Samba on the Ubuntu box (I think it's already installed in 7.10, btw)...... 

As mentioned above, I've already spent hours trying to figure Samba and networking out, but I don't understand it yet. But will keep trying...

> **freebeer said:**
>  ...................... is that XP Home cannot join a domain.  It's been deliberately disabled so that folks who do need to connect to a domain have to buy the more expensive Pro version.

Thanks Freebeer. This was some very useful information. You gave me a reason why Windows XP home edition has an issue with networking. This gave me something to look for.  I won't have time to work on this again for a while, so I want to post what I've found so far so that it will all be together. And, maybe, someone else may be able to use it or to give me more information, advice, etc.

**[SIZE=4]Windows XP Home Edition Joining a Domain[/SIZE]**
Part of the time I was looking for a solution to the "Windows XP Home edition can't join a Domain" issue. From searching the Internet it looks like a number of people have had the same problem. It also looks like there might be some  solutions, which I've listed below. I'm listing the follow Windows XP Home Edition Domain info with the hopes that someone, who is more knowledgeable than me, can figure it out and make it work. 

[B][SIZE=3] Two Possible Alternatives
[/SIZE][/B] >  The option to join a domain is not available on an xp machine, but here are TWO alternatives:
                                             [CENTER]NOTE: 
                **Windows XP Home Edition is not designed to join domains; only workgroups**.[/CENTER]
                #1:
                Visit [http://vowe.net/archives/001639.html](http://vowe.net/archives/001639.html) and download  the free and widely available Xteq X-Setup  6.1 utility. You can then join domains with WinXP Home Edition. 
                #2
                1. Log into XP Home using a local computer account that does not have a password. 
                2.                  Open My Computer, click the Tools menu, then click Map Network Drive.
                3.                  Select a folder on your network by clicking on the Browse button. 
                4.                  After selecting the folder, click on the different user name link on the page.                
5. In the Connect As dialog box, for user name enter domainx\user (where domainx is the domain you want to connect to).
              6.  Enter your domain user password and then click OK. 
                7.                  Check the Reconnect at login box and press Finish. 
8. Now when you start up the computer go to My Computer and double click on the networked drive. This will cause XP to send the credentials to the Domain and allows you to access the drive. 
9.                Now you can access files and folders throughout the domain without having to your user name and password.
Source:  [http://www.staffkit.com/resources/join_domain_windows_xp_home.htm](http://www.staffkit.com/resources/join_domain_windows_xp_home.htm)
[B][SIZE=3]
If anyone  can make it work, please post back here and let me know.[/SIZE][/B] I'll also post some more info below

Best Wishes,
Stephen

---

### Post by Stephen Winters on 2008-02-23
**[SIZE=4]Domain for Windows XP Home Edition?[/SIZE]**
I found this utility that has a place to enter domains. Can someone use it to set up a network with Windows XP Home edition?

> **[SIZE=3]Windows XP Home cannot join a domain, or can it?[/SIZE]**

 **[SIZE=2][by]("http://vowe.net/cgi-bin/mt.cgi?__mode=view&_type=entry&id=1639&blog_id=2") [Volker Weber]("http://vowe.net/about.php")[/SIZE]**

  Normally, Windows XP Home Edition cannot join network domains, simply peer-to-peer workgroups. However, there is a fix which can solve the problem and allow WinXP Home Edition to join a domain. Microsoft wanted to cripple Windows XP Home Edition so that it could not be used on domains, which would force many to upgrade to the more expensive Windows XP Professional Edition simply to join a network domain. However, it -is- possible to get on a domain using Windows XP Home Edition.
This can also be accomplished with the free and widely available Xteq X-Setup 6.1 by navigating to the "Network \ Auto Login \ Windows NT/2K/XP \ Settings" option within X-Setup. Simply enter the appropriate information and click "Apply Changes" - upon your next reboot, you can then join domains with WinXP Home Edition. Problem solved. X-Setup includes many other useful Windows XP tweaks / hacks / etc. for Windows XP as well, all free for personal use.
[Download here »]("http://www.x-setup.net/downloads/home.asp")
Source: [http://vowe.net/archives/001639.html](http://vowe.net/archives/001639.html)
Xteq X-Setup has developed into a shareware product, which available here: [http://www.x-setup.net/downloads/home.asp](http://www.x-setup.net/downloads/home.asp). Here is a link to the earlier freeware versions: [http://www.mdgx.com/xset.htm](http://www.mdgx.com/xset.htm)

I have downloaded and installed Xteq X-Setup 6.6 (the last freeware version) and it does have a place to enter domains. However, I'm not yet knowledgeable enough how to use it to set up my network.

> **[XP Home Domain Fix (Inbox)]("http://chris.pirillo.com/2002/02/26/xp-home-domain-fix-inbox/")**

                                        February 26, 2002 at 4:47 am              · in [General]("http://chris.pirillo.com/category/general/")               · [Comments]("http://chris.pirillo.com/2002/02/26/xp-home-domain-fix-inbox/#commentary")                                           
                                           
                                                            Normally, Windows XP Home Edition cannot join network domains, simply peer-to-peer workgroups. However, there is a fix which can solve the problem and allow WinXP Home Edition to join a domain. Microsoft wanted to cripple Windows XP Home Edition so that it could not be used on domains, which would force many to upgrade to the more expensive Windows XP Professional Edition simply to join a network domain. However, it -is- possible to get on a domain using Windows XP Home Edition.
 [SIZE=1][COLOR=Silver] Method 1: this can also be accomplished with the free and widely available Xteq [X-Setup 6.1]("http://www.xteq.com/products/xset/") by navigating to the “Network \ Auto Login \ Windows NT/2K/XP \ Settings” option within X-Setup. Simply enter the appropriate information and click “Apply Changes” - upon your next reboot, you can then join domains with WinXP Home Edition. Problem solved. X-Setup includes many other useful Windows XP tweaks / hacks / etc. for Windows XP as well, all free for personal use.[/COLOR][/SIZE] 
  Method 2: as Serdar Yegulalp pointed out in his [Win2kPowerUsers]("http://www.win2kpowerusers.com/") newsletter today also, this can be accomplished using Microsoft's TweakUI for Windows XP, but that has been pulled from Microsoft's Web site for the time being. I feel that it is very possible, if not highly probable, that Microsoft will prevent this
workaround from being used with future versions of TweakUI with Windows XP Home Edition, as they authored both Windows XP and TweakUI, and they don't want Windows XP Home Edition users to be able to join network domains. A copy of TweakUI for WinXP can be obtained [here]("http://www.majorgeeks.com/") [http://www.majorgeeks.com]("http://www.majorgeeks.com/"). [COLOR=gray][CptSiskoX][/COLOR]
[COLOR=gray]Source: [/COLOR][http://chris.pirillo.com/2002/02/26/xp-home-domain-fix-inbox/](http://chris.pirillo.com/2002/02/26/xp-home-domain-fix-inbox/)
                [B][SIZE=3] 

TweakUI
[/SIZE][/B][SIZE=3][SIZE=2]Just a note, I recently downloaded a copy of TweakUI from the Microsoft website. The version I downloaded did not appear to have any place to enter a Domain. Either it has been eliminated from TweakUI, or I just didn't see it. So, I would suggest trying to download it from[/SIZE][/SIZE]****[http://www.majorgeeks.com]("http://www.majorgeeks.com/")[SIZE=3][SIZE=2] or trying to find another copy on the [/SIZE][SIZE=2]Internet.[/SIZE][/SIZE][B][SIZE=3]

Another Option:[/SIZE][/B]

> **Windows XP Home Accessing data on a Domain Server**
You should have [checked first your Network adapter]("http://www.windowsnetworking.com/j_helmig/wxpnicch.htm"), then you should [URL="http://www.windowsnetworking.com/j_helmig/wxphlnch.htm"]verify / configure the
network setup[/URL] to make sure that your network is working properly.

Unlike [Windows XP Professional]("http://www.windowsnetworking.com/j_helmig/wxpjoind.htm"), Windows XP Home Edition is NOT able to join a Domain:
([no possibility to define the Domain name]("http://www.windowsnetworking.com/j_helmig/wxphlnch.htm#domain") in the [Properties of your XP Home Edition system ]("http://www.windowsnetworking.com/j_helmig/wxphlnch.htm#name"))

But you can still access data on a Windows NT4 or Windows 2000 Domain server : to [read more about this]("http://www.windowsnetworking.com/articles_tutorials/wxphdoms.html") go here: [http://www.windowsnetworking.com/articles_tutorials/wxphdoms.html](http://www.windowsnetworking.com/articles_tutorials/wxphdoms.html)

When I get some more time I'll have another look at these possible solutions. In the mean time, maybe someone else can be helped by this information.

Best Wishes,
Stephen

---

### Post by freebeer on 2008-02-23
> **Stephen Winters said:**
> Hi Freebeer,
   Thank you so much for taking the time to explain some things to me. I'm very new to Linux, and I also know very little about networking.  You response has helped me to understand a few things a little better. I do have some questions. 

Glad I can be of some help. :D

> Could you point me to someplace where this is explained in more detail? I had never heard about this before (which isn't surprising since I have looked into this before). The part I'd really like to see in writing is where it talks about the router having a different IP address than my internet address, and how that would protect my computers better.....


Well, I couldn't think of a specific place/link as most of my information was gathered and gleaned from many sources.  I did a quick little google and found [this]("http://www.homenethelp.com/web/explain/about-NAT.asp") though.  I only briefly glanced it, but I think it covers the key things you were wondering about.

> 
For the time being I've connected both computers to the router, which is connected directly to the Internet. But they are not yet networked together.

Semantics here.  The are networked together... you just don't have them communicating with each other yet via shares. ;)

When you plugged in both machines into the router, the router acting as a DHCP server, gave each of the machine a unique **internal** IP address.  This is usually in the form of 192.168.1.100 and 192.168.1.101.  (This is the usual default addresses most routers use.  The actual numbers aren't all that important except to note that each machine has a unique one.)  If you were to plug one of the machines directly to your modem (bypassing your router) and restart, your ISP would give you a different IP address.  This direct access exposes you to the nasties.

When you're connected to the 'net through a router, your modem has your **external** address and the router acts as your gateway to it.  Your **internal** machines ask for data, say a web page, the router passes it on to the modem and on to the 'net.  The web site sees your request and serves up the page and sends it to your **external** address.  The page arrives at your router, which then redirects the request to the appropriate machine requesting the page via its **internal** address.  The router knows that you requested the page and so it send it on.  This, in a nutshell, is the "translation" part.  Sounds complicated, I know, but it becomes second nature after you've worked with it for a while.  

Why is this relatively secure?  Well, if I wanted to go sniffing about your computer, I need to know your IP address.  There are means for me to do so, but I can only know your **external** address.   But I can only get as far as your modem because the router won't let me on to your internal network. (unless you've deliberately forwarded the ports in the router).

> I just don't want to open up my computer

Fair enough!  An admirable goal.  You can confirm to yourself your exposure by heading [here]("https://www.grc.com/x/ne.dll?bh0bkyd2") and testing both machines.  You can try each machine from behind the router, or directly connected to your modem to see if there's any difference.  They also do a pretty good job of explaining stuff, too.  :D

Now on to the domain issue:  Just ignore domains.  You do NOT need to set up a domain in order to share with XP Home.  Domains give you additional security and authentication, but it is overkill for a simple home network.  A simple workgroup share is fine, particularly when you're behind your router.

If I'm not mistaken, 7.10 already comes with Samba set up with a basic network share.  (I'm using 6.04 at home, so I had to set it up myself.)  You probably just have to change a configuration here or there to get all the machines on the same page.  We can help you with that once you're ready.  :D

---

### Post by Stephen Winters on 2008-02-24
Hi Freebeer,
    Thank you again for your very usefull information. I very much appreciate your thoughtfulness and consideration in your detailed reply, and for those links you gave me. This gives me a lot to ponder. Also, thank you for your willingness to help me through this.

Best Wishes,
Stephen

---

