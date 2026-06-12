---
title: "Serious Lag Over Telnet"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Unicow on 2008-08-19
I'd like to preface this by saying that I'm not the most knowledgable person when it comes to internet protocols and technical terms, so it's possible that I might get my jargon mixed up and explain something badly. Thanks for bearing with me.

I've just recently moved into my school dorms and I'm experiencing a problem with my ubuntu partition on the school wireless network. Things running TCP/IP are extremely laggy -- connections over telnet can often lag between thirty seconds to two minutes, and occasionally, they'll just be dropped outright. Meanwhile, web pages seem to work fine, and stuff that uses UDP like some IM services are a-okay. I've been doing some tests and my ICMP seems to be blocked. Messing with my MTU doesn't help -- I experimented at several different sizes.

The weird thing is that things seem to be working fine in Windows -- speeds go lightning fast. This is sort of frustrating, because it seems to indicate that there's SOMETHING that I can do to get ubuntu working proper, but the what is completely eluding me.

For the record, I'm using the native linux wireless drivers that kubuntu detected when I installed. 

Can anyone help me?

edit: adding more information to original post.

---

### Post by Unicow on 2008-08-19
A gentle nudge back to the top. I'm burning a LiveCD as we speak to test it out on that -- maybe it has something to do with ubuntu itself.

---

### Post by Unicow on 2008-08-19
Hopeful bump. I'm getting sort of frustrated, having to hop back into XP whenever I need to do this stuff. I've ascertained it's not my client, either -- even when I telnet straight into the MU*s via konsole, I'm getting that horrible lag, whereas it's more or less instantaneous via the telnet client in MS-DOS on my XP partition.

---

### Post by Unicow on 2008-08-19
> **Unicow said:**
> A gentle nudge back to the top. I'm burning a LiveCD as we speak to test it out on that -- maybe it has something to do with ubuntu itself.

Well, the problem is in the LiveCD too, which indicates that whatever the problem is, it's inherent in ubuntu. I'm really starting to get discouraged.

edit: astfgl.

---

### Post by Unicow on 2008-08-20
Added more information to the original post. Bump.

---

### Post by cariboo on 2008-08-20
Don't be in such a rush, it could be that the person who can help you with your problem just hasn't seen this post yet. If you keep bumping your post people will see all the responses and not bother reading it. 

What have you done to diagnose your problem, have you talked to the IT people? What are you using telnet for, on most linux distros telnet is not enable because of the security risks.

Jim

---

### Post by Unicow on 2008-08-20
> **cariboo907 said:**
> Don't be in such a rush, it could be that the person who can help you with your problem just hasn't seen this post yet. If you keep bumping your post people will see all the responses and not bother reading it. 

What have you done to diagnose your problem, have you talked to the IT people? What are you using telnet for, on most linux distros telnet is not enable because of the security risks.

Jim

I apologize for so many bumps. I'll stop that.

As for diagnosing, I've done pretty much all that I could think of. I've eliminated it being a problem with the MTU, and I know it's not from some utility that I'm using to access telnet, because everything I've done, I've done straight from console. I also know that it's something inherent in ubuntu in this situation, because a boot from a Live CD produced the same results, so I know it's not something I've done since installation to do this.

As for the why -- I use telnet to access several different MUCKs. One's a social things for me and my friends, and another, I'm getting some help in learning to code things. They use TCP/IP to connect, and because of the lag I have described are as such completely unusable. I know that telnet is enabled because I've done it before many times on this installation.

I'm going to be heading to find the campus sysadmin after I finish posting this, actually, to see if I can't get it resolved there.

Edit: Just got back from meeting with the campus sysadmin, and I have to say it was a little disheartening. He told me, more or less, that everything on the campus is running Windows, that all he himself has experience with is Windows, and that he even outright dislikes linux because, apparently (he rambled off on a story), in a demonstration once to show how easy linux was, a couple of guys tried to install Red Hat on a Windows box and ended up destroying it. Basically, I've got no help coming from this guy.

I don't know if this is worth mentioning, but some of my instant messengers are also having problems connecting in linux -- mainly, AOL instant messenger, which can only seem to connect 1/2 of the time. My MSN messenger is able to always connect, though.

---

### Post by Unicow on 2008-08-22
A hopeful bump.. No one knows why ubuntu might lag in TCP connections where Windows does fine in a school network environment? I really hate having to boot into Windows for anything...

---

