---
title: "sharing folders"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-07-21
I just dual booted my hp win 7 machine with ubuntu, and I would like to basically sync with my little machine that I have been using ubuntu with, how can I just share folders, I can't seem to get there with my network tab, I installed samba, but still can't share anything, what am I doing wrong?

---

### Post by plucky on 2010-07-21
> **beelzebufo said:**
> I just dual booted my hp win 7 machine with ubuntu, and I would like to basically sync with my little machine that I have been using ubuntu with, how can I just share folders, I can't seem to get there with my network tab, I installed samba, but still can't share anything, what am I doing wrong?

Right click on the folder you want to share and select **Sharing Options**.

Tick the boxes and it will install the required software if it not already installed.

Then Log out and log back in and you should now be able to share the folder.
(**Right Click > Sharing Options > Tick Boxes**)

Good Luck

---

### Post by gdonwallace on 2010-07-21
You are on the right track.

You have to have Samba installed so that Ubuntu and Windows can see each other across the network.  But you also have to pick a folder and create the share for it.  Be careful of the name of the share, Ubuntu will warn if the name is too long, other than that; once the share is setup it should be fine.

---

### Post by HermanAB on 2010-07-21
Howdy,

In order of increasing difficulty:
1. FTP
2. SSH
3. NFS
4. Samba

To give you some idea, FTP and SSH 'Just Works' right out of the box.  The only people that have trouble with those two, are the ones who insist on changing the defaults.

NFS requires two lines of configuration: One line on the server and one line on the client.  

Samba however, requires hundreds of lines of configuration and has a guide book that is two inches thick.

Soooooo, pick your poison.

---

### Post by Morbius1 on 2010-07-21
> **HermanAB said:**
> Samba however, requires hundreds of lines of configuration and has a guide book that is two inches thick.

Soooooo, pick your poison.
The method proposed by plucky will produce this on a given share:
net usershare info:
> [j]
path=/windows/J
comment=
usershare_acl=Everyone:F,
guest_ok=yBy my count that's 5 lines and I didn't even have to take my shoes off to count that high. :)

---

### Post by beelzebufo on 2010-07-21
so, I actually have to set this up via command line?  I thought there should be a way to do it just via graphical interface... I'm really new to this so can I just get a step by step, my router is a net gear set up on windows, but the two computers are ubuntu, thanks

if I go into my network tab, I double click windows network, then workgroup and I get an unable to mount location error

---

### Post by Morbius1 on 2010-07-22
The five lines I referred to above is done automatically without your intervention.

If you followed plucky's advice you did something like this:

Open Nautilus
Right click on some folder say ... Documents
Select "Sharing Options"
Select "Share this folder", "allow others to create and delete..", and "Guest access"
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
You should have just created a public samba share.

If you run the following command you should get this output:
```
net usershare info
```> [documents]
path=/home/your_user_name/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


---

### Post by Shalmainia on 2010-07-22
I have a problem, I changed all the computers in the household to the workgroup "mshome" because the majority of those computers are Windows 7. I then shared my directories. However, I can see them, they can't see me.

Also, I used to have this folder, now I don't... so how do I remove it?

I typed in ```
net usershare info
```
```
info_fn: file /var/lib/samba/usershares/streaming is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```

---

### Post by Morbius1 on 2010-07-24
> info_fn: file /var/lib/samba/usershares/streaming is not a well formed usershare file.
info_fn: Error was Path is not a directory.```
net usershare delete streaming
```

---

