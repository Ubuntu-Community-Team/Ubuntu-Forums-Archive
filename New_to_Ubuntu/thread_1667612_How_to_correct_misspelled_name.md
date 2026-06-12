---
title: "How to correct misspelled name"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-15
Hi Community:

I reinstalled 10.04 yesterday, and spelled my name wrong at the first step of the installation.

I spelled "Smith" as "Amiht."

I guess that I should have typed a little slower.

Now, the logon screen says: "Phil Amiht" and I want to change it to "Phil Smith"

How do I do that?

Thank you,

Phil Smith
Duluth, GA

---

### Post by SPr on 2011-01-15
See ```
man chfn
```.

---

### Post by Nickjpost on 2011-01-15
Hi! You can edit it by clicking on System, then Administration, then select Users and Groups. Highlight your name (or misspelled name as it were, haha). Near your current name is a "Change..." option; click on that then you can edit your name.

---

### Post by Old Jimma on 2011-01-15
Hi:

I tried:

sudo chfn -f Phil Smith

got error: User "Smith" does not exist. (I'm having an existential crisis, now!)

Then, I tried: System > Administration > Users and Groups > change (next to the "Phil Amrht" account, then highlighted "Amrht" and changed it to "Smith." Then I rebooted.

The change didn't take. Still "Phil Amrht" at the login screen.



Thanks,
Phil SMITH

---

### Post by Nickjpost on 2011-01-15
Phil, try to create a guest login, log on as guest (or whatever you named the logon) and edit your name in System>Admin>Users & Groups as I previously stated and see what happens

---

### Post by Old Jimma on 2011-01-15
Hi Nickjpost:

Thanks for your persistence. Your suggestion worked perfectly!

No more "Phil Amiht"!!

Thanks!
Phil SMITH

---

### Post by Nickjpost on 2011-01-15
Great! Glad I could help. Would you mind marking the post as <Solved> please?

---

### Post by SPr on 2011-01-16
> **Phil Smith said:**
> Hi:
I tried:

sudo chfn -f Phil Smith

got error: User "Smith" does not exist. (I'm having an existential crisis, now!)

You are absolutely correct. The man page is misleading and I apologise for not spotting it when I read it prior to posting.

It implies that the correct usage is:
chfn -f "Phil Smith"
(use quotation marks because there is space in the full name.)

The usage is:
chfn -f username
So if you log in as phil then use
chfn -f phil

---

