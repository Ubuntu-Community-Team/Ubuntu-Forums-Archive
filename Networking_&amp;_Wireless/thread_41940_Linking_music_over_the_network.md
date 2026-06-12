---
title: "Linking music over the network"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by spiffytech on 2005-06-15
I'm trying to get my Ubuntu computer to access my music collection over the network via amarok. I can find the files with the network browser, but I can't link to the folder. Amarok won't browse the network, so I'm trying to make a symbolic link to the music to the music folder, dut it doesn't work

---

### Post by ecliptik on 2005-06-15
What OS is the other computer using and what network file system are you using? Samba? NFS?

If both machines are unix based I'd use NFS, I've found it's a little simpler to use and the performence of it is better if you want to steam music/movies over a network.

---

### Post by Mr. Electric Wizard on 2005-06-15
I can't find the thread right now, but I think you have to mount a share to a location, a location on the linux pc.
Then browse to that location in your music program...

---

### Post by mjsoccer1 on 2005-06-16
I had a that exact problem... thanks to everyone on here, I figured it out.  If you are using Samba (or if its a Windows machine), add this line to /etc/fstab:
*mount -t smbfs //remoteservername /mnt/Music*

You will have to make a folder called Music in your mnt directory, and you will have to use either apt-get or synaptic to get the smbfs package.  Hope this helps!

---

### Post by spiffytech on 2005-06-16
The other computer is running SomplyMepis 3.3.1-1, a Debian-based distro. The media folder on it has a symbolic link to another partition on it's drive. Using Samba, I mounted the folder, but I can't navigate inside it after the linked portion of the folder heiarchy in Amarok or the Ubuntu machine.

---

