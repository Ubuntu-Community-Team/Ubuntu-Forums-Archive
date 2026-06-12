---
title: "So, just how safe are my comms?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2007-12-03
hello all

i have what i'm led to believe is a pretty secure system (ubuntu 7.10 with all the updates, the latest thunderbird) and get my gmail through an ssl connection. however i do have to connect to any network i can find, be they my own or other peoples' wired and unsecured wireless networks

i currently work in a country where network backbone integrity is unverified  (choosing my words very carefully for the same reason) and often send emails that need to stay confidential.

so what would the experts tell me about the security of my email? what is possible, and what is likely? is there anything better i could be doing? for that matter, how private is data i enter in web forms such as this?

many thanks to all
Roger

---

### Post by dionyziz on 2007-12-03
Hey there,

First of all, all your TCP/IP connections, including your HTTP connections, FTP connections, instant messaging, and so forth (e.g. the form data you submit to forums like this) go through intermediate hosts, such as your ISP. These hosts can sniff the data fully and log the data you are sending and receiving accordingly, to its full extend. They can even interfere with what you send or receive (e.g. someone is technically able to login as you and submit posts here, providing he is one of your intermediate hosts).

This problem can be solved by using secure protocols such as HTTPS, SSH, SCP. HTTPS doesn't allow interfering or sniffing by intermediate hosts.

You are not anonymous, however. Although intermediate hosts can no longer read your data or modify it, they can still sniff your secure connections to learn about the following:
- The time and date a connection occurred.
- The target machine (ubuntuforums.org for instance) and its physical location.
- Your current physical location (to some degree -- e.g. your city).
- The protocol you're using (e.g. HTTPS).
- How often you connected and how long each connection lasted.

Also keep in mind that if you don't use a trusted DNS, they can always interfere with your communications by emulating the target host (scamming).

I hope this helps! :)

---

### Post by rogerdean on 2007-12-05
That's extremely helpful, thanks very much. So I think I'm right to be fairly comfident at least about my message content, although of course it also depends on the security of the recipient's connection!
Anyone got anything further to add?
Allbest

---

### Post by mozetti on 2007-12-05
You can look into using gpg for encryption. And you can use fee DNS servers, like [http://www.opendns.com](http://www.opendns.com) , instead of the ones provided by the ISP(s).

If you're concerned about websites you visit getting information about you, you can also use Tor to anonymize (somewhat) your browsing behavior. This doesn't help from the ISP aspect however, because you still need to use their connection to get to TOR.

---

