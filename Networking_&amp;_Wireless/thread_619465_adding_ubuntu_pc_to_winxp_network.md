---
title: "adding ubuntu pc to winxp network"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by treion on 2007-11-21
I'm a first time user of ubuntu, my problem is how do i add it to an existing network group. I have 2 pc connected to the net via modem/router. the ubuntu can access the net see the other pc, but the other xp pc's can't see it in the network. all updates done.  i'm planning to play starcraft with the other pc's in a network game is it possible?

---

### Post by misconfiguration on 2007-11-21
You should be able ping the ubuntu box from the XP machines with no problem. It gets a little more involved if you want to actually share resources betwixt machines. In order to do so you'll have to install samba and configure it properly. 

If you have Starcraft working on the ubuntu box you can link game with the IPX protocol; you don't have to be members of the same domain.

If you'd like to add the ubuntu machine to the very same domain that should have been done in your network configuration, when the box was setup. 

Generally domain and host names can be set in /etc/hosts.

---

### Post by treion on 2007-11-21
thanks for the quick reply. as i have mentioned the terminologies and set-up are all greek to me right now. it's my first crack at ubuntu with no knowledge at all

where do i set the ipx protocol in the ubuntu box?
please give link on this samba, i might DL the wrong ones hehehehehe
can't host name domains be re-configured after installation?

---

### Post by luvdemheels on 2007-11-21
Click System, Click Administration, Click Shared Folders. It should prompt you to install samba there. After it is installed there is where you can configure it.

p.s. the (SMB) is what you will need.

---

### Post by misconfiguration on 2007-11-21
Yes, domain names are most definitely re-configurable.

The solution to samba is posted above (thanks).

Also, you don't need to enable IPX/SPX is similar to TCP/IP pretty close to tcp and udp. 

It's an option in Starcraft, they chose to use these protocols for network play. It has nothing to do with your ubuntu machine per se; sorry for the confusion. 

Keep asking for help if you need it; it's worth tinkering and sticking with it. It can be a frustrating journey but like I said.. It's worth it.

Best of luck to you mate!

---

### Post by treion on 2007-11-21
@luv: thanks will try tonight.where do i get samba? is it built-in to be installed?
@msconfig: i'll surely be asking more questions :)  are you from australia? can't help to notice the "mate" thingy.. i'm in NZ right now

---

### Post by misconfiguration on 2007-11-21
I'm actually from the States > Indianapolis => Indiana to be exact ;).

To install Samba : Open the command line and execute the following.
```

sudo apt-get install samba smbfs

```

Cheers :)

---

### Post by treion on 2007-11-21
let me get this right:
I download samba (from its website)to the share folder as instructed by luv, then install it via the terminal commands Msconfig wrote.  correct?

---

### Post by hkgonra on 2007-11-21
the commands msconfig wrote do it all for you , no need to go to samba website.

---

### Post by treion on 2007-11-22
installed samaba, but now my starcraft won't run. what could have happened?

---

### Post by K.Mandla on 2007-11-22
Moved to networking and wireless.

---

