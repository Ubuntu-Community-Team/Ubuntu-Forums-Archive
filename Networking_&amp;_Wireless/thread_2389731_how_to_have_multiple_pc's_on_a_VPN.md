---
title: "how to have multiple pc's on a VPN"
date: 2018-04-20
forum: Networking &amp; Wireless
---

### Post by matt18 on 2018-04-20
ello all. 

Thank you for reading this and contributing to my education:)

I am curious to know if what i would like to learn can be done

Scenario:

I have a small LAN, 10 computers that are desktops. I have 3 laptops that are in any part of the united states or the world at any given time. Some may even be 1 mile away. 

Here is my goal. Set up a VPN server so that all 3 laptops, no matter how far from the homebase they are, can connect to the VPN at the same time, if possible, and be able to see and differentiate which one of the desktops they are browsing through. All 10 desktops must be accessable via VPN and once a laptop is hooked into said VPN, be able to see 10 different "folders" or "drives" that let the user know which desktop is which.

Unless VPN doesnt work like that and all 10 desktops are pooled into a single folder or drive sorta speak.

thanks

---

### Post by SeijiSensei on 2018-04-21
Life will be easier if you use a central server where all the users' folders are stored. It sounds like you want to have peer-to-peer sharing of the individual client machines. That's a lot harder to manage than a central server.

---

### Post by matt18 on 2018-04-22
DANG IT!!! my reply didnt stick. 

ok cool. thanks for the reply. Is there a way to make it so when a desktop creates a new folder on their machine that it syncs with the server so anytime they add files to that folder it adds it to the central server? these are windows machines.  

I know with a lan, that if i right click, share the folder, it shows up under network places on my machine and the other users in the network. im looking for something simular but with vpn. 

How would a central server idea work? would each user have to copy files to it or is there a way to share a folder between the server and user? IE on the server, i would want a folder named products and its shared with desktop 1 which is in charge of products.

thanks

---

