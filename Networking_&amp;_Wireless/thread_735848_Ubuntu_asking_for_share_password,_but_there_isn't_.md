---
title: "Ubuntu asking for share password, but there isn't one..."
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Cenyu on 2008-03-26
I am trying to access my WinXP share from Ubuntu via the normal "Places--Network".

It opens the Network and shows my wireless Ad Hoc printer, and my Workgroup, so I double click my workgroup.  Sometimes it freezes here and doesn't allow me to pass, other times it lets me pass and won't let me double click anywhere else.

When I restart it mostly starts asking for a username password, domain, etc... of the WinXP machine I am trying to connect to however it is configured without one.

All of my other Vista, or XP machines can access this share with no problems.  The Live CD's that I've downloaded for Ubuntu can mostly all access this share.  I am using Ubuntu 8.04 (with great success except for this issue, I might add).

I'm running an HP dv9500z laptop with a USB Belkin Wireless key.

Also, I have been able to use browsers to access and play or view files in this share, but I can't copy or paste.  It says "Cannot Mount" and then won't allow me to access it.

Please help.  I'll provide any other information that you ask.  Not sure what I could have missed.

In conclusion, Cannot access properly set up XP share through Ubuntu.

---

### Post by Eiríkr on 2008-03-26
First off, Ubuntu 8.04 Hardy Heron is still in **beta status**.  This means that various things are bound to still not work properly.  

Regarding your post, it sounds like there are a couple different issues here:
[list=1][*]Browsing via Places -> Network sometimes doesn't work properly.  This is a common issue, but unfortunately I'm not aware of any clear solution.  The workaround is to access the share server machine directly.  Click the location bar in your Nautilus file browser (usually hidden by default, but can be displayed by hitting Ctrl+L or clicking View -> Location Bar), and type in:
```
smb://IP.ADD.RE.SS
```
Replace the caps with the IP address of your Windows machine.  Sometimes the Windows computer name will work too.  You can find what this is in Windows by right-clicking the My Computer icon, then select Properties, then click the Computer Name tab.  
[*]You say, "when I restart" -- when you restart what?  Do you mean reboot your Ubuntu machine, or reboot your Windows machine, or close Nautilus and re-open it, or turn your hourglass back over?  ;)  Please be more specific.
[*]The domain referred to in the dialog is the same as your Windows workgroup.  You can find what this is in Windows by right-clicking the My Computer icon, then select Properties, then click the Computer Name tab.  
[*]From other threads I've read, there is a bug in the Samba code regarding no-password Windows accounts.  One of the more recent threads about this is [thread=705983]this one[/thread].  I describe a workaround for this issue that goes into share permissions on the Windows side in [post=4454301]this post[/post].  Try that out and see if it helps.
[/list]

Cheers,

Eiríkr

---

### Post by Cenyu on 2008-03-26
I used the smb://MYIP/ and got access.  I did this before, however it doesn't afford me the access I want.  I can play video and music, and open documents, but I cannot make any changes to them or even copy them to my machine.  It gives me the error, "The Specific Location was not Mounted."

When I say restart I mean when I reboot my laptop and choose Linux.  (Since I am currently running dual boot.  Vista on hd(0,0) and Ubuntu on (hd1,0))

I also thought that the 'domain' would actually be referring to my 'workgroup'.  Which I then placed in the box.  The weird thing is, when it DOES first ask me for a username/password, I can give it ANY false information, or an account from the XP machine I'm trying to access and it grants me access to that folder, but then it will invariable ask once again whilst browsing my share's folders, and now it will no longer accept that username/password.

If I umount the share by right-clicking it on my desktop and clicking unmount I can now use my original username/password again.  However this does not work all the time either.

Not to mention, the biggest problem I have trying to access this share is when I click on my workgroup or the specific PC in that workgroup, and the curser just shows work and nothing ever happens.

Really not sure what to do about it.  I don't like the idea of once again having to set up an FTP server on my XP machine, as that is very annoying and a little more difficult to maintain.

This is not the first time I've had this problem while trying to access a windows machine this way, there is no firewall enabled (Norton is off, and WinXP firewall is off).

Don't think I left anything out...  Trying to give as much info as possible.  :)

I don't think this problem has to do with the hardy release actually.  I've had this same prob. with other releases.  Prolly just my own incompetence, or ignorance.

The one notion that I did have:  Everything seems to give me errors while trying to mount the network permissions.  Maybe the apps don't have root privelages and this may be necessary to mount network shares?  Not familiar with how to mount a network share in the terminal.  Maye if you could tell me how to do that it would work?

---

### Post by Eiríkr on 2008-03-26
Crashing for tonight, but have you tried making the Windows share available for "Everyone" as mentioned in the linked-to post?

G'night,

Eiríkr

---

### Post by Cenyu on 2008-03-26
It's not a server edition OS.  There doesn't seem to be a place to specify rights or permissions.  Just 2 checkboxes.  Share this to network users and local users, and Allow other users to change the files in this share.  (not worded precisely but I'm sure you know what I'm talking about)

Is there another place to set up permissions in XP?  Even if there is, why would the other Win-based machines be able to access it but not me?

My Gentoo machine had no problems accessing my share either.

I'm off for the night as well.  :)  At least I've got the system running fine.  Even have Compiz, my Bluetooth, and a bunch of other nifty little features running.  (almost straight outta box)

