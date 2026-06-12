---
title: "Problems with Transmission Bit Torrent..."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by S0VERE1GN on 2008-12-11
Hey all, I seem to be having a problem finding an open port on transmission. 
I just upgraded to Ubuntu 8.10, and i have a feeling that there is some sort of firewall blocking my ports that i cant find. 

any help?

---

### Post by Sinkingships7 on 2008-12-11
> **S0VERE1GN said:**
> 
I just upgraded to Ubuntu 8.10, and i have a feeling that there is some sort of firewall blocking my ports that i cant find. 

It's probably your router. Are you behind one, by any chance?

---

### Post by frankleeee on 2008-12-11
You might consider Deluge from add remove, it has been the best I have used, very fast, encrypted (no throttling for me) and can choose random ports.

---

### Post by handy on 2008-12-11
Transmission works fine for me, on Arch, behind the IPCop firewall (which is on a dedicated machine) without any configuration of Transmission *(**[Edit:]** or IPCop /edit)* at all to get it to work?

---

### Post by frankleeee on 2008-12-11
In the past using transmission I have had it read no open ports but work anyway, have you tried to see if this is the case.

---

### Post by eternalnewbee on 2008-12-11
I'm having problems with Transmission, too. When I run it I also get the side effect of FF not being able to open any web pages. After I close Transmission, everything goes back to normal...

---

### Post by handy on 2008-12-11
I suggest having a look at the [***_Transmission forum_***]("http://forum.transmissionbt.com/") on this one.

---

### Post by laceration on 2008-12-12
I would rather get a root canal than set up Port forwarding or configure ports.  If your bit torrent client doesn't do that for you, it's not worth a hill of beans.  I have preferred to use Deluge because it does this and is nicer + more featured than transmission imho.  Nevertheless, a couple of weeks ago I'd try a bt download and couldn't get any open ports.  I tried transmission too, same problem. 

Could some upgrade have broken something like the ability of programs to use ports??

Confronted with the Chinese algebra of port-ology, I went to the Deluge website and installed a current .deb.  Programs in the standard repositories are often not close to up to date.  That fixed the problem.

---

### Post by Bölvaður on 2008-12-12
> **laceration said:**
> Could some upgrade have broken something like the ability of programs to use ports??

It is most probably because you are behind router that doesnt have open port, or that transmission isnt set to that port. Ports are open on the computer when it is needed so there is very slim chance that it is software problem.

---

### Post by billgoldberg on 2008-12-12
> **laceration said:**
> I would rather get a root canal than set up Port forwarding or configure ports.  If your bit torrent client doesn't do that for you, it's not worth a hill of beans.  I have preferred to use Deluge because it does this and is nicer + more featured than transmission imho.  Nevertheless, a couple of weeks ago I'd try a bt download and couldn't get any open ports.  I tried transmission too, same problem. 

Could some upgrade have broken something like the ability of programs to use ports??

Confronted with the Chinese algebra of port-ology, I went to the Deluge website and installed a current .deb.  Programs in the standard repositories are often not close to up to date.  That fixed the problem.

Forwarding ports takes less then one minute.

---

### Post by laceration on 2008-12-12
> Forwarding ports takes less then one minute. 

Really?  Would you care to backup your assertion with a little 1-minute primer?  I tried to tackle port-forwarding and encountered dense, laborious and voluminous instructions that have made my head swim.  I concluded this was something best concealed from me the end user just as I wouldn't to use assembly language to preform a chore such as listing directory contents.  Maybe I clicked on the I'm feeling lucky that day and wasn't.

---

### Post by S0VERE1GN on 2008-12-12
I ended up switching to K torrent, and it works great!!! thanks for the suggestions though. I think it has something to do with my router or my internet provider.

---

### Post by handy on 2008-12-13
For what it's worth, I recently experienced trouble with Transmission, & ended up fixing it by deleting the ***~/.transmission/<files>***

I left the directories, just took any files out of there, they are dynamic files & one of them must have been corrupt for one reason or another.

---

### Post by NeddyDownUnder on 2010-05-14
**EDIT: LOL just realised how old this thread was... Sorry **


> **laceration said:**
> Really?  Would you care to backup your assertion with a little 1-minute primer?  I tried to tackle port-forwarding and encountered dense, laborious and voluminous instructions that have made my head swim.  I concluded this was something best concealed from me the end user just as I wouldn't to use assembly language to preform a chore such as listing directory contents.  Maybe I clicked on the I'm feeling lucky that day and wasn't.


For most cases it really does take less than a minute... You simply look at the port number the torrent client wants to use and enter that number into your router's port forwarding page along with the ip address of the computer running the torrent client.(enable both TCP and UDP although I don't know if Transmission uses UDP) Additionally ensure the torrent client computer has a static IP... (otherwise you won't have an IP address to enter into the router)

Hopefully this demonstrates simple port forwarding to you so you can use it in the future. It's nice to know how to use it and once you understand it a little it really does take seconds... :)

Cheers,

Ned

---

