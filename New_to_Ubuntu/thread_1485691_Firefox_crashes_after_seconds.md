---
title: "Firefox crashes after seconds"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by il pepe on 2010-05-17
ever since i upgraded ubuntu to 10.04, firefox (3.6.3) crashes after seconds.
I can loaded the standard google page, but when i want to go to another page it crashes.
Same thing in safe mode...

How can i solve this?
How do i install an older version of firefox, or wouldn't that change anything?

---

### Post by Kobalt on 2010-05-17
Do you have any plugin/extension installed for your Firefox? Did you try disabling them?

---

### Post by il pepe on 2010-05-17
i did, in safe mode, nothing changed...

mayby it's the theme? if i run in terminal then a lot of messages pop-up about the theme no longer being supported. I don't know how to change this, as i can't get in to the add-ons section without crash...

---

### Post by Kobalt on 2010-05-17
Try to move your Firefox profile elsewhere (it in the hidden .mozilla directory of your Home folder), to create a new profile then you'll manually import bookmarks or history form the old one.

---

### Post by il pepe on 2010-05-17
still the same :-(
and i need ff for citrix receiver

---

### Post by il pepe on 2010-05-17
mayby extra info: when i load a page i actually can see parts of the page, and then i get the crash report...

---

### Post by Kobalt on 2010-05-17
Did you try to completely remove and purge Firefox through Aptitude ?

---

### Post by il pepe on 2010-05-17
i tried it just now. removed everything.

I reinstalled it now and now firefox won't even start: fragmentatio fault and failed to start libmoon...

Any help now?
Doesn't work in safe mode either

---

### Post by Kobalt on 2010-05-17
Try to search for that libmoon package in Synaptic (it's a Silverlight plugin) and remove it completely.

---

### Post by il pepe on 2010-05-17
BUKA!! Fixed!!!

Thanks a lot!!!

That is what i call live support!!

---

### Post by Kobalt on 2010-05-17
You're welcome :)

---

### Post by ibm450 on 2010-06-13
> **Kobalt said:**
> Try to search for that libmoon package in Synaptic (it's a Silverlight plugin) and remove it completely.


beautiful, this fixed my problem with FF closing after it loads up.
):P

---

