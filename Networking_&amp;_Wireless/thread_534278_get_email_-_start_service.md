---
title: "get email - start service"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by fatmtbiker on 2007-08-25
So let me start off with this is just an idea and I am not sure if it can be done.  Hopefully someone out there will know.  Here is the setup I would like to have done.

1.  I send an email to [email]xxx@mydomain.com[/email]
2.  My server has a mail client to get all mail sent to [email]xxx@mydomain.com[/email]
3.  Once it gets an email from [email]xxx@gmail.com[/email] with subject = start vpn then it starts my ssl explorer vpn server.
4.  Once I am done I can send another email to [email]xxx@mydomain.com[/email] and stop the service.

---

### Post by kidders on 2007-08-26
Hi there,

It's worth at least mentioning that running an SSH server is by far the *smartest* way of remotely controlling your PC ... but having said that, lots and lots of devices (eg phones) aren't SSH-capable, so you may not be able to go down that road.

Anything capable of grabbing mail and piping it through a script can be made to do what you're looking for. It's quite possible that even Thunderbird could manage it, with a little tweaking. The "normal" way of doing this sort of thing is with a Postfix server, although you may not want/need to install all that software.

The trouble you'll have is that things that handle mail should absolutely never run with the privileges necessary to start & stop local services ... there are very real risks involved in doing so ... so you'll have to poke some holes in your Linux box's security, to manipulate it into letting them do so.

I suggest you do some reading, decide what sort of local software you feel suits your needs best, and if you need a hand with the specifics, I'd be more than happy to help you out.

---

