---
title: "error fetching mail"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-05-01
I just got finished speaking with the folks at my internet provider - grrrr. They gave me to know in no uncertain terms that they provide support for windows users, and pretty much only windows users. I set up Evolution myself, so needless to say, I may have done something wrong.

When I hit send and receive I got this error:

Unable to connect to Pop.suddenlink.net 
No support for requested authenication mechanism

I don't really understand the whole key ring thing so I may have made a mistake there somehow.

So does this mean I can't use evolution at all or does anyone know of a fix for this?

any help would be appreciated

---

### Post by Titan8990 on 2009-05-01
You chose the wrong authentication type. There should be button to probe the server for the type of authentication it accepts but it doesn't always work.

---

### Post by mystmaiden on 2009-05-01
Thanks! Now how do I get back to the set up screen to fix that? Would it be easier to uninstall evolution and reinstall it?

edited to add: I found where to change the settings, but now it asks for smtp password, and I'm not at all sure which password they are looking for... Is this the one I have set up with suddenlink for that email? If so it is refusing it.

---

### Post by Ericyzfr1 on 2009-05-01
You may also want to double check that you format exactly as the server info shows, in your post you wrote "Pop" I don't believe there should be a cap.

---

### Post by Ericyzfr1 on 2009-05-01
> **mystmaiden said:**
> Thanks! Now how do I get back to the set up screen to fix that? Would it be easier to uninstall evolution and reinstall it?

edited to add: I found where to change the settings, but now it asks for smtp password, and I'm not at all sure which password they are looking for... Is this the one I have set up with suddenlink for that email? If so it is refusing it.

It is your password, the same you would use in webmail.

This article describes steps how to add an email account to Outlook XP.
Note: Before adding or modifying an email account, you will need to know the following information:
·
Your Suddenlink e-mail address and password
·
Incoming and Outgoing mail servers for your area
o  Incoming Mail Server = pop.suddenlink.net
o  Outgoing Mail Server = smtp.suddenlink.net

I got these information from the suddenlink website, it is not more complicated than Outlook.

---

### Post by mystmaiden on 2009-05-01
There was a bit about the keyring set up involved in this as well as the information [Ericyzfr1]("http://ubuntuforums.org/member.php?u=579644") listed, that may be where I fell short. Whatever the cause, it is refusing my email password.

---

### Post by Pete Abel on 2009-05-05
> **mystmaiden said:**
> There was a bit about the keyring set up involved in this as well as the information [Ericyzfr1]("http://ubuntuforums.org/member.php?u=579644") listed, that may be where I fell short. Whatever the cause, it is refusing my email password.

I'm told that with the POP3 email program, you have to use your email address INSTEAD of your UserID when you set up the program. Perhaps that will help?

---

