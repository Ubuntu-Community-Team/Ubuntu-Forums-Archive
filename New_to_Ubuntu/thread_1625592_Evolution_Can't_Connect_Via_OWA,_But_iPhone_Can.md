---
title: "Evolution Can't Connect Via OWA, But iPhone Can?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by feuertod on 2010-11-19
So for around a year, I used OWA in evolution, and was happy.

Lately our exchange administrators have been upgrading Exchange and OWA a lot over the last month.

Since then I've reconnected a few times using other methods such as MAPI. It's been hit and miss.

After the latest upgrade, I can't connect via OWA or MAPI in evolution, but I can get my mail via OWA on my iPhone!

So, I'm hoping it's just me not understanding how to connect Evolution back up, because it seems crazy to me an iPhone can connect, but Evolution can't. 

Any ideas? I'm crazy enough to give you the OWA endpoint.

[https://echo.entertainment.com/owa](https://echo.entertainment.com/owa)

---

### Post by cariboo on 2010-11-20
Can you connect to the mail server with a browser?

---

### Post by feuertod on 2010-11-23
> **cariboo907 said:**
> Can you connect to the mail server with a browser?

Yes. At the URL above. Login get mail no problem via OWA. echo.entertainment.com 

My iPhone can get the email too.

That's the frustrating part. iPhone, not a computer, can, but a normal computer running Ubuntu cannot connect to OWA with Evolution.

---

### Post by stmiller on 2010-11-23
Evolution and the mapi plugin for exchange only works on the local exchange network. If you are trying remotely, it is not going to work.

You should be able to do regular imap with exchange and evolution remotely, though.

---

### Post by surfdoc on 2010-11-27
Just been pulling my hair out with this one myself. 

iphone - connected to exchange effortlessly.
evolution - tried messing with various options for 1 hr and no luck

Unfortunately I cant seem to get IMAP access to this particular account either. 

In windows I used an app called DavMail with thunderbird. This worked fine. I might give it a go in ubuntu, but I seems a pitty since evolution claims to support exchange directly.

---

### Post by feuertod on 2010-12-02
> **stmiller said:**
> Evolution and the mapi plugin for exchange only works on the local exchange network. If you are trying remotely, it is not going to work.

You should be able to do regular imap with exchange and evolution remotely, though.

[LIST]
[*]Wasn't trying remotely
[*]MAPI in Evolution no longer works since the latest Exchange / OWA upgrade. MAPI should of been renamed to CRAPI IMHO; HTML email support was flaky, doing things like scrambling entire messages to other recepients.
[/LIST]

Maybe I'll try IMAP

Just basically I guess I need to rant / vent that I find it ridiculous that iPhone has no problems connecting via OWA, yet Evolution cannot connect via OWA.

---

