---
title: "Is this even possible?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by squishyalt on 2008-06-08
I want my new Ubuntu 8.04 laptop to act like my Windows laptop in respect to connecting to wireless networks.

With my Windows box, it detects new wireless networks and tells me that they are available.  If I want, I can click "Connect to network" select a wireless network and click "Connect".  If there is a needed password or key Windows prompts me for it and then uses it to authenticate me on the network.

At that point, I can see all shares on the network.

Everything that I have seen that discusses seeing Windows shares from Linux talks about knowing the network name and a whole bunch of other crap that I don't know - and will probably not know on most of the networks that I connect to at friends homes and wireless cafes.

Am I missing something here?

With all of the strides that Linux has made, making it connect to networks as simply as a silly little XP Pro laptop seems like a no-brainer.

I MUST have missed something here.  It can't be true that the only way to connect to networks is to hit the command line with a bunch of info that no Windows user ever even has to think about.

Help a newbie out, will ya?  What am I missing?

---

### Post by sstusick on 2008-06-08
Not sure what  your problem is, but I connect to wireless networks just fine, with one or two clicks of the mouse. 

Are you using the Network Manager?

---

### Post by squishyalt on 2008-06-08
The what? 

I am currently connected to my network by CAT5.  So that'll remove any wireless issues for now.

I clicked on Places > Network to open the "Network - File Browser".  I see "Windows Network" and double click it.

I then see my network's name and double click it.

The top of the browser now says "Windows shares on wfpp - File Browser" but NOTHING shows in the browser. 

I don't see any PCs on the network or any shared folders.

I REALLY want to ditch Windows, but Linux has to match its ease of use or it ain't gonna happen.

---

### Post by squishyalt on 2008-06-08
O come one....how can Linux expect to compete in networks that it can't even join?

There must be an easy answer for this.....

---

### Post by srt4play on 2008-06-08
> **squishyalt said:**
> I REALLY want to ditch Windows, but Linux has to match its ease of use or it ain't gonna happen.

Nobody is here to convince you to ditch Windows. This forum is here to help you once you have made the decision to put forth an honest effort into learning a completely new and different system.

Network Manager is usually used to connect with a wireless network, and was mentioned because you were talking about connecting to wireless networks in Windows. I think the problem you are trying to get help with is getting Ubuntu to see Windows file shares.

What do you see when you go to Places -> Network ?

EDIT:  I just saw where you described what is in Places -> Network.  Have you tried mapping to the Windows share via Places -> Connect to server ?

---

### Post by steveneddy on 2008-06-08
I pretty much travel the country with my laptop, which is Ubuntu only (8.04) and wireless or wired works perfectly every time. 

If I need a password, the person running the network gives me the password and I can log in. No Problem.

Maybe try this.

Open **Network Manager**.

```
System --> Administration --> Network
```

I suppose you are on Hardy 8.04, so you want to click the **Unlock** button and enter your password.

Under the wired and wireless sections, go to **Properties** and select the **Roaming** option ([COLOR="Blue"]check the box[/COLOR]) and close Network Manager.

Try to connect again.

To connect to a Windows network, you may want to install Samba if it isn't already.

---

### Post by askreet on 2008-06-08
> **squishyalt said:**
> The what? 

I am currently connected to my network by CAT5.  So that'll remove any wireless issues for now.

I clicked on Places > Network to open the "Network - File Browser".  I see "Windows Network" and double click it.

I then see my network's name and double click it.

The top of the browser now says "Windows shares on wfpp - File Browser" but NOTHING shows in the browser. 

I don't see any PCs on the network or any shared folders.

I REALLY want to ditch Windows, but Linux has to match its ease of use or it ain't gonna happen.

You seem to be talking about two different things.

"Joining a network", to me, means connecting wirelessly and obtaining a valid IP address.  Also, having access to the Internet.

What you are talking about here is browsing a NetBIOS network, which is different.

You see the name of your Windows "Workgroup", correct?  And inside there are no computers?  In Windows XP you can see all the computers?

Just trying to get the facts.  Best of luck, too.

---

### Post by squishyalt on 2008-06-08
> **askreet said:**
> You seem to be talking about two different things.

