---
title: "Remove ssh"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by spillage2 on 2010-08-10
hi,

can anyone tell me how to remove ssh fully. 

i seem to have messed up setting up my keys and would like to start from scratch.

i ran sudo apt-get remove openssh-server but when i reinstall i still get a problem with my public key.

thanks

spill.

---

### Post by Bachstelze on 2010-08-10
Your keys are personal files, they will not be affected by system changes, such as reinstalling a package.  If you want to delete your keys, the are in ~/.ssh (filenames generally start with id_).

---

### Post by spillage2 on 2010-08-10
ok thanks so by deleting them I should be able to start again. 

the problem is every time i try to connect i get permission denied (public key)

the forums talk about copying the public key via ssh but I cant do that so i just created the authorized_keys folder in the .ssh file and copied it with a pendrive.

---

### Post by Bachstelze on 2010-08-10
> **spillage2 said:**
> ok thanks so by deleting them I should be able to start again. 

the problem is every time i try to connect i get permission denied (public key)

the forums talk about copying the public key via ssh but I cant do that so i just created the authorized_keys folder in the .ssh file and copied it with a pendrive.

You should've copied the public key *before* disabling password authentication. ;) Can't you just copy them using an USB stick or something?

---

### Post by endotherm on 2010-08-10
whenever you want ot remove a package and it's config files, use 'purge' instead of remove:
```
sudo apt-get purge openssh-server
```

---

### Post by spillage2 on 2010-08-10
ok thanks all 

i have deleted everything in my .ssh folder and managed to create a key and send it to my server over ssh to use to log in and that is all up an running well.

I take it i need to create a new key on each comp I am going to use to connect to my server ie one more comp on my home network and an xp comp at work or do I just copy the key from the first comp i created and use that?

if i need to create a new key for each comp how would i be able to send the new key to the server over ssh?

sorry for coming across as a bit dunce but never been that involved in comps and it seems ubuntu is drawing me into very new surroundings.

---

### Post by Bachstelze on 2010-08-10
> **spillage2 said:**
> 
I take it i need to create a new key on each comp I am going to use to connect to my server ie one more comp on my home network and an xp comp at work or do I just copy the key from the first comp i created and use that?

You can copy them over.

---

### Post by marshmallow1304 on 2010-08-10
> **endotherm said:**
> whenever you want ot remove a package and it's config files, use 'purge' instead of remove:
```
sudo apt-get purge openssh-server
```

Purge does not remove personal configuration files (i.e. anything in $HOME).

---

### Post by spillage2 on 2010-08-10
ok so i can copy the dsa file from my first client comp and copy it to my client comps.

thanks

spill.

sorry being a right dimwit.

just forgot to delete the know_host data again....:( once this was done i was able to log in with password and move key over.

---

### Post by pavi_elex on 2012-03-09
```
sudo apt-get remove --purge openssh-server && sudo apt-get install openssh-server
```

---

### Post by nothingspecial on 2012-03-09
This thread is old and must be sent back to bed.

Closed.

---

