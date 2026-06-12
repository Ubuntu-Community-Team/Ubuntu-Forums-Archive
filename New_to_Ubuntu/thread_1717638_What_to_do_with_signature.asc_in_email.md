---
title: "What to do with signature.asc in email?"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-03-30
I receive emails with signature.asc attached, for example security announcements from Ubuntu. I presume this attachment is a GPG signature.

If I wanted to verify the email, I presume I would use signature.asc. But how? What do I do with it?

---

### Post by Locke_99GS on 2011-03-30
You set up Evolution or Thunderbird (or others, perhaps?) to use GPG. If you have the keys installed for the ubututu-security team (or whoever sends you those messages) then the mail reader can tell you if it is authentic or not.

---

### Post by Paddy Landau on 2011-03-30
Thanks for the reply.

As I understand it:

[LIST]
[*]First, I need to set up Thunderbird to use GPG. I don't know how to do that; is it complex?
[/LIST]

[LIST]
[*]Then, I need to get the public key for the person sending the email. Presumably it would be stored on a public server. I think I can figure out how to do this.
[/LIST]

---

### Post by Locke_99GS on 2011-03-30
For Evolution, you just need to have a private key - it'll use your default gpg signing key if you have multiple. When creating a message, I go to *Options > Sign with PGP* (or something like that) and it signs it. 

When reading new mail, if you have the proper public key it'll automagically test the signature and let you know with a giant green bar in the message saying that it is properly signed. I've never seen a bad signature, but I'd speculate that it would be a giant red bar in such a case.

For Thunderbird, I'm not sure how to do it, I only know that you can :) Perhaps, given you have gpg set up with your private key and the public key's of others, it might automatically work as well??? 


I put a link to my public key with in the signature of my emails.

---

### Post by Paddy Landau on 2011-03-31
Thank you, I figured it out.

There is a great add-on for Thunderbird called [Enigmail]("https://addons.mozilla.org/en-US/thunderbird/addon/enigmail/").

I found it easy to use, and it even led me through setting up my own key.

Thanks for prompting.

---

