---
title: "Help, just lost ALL my data!"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by wcdrotar on 2010-10-15
I was working on getting a tar.gz installed.  I think it was decompressed already since it was a folder.  I opened a text file inside that was called install.pl.  When I did so I chose to make it run in the terminal.  

While in the terminal I chose a file destination /home/.  The next thing I know all my data is gone.  EVERYTHING.  It's like a clean install.  

I spent over six-seven hours waiting for downloads and customizing this.  I REALLY would like to fix it so that everything comes back.  Does anyone know how to remedy this? 

And how to install Zimbra for that matter which I've spent like two hours trying to get going.  

Thanks if you can help!  It's very frustrating having a clean install when I worked so hard to get everything up.

---

### Post by kidders on 2010-10-16
Hi there,

> **wcdrotar said:**
> Does anyone know how to remedy this?That depends on what the perl script did. If it deleted data, your best option is a forensic data recovery utility. Where did the script come from?

> **wcdrotar said:**
> And how to install Zimbra for that matter which I've spent like two hours trying to get going.What are you having trouble with?

---

### Post by wcdrotar on 2010-10-22
> **kidders said:**
> Hi there,

That depends on what the perl script did. If it deleted data, your best option is a forensic data recovery utility. Where did the script come from?

What are you having trouble with?

It was from Zimbra, which is basically "zmail".  It's UT-Dallas' choice for a secure desktop mail client, which is what I was trying to get working.  I reconfigured everything AND made a backup (I backup regularly now and send the files to myself in a dated email so I don't lose junk again).  

However, just because this has happened to people before (and because this is half the fun of linux) I'd still like to learn what happened and how to prevent it.

---

### Post by kidders on 2010-10-22
> **wcdrotar said:**
> I'd still like to learn what happened and how to prevent it.You'd have to look at the script to know for sure. It seems logical, for instance, that the script would notice the install destination (ie /home) exists, and delete it. If it were me, I'd start there & look at what happens when a chosen install location already exists.

---

