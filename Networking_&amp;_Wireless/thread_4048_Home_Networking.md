---
title: "Home Networking"
date: 2004-11-11
forum: Networking &amp; Wireless
---

### Post by tekwerx on 2004-11-11
Need some help here, please...

Trying to figure out how to get my two machines (both running Ubuntu updated to "Hoary") to talk to each other.  Ive got a bunch of files on one Id like xferred to another.  I can get the machines to see each other if I install Samba, but I still cant see anything in the other comps over the network.  Anyhow, I dont think I should need to enable a Windows network for two Linux machines...Im sure theres a native Linux way to do it.  Thanks in advance!

Tek

---

### Post by tekwerx on 2004-11-11
*bump*

---

### Post by wossname on 2004-11-11
Using SMB isn't a bad option.
NFS can sometimes be tricky to set up, but will also do the trick.

If your filecopying isn't on a regular basis, but more of a one-off, I suggest you use. scp.


example syntax: 

yourusername@yourhost1:~ $ scp -r yourhost2:/path/to/dir ~/whereyouwantit

the "-r" option is for recursion, needed for dir's.

---

### Post by tekwerx on 2004-11-11
Alright, but how do I set it up permanently?  SMB, as I said up above, will let me see the other machines, but not send/recieve anything from them.  So how do I get some kind of a permanent connection going between them, SMB or otherwise?

---

### Post by tekwerx on 2004-11-11
*bump*

 :-k

---

### Post by tekwerx on 2004-11-11
So noone knows how to network two Linux PCs together?   #-o 

Alrighty then....

---

### Post by tekwerx on 2004-11-11
*another bump*

 :x

---

### Post by m9dhatter on 2004-11-11
[QUOTE=tekwerx]*another bump*

 :x[/QUOTE]
 if you want native, there are several avenues to choose from.
nfs: this is quick low down and dirty 
ftp: easy to set up a server and there are plenty of clients to choose from.
samba: this is by far the nearest thing to windows networking you can have so if you plan on connecting to windows machines in the future, its better to have this ironed out.

---

### Post by tekwerx on 2004-11-12
I dont plan on having any Windows machines connected in the future, but I'll take any of the three...just need someone to tell me how to do one of em...

---

### Post by tekwerx on 2004-11-12
Still another *bump*

...


I just need something that works, easily and quickly...please...anyone.

---

### Post by Crisis on 2004-11-12
I would recommend NFS for an all *Nix environment.  It should be pretty easy to setup a share and connect.

To setup a share, add something like this in the file /etc/exports:

```
/share -alldirs 192.168.0.100
``` 

/share in that example is a path that you want to share to another computer.  192.168.0.100 is the IP of the computer you want to be able to connect.

On the other computer, do something like this:

```
mount -t nfs 192.168.0.99:/share /share
```

This will connect to the machine with the share (192.168.0.99 in this example), and mount it on the local machines /share folder.

You can add this to /etc/fstab to make it happen at each boot:

```
192.168.0.99:/share    /share   nfs    rsize=8192,wsize=8192,timeo=14,intr 0 0
```

There are man ymore options you can do and I recommend you read up to find how to more closely meet your needs.  Hope this helps!

---

### Post by az on 2004-11-12
Also, take note of the faq on the Ubuntulinux.org website regarding Out-of-the-box nfs server:

I am trying to set up an NFS server. I think I've done everything right, but it doesn't seem to work. I get an error "mount: RPC: Remote system error - Connection refused". What have I missed?
By default, the portmap daemon listens only on the loopback interface (localhost). You can change this by editing /etc/default/portmap and removing the "-i 127.0.0.1" option from the command line arguments.
This FAQ applies to: warty 


Also, is there no gui to set up NFS in Ubuntu?

---

### Post by poptones on 2004-11-12
*Also, is there no gui to set up NFS in Ubuntu?*

Don't really need a gui, just need a proper script to get the basics working. 

What would be nice is to have sharing tabs in the property sheets of folders. Mandrake has these, I thought they were just part of gnome but I guess not. Nautilus doesn't change the folder icons to show sharing in ubuntu, either - unfortunately. Hopefully this will all become part of ubuntu real soon now, because it's the only dull surface on an otherwise incredibly shiny product.

Setting up sharing isn't too hard, but it can be tricky if you're a noob because the nfs howto has lots of instructions like "restart this" and "start that" but doesn't even tell you how to do these things.

I'll put together a script that will automatically do all the stuff you need to get nfs sharing working, but I won't be able to finish it until tonight or tomorrow.

