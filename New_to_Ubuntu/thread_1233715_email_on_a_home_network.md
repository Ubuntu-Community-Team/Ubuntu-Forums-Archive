---
title: "email on a home network"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by brawd on 2009-08-07
Hi,

I tried looking for 'email on a home network' and 'email on an intranet' and got so many replies my brain got fried because the replies were of the 'email', 'network' and 'intranet'.

So I have (the usual) home network of Ubuntu and XP mix. Everybody can see shared folders on the other machines.

Now that I've got to that stage can I now use the home network, (or is it intranet), to send messages to each machine?  And maybe ring a bell for attention.

It would be extremely handy to be able to send a quick message between machines, without actually installing a server. (Optimist that I am I installed a server once, silly me!).

Any and all suggestions gratefully received, even if it does mean installing a server.

regards,

brawd.

---

### Post by amac777 on 2009-08-07
Hello, getting internal email on a home network will probably require you run your own mail server. For local mail only, it's actually not that hard to set up. You would basically need to do the following three steps:

1. Install the package 'postfix' and during the setup tell it "Local Delivery Only". This is your SMTP server. 

2. Install the package 'courier-pop'. This is your pop3 server.

3. Setup outlook or evolution or whatever mail program you like on each of the computers to use the SMPT and POP3 servers you setup in steps 1 and 2.

If that sounds like something you want to try, I can give you more detailed steps.



But if all your are looking for is instant messaging between the computers on your network, then you don't need "email", you need instant messaging. One way is to run your own "jabber" server and then each computer on your network can run a jabber client such as pidgin. That might be a lot easier to setup.

---

### Post by brawd on 2009-08-09
Thanks for that information and sorry I was a while getting back - I was forced to take my wife out for her birthday instead of working on my Ubuntu, lol.

The packages returned an error when I tried to install them, and synaptic reports a 'broken' package when I take on the regular updates. I'll have to fix that first then get back to my email bit.

regards,

brawd

---

### Post by amac777 on 2009-08-09
Good luck getting your synaptic problems fixed. One way you can try to solve that problem is to remove the broken package. For example:

```
sudo apt-get remove broken-package
```

(obviously, change 'broken-package' to whatever the broken package name is.)

-------------

About getting your home email working, just to further supplement my instructions for step 1 above, you will need to slightly adjust the configuration for postfix to allow other computers to send mail via your server for local delivery. To do this, edit the postfix main.cfg file by doing:

```
sudo nano /etc/postfix/main.cf
```

And then make the following changes (amend one setting and add one new line as marked in red):

```
inet_interfaces = [COLOR="Red"]all[/COLOR]
default_transport = error
relay_transport = error
[COLOR="Red"]home_mailbox = Maildir/[/COLOR]
```

Then restart postfix by doing:

> sudo /etc/init.d/postfix restart

Also, make sure you have a user and password setup on your server for each user who wants their own email account. Go to "System->Administration->Users and Groups" and add new users for each person's account.

Then, on each computer in your house, setup their email client (outlook, evolution, etc) to use pop3 and smtp with the IP address of your server (for example, 192.168.1.1). This IP should be a fixed IP so it stays the same all the time. Each user should use their own username/password as you previously set up on the server.

Hope that helps. Let me know if you run into any problems.

---

### Post by halitech on 2009-08-09
are you wanting to send actual emails or more like a popup note to the recipient? If you just want to send a quick message with an alert and popup box, look into linpop

[http://linpopup2.sourceforge.net/](http://linpopup2.sourceforge.net/)

which works with winpopup on windows

[http://www.lantalk.net/winpopup/](http://www.lantalk.net/winpopup/)

---

### Post by brawd on 2010-02-10
My apologies to all who have been good enough to reply. It's only now that I have continued the installation. About the time I started on this I also messed about with a couple of other Linux distros, but finally settled for Ubuntu again. This time it's 9.10 64 bit.

I decided on the postfix approach as I would like to start to maximise my home network - that is make it more useful if I can, and to be quite honest, start to learn about networking.

I've downloaded and installed postfix and courier-pop.
I jotted down the configuration names using Evolution mail.
Then I got stuck. The problem being there are loads of files that can accompany postfix and I'm not sure which I need. I've also downloaded the docs to read to try a next step, all the while hoping that this note will catch the eye of someone who is good enough to help.

Courier seemed to download and then disappear into the ether, or somewhere inside the box. Possibly I'll have to find that first before I can configure it.

Anyway this is as far as I've got, Postfix and Courier-pop downloaded.

regards,

brawd.

---

