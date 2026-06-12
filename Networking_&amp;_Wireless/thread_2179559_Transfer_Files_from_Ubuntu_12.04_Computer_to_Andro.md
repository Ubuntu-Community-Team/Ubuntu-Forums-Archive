---
title: "Transfer Files from Ubuntu 12.04 Computer to Android Phone"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by Michael_Kolonay on 2013-10-08
Lately I have taken to the hobby of trying to make my Android powered LG Optimus G as in touch with my home network as possible when I am out of the house.  So far, I have managed to connect it to my ssh server via ConnectBot as well as share my desktop via a VNC server and bVNC Android.

Now I am looking to add the capability of transfering files from my home system to my phone.  Assuming this is possible (and can be done free of charge), my question is: what is the route I should take?

I have thought about using ssh (in this case a server on my phone).  I have found a program, SSHDroid, which allows me to connect to my phone as a server while I am on my home network, but I have not figured out how to make this program function remotely (I did use whatsmyip.org from the phone to find its IP address while on 3g).  

When the server up while on 3g the address it displays is: **sftp://root@fe80::548c:5e5a:b3b0:7508%rmnet_usb0:2222** (aside from the port number this doesn't mean much to me...) 

That said, I am not set on the idea of using the phone as an ssh server; as long as my goal of transfering files while connected to 3g is accomplished.

---

### Post by TheFu on 2013-10-08
That address is IPv6, but it is like localhost, 127.0.0.1.  You can get a certificate with that at [https://ipv6.he.net/certification/](https://ipv6.he.net/certification/) for free. Sign up and learn.  You really want to find the public IP address

Do you want to push or pull the files?  Pulling you can use sftp, scp, rsync over ssh .... each will be secure.  The ssh server at home already supports these things - well, you might want to install rsync.

If you trust 3rd parties, then there are lots of auto-sync apps like dropbox. If you stay below their total size, file size and total count of file limits, this can work.

Or you can do like I do and physically connect a USB port then drag-n-drop the files over.

BTW, I really hope you use a VPN when using any VNC.  Almost none of them support encyption and leaving a non-encrypted VNC on the internet is asking for trouble.

---

### Post by Michael_Kolonay on 2013-10-08
Thanks, The Fu,

I have found the public IP address on WhatsMyIP, but I am unable to reach the server on that address either.  I simply tried: **ssh -p 2222 root@"public-ip-address" **from the computer I want to use to connect to the phone.  After some time the connection simply times out.  Am I entering the command correctly?

Obviously the USB port is the best option when you have physical access to the computer, but as I stated, my goal is to be able to have complete access to all of my files from anywhere.  What I am trying to avoid is ever wanting for a file simply because I am not at home.  That said, dropbox or something of the sort would work, but it wouldn't be very optimized; I cannot keep my whole home network on dropbox, and having to upload a file to there and then download it to the phone seems like more work than necessary.

p.s.  And I am tunneling my VNC through ssh, so I think as far as that is concerned I am secure.

Update: Upon further review I thought about what The Fu was saying about the Ipv6 address being like local host.  This leads me to believe my ssh server program is not working correctly while on 3g (that would explain why there were so many settings about wifi).  I am using SSHDroid; anyone know of a better option for a program or a connection method?

---

### Post by TheFu on 2013-10-09
There is a client-side and a server-side for this stuff.  If you run the server on your home PC, then the client on the phone can "pull" files if there is a network connection at all - cell, wifi, whatever.  Then the network limitations of the cell network do not matter.  Just setup an internet accessible ssh server for your home PC just like anyone else does. Lots of howtos exist for lurkers. Seems that you already have this working. Then use any sftp, scp, ssh client on android. Be happy.

I'm not certain if you are trying to pull from the cell phone or push to the cell phone. Pushing will be nearly impossible, as cell networks often use private network addresses to protect their customers from unwanted outside connections. It is a security thing for the average - not-network-smart - consumer.

When you use ssh, please use key-based authentication, not passwords.  Also, secure the ssh connection on the computer side with **fail2ban** or **denyhosts** to prevent all the overseas hackers from having unlimited attempts against your passwords/keys. The default fail2ban settings probably do all you need if you use port translation on the router 2222 ---> 22 on the server.

BTW, OpenCloud might be worth a look too - I wasn't happy with the performance, but many people are.  I didn't like that using http was possible either. Should only allow https for stuff like that, IMHO.

Yes, tunneling VNC thru ssh is secure. Fantastic.

---

### Post by Michael_Kolonay on 2014-01-05
TheFu,

In reading through some of my old posts I realized I never solved this thread, and the answer seems simple now that I am looking at it with fresh eyes.  The server is on my home desktop computer, so I am trying to pull files to the cell phone.  That said, my real problem seems to be that I am unclear as to the syntax of command line file transfer via ssh.

Would it be too much to ask for a simple example?  For clairity, lets forget the cell phone for now and pretend I am working from a laptop trying to connect to my home server.  What would the command the send a file test.txt found in the home folder of the server to the home folder of the laptop?  For the life of me I cannot find a simple example like this which would illustrate the basic syntax.

---

### Post by tgalati4 on 2014-01-05
```
man scp
```

[https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)

---

### Post by Michael_Kolonay on 2014-01-05
Perhaps I misunderstood TheFu, but from what I can tell he seemed to indicate that it possible to connect the host desktop via ssh and then copy files with scp or the like.  However from what I can tell the command I am looking for looks like this:

[B]scp <file> <username>@<IP address or hostname>:<Destination>
[/B]
thus based on the example I was hoping to get it would look like this:

[B]scp test.txt <username of phone>@<IP address of phone on 3g>: /storate/sdcard0/Test/test.txt
[/B]
I don't know what the <username of the phone> is because I never had an option to change it from whatever the default is (and I have not rooted it), and as I stated previously I cannot get the IP address of the phone while on 3g.  Admitedly, this is a bit of a bait and switch since I only asked for and example for a laptop (which assuming it was connected to a normal network would have an easily identifiable IP and username).

---

### Post by TheFu on 2014-01-05
[http://kb.iu.edu/data/agye.html](http://kb.iu.edu/data/agye.html)

If you don't know the username and password on the phone, then you can stop. It will not work.  You may be able to "pull" the files to the phone, however.

The source and target can be local OR remote.  See the link above for example.

ssh is the remote terminal.

scp is the rcp version to remotely copy files .... rcp = remote copy.  scp is an interface like the old rcp to make changing scripts easier.

sft is the "ftp" version to remotely copy files ... ftp = file transfer protocol.  sftp is an interface like the old FTP to make changing scripts easier.

ssh, scp, sftp all use openssl for encryption.

As I said above ... er ... 2+ months ago ... **use an scp/sftp client on the phone.** I doubt you will be able to push files to the phone without knowing the userid and password to the phone. The only real option is to **pull files.**

---

### Post by tgalati4 on 2014-01-05
If you install ES File Manager on the Android phone and you are connected via WiFi, then moving files back and forth is easy.  I have no idea how to do it through 3g without using a 3rd party file service like dropbox or Ubuntu One.

---

### Post by Michael_Kolonay on 2014-01-05
ES File Manager seems to have potential.  Can anyone see a reason I cannot connect through the app to my server as an sftp server?  Simply typing in my server address does not get me access.  I'm just guessing here, but could it have something to do with the app not supporting public key authentication?

---

### Post by r3dd on 2014-01-05
Is port 22 open on your router and firewall all the way to the server?

---

