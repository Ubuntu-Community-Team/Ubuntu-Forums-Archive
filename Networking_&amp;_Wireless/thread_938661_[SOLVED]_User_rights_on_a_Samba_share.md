---
title: "[SOLVED] User rights on a Samba share"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by NeillHog on 2008-10-05
I have a samba share set up on my Kubuntu PC.
It is working great. My son can see it from his XP PC.
I set up a samba user with my son's login name and password.

Here is the share out of my smb.conf
[SharedFiles]
    path = /home/neill/SharedFolder/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = neill
    force group = neill

Up to now everything is great but ...

... there is always a but isn't there ...

He appears to have full rights on the share and can also delete the files. And this despite my having set up the rights on the shared directory so that only the owner has all rights, others are read only.

Is this normal?
What can I do to change things so that he only has read access?

Thank you in advance for any and all help.
Neill

---

### Post by NeillHog on 2008-10-05
Having spent an afternoon looking in to this, I am still non the wiser.
Is it maybe something to do with the line 
directory mask = 0755
in the conf file.

This line suggests that the owner can do everything but that the user also has most rights.

I am sure this is trivial but it is well over my head.

Thank you!

---

### Post by Iowan on 2008-10-05
I used to think I understood Samba - the "new" version has made me much less confident.  My suspicion is that the **force user=neill** line gives everyone the same rights as **neill**.  You might comment out the **force user=** line - leave the **force group=** line, and give the group read-only rights.  Another option might be to change the share to read-only, and see if the owner can still add files.

---

### Post by NeillHog on 2008-10-06
Thank you for that.
I really don't understand Samba but I will try both your ideas and get back to you to let you know if either work.
Thanks again
Neill

---

### Post by superprash2003 on 2008-10-06
change
read only = no
to
read only = yes

---

### Post by NeillHog on 2008-10-07
Is it really that easy?
Thank you so much.
I am currently 600 kilometres away from my PC (PC in Germany and I am in Italy) but as soon as I get back I will try that.
Wish I was going home tonight so I could write "it works!"
Neill

---

### Post by Kemon on 2008-10-07
You can install a very simple apllication
```
sudo apt-get install system-config-samba
```

Then go to System -> Administration -> Samba
You can also set a password on the share with different users and pw.

---

### Post by NeillHog on 2008-10-08
Now I really need to get home and try that out.
You mean I really didn't need to spend a year getting Samba to work? I could have just installed this application and done it all from there?
Thank you.
I will try that as well tonight.
Neill

---

### Post by NeillHog on 2008-10-08
Thank you both of you.
It is now as I wanted it.

sudo apt-get install system-config-samba
installed the program as Kemon said it would.
I can use that to decide if a share is writable or not.

But it has added a line
valid users = Max, alison, avahi-autoipd, avahi, backup, bin, daemon, dhcp, games, gnats, haldaemon, hplip, irc, klog, list, lp, mail, man, messagebus, neill, news, nobody, proxy, root, sync, sys, syslog, uucp, www-data

Any idea why it did that? The only users that I needed were Max and Neill. Who are all these users anyway? I deleted everyone except Max and neill. Do I really need this line?

Also the tip about changing read only worked perfectly.
Thank you both of you.
Neill

---

### Post by Iowan on 2008-10-08
Those all look like internal system "users".  Dunno why the easy way added all that... but it might be an argument for the hard way... plus, look how much you learned ;) Having the **valid users=** probably isn't a bad idea, cleaning out the extras is probably good, too. Congrats - mark this one [SOLVED] (Under Thread Tools).

---

### Post by NeillHog on 2008-10-09
@Iowan

I definitely agree with you about the "hard" way being the way where you learn the most.
In future I will be able to set up my shares manually. :-)

But it is not bad for Linux when there are "easy" ways. A lot of people want easy and will stay with some pretty awful OS because it is easy.

A last question.
If I want to give some one else rights on exactly the same directory but give them read and write - how do I do this? I understand that I have now given both max and neill read rights on this share. Do I set up an identical share with write rights and different users allowed?

Thanks!
Neill

---

### Post by superprash2003 on 2008-10-09
you could try creating another share with the same share folder link and setting read only to no and mentioning the users

---

### Post by NeillHog on 2008-10-09
OK!
Will do and get back to you with the results.
Neill

---

### Post by warchief_ryan on 2008-10-09
You can do it with the file/group permissions, but you'll have to remove "force user =" and "force group = " so not everyone that accesses the share is using that one username and group. Might also need to tweak the create mask and directory mask as well.

Adding another share to the same shared folder seems like a bad idea to me as there might be conflicts of some kind.

---

### Post by Iowan on 2008-10-09
There's another option called **write list=** that gives write permissions (supposedly overrules read-only).  Another option is to create a group and include the group in **valid users=** or **write list=** - group membership would determine access. Again, the force user/group would interfere.

---

