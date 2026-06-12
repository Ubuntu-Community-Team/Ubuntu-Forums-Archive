---
title: "Setting up Evolution"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Matsuri on 2007-08-06
Hello,

I've finally gotten tired of webmail. I've started setting up Evolution as my mail client. I've entered all the information in correctly, smtp and pop server, username / password, etc. 

Upon clicking send/receive I can receive mail from the server, but after a long wait the send service times out and doesn't send anything. I can still send mail via the webmail and still receive mail. The send function just seems to not work when I'm using Evolution.

Any thoughts?

Matsuri

---

### Post by Mr. C. on 2007-08-06
More details are necessary regarding your SMTP server and its configuration.

MrC

---

### Post by radthad on 2007-08-07
Who's your mail provider?

Check and make sure you've configured everything properly according to your mail provider - different ports rather than 'default' smtp/pop ports, and you've enabled SSL and TLS security.

---

### Post by Matsuri on 2007-08-07
I'm using 1and1 mail. The provider asks that SPA is turned off and they give an optional port other than the default that you may use. I have not been able to try the other port because I can not find where on evolution such an option is available.

---

### Post by Mr. C. on 2007-08-08
I'll say again... more *specific* details are required.

[LIST]
[*]What port did they give you?
[*]What is the name of the SMTP server?
[*]Do they require authentication?
[*]If so, what type?
[/LIST]
It is very difficult to help without the necessary details.  I'm personally not going to go hunting the 1and1 website to find information you could easily post.

MrC

---

### Post by Matsuri on 2007-08-08
Why do you need the other information? It is all entered properly into evolution. Giving you the exact port numbers would do what? Would it not be simpler just to show me where I can change the port number in evolution?

Even though I see very little value in you having specifics when you cannot test and play with their settings here you go:

Encryption: None
Server: smtp.1and1.com
Port: Default (25) RFC 2476, opt. 587
Not allowed to use SPA

---

### Post by Mr. C. on 2007-08-08
It must be the phase of the moon today, as the resistant users are out in full force.

The information *does* help, even if you don't understand how.  I did use the information to determine exactly what type of connection you need, and how you need to configure your Evolution.

Mail server ports are routinely configured to require different settings.  Knowing the ports allowed me to connect to the mail server to determine what is required, so that I don't give you bogus information.  This is clearly something you don't understand.

Both the 1and1 ports are configured with the same settings.

Enter the port number after the email server name, as in:

```
smtp.1and1.com:587
```

You could have easily found this in the Evolution manual... but I suppose that was not necessary either.

MrC

---

### Post by Matsuri on 2007-08-08
I do thank you for your time, I also am sorry if I was a "resistant" user, I will admit I'm not in the best of moods.

I knew exactly what I needed for the server, I just needed to know how to change the ports.

Thank you once again,
Matsuri

---

