---
title: "Guest session without &quot;indicator applet session&quot;?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by llakais on 2010-07-15
Hello,

I recently removed the "indicator applet session" from my top panel.  I figured I didn't need any of the shortcuts/options it provided, until I realized that I don't know how to enable a "guest session" without it.

Does anyone know how to start a guest session without the applet?

Thanks so much!

---

### Post by ubunterooster on 2010-07-15
You mean logging in to a guest account?

I use Ctrl+Alt+L, wait for locking, wiggle mouse, then instead of entering my regular password, log in as the guest acct.

---

### Post by llakais on 2010-07-15
> **ubunterooster said:**
> guest acct.

do you mean a special account that you created?  I wasn't aware that Ubuntu had a "guest account" option.

Also, sorry I forgot to mention before that I'm running 10.04

---

### Post by ubunterooster on 2010-07-15
Sorry I confused the two terms "account" and "session" (the guest account is not a default, I created it)

---

### Post by llakais on 2010-07-15
cool - do you mind posting what options you used for the guest account you created?

---

### Post by ubunterooster on 2010-07-15
screenshot shows permissions

(password is set to "password" so it can be guessed easily)

---

### Post by llakais on 2010-07-15
thanks!

---

### Post by ubunterooster on 2010-07-15
You are welcome, although I feel inadequate in forgetting what a guest session is (perhaps I'll remember in the morning)

---

### Post by mcduck on 2010-07-16
> **ubunterooster said:**
> You are welcome, although I feel inadequate in forgetting what a guest session is (perhaps I'll remember in the morning)

The guest session creates a new, temporary, user account with extremely minimal permissions (pretty much only access to account's own home is allowed). When the temporary user logs out the whole account and it's home directory gets destroyed.

So it's a great way to let other people to use your computer, they have no possibility of messing your system or seeing your files, and on the other hand whatever they do on the machine won't be left behind so they can safely check their e-mails or their bank accounts or whatever.

I suppose the biggest difference between using the guest session and normal guest account is that the guest session gives even less permissions to the guest user, and that it always gives the guest user a fresh, untouched desktop and then destroys it afterwards. (of course you can still configure the guest session's desktop just like you can configure the default desktop any other newly created users will get, by putting the configuration files and other stuff into /etc/skel).

---

### Post by llakais on 2010-07-16
> **mcduck said:**
> it always gives the guest user a fresh, untouched desktop and then destroys it afterwards.

Is there any way to configure a guest "account" in this fashion?  For instance, sometimes I want to lend my computer to a family member, and it would be nice if all the stuff they download/save would be wiped automatically like it is for a guest "session."

That way I could tell family members the password to the account and I wouldn't have to be around for them to check email, etc. on my comp.

any ideas?

---

### Post by ubunterooster on 2010-07-16
McDuck said> **mcduck said:**
> ...of course you can still configure the guest session's desktop just like you can configure the default desktop any other newly created users will get, by putting the configuration files and other stuff into /etc/skel.

---

### Post by llakais on 2010-07-16
Whoops, doh!

---

### Post by mcduck on 2010-07-17
> **llakais said:**
> Is there any way to configure a guest "account" in this fashion?  For instance, sometimes I want to lend my computer to a family member, and it would be nice if all the stuff they download/save would be wiped automatically like it is for a guest "session."

That way I could tell family members the password to the account and I wouldn't have to be around for them to check email, etc. on my comp.

any ideas?

Like I said, you can just put any stuff, including configuration files, into /etc/skel, and they will be automatically included when a home directory is created for any new user account. I usually create a fresh, new user, then adjust the desktop and all the settings to my liking, and then copy all the related setting files from that account's home into /etc/skel. (Afterwards I just remove that account itself as I don't need it any more.)

But your situation  has the problem that you can't log directly into the guest session, it can only be started by somebody who already has an account and is logged in (meaning that you can only start it from the panel applet on a user's desktop, not directly from the login screen).

Normal guest account can of course be made accessible form the login screen but you'd need to do some manual tweaking to automatically wipe guest account's home directory. And also an open guest account could count as a security vulnerability, especially on a machine that's connected to any network...

---

### Post by llakais on 2010-07-17
> **mcduck said:**
> some manual tweaking to automatically wipe guest account's home directory.

Yeah, do you any any specific info on how to do this?

I know it is a little bit of a vulnerability, but as I would only give the password to my immediate family members (who I obviously trust!) I think it should be okay.

thanks again man!

---

### Post by mcduck on 2010-07-17
> **llakais said:**
> Yeah, do you any any specific info on how to do this?

Sorry, I can't help you there as I've never doe that. I use the guest session for random people who wish to use my computer, and set up their own (real) accounts for all the people who I want to be able to use the machine when I'm not around. After all, if they need to use the machine regularly then they would probably like to be able to save some files and keep their settings as well.. Of course I don't give them anything else than basic user privileges, and I also make sure they have no access to my home dir.. :)

---

### Post by llakais on 2010-07-17
> **mcduck said:**
> I use the guest session for random people who wish to use my computer, and set up their own (real) accounts for all the people who I want to be able to use the machine when I'm not around. After all, if they need to use the machine regularly then they would probably like to be able to save some files and keep their settings as well.. Of course I don't give them anything else than basic user privileges, and I also make sure they have no access to my home dir.. :)

That sounds like a good plan, I'll go with that.

---

