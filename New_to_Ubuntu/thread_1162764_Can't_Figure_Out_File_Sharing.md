---
title: "Can't Figure Out File Sharing"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by DArtagnon on 2009-05-18
Just like the title says.  I want to be able to share directories from my computer so that they are accessible from other computers on my LAN with no username or password required.

If the other computers could just go Places -> Network -> dartagnon-desktop -> sharedFolders and grab my shared files, that would be ideal.

---

### Post by labinnsw on 2009-05-18
[Have a look at this tutorial]("https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html"). I used it to network a virtual XP with my 8.04. It is intended for a real network.

I would give it a read through before I start doing anything.

After installing and configuring Samba, the sharing part is simple.

---

### Post by nothingspecial on 2009-05-18
All computers Ubuntu?

```
sudo apt-get install openssh-server
```

In your menus Places > Connect to Server

Change the Service type to ssh

In the server box type username@ipaddress (your computers ip address can be fount by right clicking on the network applet in your panel and choosing connection information)

Check the add bookmark box then choose a bookmark name then your other computer will be accessible from your menus for ever more.

As long as you tell your router to use static ips

---

### Post by clive littlewood on 2009-05-18
Hi

If all computers are Ubuntu then try Giver.

It's in the repos and also see entry in my Blog (see below)

This is a great sharing app.    :D

Clive

---

### Post by 3rdalbum on 2009-05-18
You don't need to edit plain-text configuration files to use Samba.

Install the Samba server package, right-click the folder you want to share, and go to Properties. Under the "Sharing" tab, click "Share this folder" and "Allow guest access". Then there's a button called "Create share". Click that, and your share is created.

Too easy.

If you want more control, for instance you want to create an invisible share or limit access based on username, you can use system-config-samba from the repositories. Bear in mind that Mac OS X doesn't provide any way for users to access invisible shares, so avoid them if you have Macs that need access.

---

### Post by tom56 on 2009-05-18
> **3rdalbum said:**
> You don't need to edit plain-text configuration files to use Samba.

Install the Samba server package, right-click the folder you want to share, and go to Properties. Under the "Sharing" tab, click "Share this folder" and "Allow guest access". Then there's a button called "Create share". Click that, and your share is created.


You don't even need to install the package. When you click Sharing it will offer to install the relevant bits for you.

---

### Post by 3rdalbum on 2009-05-18
> **tom56 said:**
> You don't even need to install the package. When you click Sharing it will offer to install the relevant bits for you.

Does it now? That's pretty cool, I know the old Shared Folders program used to do that.

---

### Post by DArtagnon on 2009-05-19
> **nothingspecial said:**
> All computers Ubuntu?

```
sudo apt-get install openssh-server
```

In your menus Places > Connect to Server

Change the Service type to ssh

In the server box type username@ipaddress (your computers ip address can be fount by right clicking on the network applet in your panel and choosing connection information)

Check the add bookmark box then choose a bookmark name then your other computer will be accessible from your menus for ever more.

As long as you tell your router to use static ips

This is what I ended up doing.  Thanks for all your suggestions.

---

### Post by bacardiandwatermelon on 2009-05-19
> **3rdalbum said:**
> You don't need to edit plain-text configuration files to use Samba.

Install the Samba server package, right-click the folder you want to share, and go to Properties. Under the "Sharing" tab, click "Share this folder" and "Allow guest access". Then there's a button called "Create share". Click that, and your share is created.

Too easy.

If you want more control, for instance you want to create an invisible share or limit access based on username, you can use system-config-samba from the repositories. Bear in mind that Mac OS X doesn't provide any way for users to access invisible shares, so avoid them if you have Macs that need access.

This method doesn't work for me in jaunty, I had to stick with editing the smb.conf file. It would create a share but windows machines could never access the folder :-(

Oh and thanks for finding Giver... I needed something like that.. Cheers :-)

---

