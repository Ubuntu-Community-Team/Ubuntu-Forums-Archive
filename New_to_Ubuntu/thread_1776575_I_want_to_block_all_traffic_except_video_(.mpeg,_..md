---
title: "I want to block all traffic except video (*.mpeg, *.avi, *.mp4, etc..) files and text"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by hriata on 2011-06-06
I want to block all traffic except video (*.mpeg, *.avi, *.mp4, etc..) files and text files. Is there a way to do this with iptables or any other program? The reason i want to do this is because i have a Windows network that keeps getting infected by viruses, i was hoping if i use Ubuntu as a server to manage security and let only video and texts files circulate through my network, it would solve my problem. I am open to suggestions. Thanks.

---

### Post by calef13 on 2011-06-06
I'm no expert, but as far as I know, you can't block traffic based on what format it is very easily. I don't think iptables has this capability. A far easier option is to try and keep your windows clients secure, you might wanna try noscript if you are using firefox.

---

### Post by SeijiSensei on 2011-06-06
You can do this if you force all web traffic through the [Squid]("http://squid-cache.org/") proxy.  Unless you're willing to get your hands dirty and edit configuration files, this isn't the easiest of solutions, though.  You can use Squid's "ACLs" to permit some types of files and block the rest.

It's probably easier to enforce this on the Windows machines.  Make sure everyone is using Firefox, then install NoScript to block downloads that rely on Javascript trickery like Antivirus 2010.  Your users won't be happy, but they'll be safer.

I presume all the Windows machines have antivirus protection including scanning all downloaded objects automatically?  None of the users are running as Administrator, of course, right?  There's a lot you can do to improve security on the Windows side, but nothing is going to stop people downloading executables that appear to be celebrity sex videos except some training on your part.

---

### Post by crispy_420 on 2011-06-06
IP tables is for blocking protocols (http, ftp, etc.) and not specifically content. What you needs is a content filter. How is your server being used now? As a LAN device providing local services like shares and such? Would you be willing to redeploy as a gateway device that can control content like downloads, protocols and where it is acceptable to go online?

If that is the case look into Untangle Server: [http://www.untangle.com/](http://www.untangle.com/). It is prebuilt to do this and more at the cost of zero. Setup literally takes no time on decent hardware but does require dual NIC in PC.

---

### Post by hriata on 2011-06-07
I will not have any problem even if my network is not connected to the net.. i am concerned about my local network security. Let me try to explain it this way.. We have network of 20-25 Windows Boxes without a dedicated server and sharing net through ADSL modem router. The files are shared using windows networking and workgroups with entries of Private Static IP's for every box, very simple. Since this is very insecure and the systems usually get infected by viruses when someone with a infected USB stick of CD.DVD and infects a system, it usually propagates throughout the network. I have tried installing Anti-Viruses in the past but anti-virus alone is not good enough, and the users are not that good with computers too. What i need is something that blocks everything except some type of files that i want to circulate through the network. I am assuming if i can have that service my problems will be solved. Thanks again; :)

---

### Post by SeijiSensei on 2011-06-07
> Since this is very insecure and the systems usually get infected by viruses when someone with a infected USB stick of CD.DVD and infects a system, it usually propagates throughout the network.

Sounds like your problem is malware being brought in on media like USB sticks, not downloaded over the Internet. You really need to reconsider installing a good antivirus program on the Windows boxes.  Otherwise infections like these will just spread across the network via Windows file sharing.  A good active scanner will detect the infection on the stick and block it from spreading over the network.

---

### Post by hriata on 2011-06-07
I am currently running and experimenting untangle, it is very good so far.. will keep you updated.

---

### Post by hriata on 2011-06-07
It now seems that i need something that is similar to untangle that can be implemented for my local network. I find that untangle is a very powerful firewall for filtering contents from the cloud, but right now i cannot seem to get it to filter traffic that circulate through my local network, Can i use it to filter local traffic also, if so, plese tell me how, i would be very grateful.

---

### Post by crispy_420 on 2011-06-08
Does each user have a share on the local system or is it centralized sharing on the server?

As far as flash drives and optical drives what have you tried to limit the risk of spreading from that front? Disable auto run? Limit users rights?

---

### Post by twopointfour on 2011-06-08
I'm not sure this is a good idea. It's *really really hard* to control a network like this. Just ask China :).

The problem is you have a whole lot of protocols, and a lot of these use encryption. If someone goes to an HTTPS website to download something, your Ubuntu proxy server won't be able to tell what is being downloaded, because it's all encrypted. The only way around this would be to transparently man-in-the-middle all HTTPS connections and generate new SSL certificates on the fly with your own certificate authority (CA), and at that CA to all the web browsers on your network so it's trusted.

There are other protocols took, like samba for windows file sharing, jabber for things like Google Talk, pop, smtp, and imap for email, maybe some video game protocols, ftp and ssh. Some of these may or may not use encryption, and not all of the clients are as easy to add a CA to as a web browser.

Not to mention a lot of random things you didn't expect will break.

If the reason you want to do this is to prevent malware on the Windows boxes, you're much better off just hardening them but still letting them access the internet freely. Format them all and re-install Windows so you're sure they don't have malware. Install anti-virus software and make sure Windows updates happen automatically. If users download malware or put USB sticks with malware in the computers, create unprivileged users and make people login as those. Then the malware will need to use privilege escalation before it can do any real damage, and the computers are regularly updated this should be very difficult. Also, people can't do stupid things like install random software that runs as an administrator.

---

### Post by hriata on 2011-06-08
They all have shares on their hard drives using CIFS/SMB!! I can centralise it though, if i want to. i think that is a safer option too.

---

### Post by crispy_420 on 2011-06-08
If you centralize the shares you will also be able to do a regular malware scans of the files in a single location. That would a time saver for you. It will ensure higher availability of files to the end user since the server is always on I assume and if you have to take a system offline due to infection the shared files would still be available.

I do agree with what someone said earlier about trying to lock down the network, it may not be feasible and even after done the threats may still occur either way. I think your best approach is to secure the boxes, provide user awareness and if possible have a policy in place to deal with bad users.

---

### Post by hriata on 2011-06-08
I will go for the centralised option, and do you think i should deploy squid and iptables too? Crispy. Thanks

---

### Post by crispy_420 on 2011-06-08
Did you start using Untangle? It should have those features type of features built in with a very friendly interface. Do you want to control content coming in? I have messed with squid only briefly combined with dansguardian but it does start very restrictive but from the sounds of it the outside is not your biggest issue. No matter how you lock own the network you will stay have the removable media threat.

There are also easier options to use to filter content. Look into OpenDNS. They have a free service where you install a client on a local system and set them as the DNS servers at the router level. At lets you control content available through them and blocks the sites you decide to be objectionable/unacceptable. The client acts like a dynamic dns client keeping them updated to your WAN IP so it stays in sync with you. Then make sure the clients can't change their network settings.

Never did ask but where is this network? Work? A school?

---

### Post by hriata on 2011-06-09
I did start using untangle and i think it's very good, the only problem is that it can only filter traffic which is on different networks. Client is a video broadcaster, Network is related to that, client just bought expensive machines that needs to run Windows XP boxes because the software they use to run their broadcast program requires it. I have a feeling i should just make 2 different networks and route only the packets that i want through to the other network. I can use untangle as a router and to filter the traffics. I think that's a good idea.

---

### Post by crispy_420 on 2011-06-09
Not sure if that would work but it couldn't hurt. Worst case scenario you may have some downtime but it would be simple to fall back to the old network topology if needed. But I think securing/locking down the Windows machines may be the single best thing you can do and we could discuss that all day but this is the wrong forum for that.

Since this work related can't the employer make some policies to prevent users from infecting their systems with removable media? Also maybe some user training is in order to prevent malware issues? If they are bringing in infected drives that means they have infected home PCs so the training could be made to look like you are actually helping them solve their problems. Try to get them to install antivirus software at home, there are plenty of great free solutions (avast, AVG, MS Security Essentials, etc.). Also see if the employer would be willing to purchase a good AV solution for the work systems too.

I could go all day but anyway. Hopefully this works out for you.

---

### Post by hriata on 2011-06-09
Thanks again Crispy, i'll try this option for now, and we will also definitely have employee trainings, that is a must, i have discussed it with my client regarding training and AV solutions, he says i can do whatever i want to safeguard the network and he is willing to invest. So hopefully we'll be able to solve this problem. :)

---

### Post by crispy_420 on 2011-06-09
Can we call this solved or is that still up in the air?

---

