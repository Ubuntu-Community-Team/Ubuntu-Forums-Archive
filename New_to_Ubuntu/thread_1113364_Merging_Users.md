---
title: "Merging Users"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by myolbug on 2009-04-01
I have 8.10 32 bit on an older computer.  I am having some weird issues with only one of the user profiles.  Unfortunately I now need info from that user profile.  Can I as root merge all of them into one so that I can have full access to all of the info?

If I can, can you please provide step by step code?

Thanks,
R

---

### Post by kanikilu on 2009-04-01
Because you say that there is something wrong with one of the profiles, I probably wouldn't try to do some sort of "automatic" merge (if that can even be done). I would just move the files you need into your new profile and then change the owner/group to yourself.

So, if you have /home/gooduser and /home/baduser, and, for instance you wanted the "Documents" directory from the bad profile, you could do this:

```
sudo mv -i /home/baduser/Documents/* /home/gooduser/Documents/
sudo chown -R gooduser:gooduser /home/gooduser/Documents
```

Just repeat that for everything you want to move over.

Alternatively, if you no longer need the "baduser" profile at all, you could move the whole directory to be in your "gooduser" directory:

```
sudo mv /home/baduser /home/gooduser/
sudo chown -R gooduser:gooduser /home/gooduser/baduser
```

You won't be able to login as "baduser" anymore after this, so be sure that's ok before doing it.

Lastly, you can also do pretty much all this in a GUI if you prefer. Just run **gksu nautilus** from a terminal. Just don't forget to change the owner/group to your "gooduser" when you're done.

---

