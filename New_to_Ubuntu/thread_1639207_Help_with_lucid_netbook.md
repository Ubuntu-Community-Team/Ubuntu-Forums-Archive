---
title: "Help with lucid netbook"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by xerograv on 2010-12-06
Hi there been running lucid netbook on my hp laptop.
Been running perfectly until I began to run out of space on my partition. I deleted and moved a bunch of files and got back all the space.
Then All my programs disappeared ie the buttons up the side were all gone except favs files and system. Some of the system options are gone too like ubuntu software center and others.

Any Ideas?
Thanks.

---

### Post by snowpine on 2010-12-06
The obvious conclusion is that something you deleted is causing this behavior. Since I don't know what you deleted, I'd suggest going into your Trash and restoring the files one by one until you find the culprit. (Hopefully you haven't emptied your trash yet!)

---

### Post by xerograv on 2010-12-06
hmmm, I only deleted some avi files and removed a drum machine program, a dvd writing program. didn't think they had that much to do with the system.

And yes, unfortunately  I did empty the trash of avi files and maybe a few pics. could that really have done this?

---

### Post by bodhi.zazen on 2010-12-07
> **xerograv said:**
> hmmm, I only deleted some avi files and removed a drum machine program, a dvd writing program. didn't think they had that much to do with the system.

And yes, unfortunately  I did empty the trash of avi files and maybe a few pics. could that really have done this?

Sometimes configuration files become corrupt. You can test this by logging in as another user. If things look good, your first user has corrupt configuration files. In that event, if you delete them they will automatically be regenerated. Just take care not to delete any data you want to keep.

---

### Post by xerograv on 2010-12-07
Ok thanks, I only have one user so I thought ok, i'll set up a new one. Apparently that function is gone as well. 
At the log in screen I decided to choose the gnome desktop (as opposed to the netbook one) and it seems there is no applications on this computer anymore. I have shortcuts to Firefox (and Skype in netbook desktop) but no open office, gimp etc.

I thought well, why don't I try to open a document, it worked fine my excellent half finished soon to be famous novel ;) opened in open office so I think all my applications are there. 

Could this be something up with the panel?

---

### Post by xerograv on 2010-12-07
> **bodhi.zazen said:**
> Sometimes configuration files become corrupt. You can test this by logging in as another user. If things look good, your first user has corrupt configuration files. In that event, if you delete them they will automatically be regenerated. Just take care not to delete any data you want to keep.

I was able to create a new user and it seems your right bodhi. 

Can I delete the corrupt user now or will that make it worse?

---

### Post by bodhi.zazen on 2010-12-07
> **xerograv said:**
> I was able to create a new user and it seems your right bodhi. 

Can I delete the corrupt user now or will that make it worse?

What I do in this case is boot to recovery mode and as root move the old user's home and make a new one.

```
mv /home/old_user /home/old_user.bak
mkdir /home/old_user
chmod old_user:old_user /home/old_user
```

Then reboot and you should be good to go.

Move any data you want, but not configuration (. or dot files) from the old home to the new. Once you are done, delete the old home.

Alternately use the new user and delete the old one.

Either way, you should be good to go.

If you really want, you can try to determine what exactly was corrupt, but you may not be interested in the gory details =)

---

### Post by xerograv on 2010-12-08
Well thankyou very much **bodhi.zazen**
It appears that my user was on the skids for awhile now. I thought my laptop was limited but my new user profile works amazing now. All the graphics and sound are perfect.

Thanks for your time!

---

### Post by bodhi.zazen on 2010-12-08
> **xerograv said:**
> Thanks for your time!

You are most welcome. It is painful when the config files become corrupt.

---

