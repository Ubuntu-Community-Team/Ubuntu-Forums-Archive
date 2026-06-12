---
title: "Network problems, can't see workgroup"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by johnb820 on 2006-10-29
Hi everyone

I am having a few problems with my network on a freshly installed edgy getting it to see the rest of my computers.  Right now I got my internet working by disabling and enabling my eth0 which tells me that my eth0 connection can work properly.  I can even ping both those two computers.  However, when I try to view my network which has 1 ubuntu box and 1 xp box it doesn't see either of them or the workgroup.    

Lastly, whenever I restart edgy, my network is not recognized whatsoever, no internet.  I have been searching on these forums for two days now trying to fix these problems but nothing seems to work.  Any help would be much appreciated because I have run out of ideas.

---

### Post by johnb820 on 2006-10-29
I was able to see the other computers by manually putting in an IP address

smb://192.168.0.102

I am still not able to see workgroup under windows network though.

---

### Post by featherking on 2006-10-29
Can you ping your xp box's host name, i.e. ping RON? If not

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

now trying pinging RON(or whatever your xp box's name is), All that should allow you to ping a windows machine name by installing the Windows Internet Naming Service (WINS), perhaps that will solve your workgroup issue because now you can see their names?

---

### Post by johnb820 on 2006-10-29
I did what you said and I can now ping names, but they still do not appear under windows network.

---

### Post by featherking on 2006-10-29
what do you see if you type smbtree in the terminal, it will ask for your password

---

### Post by johnb820 on 2006-10-29
WORKGROUP
        \\UPSTAIRS                      upstairs server (Samba, Ubuntu)
failed session setup with NT_STATUS_IO_TIMEOUT
        \\SPAREROOM                     Upstairs
                \\SPAREROOM\JMB Bkups      
                \\SPAREROOM\C-Erins Room   
                \\SPAREROOM\SharedDocs     
                \\SPAREROOM\IPC$                Remote IPC
        \\BARKERJB                      Samba 3.0.22
                \\BARKERJB\print$         
                \\BARKERJB\File System    
                \\BARKERJB\downstairs     
                \\BARKERJB\IPC$                 IPC Service (Samba 3.0.22)
                \\BARKERJB\ADMIN$               IPC Service (Samba 3.0.22)

---

### Post by featherking on 2006-10-29
Well that command is similar to the view workgroup command in windows. So right there you can see that everything should be working fine, because your computer can see all those shares in your workgroup. 

Where are you going to try and view the workgroup? Are you going to Places>Network Servers?

---

### Post by johnb820 on 2006-10-29
I go to network servers, and it sees "windows network" then when I enter there I see nothing.  I know I should be seeing workgroup because as you said it should all be there.

---

### Post by featherking on 2006-10-29
check and see if you have this installed in synaptic

libgnomevfs2-extra

also check if you are missing any of the libgnomevfs2 packages. These are what allow you to view certain things in nautilus

---

### Post by johnb820 on 2006-10-29
Sorry, I don't know if you are still there or not, but I do have the libgnomevfs2 packages all in order.  I can't figure out for the life of me why I don't see the workgroup.

---

### Post by LinuxJosh on 2006-10-29
I'm Also in the same boat, i could share files with windows networks in dapper but now since I have done a fresh install with edgy I can not.

---

### Post by johnb820 on 2006-10-29
Surprisingly, I can actually share files, but my problem is that the network does not show up under network servers.

---

### Post by navlelo on 2006-10-30
I think I have the same problem, which is further discussed in [this thread](http://ubuntuforums.org/showthread.php?t=286528) which helped me (to some degree).

> **featherking said:**
> check and see if you have this installed in synaptic

libgnomevfs2-extra

also check if you are missing any of the libgnomevfs2 packages. These are what allow you to view certain things in nautilus
I've checked the libraries, and as far as I can see with my newbie eyes, everything looks properly installed (I taught myself Synaptic today :KS ). I reinstalled libgnomevfs2-extra and libgnomevfs2-bin just to be on the safe side. -> No change.

---

### Post by Bezvardis on 2006-11-15
I have exactly the same problem. The packages seem to be in place, ping works (but only when I do it with numbers), my other computer (MacOSX) can see Ubuntu share, but Ubuntu does not see the Mac. Any insights or possible new solutions in this since the last posts?

---

### Post by KermitJr on 2006-12-30
I'd just like to add that this was working fine one day and the next, poof!... running kubuntu.  I now can't see anything when browing remote:/ and then sometimes I see mshoe, sometimes not.

I ran smbtree and it shows the other computers but I noticed their ip addresses were incorrect.

not sure what's going on.  I have wins turned on to my laptop (thought that might help) but nothing yet.

KermitJr

---

### Post by Liv3dN8as on 2008-02-29
I just wanted to say that I am also having this problem. I am using 7.10 and right now the only way that I can easily get around this is to type smb://<name>or<ip> and bookmark it. Hey it works.

---

### Post by enquirerPuli on 2008-05-01
I had the same problem, so I googled the quiestion in 100 ways, and still don't know the answer.
But
I realized that when I turn off my firewall (Firestarer) almost everything works properly.:-D
So it seems to me that it should be some kind of iptables configuration problem, but still don't know how to solve it.
I think it might help some experts to localize the problem.

---

