---
title: "Workgroups not showing up"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Onyxblack on 2008-03-16
Ok, well first off I had this originally working before i changed to a different router... 

I originally had a d-link DI-624 (piece o crap 30 dollar router) and just upgraded to a d-link DGL-4500 (200$ top of the line gigabit router.) I am able to use the internet just fine but when i try to go to my windows network the workgroups don't show up. I have searched for 2 hours on this forum with no luck. If some one can help me out that would be awesome!

---

### Post by Iowan on 2008-03-17
This should give your thread a bump...
Could there be firewall settings in the router that require adjustment?

---

### Post by Onyxblack on 2008-03-17
As far as i can tell its not the router firewall - ive disabled it completely and still no luck, I'll try a few things once i get home and see how it turns up.

---

### Post by Onyxblack on 2008-03-17
ok, well heres an update... 

when i go to "smb://192.168.0.78" it shows the shared folders on one of my machines.... seems its working but just not showing my workgroup/complete list of my computers. I really dont want to have to keep a text doc with ip's to copy n paste when i want to access them.... any hints on what you guys might think be happening?

now that im able to access my webserver through the network....

[http://rsbb.servebeer.com/ubuntu/desktop.png](http://rsbb.servebeer.com/ubuntu/desktop.png) - an image of ubuntu running 3840x1024 wide :D

---

### Post by Eiríkr on 2008-03-17
I cannot get the workgroup to display properly in Nautilus, but it shows up just fine in Konqueror.  I'm really not sure what's the issue.  Clicking Go -> Network, I can see the Windows Network icon just fine.  Clicking this shows me the specific workgroup I'm running, but trying to click that just gives me an error stating "The folder contents could not be displayed.  Sorry, couldn't display all the contents of 'Windows Network: workgroup'."  Thing is, this is on the very machine that's the Samba server...  Shares display just fine in Konqueror, and in my XP Samba client, which really makes me think it's a Nautilus problem.  

Anyone have any ideas?  I'm seeing *numerous* posts here on the boards about workgroup shares not showing in Nautilus, so it's clearly a usability issue that's affecting quite a few people.  

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-19
One of the machines in the group should be acting as "listkeeper" (Master browser?).  No idea why Konquerer would find it and Nautilus would not.

---

### Post by Eiríkr on 2008-03-19
I'd done some futzing with the smb.conf file to bug-hunt for some posts on the list, but had changed everything back and reloaded the conf file afterwards.  Yet somehow Nautilus lost workgroup visibility until after I rebooted.  Strange.  And none of what I changed had to do with master browsers -- I'd toggled the [font=courier]wins support[/font] setting (from "yes" to "no", now back to "yes"), among others, but had never touched the [font=courier]preferred / domain / local master[/font] settings.  ... ?  Wierd.

---

