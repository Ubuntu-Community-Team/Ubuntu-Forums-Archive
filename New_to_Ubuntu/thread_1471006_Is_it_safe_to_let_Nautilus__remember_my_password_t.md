---
title: "Is it safe to let Nautilus  remember my password to access my HDD partitions?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Milkman08 on 2010-05-03
Hi all :)

I have to give my password to Nautilus each time I boot into UBUNTU.
I want to let it remember the password, But I'm not sure if it's safe or not.
So is it really safe?

---

### Post by _0R10N on 2010-05-03
> **Milkman08 said:**
> Hi all :)

I have to give my password to Nautilus each time I boot into UBUNTU.
I want to let it remember the password, But I'm not sure if it's safe or not.
So is it really safe?

What do you mean by each time?? login into Ubuntu or access the partition? Anyway, the answer to you question is relative. I mean, once you've mounted the partition, anyone who has access with your user/password will have access to them. If you didn't mount them, since he/she has the password, he/she can mount them by him/herself.

If you're concerned about securing your files, think of installing truecrypt and have those files in an encrypted volume.

---

### Post by Milkman08 on 2010-05-03
By each time I mean Loging into Ubuntu.
By it being secure I mean someone trying to take control over my computer over the internet while Nautilus mounted the drive and has my user's password.
I know ubuntu is safe from virus and ... but I heared not untill you allow them to.
Can anyone recover my user's password from Nautilus (which Nautilus has remembered it) over the internet?

---

### Post by warfacegod on 2010-05-03
> **Milkman08 said:**
> By each time I mean Loging into Ubuntu.
By it being secure I mean someone trying to take control over my computer over the internet while Nautilus mounted the drive and has my user's password.
I know ubuntu is safe from virus and ... but I heared not untill you allow them to.
Can anyone recover my user's password from Nautilus (which Nautilus has remembered it) over the internet?

Anything is theoretically possible but in this case its highly unlikely. Especially if you are using a properly set up Firewall.

---

### Post by doas777 on 2010-05-03
well stored passwords are kept encrypted in the keyring, so as long as you don't compromise the keyring storage (by disabling it because you don;t want to supply a password) you should be fine.

---

