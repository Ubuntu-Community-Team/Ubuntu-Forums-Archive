---
title: "Can't find Network Printer - Linux Server"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by Tim_Johnson on 2014-04-30
I have two ubuntu 12.04 installs both use gnome desktop (as opposed to unity). 
I will call the server - which has the printer connected to it - **myserver**
and I will call the computer which needs access to the printer [B]myhost

[/B]FYI : I have used linux for a long time, but have used samba shares. myserver does not have samba on it.

On myserver I have the attached printer working and have *policies"* with "enabled", "accepting jobs" and "shared" checked.
Also on myserver I have "Allow Printing for everyone except these users" selected under [I]Access Control


[/I]Both computers have network access and can to connect to myserver via ssh. **But** I can't see myserver from myserver's 
Nautilus->Network window.

When I attempt to Add a New Printer, and Find Network Printer with the IP address of myhost as the host address, 
I get [I]No printer was found at that address
[/I]I don't know where to go from here. I tried putting samba on myhost, but that didn't work either.
I have the device URI for the printer, but of course it is referenced from myserver, so I don't know how to reference from myhost.
Whew! - Most difficult printer setup I've done, problem is I do it so seldom, I forget all between times :confused: and
in the past have always shared with samba.
TIA
- tim -

---

### Post by chili555 on 2014-04-30
> I attempt to Add a New Printer, and Find Network Printer with the IP address of myhost as the host address, But you said:> the server - which has the printer connected to it - **myserver**Don't you mean that you are attempting to Add New Printer at the IP address of **myserver**?

I would attempt, on myhost, to Add New Printer as something like: ipp://192.168.addr.myserver:631/lpr

A few rare printers, including my Samsung, prefer: ipp14://192.168.where.ever:631/lpr

Of course, substitute your details here.

---

### Post by SeijiSensei on 2014-04-30
On the client machine, point a web browser at [http://localhost:631/](http://localhost:631/) to gain access to the CUPS management console.  Try adding the printer there.  You'll be asked for your username and password along the way so you can get root ("sudo") privileges.

---

### Post by Tim_Johnson on 2014-04-30
> **chili555 said:**
> But you said:Don't you mean that you are attempting to Add New Printer at the IP address of **myserver**?

I would attempt, on myhost, to Add New Printer as something like: ipp://192.168.addr.myserver:631/lpr

A few rare printers, including my Samsung, prefer: ipp14://192.168.where.ever:631/lpr

Of course, substitute your details here.
I had tried that earlier - as the IP of myserver is 192.168.1.5 (static IP) I used
ipp://192.168.1.5:631/lp
as the URI in the Add New Printer dialogue on myhost.
On the second try, I got the same response when trying to print a test page
[I]Processing - The printer is busy.
[/I]And there was no prompt for user or password.
thanks for the reply
- tim -

---

### Post by chili555 on 2014-05-01
On **myhost**, to which the printer is attached, is the printer's server settings set to Publish?

---

### Post by Tim_Johnson on 2014-05-01
> **chili555 said:**
> On **myhost**, to which the printer is attached, is the printer's server settings set to Publish?
:)They are now! All is good. You fixed it. 
Not sure how to mark this thread as solved ....
cheers
- tim -

---

### Post by chili555 on 2014-05-01
> **Tim_Johnson said:**
> :)They are now! All is good. You fixed it. 
Not sure how to mark this thread as solved ....
cheers
- tim -Please use thread tools at the top to mark Solved. Glad it's working.

---

