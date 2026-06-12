---
title: "My first 4 hours (wireless network issue)"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by minigmgoit on 2009-01-31
Hello
As the title says, I am the n00biest of n00bs with a mighty 4 hours of Linux under my belt :D

It all started out great, everything was working fine then I tried to create a static IP address. Firstly using the terminal (something of which I have never needed to do before) then by right clicking the network connections tab in the tray and editing connections.
Rather stupidly I ended up manualy deleting my wireless network connections set up.
Since then I have rebooted a couple of times, had to put my WEP Key in again etc but it wont show any web pages.
It is saying that I'm connected to the network but I keep getting the "Address not found" firefox page getting thrown up.

As I said I am totally new to Linux so I'm sorry in advance as I am sure there is something very obvious that I am supposed to have done but have not.

Your help is greatly appreciated in advance.

Regards

Me

---

### Post by minigmgoit on 2009-01-31
I thought that maybe there could have been some sort of IP conflict with one of the other computers on the network but I'm not sure how to tell.

---

### Post by GammaRay256 on 2009-01-31
What is the output if you run "ifconfig" in terminal?

---

### Post by zabien1970 on 2009-01-31
This has happened to me a couple times, connected to wireless but no internet, all I had to do was turn off the modem and wireless for a minute then turn them back on and let them reboot. Give it a try and see if it works

---

### Post by minigmgoit on 2009-01-31
Sorry, what do you mean output?
Theres eth0
eth1
lo
wlan
wmaster0
Each of those has a few bits of info beside them but nothing that looks like output.

Sorry. I am totally new and very sorry for this.

---

### Post by minigmgoit on 2009-01-31
> **zabien1970 said:**
> This has happened to me a couple times, connected to wireless but no internet, all I had to do was turn off the modem and wireless for a minute then turn them back on and let them reboot. Give it a try and see if it works

Ive rebooted coutnless times now and it has not done anything to improve the situation.

---

### Post by GammaRay256 on 2009-01-31
> **minigmgoit said:**
> Sorry, what do you mean output?
Theres eth0
eth1
lo
wlan
wmaster0
Each of those has a few bits of info beside them but nothing that looks like output.

Sorry. I am totally new and very sorry for this.

Under "wlan", do you have an IP address?

Something like:

wlan     Link encap:Ethernet  HWaddr 00:13:02:24:4b:7a  
          inet addr:10.20.21.101  Bcast:10.20.21.255  Mask:255.255.255.0

If not, it will just say something like: [I]"UP BROADCAST MULTICAST  MTU:1500  Metric:1
"[/I] without an IP

---

### Post by minigmgoit on 2009-01-31
> **GammaRay256 said:**
> Under "wlan", do you have an IP address?

Something like:

wlan     Link encap:Ethernet  HWaddr 00:13:02:24:4b:7a  
          inet addr:10.20.21.101  Bcast:10.20.21.255  Mask:255.255.255.0

If not, it will just say something like: [I]"UP BROADCAST MULTICAST  MTU:1500  Metric:1
"[/I] without an IP

It has the UP BROADCAST MULTI CAST stuff and not the address, mask etc.

---

### Post by GammaRay256 on 2009-01-31
> **minigmgoit said:**
> It has the UP BROADCAST MULTI CAST stuff and not the address, mask etc.

Since the interface is not getting an IP, there must be some kind of configuration conflict somewhere.

When you were trying to get the static IP address to work (mentioned in the original post), did you modify the file "etc/network/interfaces"?
It should look like this by default

[I]auto lo
iface lo inet loopback
[/I]
If it still has static IP setup info in it, try removing that and restoring it to the original state... Then once you get the connection sorted out with dhcp, you can try static IPs again.

Other than that, I'm not sure what the next step should be...

---

### Post by minigmgoit on 2009-01-31
Thats it, I'll go and delete what I put in there and put back the "loopback" bit.

Thanks 

:)

---

### Post by monkeychick on 2009-01-31
When I first installed Ubuntu and when I tried to get on the net, I got a page not message too. My problem was something simple, when I clicked on file, work offline was ticked. So I unticked it and it worked.

---

### Post by minigmgoit on 2009-01-31
Ok, so there is definatly a problem where you said but I'm having difficulty editing it.

I am editing the text and usually when I use the arrow keys to move to the bits that need to be changed or deleted its leaving numbers instead.

