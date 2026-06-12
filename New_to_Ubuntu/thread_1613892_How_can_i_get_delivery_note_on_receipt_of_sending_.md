---
title: "How can i get delivery note on receipt of sending gmail.."
date: 2010-11-05
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-05
Is it possible to get delivery acknowledgement after sending a mail.So that i am able to know that he/she has opened my mail..I know gmail doesn't have this feauture..Do any email client have this feauture..?

---

### Post by Seq on 2010-11-05
> **getyourkarthick said:**
> Is it possible to get delivery acknowledgement after sending a mail.So that i am able to know that he/she has opened my mail..I know gmail doesn't have this feauture..Do any email client have this feauture..?

From experience, Outlook and Evolution both support this, but it would depend on your recipient deciding to return the requested read receipt. I never do, and have actually disabled the prompt.

There are other methods, such as embedding an object that references an external, traceable object (an image on your own server). Most of these other methods are no longer reliable due to being used often in spam that functionality was added to avoid this.

There is no way to guarantee a recipient received (or read) an email other than phoning them and asking.

---

### Post by Unhyper on 2010-11-05
Thunderbird has the feature, but it depends on the recipient's email provider and/or email client whether it will work. Maybe your SMTP server too. Gmail doesn't support MDN, so there goes that.

---

### Post by lisati on 2010-11-05
Read receipts and delivery notifications can be a bit hit and miss: as previously mentioned, the recipient can choose not to send a notification or disable that option in their email client. Embedding an image from your server can depend on the recipient of the email deciding to view images, and Microsoft Outlook has been known to tell porkies: I receive "Not read" notifications from MS Outlook users who have read the message in the preview panel and then deleted it; this happens often enough for me to have my server reject said messages as bogus.

---

### Post by mastablasta on 2010-11-05
read message works only sometimes in evolution. however it is best to used delivery message in thiunderbird as it seems to work better. basically it will just notify you if message was delivered but not if it was read (which is up to the user if they want to reply or not).
 
otherwise i had no issue with this in outlook but could be because of service providers on the other side not my settings...

---

