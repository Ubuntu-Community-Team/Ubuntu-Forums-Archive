---
title: "Configure Ubuntu Server Edition as NAS?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by coffeecat on 2007-09-22
Does anyone know of any fairly straightforward howtos for setting up Ubuntu Server edition to act as a NAS box? Searching this forum and general Google searches have not yet turned up anything really suitable, but it must be out there somewhere. :wink: I have fairly basic experience of networking matters and no experience of apache.

My needs are simple. I have Linux and Windows XP boxes and a Mac Mini, all connected to a fairly standard home adsl modem-router (Linksys). I want to set up a NAS box with ftp and smb and possibly nfs. Also, once installed and configured (presumably via the cli), I want to be able to do further configuration through a web interface from any of the other machines. In fact, pretty standard NAS features.

Yes, I know about [http://www.freenas.org/](http://www.freenas.org/) . That should be what I want, but I didn't get on with an earlier beta and I've run into a major problem with the latest 0.685RC1 version. I'm still working on that but I thought I would look for alternatives, and I thought that Ubuntu Server would be able to do what I want.

Just to add - I've experienced show-stopping hardware or firmware failures with no less than three dedicated but otherwise promising NAS boxes. :( I'll post details if anyone is interested - there was a major design flaw with the last one. Rather than waste any more time and money on those I thought I would try to re-use an old but perfectly serviceable desktop machine as a server. So if anyone was thinking of suggesting a dedicated NAS box - thanks for the thought, but no thanks.

---

### Post by Bagoo on 2007-09-25
same here, any SUGGESTIONS!

THX

---

### Post by njparton on 2007-09-29
I'd be interested in a how to for this too.

FreeNAS is based on FreeBSD and doesn't appear to be friendly with a lot of recent hardware, whereas ubuntu is much more friendly. I'm thinking about buying a cheap socket 754 uatx MB with onboard gigabit lan as the basis for my NAS, but I'm worried about compatibility/drivers etc.

Can using ubuntu server for a NAS also be set up so that the NAS can be administered via http from a browser (even under windows) like FreeNAS?

---

### Post by coffeecat on 2007-10-04
> **njparton said:**
> Can using ubuntu server for a NAS also be set up so that the NAS can be administered via http from a browser (even under windows) like FreeNAS?

Exactly. Just what I would like to see. Thankyou both for replying. Glad to see I'm not entirely alone. By the way, having wasted some hours with FreeNAS, all I can say is that I won't be wasting any more. The current RC iso simply DOESN'T WORK, in that a fresh installation boots up to several errors and a prompt for a non-existent login name and password. Several people have posted on the FreeNAS forums about this and the response from the FreeNAS devs is.... a deafening silence. :(

Anyway, I've just discovered [this thread]("http://ubuntuforums.org/showthread.php?t=445675") and, more importantly, [the Ubuntu Home Server Forums]("http://forums.ubuntuhomeserver.org/"). I haven't had a chance to read the latter yet, except to see that the last post there was nearly a month* ago. I may join and stir the pot a bit. I'm posting this in case others might wish to do the same.

**Edit:** * Oops, not quite. More like 10 days or so ago, but it is rather quiet there.

---

### Post by njparton on 2007-10-04
Have you tried OpenFiler?

It looks a tad too complex to my mind, by some benchmarks I found on the web suggest it performs much better than FreeNAS in doing Linux > Samba > Windows transfers.

---

### Post by coffeecat on 2007-10-04
> **njparton said:**
> Have you tried OpenFiler?

No I haven't. I hadn't heard of it before, but it looks as though it might be just what I was looking for. Particularly as it's Linux based rather than BSD based so the disc-naming and filesystems are going to be what I'm used to. Moreover, according to [Distrowatch]("http://distrowatch.com/table.php?distribution=openfiler"), it's **British** (chest swells with pride :wink: ), so it must be good!

Thanks for the suggestion. The [homepage is here]("http://www.openfiler.com/") in case anyone else is interested. I've bookmarked it and I'll download the iso tomorrow and see how I get on.

Thanks. :)