"Joining a network", to me, means connecting wirelessly and obtaining a valid IP address.  Also, having access to the Internet.

What you are talking about here is browsing a NetBIOS network, which is different.

You see the name of your Windows "Workgroup", correct?  And inside there are no computers?  In Windows XP you can see all the computers?

Just trying to get the facts.  Best of luck, too.

Correct.  I can see the network name and even workgroup name.  But, when I d-click the workgroup no Windows PCs ever show up.

Thanks for the help!

---

### Post by squishyalt on 2008-06-08
> **steveneddy said:**
> I pretty much travel the country with my laptop, which is Ubuntu only (8.04) and wireless or wired works perfectly every time. 

If I need a password, the person running the network gives me the password and I can log in. No Problem.

Maybe try this.

Open **Network Manager**.

```
System --> Administration --> Network
```

I suppose you are on Hardy 8.04, so you want to click the **Unlock** button and enter your password.

Under the wired and wireless sections, go to **Properties** and select the **Roaming** option ([COLOR="Blue"]check the box[/COLOR]) and close Network Manager.

Try to connect again.

To connect to a Windows network, you may want to install Samba if it isn't already.

OK....here's the stupid question of the day....where is this magical "Network Manager".  I don't see anything by that name on any of my menus.

---

### Post by Unix_Slayer on 2008-06-08
It's most probably Windows fault, and not Ubuntu.

---

### Post by squishyalt on 2008-06-08
> **Unix_Slayer said:**
> It's most probably Windows fault, and not Ubuntu.

Oh well....problem solved then!

---

### Post by squishyalt on 2008-06-08
I made sure that my profile was roaming.  

I installed Samba via package manager.

Now I also see "Workgroup", but it is only the Ubuntu machine.

Still no XP machines showing.

---

### Post by steveneddy on 2008-06-08
> **squishyalt said:**
> OK....here's the stupid question of the day....where is this magical "Network Manager".  I don't see anything by that name on any of my menus.


You quoted my post that told you where it was.

I posted because you wrote:

> 
I want my new Ubuntu 8.04 laptop to act like my Windows laptop in respect to connecting to wireless networks.

With my Windows box, it detects new wireless networks and tells me that they are available. If I want, I can click "Connect to network" select a wireless network and click "Connect". If there is a needed password or key Windows prompts me for it and then uses it to authenticate me on the network.


My machine is set up like I told you to do yours.

Unless you are only using a few networks, then make the machine [COLOR="Blue"]roaming[/COLOR] and it should connect.

Why don't you [look here]("https://help.ubuntu.com/8.04/internet/C/index.html").

---

### Post by steveneddy on 2008-06-08
Bookmark [this page]("http://ubuntuguide.org/wiki/Ubuntu:Hardy").

---

### Post by squishyalt on 2008-06-08
steveneddy,

Maybe I am asking this wrong.  I am connected to my network.  If I were'nt I could not be writing this from the Ubuntu machine connected to my network.

My problem is that I can;t see the XP machines on my network.

---

### Post by steveneddy on 2008-06-08
> **squishyalt said:**
> steveneddy,

Maybe I am asking this wrong.  I am connected to my network.  If I were'nt I could not be writing this from the Ubuntu machine connected to my network.

My problem is that I can;t see the XP machines on my network.

Are the windows machines sharing any folders?

---

### Post by squishyalt on 2008-06-08
> **steveneddy said:**
> Are the windows machines sharing any folders?

Yes.  And the folders aren't password protected.

I don't even see the PC names.

I've tried smb://wfpc/kong (kong is an XP Pro box with a whole hard drive shared for "everyone" - i.e. no password needed).  But, it doesn't show up.

I get "Couldn't display "smb://wfpc/kong/". Error: Failed to mount Windows share  Please select another viewer and try again."

---

### Post by squishyalt on 2008-06-11
Pffftttt......linux indeed!

---

### Post by steveneddy on 2008-06-11
Well - it works for me. I'm on a Windows network of some kind all day long, so maybe you should go and read the links that I gave you above. Maybe you'll "stumble" onto something.

Another thought is maybe the network isn't set up correctly. It may not be an Ubuntu problem at all. Remember to check all possibilities.

---

