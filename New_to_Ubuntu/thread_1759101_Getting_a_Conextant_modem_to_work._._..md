---
title: "Getting a Conextant modem to work. . ."
date: 2011-05-15
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-05-15
Hi! Just for fun, I've been trying to get the internal modem in my Dell Inspiron 1520 working. I believe it's a Conextant. I've tried a few How-To guides, but they are all pretty outdated and nothing has worked so far. Does anyone have any idea how I might get this working in Ubuntu 11.04? It might be neat to  be able to ssh into my servers anywhere there's a phone jack :D

---

### Post by corncob on 2011-05-15
When I had dialup I used a program called 'gnome-ppp' from synaptic.  I did have a hardware modem though.  It wasn't good at finding win modems but something to try.

---

### Post by pi.boy.travis on 2011-05-15
I'm using wvdial, the CLI backend for gnome-ppp. What I need is a Conextant driver. . .

---

### Post by gandaran on 2011-05-15
> **pi.boy.travis said:**
> I'm using wvdial, the CLI backend for gnome-ppp. What I need is a Conextant driver. . .
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by lkraemer on 2011-05-16
You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download the
ScanModem.tool and execute that script to get the information on the
modem. Then subscribe to the Linmodems discussion list.
Send Marvin an email (in plain text..ONLY) to the discussion list.
He will analyze your results and get back to you on what to do to get
the correct drivers to get the Modem working.

You can also search the archives posted there for your model and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your model and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR
Hardware Modem with your serial port or USB to serial Adapter and forget
the extra multiple days' hassel of the Winmodem..........

lk

---

### Post by pi.boy.travis on 2011-05-16
> **lkraemer said:**
> You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download the
ScanModem.tool and execute that script to get the information on the
modem. Then subscribe to the Linmodems discussion list.
Send Marvin an email (in plain text..ONLY) to the discussion list.
He will analyze your results and get back to you on what to do to get
the correct drivers to get the Modem working.

You can also search the archives posted there for your model and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your model and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR
Hardware Modem with your serial port or USB to serial Adapter and forget
the extra multiple days' hassel of the Winmodem..........

lk

I've actually already checked into linmodems, and after breaking the sound on my laptop several times, I found a USR USB modem on ebay for crazy cheap. Now I'll be able to fax and dial-in like it's 1989!

---

