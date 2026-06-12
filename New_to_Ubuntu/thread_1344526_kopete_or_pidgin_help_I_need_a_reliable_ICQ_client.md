---
title: "kopete or pidgin help I need a reliable ICQ client"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by mvalviar on 2009-12-03
Hi. I'm in dire need of a reliable ICQ client. I tried pidgin but I cannot send/receive offline messages. Its difficult to connect to ICQ using it. I always get "connection reset by peer". I always have to retry multiple times. I do this so often that I always receive the message "you've been connecting and disconnecting too many times..." from ICQ.

I tried kopete it handles offline messages fine. But it is much more difficult to ICQ using it. It says "Connecting..." for so long try to put it offline and online again hoping that it connects but it takes a stroke of luck.

Please help me. I know that there are other IM networks but this is what my boss requires. I there a browser or cross platform client I can use?

I already tried to run the windows client it wine but it doesn't run.

---

### Post by earthpigg on 2009-12-03
have you tried empathy?

---

### Post by mvalviar on 2009-12-03
> **earthpigg said:**
> have you tried empathy?
empathy is built on the same library as pidgin so I doubt there will be any difference. Nonetheless I'll give it a try.

Edit:
Tried it. It connects faster and more reliable that kopete and pidgin. I get "Network error" everytime it fails. However it can't receive or send offline messages.

---

### Post by mvalviar on 2009-12-03
tried meboo. I works perfectly. Of course I hate to use my browser of IMs. I've read from wikipedia that it's based on libpurple. So why is it that pidgin can't perform like meboo (i.e connect fast and send/receive offline messages in ICQ)??

---

### Post by k3lt01 on 2009-12-03
When you were using pidgin did you have pidgin-otr installed? The otr stands for Off The Record and from memory it the Offline message handling component.

---

### Post by howefield on 2009-12-03
> **mvalviar said:**
> I tried pidgin but I cannot send/receive offline messages.

Have you tried the new version of Pidgin, released a few days ago. I think it is 2.6.4, the changelog mentions a fix for offline icq messages which was broken in 2.6.3.

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

---

### Post by mvalviar on 2009-12-03
> **howefield said:**
> Have you tried the new version of Pidgin, released a few days ago. I think it is 2.6.4, the changelog mentions a fix for offline icq messages which was broken in 2.6.3.

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

I have pidgin's ppa repo. I just ran an update but pidgin wasn't updated. I still have 2.6.3.

---

### Post by dazzlindonna on 2009-12-04
Same issue here.  Hoped to be able to get 2.6.4 via PPA so the offline crash fix would be implemented, but the PPA only has 2.6.3. :(

---

### Post by howefield on 2009-12-04
> **mvalviar said:**
> I just ran an update but pidgin wasn't updated. I still have 2.6.3.

I'd expect the ppa will be updated over the next few days or so.

---

### Post by mvalviar on 2009-12-15
2.6.4 is on the repos. ICQ offline messaging works fine again. I just wish I could connect to ICQ easy. When I lauch pidgin my other IM accounts connects in a snap. ICQ gets left behind and returns with a "Connection reset by peer". I could click on reconnect and it returns with the same message. If I keep on clicking I get "You are reconnecting/disconnecting too many times please wait for 10 mins...". If I leave it as it is it could take 5-10mins before it connects to ICQ. I have pidgin on window$ too. I don't experience this there.

As a temporary fix. I loggin my icq on meebo while waiting for it to connect in pidgin. 

Any suggestion?

---

### Post by k3lt01 on 2009-12-15
I use my ICQ a couple of times a day in Pidgin and don't experience any problems at all. Maybe your Pidgin settings folder  (.purple) has been corrupted.

---

### Post by mvalviar on 2009-12-15
I could try removing .purple. Will saving my logs dir save all my logs?

Come to think of it. I haven't changed my .purple folder for over a year now. Since I have a separate home and root partition.

---

### Post by collinp on 2009-12-15
> **mvalviar said:**
> I could try removing .purple. Will saving my logs dir save all my logs?

It should, I doubt any logs are stored outside that directory.

---

### Post by mvalviar on 2009-12-15
> **Hellow said:**
> It should, I doubt any logs are stored outside that directory.

Ok I'd have to try it later. If I close pidgin now and this process doesn't work it would be a while again before I could connect.

---

### Post by mvalviar on 2009-12-16
Yay! It worked. Pidgin rocks again! Empathy? What empathy? Proudly marking this as solved.

---

