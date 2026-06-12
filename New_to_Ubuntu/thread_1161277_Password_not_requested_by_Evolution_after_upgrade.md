---
title: "Password not requested by Evolution after upgrade"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Newbie-Doo on 2009-05-16
Hello.

I just upgraded from Gutsy to Hardy. Since then, Evolution no longer asks for my (user) password when I send emails. I have the "Save password" box un-checked. I found a similar topic which suggested un-checking "Save password" in the Receive Email tab also, so I did that too, but Evolution is happily sending and receiving emails anyway.

Several posts I found seemed to prefer things this way, but I liked typing in my password in order to send emails. This is hardly a major problem, I know, but I would prefer to revert to my old habits if I can.

Thanks.

Newbie-Doo

---

### Post by guywithcable on 2009-05-16
Does your email server require a password? Is "Server requires authentication" checked?

---

### Post by Newbie-Doo on 2009-05-17
> **guywithcable said:**
> Does your email server require a password? Is "Server requires authentication" checked?

Yes (I'm fairly certain, although it's been a while) to the first question, and Yes to the second.

Thanks.

---

### Post by mprince on 2009-05-17
Check the Gnome menu and see if you have:

Applications>Accesories>Passwords&Encryption Keys

Then click on the Passwords tab.

Your Evolution password may be stored there.

---

### Post by Newbie-Doo on 2009-05-17
> **mprince said:**
> Check the Gnome menu and see if you have:

Applications>Accesories>Passwords&Encryption Keys

Then click on the Passwords tab.

Your Evolution password may be stored there.

In the Passwords tab it shows my POP address. (I think - format is pop://me@mailserver.) But when I click on Properties, the password box is empty.   ???

Thanks.

---

### Post by mprince on 2009-05-17
If you want to be prompted for your password in Evolution then you would 'delete' that key.

Make sure it's highlighted.

Edit>Delete Key

---

### Post by Newbie-Doo on 2009-05-18
> **mprince said:**
> If you want to be prompted for your password in Evolution then you would 'delete' that key.

Make sure it's highlighted.

Edit>Delete Key

It won't let me delete it. When I hit Delete, I get a dialog box that says:

Allow application access to keyring?
The application 'seahorse' (/usr/bin/seahorse) wants to access the password for [pop account] in the default keyring.

There are 3 boxes, with the choices Deny, Allow Once, and Always Allow.

As a card-carrying newbie who has no idea what Seahorse is, I hit Deny, after which, nothing happens.

Thanks.

---

### Post by mprince on 2009-05-18
Try to delete that pop key again, but this time click 'Allow Once'. That will delete it.

---

### Post by Newbie-Doo on 2009-05-18
> **mprince said:**
> Try to delete that pop key again, but this time click 'Allow Once'. That will delete it.

Yep, that did it. The deletion worked, and my test email prompted me for my password! You've made an old codger's day!

Thank you very much.

Newbie-Doo

---

### Post by mprince on 2009-05-18
Seahorse is just the application you were just using. It stores all of your encryption keys and passwords.

You've definitely earned a Newbie-Snack :popcorn:

---

### Post by Newbie-Doo on 2009-05-18
Thanks for that snack - I will enjoy it! I haven't learned the appropriate reciprocal gesture yet, but be assured you deserve it in my book!

Also thanks for the heads-up about Seahorse. After a couple of other more basic things to learn, I'm going to start reading up on encryption. (Gotta learn some terminal commands first, I think.) And I've already found several great places to start here on this forum - what a great resource!

Newbie-Doo

---