Night.

---

### Post by Cenyu on 2008-03-26
Before I go to bed I wanted to add, Nautilus does not allow me to do the smb://Internal IP Here trick.  But Firefox does.

And when the Network File Browser finally times out it gives me this:

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

On this current session I rebooted the machine and tried the local network.  It froze immediately after I clicked on Windows Networks.  However I was still simultaneously able to access these folders through Firefox.  Again, Firefox does not let me copy and such because "The Location is not Mounted."  But the problem doesn't seem to be Gnome, my Kernel config or the fact that it's Hardy, or my permissions on my server share.  Although, what's left I have no idea...

---

### Post by Eiríkr on 2008-03-26
> **Cenyu said:**
> It's not a server edition OS.  There doesn't seem to be a place to specify rights or permissions.  Just 2 checkboxes.  Share this to network users and local users, and Allow other users to change the files in this share.  (not worded precisely but I'm sure you know what I'm talking about)

Okay, now you've got me confused.  I don't have any Windows server OS here either.  I've got XP Pro on my end; maybe you've got XP Home instead?  Here are some screenshots showing the steps.  First I right-click on a folder and select Sharing and Security.  Then I click the "Share this folder" radio button.  Then I click the "Permissions" button to the middle right of the dialog, and make sure that "Everyone" is shown in the list, and that the permissions I want "Everyone" to have are checked below: "Full Control", "Change", and "Read".  Can you find these dialogs on your machine?


> **Cenyu said:**
> Is there another place to set up permissions in XP?  Even if there is, why would the other Win-based machines be able to access it but not me?

Assuming that by "me" you mean your Ubuntu machine, as I noted before, it appears to be a bug in the Samba code.  This therefore makes the problem specific to Unixy machines trying to access a null-password Windows share via Samba.  It will **not** affect any Windows machines attempting to access the same share.


> **Cenyu said:**
> My Gentoo machine had no problems accessing my share either.

That might depend on the version of Samba installed on your Gentoo machine; I'm not sure how old this bug is.  If your Gentoo Samba is v3.026, then there might be a bug specific to the Ubuntu package, or maybe it's a configuration issue.  If the latter, it'd be helpful if you could post your Gentoo machine's smb.conf file.  This is located in Ubuntu at [font=courier]/etc/samba/smb.conf[/font].  


> **Cenyu said:**
> Before I go to bed I wanted to add, Nautilus does not allow me to do the smb://Internal IP Here trick.  But Firefox does.

Interesting.  But what do you mean, "does not allow me to"?  Do you mean that you can't find where to type in the URL (try hitting Ctrl+L or clicking View -> Location Bar), or that doing so generates an error (please post it), or that Nautilus developers appear in a puff of smoke and slap your hands when you try to enter the [font=courier]smb://[/font] URL?  ;)


> **Cenyu said:**
> And when the Network File Browser finally times out it gives me this:

I confess I have no idea what the Network File Browser is, so I'm afraid I can't help you with that one.  


> **Cenyu said:**
> On this current session I rebooted the machine and tried the local network.  It froze immediately after I clicked on Windows Networks.  

I'm assuming you mean Nautilus froze, and not your whole computer?  And by "tried the local network", do you mean Places -> Network -> Windows Network -> WORKGROUP -> SERVER -> SHARE?


> **Cenyu said:**
> However I was still simultaneously able to access these folders through Firefox.  Again, Firefox does not let me copy and such because "The Location is not Mounted."  

This makes sense, as Firefox is not designed as a file browser, and thus does not handle file operations like copying.


> **Cenyu said:**
> But the problem doesn't seem to be Gnome, my Kernel config or the fact that it's Hardy, or my permissions on my server share.  Although, what's left I have no idea...

It might still be permissions on the Windows side, if "Everyone" does not currently have access.  Follow the steps described above and refer to the screenshots.  If the screenshots don't correlate to anything you can find on your Windows install, someone who's familiar with XP Home will have to chime in.  

One other possibility is that your network settings might be slightly different on the two machines.  A while back I had mistakenly set two different network masks when testing some things, and missed changing those back for quite a while.  I was able to access my shares via the CLI (my normal mode), but couldn't browse them.  My Windows machine had a network mask of 192.168.0.255, and my Ubuntu machine had 192.168.255.255.  I had thought that the broader Ubuntu mask was a superset that included the narrower Windows one, but apparently not.  Anyway, you might want to look into your network settings themselves and see if there are any obvious discrepancies.  

HTH,

Eiríkr

---

### Post by Cenyu on 2008-03-27
Hmmm...

Well, I think I might go about this a bit differently for now.

Just started with a fresh install.  Invariably I mess one or two things up the first time I use a new distro.  So for now I'll just set up a private FTP.  At least then I can access my files from anywhere.

It's a bit of a hassle, but shouldn't take too long to set up thank god.  Still not sure why I'm having probs. with samba, but my XP was never meant to be a server anyway.  Although I'm not really asking it do to too much, you can't expect much from a Microsoft product.  :-P  Standardization is not their primary goal.  Proprietary access is.

Anyway, I'll prolly get back on the forums in the future and see if I can figure out what's going on, but the rest of the system is working near perfectly for me right now.

Thanks for your help, it was appreciated.  :-D

~Cenyu

---

