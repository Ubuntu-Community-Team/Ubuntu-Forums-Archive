---
title: "Postfix Changes HTML Formatting of CDO Email"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by dave90 on 2014-02-14
We just migrated to office 365, and in that migration, we started using postfix for our hundres of automated emails.  However, postfix appears to be changing / losing html formatting when sending an email.

I know this is postfix because of the following tests:
All tests use the same page / sample email

Test 1 - Sent from exchange server - normal formatting / email (old method before switchign to O365)
Test 2 - Send using embedded authorization, straight to O365 servers - normal formatting
Test 3 - Send using smtp relay (Postfix), formatting gets jacked up.  An example is hyperlinks, sometimes they work, sometimes they won't, it iwll display the link instead of what is embedded int eh <a></a> tags.  Another example is during tables, a random <td> will show up, or, even worse, it will treat a </tr> as something it isn't, and not all of the data will show up on the email.

It does seem to affect tables more than anythign else, and when htere is a loop of data being displayed.  And, if the results have, for example, 30 results, maybe lines 8 and 24 and 27 will have odd formatting, when the rest are just fine.

---

### Post by dave90 on 2014-02-14
The email is generated from classic asp if that matters.

---

