---
title: "Mounting iPod touch with root access"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-10-01
How can I mount an iPod touch in Ubuntu with access to the root and not only the media folder?

I tried to do things with ifuse and it didn't work or I didn't understand.

I succeeded to mount my iPod with ifuse without root access in /home/user/iPod but now I would like to get it work with root access. 

So how can I mount my iPod touch with root access (something with afc2)?

help!

---

### Post by toiletgoose on 2010-10-18
Hi There... this is what I did:

1. Create a directory /media/ipod for example.
2. Permission this directory to the user.
3. Issue the command "ifuse /media/ipod --root" as the user.
4. The ipod should be mounted and you should see the "/var" directory.

I think this depends on how you jailbroke your ipod... I have OS4 on my 2nd Gen and I think that the AFC2 process is running on the device to allow for root.

Hope it works for you. I just had to remember how to do it this morning and found your post while poking around.

---

### Post by Avidanborisov on 2010-10-25
hi, Can you explain from the beginning? 
I have a jailbroken iPod touch 2g mc model 4.0 and AFC2 thing works on Windows.
When I try I get an error : "the mount point specified does not exist" 
Help!

---

### Post by Avidanborisov on 2010-10-31
Someone?

---

