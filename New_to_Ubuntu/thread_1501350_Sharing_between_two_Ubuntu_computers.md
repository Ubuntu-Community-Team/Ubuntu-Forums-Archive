---
title: "Sharing between two Ubuntu computers"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by humphreybc on 2010-06-04
I have a laptop running 10.04 and a netbook running 10.04.

I want to be able to easily access some folders in my laptop's home directory from my netbook, while I'm in the house. When I'm away from home, I've got Dropbox.

I've right clicked on the folder I want to share, chosen to share it, given it a name etc and it appears under "Network" in Nautilus on my netbook - but when I go to connect, it prompts for a password. I enter in my user password, which is the same for both laptop and netbook, but nothing happens - the dialog goes away and then pops up again, prompting for a password.

And yes, I know about SSH and "Connect to Server." I actually have a server that I've set up like that. But I shouldn't have to use SSH to share across two desktops.

---

### Post by llawwehttam on 2010-06-04
You are using samba to do this and your samba password is different to your user password.

Open a terminal and type:

```
smbpasswd
``` and it should promp you to give a new samba password

---

### Post by humphreybc on 2010-06-04
It asks me for my old SMB password. I don't know what that is, it's a fresh install.

---

### Post by llawwehttam on 2010-06-04
```
sudo smbpasswd youusername
```?
Dude I thought you were the ubuntu geek lol

---

### Post by humphreybc on 2010-06-04
I only pretend to be :P

Hooray for progress, thankyou!

---

