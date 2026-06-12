---
title: "Transfering large amounts of data."
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by patrickaupperle on 2008-05-22
I have an Ubuntu laptop and my friend has a windows xp laptop. He wants to give me a large amount of data. My internet is too slow, so that is not an option. I was thinking of going through the Ethernet. I only had standard ethernet cables. I plugged us together and we managed to connect to the network. After that, I do not know what to do. Is this at all workable? Is there a better way to pull through ethernet or wireless?

---

### Post by Bubba64 on 2008-05-22
> **patrickaupperle said:**
> I have an Ubuntu laptop and my friend has a windows xp laptop. He wants to give me a large amount of data. My internet is too slow, so that is not an option. I was thinking of going through the Ethernet. I only had standard ethernet cables. I plugged us together and we managed to connect to the network. After that, I do not know what to do. Is this at all workable? Is there a better way to pull through ethernet or wireless?

Personally not ever figuring out how to do transfers from computer 2 computer I bought a 2 gig thumb drive.

---

### Post by patrickaupperle on 2008-05-22
> **Bubba64 said:**
> Personally not ever figuring out how to do transfers from computer 2 computer I bought a 2 gig thumb drive.

It is more like 20 gigs of data. I could use an external, but I was hoping for a way that only requires 1 transfer.

---

### Post by Bubba64 on 2008-05-22
> **patrickaupperle said:**
> It is more like 20 gigs of data. I could use an external, but I was hoping for a way that only requires 1 transfer.

Somebody will probably post with a link on instructions how to set up what you want, it can be done I just don't know how.

---

### Post by solitaire on 2008-05-22
Ok I've a quick 'n' dirty way

Once the 2 machines are connected.
on one of the machines install and start an FTP Server. if it's on the Windows then all he needs to do is point the FTP directory to be the main folder that stored the data you want. and he should set it for full access.

All you need to do is open Firefox and enter FTP://<windows IP address>

Hopefully you should see the files you require then it's just a "Copy / Paste"

Or 

You could set a SMB share and browse the network to his shared folder...

---

### Post by patrickaupperle on 2008-05-22
> **Bubba64 said:**
> Somebody will probably post with a link on instructions how to set up what you want, it can be done I just don't know how.

:)

---

### Post by tamoneya on 2008-05-22
solitaire's idea should be good for most purposes but I would like to add in ssh/scp.  The difference is that it includes encrypting.  I may jsut be a little paranoid but it is a good thing if you are transfering to servers outside your local network and there is some sensitive information.  You should note however that the encrypting makes the process slower than ftp.

---

### Post by patrickaupperle on 2008-05-22
> **solitaire said:**
> Ok I've a quick 'n' dirty way

Once the 2 machines are connected.
on one of the machines install and start an FTP Server. if it's on the Windows then all he needs to do is point the FTP directory to be the main folder that stored the data you want. and he should set it for full access.

All you need to do is open Firefox and enter FTP://<windows IP address>

Hopefully you should see the files you require then it's just a "Copy / Paste"

Or 

You could set a SMB share and browse the network to his shared folder...

Thank you, I did not even see your post. Would this work if I only have openssh? I already have open ssh up and running and am more familiar with this. So will this work? How fast (about) would it go?

---

### Post by solitaire on 2008-05-22
patrickaupperle

I'm not sure, I've never tried sharing from Linux to Windows. I've usualy used a USB drive :D

Hopefully someone in here will help you with your question :D

---

### Post by solitaire on 2008-05-22
> **tamoneya said:**
> solitaire's idea should be good for most purposes but I would like to add in ssh/scp.  The difference is that it includes encrypting.  I may jsut be a little paranoid but it is a good thing if you are transfering to servers outside your local network and there is some sensitive information.  You should note however that the encrypting makes the process slower than ftp.

The way patrickaupperle's post sounded was that the laptop and machine were in the same location with a wired Network between them (for the purpose of the file transfer) and not going via the net. That's why i didn;t bother with SSH or anything like that. As i said it's a quick 'n' dirty way :D

---

### Post by patrickaupperle on 2008-05-23
> **solitaire said:**
> The way patrickaupperle's post sounded was that the laptop and machine were in the same location with a wired Network between them (for the purpose of the file transfer) and not going via the net. That's why i didn;t bother with SSH or anything like that. As i said it's a quick 'n' dirty way :D

Is ftp easy to set up? And get rid of?

---

