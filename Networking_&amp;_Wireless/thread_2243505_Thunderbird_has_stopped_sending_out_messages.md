---
title: "Thunderbird has stopped sending out messages"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2014-09-09
I think I can receive new messages. TB says it is checking the pop3. Sending does not cause the email to be checked or sent. This is new. Just happened? 

Is there a way of checking the logs to see why it has failed?

Robin

---

### Post by Robbyx on 2014-09-09
I think I will be able to find the fault. I just went into safe mode and I could send email. So it looks like it is an extension.

When I start in safemode I get this error message:

robins@robins-EP35-DS3L:~$ thunderbird -safe-mode
(process:9596): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

Any suggestion as to how to clear this?

---

