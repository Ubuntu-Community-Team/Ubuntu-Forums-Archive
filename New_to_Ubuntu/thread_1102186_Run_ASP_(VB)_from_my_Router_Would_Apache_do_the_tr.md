---
title: "Run ASP (VB) from my Router? Would Apache do the trick?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Panarchy on 2009-03-21
Hello

Since I can't run IIS on my Router/Switch (ASUS WL700gE) I would like to try XAMPP/Apache instead. 

This would run on either the default firmware, or on OpenWRT.

I am looking for a web-server that can run on my Switch/Router that will be able to host the default web-pages created with IIS on a print-server (Win XP Pro or Server 2003).

Would you recommend Apache for this?

If so, how do I configure Apache to allow for ASP?

If not, please recommend a different Web-Server that can host ASP pages.

Thanks in advance,

Panarchy

---

### Post by Xiong Chiamiov on 2009-03-23
I'm not really sure if a router has enough resources to run something like that.  Obviously it can run something, since you have a web interface, but still, even the light servers, like lighttpd and nginx, probably won't do so well.

To run ASP on linux, you'll have to use [Mono](http://en.wikipedia.org/wiki/Mono_(software)), I believe, which is never a fantastic idea.  But then again, neither is ASP.

What exactly are you trying to do?  We might be able to help better if you tell us the actual thing you want, rather than something on the path to getting that.

---

### Post by directhex on 2009-03-23
ASP and ASP.NET are completely unrelated services which only share part of a name.

The WL-700gE has 64 MiB of RAM, so it probably DOES have enough to host ASP.NET services with Apache and mod_mono. But there's no way to write ye olde ASP without IIS or PWS.

---

### Post by Panarchy on 2009-03-23
> **Xiong Chiamiov said:**
> I'm not really sure if a router has enough resources to run something like that.  Obviously it can run something, since you have a web interface, but still, even the light servers, like lighttpd and nginx, probably won't do so well.

To run ASP on linux, you'll have to use [Mono](http://en.wikipedia.org/wiki/Mono_(software)), I believe, which is never a fantastic idea.  But then again, neither is ASP.

What exactly are you trying to do?  We might be able to help better if you tell us the actual thing you want, rather than something on the path to getting that.

I am trying to host the default print-server website that is created with IIS. Unfortunately, it is in ASP :(

If you could please recommend another service (tried CUPS, didn't do it for me) that can run on Apache which will have the ability to;

[LIST=1][*]List printers
[*]List documents from specific printers
[*]Cancel/Restart documents
[*]Distribute drivers (to at the very least, Windows XP)[/LIST]

Thanks in advance,

Panarchy

---

### Post by beercz on 2009-04-02
I have a similar issue.

If it can be done, what is the best way of running an website written in ASP (not ASP.NET) with a MS Access database behind it, on an apache server?

Thanks in advance.

---

### Post by directhex on 2009-04-02
> **beercz said:**
> If it can be done, what is the best way of running an website written in ASP (not ASP.NET) with a MS Access database behind it, on an apache server?

Can't be done.

Sun used sell an ASP server, but you can't buy it anymore

---

### Post by beercz on 2009-04-02
Thought not - but I thought I would ask anyway.

Thanks for the reply though.

---

### Post by beercz on 2009-04-02
This may be some sort of half way house though:

[http://apache-asp.org/](http://apache-asp.org/)

---

### Post by directhex on 2009-04-02
> **beercz said:**
> This may be some sort of half way house though:

[http://apache-asp.org/](http://apache-asp.org/)

Sure. All the downsides of ASP's functionality - and doesn't interpret VBScript or JScript (the languages used by Microsoft ASP), only its own PerlScript

---

