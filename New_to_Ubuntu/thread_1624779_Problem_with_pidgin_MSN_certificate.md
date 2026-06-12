---
title: "Problem with pidgin MSN certificate"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by locodog on 2010-11-18
Today I've started Pidgin 2.7.5 (on ubuntu 10.04) and it cannot connect to MSN because SSL certificate error. I've searched net for solution and found that when you select "use HTTP method" it should solve problem. And it did, for about half hour, after that I keep getting the same error. Can somebody help me to solve this, step by step, please?

Here is picture attached.

---

### Post by dhunt84971 on 2010-11-18
You need to stop Pidgin and rename the certificates folder to certificates.old under the .purple folder.  Then restart Pidgin.  This will cause Pidgin to reaquire the certificates.
 
Unfortunately, I do not have the entire path to .purple.
 
Perhaps someone else can provide this info?

---

### Post by dhunt84971 on 2010-11-18
The following link may be helpful, too:
 
[http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/](http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/)

---

### Post by dhunt84971 on 2010-11-18
If you are still trying to fix this, the problem was solved on another thread...  The following link was referenced there:

[http://retrohack.com/why-cant-we-all-just-get-along/#more-3107](http://retrohack.com/why-cant-we-all-just-get-along/#more-3107)

I have applied the method shown in the link above with success.

---

### Post by locodog on 2010-11-18
I'm still fighting with this problem. I've readed dozens of post and I still cannot find folder where pidgin keeps it's certificates so i can replace it with certificate I've downloaded... If somebody please can give me step by step guide...

add:
I think I solved the problem: in folder /usr/share/purple/ca-certs/
i've copied two files:
GTECyberTrustGloblRoot2018.crt
omega.contacts.msn.com.txt---pidgin---projects---files.andreineculau.com

and for now msn from pidgin is working... I will wait some more to see if solution is finall.

---

### Post by dhunt84971 on 2010-11-18
Here is where mine is:

cd /home/dave/.purple/certificates/x509/tls_peers

You will obviously need to change dave to your username.

Note:  This folder is hidden, so if you are going to use Nautilus to find it, be sure to Show Hidden Files, under View.

---

### Post by locodog on 2010-11-18
I've solved problem, I've replaced file omega.contacts.msn.com in ```
/home/myuser/.purple/certificates/x509/tls_peers
``` with this one (attached, if somebody else needs it).

Just remove .TXT extension, so filename remains only ```
omega.contacts.msn.com
```

---

### Post by ijoaum on 2010-11-18
It works. 
Thank you!

I've just downloaded the file above and moved into tls_peers dir.

---

### Post by locodog on 2010-11-18
Heh, it's nice to know that I helped somebody here instead of just looking for help :)

---

### Post by wbrb on 2010-11-18
Had this issue today after updating pidgin.

From:
[http://developer.pidgin.im/ticket/12906](http://developer.pidgin.im/ticket/12906)

Opening [https://omega.contacts.msn.com/](https://omega.contacts.msn.com/) in firefox, exporting the cert to your desktop and then dumping it into your ~/.purple/certificates/x509/tls_peers folder as a new login.live.com file seems to work just fine.

Seems odd considering how well pidgin has worked for me. Figured I'd post it here.

---

### Post by WarByte on 2010-11-18
> **locodog said:**
> I've solved problem, I've replaced file omega.contacts.msn.com in ```
/home/myuser/.purple/certificates/x509/tls_peers
``` with this one (attached, if somebody else needs it).

Just remove .TXT extension, so filename remains only ```
omega.contacts.msn.com
```

During the day I deleted the file, clicked on modify my account, second attempt would work. The problem would appear again though. Just tried the file and can confirm it works  :)   hope the message doesn't pop up again. Thank you!

Edit: Message popped up again. It's always appreciated though.

---

### Post by Keot on 2010-11-19
One line fix using the terminal:-

```
$ openssl s_client -showcerts -connect omega.contacts.msn.com:443 > ~/.purple/certificates/x509/tls_peers/omega.contacts.msn.com < /dev/null
```

---

### Post by 5oak on 2010-11-20
> **Keot said:**
> One line fix using the terminal:-

```
$ openssl s_client -showcerts -connect omega.contacts.msn.com:443 > ~/.purple/certificates/x509/tls_peers/omega.contacts.msn.com < /dev/null
```

Don't know how you did this or what it does exactly, but you did it and it sure does fix it... Finally! Thnx!;)

Edit: aaaarghhh, it's back!

---

### Post by lunatico on 2010-11-21
> **Keot said:**
> One line fix using the terminal:-

```
$ openssl s_client -showcerts -connect omega.contacts.msn.com:443 > ~/.purple/certificates/x509/tls_peers/omega.contacts.msn.com < /dev/null
```

Seems to have worked. I don't understand how is this different from just removing the certificate and letting pidgin download it again... Thanks!

---

### Post by sukruozan on 2010-11-22
Thanks locodog it really works...

---

### Post by lunatico on 2010-11-23
I keep getting this now and then... running that command fixes it for a while but it always comes back. Anyone else see this too?

---

### Post by ranea on 2010-11-23
yup, same here. it works for a couple of hours and then all of a sudden, plop! error box.

---

### Post by coolbrook on 2010-11-23
Apparently this will be resolved when version 2.7.6 pops up in the repository.

---

