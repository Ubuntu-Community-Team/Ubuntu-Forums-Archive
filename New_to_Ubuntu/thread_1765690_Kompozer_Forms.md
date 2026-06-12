---
title: "Kompozer Forms"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by quantumspiral1919 on 2011-05-23
I am trying to set up a form on my website using Kompozer.  I would like to have the form results emailed to me when the responder clicks the submit button.  anyone know how to do this?  I tried to get onto the Kompozer help forum, but several days and no permission given to join.

Thanks in advance for your help here.

---

### Post by compmodder26 on 2011-05-23
Not sure about Kompozer as I've never used it, but to simply email the form contents, set the action value to

action="mailto:youremail@yourhostingprovider.com"

---

### Post by quantumspiral1919 on 2011-05-23
Thanks for your reply.  I tried it, it didn't work.  The only choice is "Action URL", and method choices are "GET" and "POST"    I don't know how to make it email me the results.

---

### Post by compmodder26 on 2011-05-23
> **quantumspiral1919 said:**
> Thanks for your reply.  I tried it, it didn't work.  The only choice is "Action URL", and method choices are "GET" and "POST"    I don't know how to make it email me the results.

Is there an option in Komposer to edit the HTML directly?

Edit:  Just looked at a screenshot of Kompozer and there should be tab at the bottom that says "Source".  Click that and look for a tag that looks like "<form" (assuming you are using a single form on the page and not multiple).

---