Also when I do get it looking right and press ctrl x nothings happening. Am I missing something?

---

### Post by zabien1970 on 2009-01-31
> **minigmgoit said:**
> Ive rebooted coutnless times now and it has not done anything to improve the situation.

 Not sure if you understood what I meant, I wasn't referring to rebooting your computer, I meant letting the modem reboot by unplugging it for a minute or so, mine has frozen a few times and even though my computer connected to my wireless router fine it couldn't connect to the internet. Some of my friends (running windows or linux) have had this happen also on occasion.

---

### Post by minigmgoit on 2009-01-31
> **zabien1970 said:**
> Not sure if you understood what I meant, I wasn't referring to rebooting your computer, I meant letting the modem reboot by unplugging it for a minute or so, mine has frozen a few times and even though my computer connected to my wireless router fine it couldn't connect to the internet. Some of my friends (running windows or linux) have had this happen also on occasion.

No I understood. I have rebooted both things coutnless times and not got anywhere. Also I'm using the same router to conect to the internet and post this so there no problem there.

I can see whats wrong but I cant fix it. Just going to reinstall and start again.
I was expecting to have a few problems when I switched over. I am more than happy to put in the hard graft with this OS. I'm sure it will be worth it in the end.

Far better than the others anyway. :)

---

### Post by minigmgoit on 2009-01-31
Ok maybe not. That looks like far to much hassle
Basically at the moment if I type:

sudo vi /etc/network/interfaces

I see this

auto lo
iface lo inet static
address 10.1.1.30
mask 255.0.0.0

Now I know that it actually needs to look like this
auto lo
iface lo inet loopback

But I cant get it to do it.

My arrow keys keep printing letters after I delete what needs to be deleted.
I did manage to get it looking right once but when I pressed ctrl x it did nothing.

I'm trying so hard to sort this out :(

---

### Post by minigmgoit on 2009-01-31
Also after typing sudo vi /etc/network/interfaces

I always get an error message saying thateither another program maybe editing the file oran edit session for this file crashed

Is this the problem. In the terminal window there are no propts at the bottom of the window which I'm sure there was earlier on.

---

### Post by theozzlives on 2009-01-31
If you're running computers off a router, you enter the static IP in the router, not the computer. You set the computer to dynamic.

---

### Post by minigmgoit on 2009-01-31
> **theozzlives said:**
> If you're running computers off a router, you enter the static IP in the router, not the computer. You set the computer to dynamic.

Thats not really helpfull right now. 
I have mentioned what the problem is and why I can't fix it.
That doesn't really help me. 
Thanks though

---

### Post by ugm6hr on 2009-01-31
Sounds like you are struggling with vi.

Reboot with the ethernet unplugged (or even turned off from BIOS)

Perhaps try another editor:

```
gksudo gedit /etc/network/interfaces
```

---

### Post by linux_tech on 2009-01-31
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

You can use nano for simple editing also
```
sudo nano /etc/network/interfaces
```

---

### Post by gvoima on 2009-01-31
For a first time user, you really shouldn't go and mess up with network configurations via terminal and with vi, nano is simple enough for terminal use.

In the gnome menu -> System -> Administration -> Network. It's easy enough to do it from there graphically. (statis IPs)

Then if needed, learn the hard way :)

I hope you enjoy Ubuntu.

---

### Post by minigmgoit on 2009-01-31
> **linux_tech said:**
> ```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

You can use nano for simple editing also
```
sudo nano /etc/network/interfaces
```

Thanks, it just let me edit the code and save it using Nano.
I feel like such a spaz at the moment with all this stuff. I hope I pick it up.

Lets hope it works, I'll report back in a second.

---

### Post by minigmgoit on 2009-01-31
> **gvoima said:**
> For a first time user, you really shouldn't go and mess up with network configurations via terminal and with vi, nano is simple enough for terminal use.

In the gnome menu -> System -> Administration -> Network. It's easy enough to do it from there graphically. (statis IPs)

Then if needed, learn the hard way :)

I hope you enjoy Ubuntu.

Now s/he tells me :)
Never mind its all over now. I'm sitting happily typing on my Linux machine. All is good witht eh world.

And relax

---

### Post by gvoima on 2009-01-31
> **minigmgoit said:**
> Now s/he tells me :)
Never mind its all over now. I'm sitting happily typing on my Linux machine. All is good witht eh world.

And relax

:)

---

