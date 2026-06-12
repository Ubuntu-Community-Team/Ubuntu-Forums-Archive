---
title: "Default new install username and PW?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by weaslesripmyflesh on 2008-12-24
I looked at Ubuntu by installing a live USB stick. Looked good so I installed a dual boot.

I started the install and went to bed because it had to DL a bunch of files.

When I got up I booted it and was confronted with a username and password. I tried blank first then Ubuntu in both then "username" in it's box and "password" in it's box, Nothing works, any ideas?

---

### Post by HSKR on 2008-12-24
Should be your first name (all lower-case) and then whatever password you decided to use, unless, for some odd reason, it didn't ask you for a password in the installation.

---

### Post by weaslesripmyflesh on 2008-12-24
Nope that doesn't work and I am trying everything with a cap too. Do I need to re-install or is there a secret new install password designed to keep noobs from using Ubuntu ; )

---

### Post by albinootje on 2008-12-24
> **weaslesripmyflesh said:**
> Nope that doesn't work and I am trying everything with a cap too. Do I need to re-install or is there a secret new install password designed to keep noobs from using Ubuntu ; )

Boot in "recovery mode" first.
Choose "drop to root shell prompt".
Type in :
```

passwd your_user_name

```
Where your_user_name is the user you've created during the Ubuntu-installation.
While typing in the new password no "*" characters will be visible.
Hit <enter> key after filling it in.
And then, when it asks, fill the new password in again.
After that type in :
```

telinit 2

```

---

### Post by zipperback on 2008-12-24
> **weaslesripmyflesh said:**
> I looked at Ubuntu by installing a live USB stick. Looked good so I installed a dual boot.

I started the install and went to bed because it had to DL a bunch of files.

When I got up I booted it and was confronted with a username and password. I tried blank first then Ubuntu in both then "username" in it's box and "password" in it's box, Nothing works, any ideas?



You might find the following page helpful.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


Good luck. Please let me know if it helps you.

- zipperback
:popcorn:

---

### Post by weaslesripmyflesh on 2008-12-24
Good answer :) thank's, I am booting over now and crossing my fingers but this sounds like the right answer so thank's again.

---

### Post by weaslesripmyflesh on 2008-12-24
I just realized something. I think that both of these responses assume I created a username and that I remember it. I am going to give it a try anyway and try the usernames I might use but I only ever use one long password and it didn't work with any of the usernames I tried.

---

### Post by albinootje on 2008-12-24
> **weaslesripmyflesh said:**
> I just realized something. I think that both of these responses assume I created a username and that I remember it. I am going to give it a try anyway and try the usernames I might use but I only ever use one long password and it didn't work with any of the usernames I tried.

You can also create a new user at the "root shell prompt" (See: #4) like this :
```

adduser adrianus

```
Where adrianus would be the name of your new user.

---

### Post by kansasnoob on 2008-12-24
I have no answer but I've also wondered, "when you buy a computer with Ubuntu pre-installed how do you personalize it"?

I've never done it, but I've rebuilt upwards of 30 computers for folks that were still stuck with Win 98 and ME, and I know how to reassign "admin/root" privileges on a machine that I've created, but how does one change those privileges on a machine you have no knowledge of?

Obviously anyone can pop in a Live CD and just reinstall, even to a new partition, and access any files on the drive.

OTOH I didn't think the install procedure would complete without someone entering some personal info, along with the partitioning choice, etc.

---

### Post by ugm6hr on 2008-12-24
> **kansasnoob said:**
> I have no answer but I've also wondered, "when you buy a computer with Ubuntu pre-installed how do you personalize it"?

An OEM install allows you to set username and password after installation.

> When I got up I booted it and was confronted with a username and password. I tried blank first then Ubuntu in both then "username" in it's box and "password" in it's box, Nothing works, any ideas?

You have to supply some details re:location, keyboard, HD, username, password, computer name before Ubuntu will install.  If it didn't ask for those, you either did an OEM install, or your LiveUSB did not install properly.

---

### Post by weaslesripmyflesh on 2008-12-24
Thank's so much for your help, it works. Now on to other things like wifi :(

---

### Post by albinootje on 2008-12-24
> **weaslesripmyflesh said:**
> Thank's so much for your help, it works. Now on to other things like wifi :(
Let's try it. Please provide us with the following output :
```

sudo update-usbids
lspci
lsusb
lshw -c Network
lsb_release -a

```

---

### Post by kansasnoob on 2008-12-24
> **ugm6hr said:**
> An OEM install allows you to set username and password after installation.



You have to supply some details re:location, keyboard, HD, username, password, computer name before Ubuntu will install.  If it didn't ask for those, you either did an OEM install, or your LiveUSB did not install properly.

Thank you! I'd always wondered about that.

---

### Post by tomahawk 1705 on 2009-01-10
Hi I'm new to Ubuntu and this Ubuntu forum I just wanted to thank Zipperback for the great info link to re setting your username and password from grub the step by step pic's were the best. 

I was desperate I just finished installing Ubuntu the day before and really did not want to do it all over again because of my stupid actions that led me down this road.

Next time I go clicking around in login preferences I will think more logically eg. ask myself did I make a username and password?
should I  have written this info down somewhere for later reference?.

Thanks

---

