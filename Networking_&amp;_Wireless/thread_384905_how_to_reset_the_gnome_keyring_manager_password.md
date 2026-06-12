---
title: "how to reset the gnome keyring manager password"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by digitalramble on 2007-03-15
OK, I'm really irritated.  

I'm using the network manager, and it seems to think I have a keyring password.  I have NO IDEA what it is, I never set it.  I cannot seem to find anyway to reset this password.  I can't find documentation within the network manager, and I do seem to have the gnome keyring manager, but I am extremely unamused by the fact that 1) when I start it  IT  ASKS ME FOR THE PASSWORD which, of course, I can't give it, and that 2) the help file is LESS THAN HELPFUL.  In fact it consists of one chapter, "Introduction," which contains one word, "Welcome!"  Honestly.

So my question is: how do I reset the keyring password? 

I would, of course, like to obliterate this "feature" entirely, but right now I would just settle for actually setting the password.

<rant>
Why is it that network manager does not offer an option to turn off the keyring?  I understand the security issues, yadda yadda yadda blah blah blah.  Fine, default the keyring on, BUT PROVIDE THE OPTION TO TURN IT OFF.  Not all of us are storing nuclear power plant plans on our laptops, 'k?  Thanks.
</rant>

Sigh.

Any help at all would be appreciated.  I'm very very very VERY tired of manually entering the damned hex key in after going through the circus that is the keyring manager..

---

### Post by spd106 on 2007-03-15
You could try deleting the keyring.

To do this look in the ~/.gnome2/keyrings directory, then delete the default.keyring file.

This won't disable the network manager prompt, but it will allow you to create a new key with a password you know. Despite the obvious security problem most people just use their log in password.

There are various thread in this forum about using pam-keyring to authenticate automatically at log in.

---

### Post by Bjoern on 2007-09-20
I had the same problem, but after renaming the default.keyring, my system had lots of problems, didn't start properly etc. So I think that is not the way to go (I was able to recover by starting in rescue mode and restoring the original default.keyring).

Any other ways to reset the password?

---

### Post by kswenson on 2007-10-21
don't move it to a new place in the same directory...
   move it somewhere completely different and then reboot.

---

### Post by raxso on 2007-12-09
Thanks it works.... :)

---

### Post by TMartin on 2008-02-24
Found another way for deleting keyring with forgotten password (I am using Gutsy). Launch gnome-keyring-manager (will ask for forgotten  password, ignore it), show all keyrings by menu View/Keyrings. Select right one (i my case it was login, don't select session keyring) and remove it by menu Keyring/Delete Keyring.

---

### Post by liniaal on 2008-03-28
> **spd106 said:**
> You could try deleting the keyring.

To do this look in the ~/.gnome2/keyrings directory, then delete the default.keyring file.

This won't disable the network manager prompt, but it will allow you to create a new key with a password you know. Despite the obvious security problem most people just use their log in password.

There are various thread in this forum about using pam-keyring to authenticate automatically at log in.

thank you, this worked deliciously.

---

