---
title: "Can't connect pidgin using CDMA broadband connection"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by pradeepbp on 2010-01-30
I am using CDMA wireless broadband for net connection on my laptop. But pidgin does not seem to identify this connection. My status message always says 'Waiting for network connection'.
But I can surf the web using the same connection.

I am using karmic and uses wvdial to connect to CDMA broadband.

Any solutions?

update: I have found out that even Empathy is showing same behaviour

---

### Post by yeats on 2010-01-30
IM clients are going to use a different port than http, which is port 80.  Is it possible that the connection you're using only allows http traffic?

---

### Post by pradeepbp on 2010-02-01
> **chrissharp123 said:**
> IM clients are going to use a different port than http, which is port 80.  Is it possible that the connection you're using only allows http traffic?

I don't think that is the issue. I can use IM clients in Vista using same internet connection. I guess the issue here is that these IM clients are not identifying this as a working net connection. 
On Fedora, when I try to surf using the same connection, Firefox goes 'offline'. Then I would manually set Firefox to 'online' and continue. But in Karmic, at least there are no issues with Firefox :)

---