---

### Post by trash on 2005-02-19
hey poptones, did you post a script somewhere?

thanks.

---

### Post by dbernar1 on 2005-03-17
Ok, so you have all told the guy what apps to use to get from one computer to the other...or perhaps a bit more with the NFS...but still it is over IP, and that is ultimately,  in my humble opinion going to be slow...and I mean, I knew already how to FTP, when I came to this place looking for an answer...
Now, I would like to know, how do you set up a domain of your own? No internet, just a hub, and some cables, and two+ computers...that would really help me, I have been trying to figure it out for some time now, well, not very actively, but I have been looking for a way to do it... ](*,)

---

### Post by meyerm on 2005-03-25
Hmm, I'm not sure what exactly you want. But let's simply start:

> **dbernar1]but still it is over IP, and that is ultimately,  in my humble opinion going to be slow...and I mean, I knew already how to FTP, when I came to this place looking for an answer...[/QUOTE]
If you mean "Internet Protocol" with IP, then I'm confused. If not, sorry. What did you mean? :-)

NFS is based on UDP (meanwhile also TCP) which is based on IP which is (most likely in your case) based on Ethernet which... and so on  said:**
> Now, I would like to know, how do you set up a domain of your own? No internet, just a hub, and some cables, and two+ computers...
Well, I hope you didn't mean "domain" is term of Microsoft Active Whatever. If you did, have a look at the samba project. If not: What do you mean? Do you mean "foobar.com" as domain? That has noting to do with sharing your files. A domain is simply translated into IP numbers - simply a single DNS query (BTW: based on UDP which is based on IP... well, you got it *g*) before starting the connection with that other computer based on it's IP adress (there are protocols like HTTP which also use the domainname inside their requests, but that's independant from the network "problem").

Connecting your computers is as easy as plugging them in, then give each one an IP address (if you don't know which one, just take 192.168.0.1 and 192.168.0.2 for the other) and then follow the explanations above.

---

### Post by swerner on 2005-03-26
Well the original post is rather old. But home networking is rather easy, much easier than NFS. These instructions are for Warty, but should also be true for Hoary. You need to install sshd on all the computers you want access to:
```
apt-get install sshd

```
Then on the remote computer go to Computer->Network->File->Connect to Server.  Then set the following:
```
Service Type: Custom
Location (URI): sftp://username@192.168.0.2/dir/you/want
Name to use for connection: "The other computer"

```
If the username is the same on each computer then you can ignore it. 192.168.0.2 has to suit the remote computer. "/dir/you/want" is any directory you want access to, if you omit this you will just get the root folder.

This method allows you to secure access any computer, even over the internet.

Enjoy  :)

---

### Post by nilsmagnus on 2005-05-17
[QUOTE=poptones]*Also, is there no gui to set up NFS in Ubuntu?*

Don't really need a gui, just need a proper script to get the basics working. 

What would be nice is to have sharing tabs in the property sheets of folders. Mandrake has these, I thought they were just part of gnome but I guess not. Nautilus doesn't change the folder icons to show sharing in ubuntu, either - unfortunately. Hopefully this will all become part of ubuntu real soon now, because it's the only dull surface on an otherwise incredibly shiny product.
[/QUOTE]

I can see the need for this as well. My mother would for example never be able to set up home-network with nfs as ubuntu is today, but can easily do it with a m$ desktop. And we dont want that, do we? :)

---

### Post by AgenT on 2005-07-30
[QUOTE=swerner]Well the original post is rather old. But home networking is rather easy, much easier than NFS. These instructions are for Warty, but should also be true for Hoary. You need to install sshd on all the computers you want access to:
```
apt-get install sshd

```
Then on the remote computer go to Computer->Network->File->Connect to Server.  Then set the following:
```
Service Type: Custom
Location (URI): sftp://username@192.168.0.2/dir/you/want
Name to use for connection: "The other computer"

```
If the username is the same on each computer then you can ignore it. 192.168.0.2 has to suit the remote computer. "/dir/you/want" is any directory you want access to, if you omit this you will just get the root folder.

This method allows you to secure access any computer, even over the internet.

Enjoy  :)[/QUOTE]

Brilliant! Never thought one could use ssh in a GUI. Exactly what many people have no doubt been looking for.

---

### Post by wabble on 2005-10-17
I did this a little while ago, read up here.. it maybe a bit old. But it works.

[NFS HOWTO]("http://http://www.tldp.org/HOWTO/NFS-HOWTO/")

---

