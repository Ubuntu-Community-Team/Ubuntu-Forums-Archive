---
title: "Noob questions about Ubuntu server?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by LastWho on 2009-01-29
Hi, 
is it true that Ubuntu server has no graphical interface, no X server?

is it better / easier to use Ubuntu server or Debian server?

Can we manage to make an ubuntu server PC recognise and controle other PCs running windows?

thanks in advance

(ps: as noob my questions are, i assure to you that i will be very happy to read as many details as you can give me, thx and sorry for my bad eng, i m french)

---

### Post by mhh91 on 2009-01-29
i think that servers are better ran without GUI's at all :)


as for your questions,the last question is a sure yes,the other questions are not for me to answer,as i don't have the proper knowledge :)

---

### Post by spcwingo on 2009-01-29
> **LastWho said:**
>  
is it true that Ubuntu server has no graphical interface, no X server?

Not by default, but you can always add one.  ;)

> **LastWho said:**
> 
is it better / easier to use Ubuntu server or Debian server?

Debian is less bleeding-edge stuff, so a little more stable.  Other than that, they're pretty much the same (Ubuntu is based on Debian).

> **LastWho said:**
> 
Can we manage to make an ubuntu server PC recognise and controle other PCs running windows?

I haven't tried this one, but I'm sure this can be accomplished.  Just stick around and hopefully someone with a little more experience on this will chime in.  You can also try posting this in the server platforms section.

---

### Post by ibutho on 2009-01-29
You should be able to use an application called SAMBA in order to get Linux to "control" Windows computers. Personally I would go with Debian for very important servers where stability is an issue, otherwise Debian and Ubuntu are quite similar and which to use is personal preference.

---

### Post by igknighted on 2009-01-29
You can add a GUI to an Ubuntu server as mentioned above, but there aren't graphical (as in Xorg) tools to manage the server, so there almost isn't a point.  There are a few web-based management tools, Webmin being the most popular.  If you want graphical tools, this is the way to go.

Also, as for "controlling" windows computers... can you elaborate what you mean?  Do you mean actually taking over control of the machine?  This is not really a server function, that sounds more like remote desktop (possible from any desktop client).  If you mean as a Domain controller for AD, it is possible, but complicated.  You need Samba as mentioned above (this makes files available to Windows PCs), but to do the login functions of AD, you need to use OpenLDAP or some other server (Mandriva Directory Server, which you can install on Ubuntu/Debian, makes this much easier).  If this is what you want, I would go to google and do a lot of research, because it is a fairly complicated process.

---

### Post by jerome1232 on 2009-01-29
> **igknighted said:**
> You can add a GUI to an Ubuntu server as mentioned above, but there aren't graphical (as in Xorg) tools to manage the server, so there almost isn't a point.  There are a few web-based management tools, Webmin being the most popular.  If you want graphical tools, this is the way to go.

I'm going to +1 this, all of your configuration is editing text files anyways.

Gui's always make me feel like I'm not sure what is "really" being done.

---

### Post by egalvan on 2009-01-29
> **LastWho said:**
> Hi, 
is it true that Ubuntu server has no graphical interface, no X server?

On a default install;
 no graphical interface,
 no X server,
 no Desktop Environment,
 no Window Manager.

strictly Control Line Interface.

That said, it is possible to install Gnome, or KDE, or XFCE via apt-get.
On one of my machines, I have 8.04 Server 32bit, to let me access all 8GB RAM. (The server kernel has the PAE flag set).
Adding Gnome & KDE makes it equivalent to Desktop.

> is it better / easier to use Ubuntu server or Debian server?

"better/easier"-type questions tend to be personel-choice-type.
What I find "better/easier" may be "worse/harder" to others.
Experimentation is a good idea here.

> Can we manage to make an ubuntu server PC recognise and controle other PCs running windows?

others have started good answers on this.

> thanks in advance
(ps: as noob my questions are, i assure to you that i will be very happy to read as many details as you can give me, thx and sorry for my bad eng, i m french)

Reading details is a very good way to learn the ins and outs of *nix.

Welcome to the club.

ErnestG

---

### Post by LastWho on 2009-01-30
I can't find the thaks button anywhere! but thank you so much for your help

---

### Post by hyper_ch on 2009-01-30
the thanks feature is temporarily disabled. See the Forum Feedback for more information on that.

---

### Post by bruce89 on 2009-01-30
> **LastWho said:**
> I can't find the thaks button anywhere! but thank you so much for your help

The forum overlords had to disable it because of database issues.

---

