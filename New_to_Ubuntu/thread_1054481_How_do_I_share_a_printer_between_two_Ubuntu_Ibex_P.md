---
title: "How do I share a printer between two Ubuntu Ibex PCs?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-29
I've tried, and failed.  Don't ask what I've tried, it's detailed in a long boring thread [elsewhere]("http://ubuntuforums.org/showthread.php?t=1053938").  All I'm looking for here is a link to an guide or even a carefully written blog that shows how to correctly share a printer from one Ubuntu PC to another.

Thanks.

---

### Post by boof1988 on 2009-01-29
> **diablo75 said:**
> I've tried, and failed.  Don't ask what I've tried, it's detailed in a long boring thread [elsewhere]("http://ubuntuforums.org/showthread.php?t=1053938").  All I'm looking for here is a link to an guide or even a carefully written blog that shows how to correctly share a printer from one Ubuntu PC to another.

Thanks.

Barring any issues with firewalls etc. and assuming you want to share on a home network...  This is how I think it can be done:

[LIST=1]
[*]Go to *System >> Administration >> Printing*, this brings up *Printer Configuration*
[*]Go to *Server >> Settings*, this brings up *Basic Server Settings*
[*]Choose appropriate settings (I choose the ones indicated in screen-shot)
[*]Click *OK*
[*]Wait a few moments and maybe click Refresh, (I couldn't get this to work in VM :( sorry... but it has worked when I ran Ibex on my machine).
[*]Repeat for other machine and the printer should show-up at that time.
[/LIST]

Hope this helps some.  I have attached screen-shots if needed.

---

### Post by diablo75 on 2009-01-29
'Fraid to say that I've done EXACTLY that and it still does not work.

---

### Post by boof1988 on 2009-01-29
> **diablo75 said:**
> 'Fraid to say that I've done EXACTLY that and it still does not work.

Do you have any firewall settings that would prevent print sharing? (I'm clueless on firewall stuff)

Have you used these settings on both machines?

Do you give a little bit of time for the printer to be detected over the network after you make some changes to settings?

Sorry if this doesn't help any.  Maybe someone else will have some more in-depth questions or might be a firewall guru.

---

### Post by Victormd on 2009-01-29
This might seem like a dumb question, please don't be offended, but were you able to enable file sharing between the two computers?

---

### Post by diablo75 on 2009-01-29
> **boof1988 said:**
> Do you have any firewall settings that would prevent print sharing? (I'm clueless on firewall stuff)

Have you used these settings on both machines?

Do you give a little bit of time for the printer to be detected over the network after you make some changes to settings?

Sorry if this doesn't help any.  Maybe someone else will have some more in-depth questions or might be a firewall guru.

-Firewall:  I'm about as clueless as you on this.  What I do know is that Firestarter does not kick up any red flags at any point in time when I do things like browse the network for shares or open up Printers and try to add a new one (which should show the shared printer because it says it's being published).  If there are specific port numbers I should open, it would be WONDERFUL if someone knew exactly what they were.  It would be even better if these damn ports would open themselves up with little more than an admin password being entered to grant permission for their opening.  I shouldn't have to do this manually!

-The settings on both PCs match in every way.

-I have given these PCs HOURS to present a share to one another.

-No problem.  Thanks for your reply.  Better than no reply at all.

> **Victormd said:**
> This might seem like a dumb question, please don't be offended, but were you able to enable file sharing between the two computers?

No.  Someone resorted to suggesting I use sftp/SSH to login to the other PC and then access a shared folder that way.
[http://ubuntuforums.org/showthread.php?t=1054484](http://ubuntuforums.org/showthread.php?t=1054484)

This pisses me off for two reasons.  One, I shouldn't HAVE TO DO THIS.  Two, SSHing into another PC grants whoever is doing the SSHing FULL ACCESS to the PC their SSHing into.  And third, I shouldn't have to do this!

](*,)

---

### Post by MrWES on 2009-01-29
Try using the CUPS web GUI:

localhost:631 in your browser, and then goto the Administration tab, and then under Server click edit configuration file. Choose default file to start with a 'fresh' config file. Then attempt to share your printer again, but do it from within the web GUI. Should work like a charm.

Bill

---

### Post by Victormd on 2009-01-29
That's why asked about file sharing. Assuming both ubuntu machines are on the same network, it should be very straight forward.
I skimed through your other post and it seems like you've done everything right (I'd say even more than necessary).
Do you get any results from pinging the other computer? On one computer, open a terminal and type:
```
ifconfig
```
this will show you the IP address, then from the other computer:
```
ping XXX.XXX.XXX.XXX
```
where XXX.XXX.XXX.XXX is your IP address.
If you get something like:
> From 192.168.0.6 icmp_seq=1 Destination Host Unreachable
then your router might need to be configured, otherwise, we'll have to double-check your network settings.

---

### Post by diablo75 on 2009-01-29
Yes, the two PCs can ping each other.

I'll take a look at the cups admin web interface and see what happens...

---

### Post by diablo75 on 2009-01-29
Well I've reset the cups server on my other PC to the defaults, then re-enabled sharing.  I don't really think this made a difference.

However, bumping into the term "ipp" leaned me towards selecting "ipp" from the New Printer config box.  This box shows "AppSocket/HP JetDirect", "Internet Printing Protocol (ipp)", LPD/LPR Host or Printer, Windows Printer via SAMBA, and other.

I was expecting to also find something like "HP Laserjet 6p via blah blah" in here, in other words, an autodetection of the shared printer that I could just select and not have to worry about typing in an IP address.

Short of having something nice and cool like autodetection, I guess I'll just set the IP to be static and manually add the printer.  I feel sorry for the countless new comers who will have to endure this in the future, lest Ubuntu get this ironed out and make it easy for everyone and reliable. /end rant

---

### Post by boof1988 on 2009-01-30
As a last resort... (if you have an HP printer) you may try downloading and installing the latest hplip (v 2.8.12).  It has a lot of bells and whistles.  And it has helped me in the past.  The following link will direct to the download page.  The latest hplip may be available for download through Synaptic, but I don't know how to force Synaptic to get it.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

And here's another idea...

Here's a [link](http://ubuntuforums.org/showpost.php?p=6030455&postcount=7) to a post where I got some help setting up print-shares.  Turns out I had (in that instance) to type in the URI in the printer settings of the computer that is not connected to the printer:

```
http://*ip_addres*s:631/printers/*printer_name*
```

Of course your *ip_address* and *printer_name* will probably be different.

Maybe it'll help a little. *dunno*

---

### Post by diablo75 on 2009-01-30
Welp, I reinstalled Ubuntu on the two PCs in question and that solved the problem.  Pretty f-ing stupid solution, I agree.  But it took me less time and know how.

---

### Post by bayvista on 2009-02-13
Many thanks for this simple 'Howto'. I am now accessing the printer on my second Ubuntu PC.

---

