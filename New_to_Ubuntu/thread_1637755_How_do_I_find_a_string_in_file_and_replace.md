---
title: "How do I find a string in file and replace?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2010-12-04
I am writing a script that needs to look at the /etc/etter.conf file and find a value like:

dhcp_lease_time = 1800 (the 1800 can be anything not always 1800)

and take the user input and replace it.

I am using a simple bash script, would sed work?

What the best way?

Best Regards

---

### Post by ratcheer on 2010-12-04
You should be able to call sed from your bash script. It boggles the mind all the different ways you could do this. I think a sed command would look something like:

s/orig-string/new-string/

But, I'm not completely sure. I usually just do things like that in vi. I have used sed, but not so much.

Perl would be a fun way to do it, too.

Tim

---

### Post by J0hnnyBr@v0 on 2010-12-04
Yes, I agree....perhaps sed scares me a bit.  I can do it a few ways, but I want it to work for more than just my configuration.  I want to share the script with my team members, and if they don't have it exactly like mine...it may not work for them.

So instead of using sed to change line 28 in my config file.  Its probably "cleaner" to look for a known global value such as dhcp...

I'll try your suggestion and paste the results.

Best Regards,
Eric

---

### Post by J0hnnyBr@v0 on 2010-12-04
I took your advise and ran the following command.

sed 's/dhcp_lease_time =//dhcp_lease_time = 30/ /etc/etter.conf

and got the following:

dhcp_lease_time = 30 1800

So it replaced it, but I want the original value to go away as well.  So when the replacement is done it would've been:
dhcp_lease_time = 30 1800

I guess in my script I could always grep dhcp_ and then use " " as a delimeter and replace the value is a certain field...but again...not sure how to accomplish as of right now.

Best Regards,
Eric

---

### Post by ratcheer on 2010-12-05
That is why I never preferred to use sed. The string definitions and delimiters are so obtuse that the code usually ends up being long sets of slashes and backslashes - totally unreadable.

However, once you get it right, it will be portable and dependable.

Tim

---