### Post by hrsetrdr on 2018-04-22
Once configured, NFS allows file sharing between workstations via a server.

 [https://help.ubuntu.com/lts/serverguide/network-file-system.html]("https://help.ubuntu.com/lts/serverguide/network-file-system.html")

---

### Post by TheFu on 2018-04-24
With all Unix-based systems, networking can be fairly seamless using either VPNs or ssh for encrypted connections.  When you add in Windows, things are a little harder and a  VPN is normally the solution. Each VPN client could have the same or different connection certificate.  If they use the same cert, then they'd connect to the same vpn server.  You can make different client certs for each vpn client, but manually managing which cert goes with which client sorta sucks.

With the VPN, you effectively make a remote system part of the internal LAN.  OpenVPN has 2 major modes which have trade-offs for Windows networking and performance and security.  While you **can** allow clients to "browse" the network just like they are physically on the same LAN, most people don't do that over performance considerations.  There is lots and lots of openvpn guides with recommendations out there.  Each client can be provided with a static IP over the VPN with bi-directional access, if you like, but there are security and performance implications in doing that.

As for automatic sync of data between different systems, that is something that most people solve using rsync, dropbox, owncloud, nextcloud or seafile as a solution.  Pick one.  Try it out. See how it works for your needs.  I use nextcloud through a VPN and it is fine. If I didn't want to use the VPN all the time and still wanted access to the storage and sync, then I'd feel better using seafile. I would never use a cloudy storage provider like dropbox, but that's just me.

I'd also say that if you have time and are willing to create what you want, then almost anything is possible.  There are lots of alternative secure connection methods available beyond the well-know VPN solutions.
You might find that i2p, tinc, retroshare, Direct:Connect and some of the newer, private, social networking solutions that work offline will meet your needs. There are probably 20 others trying to accomplish the same stuff. And don't forget the simple options like sftp/scp. Those are very handy and there are great clients for every OS out there.   Most of these alternatives require 1 system to be on the same IP over the internet to manage all the connections to the other systems which don't have static IPs.  The single-server solution, like SeijiSensei suggests, is the most common solution.

---

### Post by SeijiSensei on 2018-04-25
> **matt18 said:**
> How would a central server idea work? would each user have to copy files to it or is there a way to share a folder between the server and user? IE on the server, i would want a folder named products and its shared with desktop 1 which is in charge of products.

For Windows users, you would install Samba on the Linux box, set up some directories where users would store files, and use "Map a Network Drive" in Windows to set, for instance, S:\ to a shared directory on the server "\\servername\shared".  Then placing files on the server is as easy as dragging-and-dropping them to drive S: or its subdirectories. You could give users private directories as well and map H:\ to each user's home directory on the server.  

If only user bill needs to see folder products, then you can create a user on the Ubuntu server named bill and put the products directory in /home/bill.  Map drive H:\ on bill's machine to /home/bill.  There are ways to do this automatically if you delve into the details.

If other users need to see the products folder, you can create groups of users and grant those groups limited or full access.

Start here: [https://tutorials.ubuntu.com/tutorial/install-and-configure-samba](https://tutorials.ubuntu.com/tutorial/install-and-configure-samba)
Also: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

I wouldn't use the SMB protocol over the Internet for security reasons, but over a VPN you should be fine.

If you have Ubuntu users, you can share directories with them using the *nix-native [NFS file system]("https://help.ubuntu.com/community/NFSv4Howto").  You can run both Samba and NFS on the same server to distribute files to Windows and *nix clients.

One big advantage to this method -- backups.  Buy a cheap portable USB drive, attach it to the server, and write backups to it every night.  I assure you that most, if not all, of your users won't be making their own backups.

---

### Post by matt18 on 2018-04-25
Awesome. Thank you much for writing this out and helping me out.  I ill be reading and taking notes. 

Once again, thanks:)

---

### Post by TheFu on 2018-04-25
NFS provides native Unix file permissions.
Samba/CIFS do not.  Samba permissions are per-share.

That is a huge consideration sometimes when you need people to work together.

I don't use CIFS or NFS over VPNs. The performance usually isn't good enough.  For situations like that, when I have a Linux client, something like sshfs is workable and secure.  But sometimes sftp really is all that is needed.

Depending on the requirements for file access, whether the clients are on the same network as the server(s), then there are lots of choices.

With a full VPN, almost anything can be attempted and it will likely work.

---

### Post by 1clue on 2018-04-25
+1 for using a NAS of some sort.

The VPN server you're talking about is available on almost any home router. I prefer OpenVPN. A coworker has an Asus monstrosity with 3g/4g radios on it, their vpn works great.

If you can get a static ip address for the vpn endpoint then that's best. Otherwise you need to do ddns, and some routers limit the ddns server you can use.

If you value security you might want to give serious thought to your configuration. While it's very easy to get at every computer on the internal network using a vpn you may want to arrange things so that a vpn user can only access certain devices and certain directories on the nas. And if possible, turn off wifi completely or at least put it on its own less-functional network.

---

### Post by SeijiSensei on 2018-04-25
> **TheFu said:**
> NFS provides native Unix file permissions.
Samba/CIFS do not.  Samba permissions are per-share.

That is a huge consideration sometimes when you need people to work together.
That hasn't been my experience with small groups of users.  They typically need a home directory and maybe a few common shares.  That seems to be the case here.

For a shared folder you can use [Unix groups]("https://www.samba.org/samba/docs/using_samba/ch09.html") to control access in Samba.  Sometimes I've used "force user" and "force group" in Samba when the ownership of files doesn't matter.  In that case they are all owned by the user and group specified in the "force" directives.  (My use case was a shared Windows accounting application that managed its own authentication.)

Like you, I prefer sshfs or sftp for secure connections.  Often they can be launched from the file managers in Ubuntu.  For instance, KDE Dolphin supports fish:// and sftp:// URLs to create on-the-fly secure connections.  I upload files to my remote webserver that way, dragging-and-dropping them from a local to a remote window in Dolphin. (These files are actually "doubly" encrypted since the SSH traffic is sent over a static-key OpenVPN tunnel to the server.)  I don't see any evidence those protocols can be accessed directly from the Windows file manager.  It looks like you need a separate client like [WinSCP]("https://winscp.net/eng/index.php").  If the users are fine with that as a solution, then I'd go with just a server running sshd, no NFS or Samba, and the usual set of *nix user and group management tools.

---

### Post by TheFu on 2018-04-25
I've used WinSCP.  It supports drag-n-drop on Windows and ssh security is fairly well understood.

The main reason NOT to use ssh-based scp/sftp as a solution is if smartphones/tablets need to do it too.  ssh stuff is considered security enough for use over the internet provided that ssh-keys are used, not passwords.  Just be certain to block all connections from places in the world that never need access - perhaps most foreign countries?   And install fail2ban to dynamically block IPs that fail authentication more than a few times.  When using keys, authentication failures basically never happen.

OpenVPN runs on Android without root and setting up an openvpn server on a Linux machine isn't _that_ hard.  It isn't trivial, but it isn't super hard, experts-only, either.

But depending on the types of users and the types of file/directory access desired, there might be some easier or more interesting, yet secure options. For productivity documents, I'd go a different direction.  For media files, I'd go a different direction too.  For huge amounts of files that all the clients need, there are still other methods.   Reference (i.e. read-only) or edit or clone and modify, each would have different techniques.   Just depends.

---

