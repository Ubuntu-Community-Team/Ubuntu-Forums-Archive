---
title: "How can I monitor total traffic *per application/process*?"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by thekwill on 2010-09-15
Hi,

I've been reading up about Netlimiter (Windows), trickle and similar bandwidth/traffic-related apps. What I am looking for is an app that logs and/or monitors the amount of traffic every other app has used.

For example, Transmission reports how much it has uploaded and downloaded in a given session and over time. I want to be able to open this app and see something like: Firefox has downloaded 50MB, Transmission has downloaded 500MB and uploaded 300MB, Ubuntu One has uploaded 5MB, etc. A per-session record would do, but actually logging usage to a database/text file would be best.

*Ideally* I'd like a cross-platform (Windows + Ubuntu) FOSS application, but I'd be happy to start with something Ubuntu-specific for now.

I must be missing something because I've found lots of questions relating to this, just no answers! :D Thanks for any guidance, I'll be adding it to alternativeto.net!

---

### Post by muteXe on 2010-09-15
Not sure if wireshark logs this kind of thing, but it's worth taking a look at (maybe).

[http://www.wireshark.org/docs/](http://www.wireshark.org/docs/)

---

### Post by thekwill on 2010-09-15
Thanks I'll take a look. Also just found out about nethogs, busy investigating...

---

### Post by fatality_uk on 2010-09-15
Wireshark is a good all round package. For more detail you also have nmap [http://nmap.org/](http://nmap.org/) using both shoulg give you ver precise details about what traffic and applications are doing on your network.

---

### Post by endotherm on 2010-09-15
i use iftop for non-logged BW usage monitoring per connection, but it doesn't go down to executables. I usually use netstat for that. not quite optimal.

---