---

### Post by dmizer on 2007-10-04
configuring ubuntu as a samba server: see the first link in my sig.
configuring ubuntu as an ftp server: see the third link in my sig.
configuring ubuntu as an nfs server: see the fourth link in my sig.

the above howtos will work on a fresh install of ubuntu server edition.

:)

edit:
a word of advice/caution.  if you're intending to use this for the long term, install dapper not edgy/feisty/gutsy.  lots of reasons for this, but primarily because it will cause you less headaches as a result of frequent upgrades.

---

### Post by coffeecat on 2007-10-05
> **dmizer said:**
> configuring ubuntu as a samba server: see the first link in my sig.
configuring ubuntu as an ftp server: see the third link in my sig.
configuring ubuntu as an nfs server: see the fourth link in my sig.

the above howtos will work on a fresh install of ubuntu server edition.

:)


Thanks for the suggestion, but that isn't really what I was after. I don't mind configuring samba, ftp and nfs if I really have to, but you missed the most important point - I want a web-interface for further configuration. That would mean learning how to set up and configure apache and, frankly, life's too short for that - at least for me. :( :wink:

FreeNAS should have fulfilled that need, but I've now given up on it. OpenFiler also looks like what I want so I'm going to see if the promise lives up to reality. But don't hold your breath. :)

Thanks for your interest.

---

### Post by dmizer on 2007-10-05
web interface:

webmin >> [http://www.webmin.com/](http://www.webmin.com/)  though that's probably still not what you're after.

setting up and configuring apache:
```
sudo aptitude install apache2
```
done.

---

### Post by coffeecat on 2007-10-05
> **dmizer said:**
> setting up and configuring apache:
```
sudo aptitude install apache2
```done.

Um, no. There'll be a bit more to it than that. I'd have to design and build all the webpages I need for each configuration page - admin, nfs, smb, ftp, reformatting the HD, network configuration - you name it! Then I'd have to work out how to get the configured web-pages to re-configure the base server software. And then... :cry:

I think you get the picture. That's why I said that life's too short. :wink:

But I'll have a look at webmin. Thanks for the link.

---

### Post by dmizer on 2007-10-05
you wouldn't have to write any pages.  install apache2 ... install webmin ... webmin is a pre configured web interface for all administrative functions of your server ... well beyond simply configuring samba, nfs, ftp ...

---

### Post by coffeecat on 2007-10-05
> **dmizer said:**
> you wouldn't have to write any pages.  install apache2 ... install webmin ... webmin is a pre configured web interface for all administrative functions of your server ... well beyond simply configuring samba, nfs, ftp ...

I see what you mean now. I'll look at that. Thanks.

---

### Post by njparton on 2007-10-10
> **njparton said:**
> I'd be interested in a how to for this too.

FreeNAS is based on FreeBSD and doesn't appear to be friendly with a lot of recent hardware, whereas ubuntu is much more friendly. I'm thinking about buying a cheap socket 754 uatx MB with onboard gigabit lan as the basis for my NAS, but I'm worried about compatibility/drivers etc.

Can using ubuntu server for a NAS also be set up so that the NAS can be administered via http from a browser (even under windows) like FreeNAS?

It would appear that VNC is the way to go for remote admin if anyone's interested.

Install vnc server in ubnutu and then a vnc client in windows or the linux box you intend to administer from. Just need to make sure the vnc server starts automatically on reboot otherwise you'll have to plug in a keyboard, mouse and display to get it up and working again.

---

### Post by Ziggen on 2007-10-15
Not ubuntu, but a ready NAS and web app

[http://www.clarkconnect.com](http://www.clarkconnect.com)
[http://www.smeserver.org/](http://www.smeserver.org/)

---

### Post by volkswagner on 2007-10-15
I agree with dmizer!

Much greater capabilities and it's Ubuntu!

I would opt for 6.06>LAMP>ssh>Webmin>Putty

Cheers

---

