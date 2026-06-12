---
title: "Help setting up a file server with Samba"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by kainzero on 2009-12-30
I just installed Ubuntu on an old box of mine, but I really cannot figure out how to share files.

Ideally this computer would just have a bunch of movies and music that it can stream to other computers.

I read some Samba guides and everything and used the file configuration tool in the Administration menu, and I configured Firestarter to open up the Samba ports, but it's not working quite right.

The network consists of a Linux machine, 2 Windows XP Desktops, a Windows XP netbook, an Imac, and a Windows 7 Desktop.

On my Windows 7 machine, the file server doesn't show up. Typing the network IP address gives me some permission denied message.

On my OS X machine, the file server does show up, but clicking on it still gives me a permission denied.

On my Win XP netbook, it shows up and I can click on it, but I get permission denied. However, if I go to Run... and type in the URL, I can access it and I can create folders and move stuff in them, but I can't rename the folders. 

I've been remotely controlling it using TightVNC on the Win7 machine, so I'm really not sure what's going on. What logs do I check, what errors do I look for, how do I know if the whole thing is running correctly?

Thanks!

---

### Post by Jose Catre-Vandis on 2009-12-30
For samba follow [this]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") to the letter and you'll be serving with samba

---

### Post by benfindlay on 2009-12-30
I assume you have successgully installed samba and configured your shares that way. Have you already edited the smb.conf and specified a network name for your server etc? If not there's a good guide [here]("http://ubuntuforums.org/showthread.php?t=202605").

What you will also need to do is add users to the permitted list in samba, if you haven't already. Type the following:```
sudo smbpasswd -L -a yourusername
```Set the password you want to use (twice), then type```
sudo smbpasswd -L -e yourusername
```to activate the user account.

That work now?

---

