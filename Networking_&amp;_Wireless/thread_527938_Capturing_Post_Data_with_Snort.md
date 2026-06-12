---
title: "Capturing Post Data with Snort"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by strider1551 on 2007-08-17
Recently I've been reading a lot about security stuff, especially password hashes and encryption in general.  I want to do a kind of self audit to what kind of data is sent from my machine during my normal web usage.  I figured the best place to start would be checking to make sure passwords used for logins are being hashed prior to being sent, rather than going out as plain text.

I was able to have wireshark capture port 80 traffic, and then filter the results for a POST request.  However, as near as I can figure, there's no way to have wireshark capture *only* POST requests.  If I left it running for a day or two as I go about my business, that's going to be a massive number of unnecessary packets.

Thus, I moved to snort.  I was able to write a rule that captured the first packet of the post, but the actual post data isn't there.
```
log tcp any any -> any 80 (content:"POST")
```
Anyone familiar enough with snort to point me in the right direction?  I should note that I'm using a custom config file, so if I need to activate any preprocessor please let me know.

---

### Post by ihristov on 2007-08-17
Not familiar with Snort in particular, but in Ethereal there is an option to "follow stream". Maybe check the Snort documentation for similar option for capturing. Actually this might not even be possible, since in many cases HTTP traffic re-establishes a new socket connection.

Maybe you have to capture all the ougoing traffic to port 80 and then have a filter that shows you only what you want.

---

### Post by strider1551 on 2007-08-17
> Maybe you have to capture all the outgoing traffic to port 80 and then have a filter that shows you only what you want. 
Yeah.  I know how to do that, I just want to avoid it.  Why log everything if I can find a way around it, especially when logging everything means a large number of excess packets?

Anyway, my latest attempt was the following:
```

preprocessor stream4: log_flushed_streams
preprocessor stream4_reassemble: both
log tcp any any -> any 80 (content:"POST"; tag:session,100,packets;)

```
Once again, I caught the first packet of the POST, but not the POST data.

What really threw me though, was when I did this:
```

preprocessor stream4: log_flushed_streams
preprocessor stream4_reassemble: both
log tcp any any -> any any

```
I tried several greps looking for strings I *know* are in the POST data, and got nothing!  Apparently I completely misunderstand how POST data is sent, or I completely misunderstand how to set up snort.

---

