---
title: "amule trouble"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by aussielinuxguy on 2011-03-20
Hi,

 I downloaded and installed amule, but when i start the program i get a message saying WARNING: You have received Low-ID!.

I think firestarter is blocking it as i read the amule help site, but it talks about routers.

My internet connection is a USB prepaid mobile broadband. How can i get amule to work ?

---

### Post by aussielinuxguy on 2011-03-21
no help, ohhh well i use nicotine-plus, which works.

---

### Post by gandaran on 2011-03-21
open the ports 4662 and 4672 in firestarter

---

### Post by Claus7 on 2011-03-21
Hello,

follow this:
and you will be ok
[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)

in addition you might have to do this:
[http://ubuntuforums.org/showthread.php?t=1048545](http://ubuntuforums.org/showthread.php?t=1048545)

Regards!

---

### Post by aussielinuxguy on 2011-03-21
[gandaran]("http://ubuntuforums.org/member.php?u=417273") and claus7, Thank You for the replies. I am going to read the links you said claus7.

---

### Post by aussielinuxguy on 2011-03-21
gandaran, i opened the ports 4662 and 4672 in firestarter.

claus7, i did read the second link that you said to follow, and did what that user said to do.

When i connect amule it downloads the server list i think it is, and when i go to Networks then click on ED2K info, i get this:

eD2k Staus: Connected
IP:  Port Server
ID   8056936
      LowID

And with Kad Info:

Status:               Connected
Connection Sate: Firewalled
Firewalled state:  Connected to buddy
Average Users:    1.51M
Average Files:      264.76M

Does that look right ?

When i double click on a download and go to Transfers window, the file turns blue but does not download.

---

### Post by Rhubarb on 2011-03-21
> **aussielinuxguy said:**
> ...My internet connection is a USB prepaid mobile broadband...
That's your problem.
From my experience with three / vodafone, most (if not all?) incoming ports are blocked.

Which essentially means you can't host a server on a 3G connection. (which is what amule is trying to do to get a "high id").
The ISP usually has some very annoying device that blocks incoming unrequested packets (dunno if it's a firewall, a NAT device, or a proxy).

For example, I'm able to ssh from my 3G connection to a server, but I can't ssh from anywhere to my 3G connection (without doing a reverse ssh connection anyway).

---

### Post by aussielinuxguy on 2011-03-21
Rhubarb, Thanks for that information. so does that mean i wont be able to use amule ?

---

### Post by Rhubarb on 2011-03-22
You can still use amule, it just means that you get a low id, which essentially means it'll take longer to download stuff as you'll have a lesser priority than those that have a high id.
It should still work, but it'll be a bit slower.

---

### Post by aussielinuxguy on 2011-03-22
ok Rhubarb, other than nicotine, amule and gtk-gnutella file sharing, is there anymore in the Synaptic Package Manager ?

---

### Post by Claus7 on 2011-03-22
Hello,

> **aussielinuxguy said:**
> gandaran, i opened the ports 4662 and 4672 in firestarter.
Nope, there are not seem to be the right ports. Check out the first link I sent you. It says exactly which port numbers you should open, and seems to do the work most of the time.

> **aussielinuxguy said:**
> 
claus7, i did read the second link that you said to follow, and did what that user said to do.
The second link was sent to you, in case the guide found in first link does not work.

It says also (the first link) that in extreme cases you might have to use different ports than the default ones.

> **aussielinuxguy said:**
> 
When i connect amule it downloads the server list i think it is, and when i go to Networks then click on ED2K info, i get this:

eD2k Staus: Connected
IP:  Port Server
ID   8056936
      LowID


seems you still have not forwarded the right ports...

> **aussielinuxguy said:**
> 
And with Kad Info:

Status:               Connected
Connection Sate: Firewalled
Firewalled state:  Connected to buddy
Average Users:    1.51M
Average Files:      264.76M

Does that look right ?

cad seems to be working right, so you do not have to worry about this.

> **aussielinuxguy said:**
> 
When i double click on a download and go to Transfers window, the file turns blue but does not download.

Low id or not, amule does not start downloading files straight away. Most of the time you have to wait. Blue, I think, is that the file is found, yet you have to wait.

Regards!

---

### Post by aussielinuxguy on 2011-03-22
Claus7, here is a screenshot. i changed the firewall settings. i downloaded a mp3 but it was at dial up speed !

---

### Post by Claus7 on 2011-03-24
Hello,

did you do exactly the same thing for your modem as well? Did you forward these ports for your modem as well? Most of the time I'm facing low id is because of not having forwarded the ports to my router. And for some reason I have to do this every single time I reboot my pc.

Check this out as well, cause it is really causing the kad thing to be firewalled, no matter what you do with firestarter. The ports now seem to be ok!

Regards!

---

### Post by gandaran on 2011-03-24
> **aussielinuxguy said:**
> Claus7, here is a screenshot. i changed the firewall settings. i downloaded a mp3 but it was at dial up speed !
always choose a file to download with the most active sources (peers) the best files are on blue text, these download fast, any other with few sources (in black text) will take a long time.

---

### Post by aussielinuxguy on 2011-03-25
amule is working properly now.

Thank You for your help.

---

