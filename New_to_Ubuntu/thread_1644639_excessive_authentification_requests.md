---
title: "excessive authentification requests"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by KWLLC on 2010-12-13
`My Linux box is is a secure location where no one else can access it without my permission. I would like to reduce or eliminate the recurring requests for authorization that is being demanded of me. I have perused the doc as much as I can follow and must admit defeat. When I authorize, a key appears in my top panel that indicates that i have elevated my access privileges but it evidently self-expires very shortly thereafter. I would like to extend that state to a nearly permanent status (say 1 authorization required for any single user session). Any help on how to accomplish this? Right now it's more irritating that MS's ACL req on Vista!

---

### Post by CharlesA on 2010-12-13
You can change the timeout.

See [here]("https://help.ubuntu.com/community/RootSudo") and [here]("https://help.ubuntu.com/community/RootSudoTimeout").

---

### Post by oldos2er on 2010-12-13
Or run **sudo -i** which opens a root terminal for as long as you need it.

---

### Post by KWLLC on 2010-12-21
Please excuse the lapse in my replies. The flu has just swept through my home and I have just recovered enough to check this thread.
I think I have misstated myself on this matter. What I am referring to is the authentication box that pops up like in the Ubuntu Software Center requiring me to enter my password to proceed to d/l or remove software. Sometime it seems to extend across several actions but other times seems to pop up for every request. I hope this clarifies my question.

---

### Post by CharlesA on 2010-12-21
You are prompted for your password in order to do anything that requires system files to be modified. You can change the timeout for sudo, but I don't know if that would effect gksudo.

---

### Post by sisco311 on 2010-12-21
> **CharlesA said:**
> You can change the timeout for sudo, but I don't know if that would effect gksudo.

Yes, it would, but USC and most modern GUI applications use policykit. policykit's timeout is hard-coded so you can't change it without re-compiling it. :)

---

### Post by CharlesA on 2010-12-21
> **sisco311 said:**
> Yes, it would, but USC and most modern GUI applications use policykit. policykit's timeout is hard-coded so you can't change it without re-compiling it. :)
Didn't know that. Thanks for the info. :)

---

