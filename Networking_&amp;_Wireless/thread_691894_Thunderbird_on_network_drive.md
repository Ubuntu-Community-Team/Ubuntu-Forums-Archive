---
title: "Thunderbird on network drive"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by ginge6000 on 2008-02-09
I've been messing around with an ubuntu server at home and thought I'd try to place my thunderbird profile on a network drive so that I can get to it from whichever computer I use. After the initial "Thunderbird is already running" issue (it doesn't seem to like not being ina folder called Profiles!) I can now run TB and it connects to my profile on the network drive.

The trouble is that whenever I click on an email to view it TB crashes and has to close. Occasionally I am able to view a small plain text email but anything with more than a couple of kB and it crashes.  Can anyone offer any guidance?

Cheers,

Ben

---

### Post by kidders on 2008-02-10
Hi there,

What you're trying is inadvisable for a number of reasons...
[LIST]
[*]It creates the possibility that you might try to access the same application data using different versions of Thunderbird, or perhaps two builds of different bitness, or for different OSs.
[*]It leaves it to the user to remember not to try to have two copies of Thunderbird access the same data at the same time.
[*]Since much of Thunderbird's user data is very database-like in structure, it's not a good idea to store it on a remote filesystem in the first place.
[*]Depending on the file sharing protocol you're using, Thunderbird may run into file naming, locking or access control problems it's not expecting.[/LIST]Storing local mailboxes on remote filesystems at all is not a good idea ... doing so for the *purpose* of sharing them with multiple Thunderbirds is a recipe for corruption, imo.

The standard way of accessing the same mail data from multiple machines is to use IMAP mailboxes.

---

### Post by ginge6000 on 2008-02-10
Thanks for your reply.  Most of your concerns aren't really a problem as it's only for my use at home so that I can access my email on either my desktop or laptop computer.  I currently have the thunderbird profile on the desktop machine and the laptop uses the same profile through my wireless router.  So far (a couple of years!) I've not had any problems!  I tend to update both the desktop and laptop at the same time so I've not had any problems with conflicting OSs or versions of Thunderbird.

What I had hoped to do was move the profile onto my Ubuntu server and set it up as a Samba share so that I don't have to leave my desktop on when I'm using the laptop.  Mostly this is due to the amount of power consumption that the desktop uses compared with the server.

If I am able to open Thunderbird, and therefore access the profile on the server then would it be safe to assume that the access controls of the Samba share are not the problem?

Hope this clears up a few things!

Ben

---

### Post by kidders on 2008-02-10
I'm not sure. Crashing suggests something low-level or counter-intuitive is going wrong ... perhaps file locking issues, or corruption of the mail database. Your use of Microsoft's networking protocols introduces an additional unpredictability, so it's hard to know where the problem might be.

I suppose a good place to start would be to make sure both Thunderbirds can read your mail data successfully when it's stored locally. Assuming that works, I would recommend trying it over NFS (ie a native filesystem model, rather than a frankensteined Linux/Windows one).

It looks like you may have been using Samba before though ... If that's true, and you'd prefer to continue doing so, then it would be worth checking for configuration differences between your new setup and the original one.

---

### Post by ginge6000 on 2008-02-11
Actually, so far I haven't done this via Samba, it was just on two Windows machines, networked together.  Are you suggesting that Samba isn't the best way of sharing the data on the linux server with my Windows machines?

Ben

---

### Post by dmizer on 2008-02-11
i've had the setup you describe for a number of years.  as long as i'm careful about making sure that all my computers have the same version of thunderbird, i don't have a problem with this setup.

they problem may indeed be HOW you are mounting your samba shares.  are you mounting them in fstab or with nautilus "connect to server" function?

if you want thunderbird to work across a network on a server, it's imperitive that you do your samba mounts via fstab, otherwise the connection is too flaky.

---

### Post by ginge6000 on 2008-02-11
Sorry, I'm a bit confused :confused:.  The Samba shares are on the (headless) linux server and I have mapped a network drive to it from my windows machine.  I *only* view Thunderbird on machines running windows

Am I supposed to do something with fstab on the server so that the shares behave differently on the windows machines?

---

### Post by dmizer on 2008-02-11
> **ginge6000 said:**
> Am I supposed to do something with fstab on the server so that the shares behave differently on the windows machines?

nope ... simply my misunderstanding of your arrangement.

i've never had windows set up in the manner you describe so i'm not familiar with windows specific problems that can arise.  you might try posting your smb.conf file from the linux server.

---

