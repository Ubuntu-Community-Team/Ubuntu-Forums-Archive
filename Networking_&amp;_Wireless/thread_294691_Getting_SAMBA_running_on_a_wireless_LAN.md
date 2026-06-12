---
title: "Getting SAMBA running on a wireless LAN"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Howlin' Hobbit on 2006-11-07
After some fussing I got SAMBA running so that both the Win98 machines and my Ubuntu machine could share files/folders. Then we moved and decided to go wireless (currently there's only one Win98 machine and my Ubuntu machine up and running).

When we got the wireless running and both computers getting to the internet I found that neither could see the other's shares. I searched here and found [this entry]("http://ubuntuforums.org/showthread.php?t=288811&highlight=Samba+wifi"), saying that I needed to install smbfs, so I did.

It worked... briefly. Now the Win machine can see the Linux box with no problem yet the Linux box doesn't see any other computers.

I open "Network Servers" and it shows "Windows Network". I open that and it shows "diablo", the workgroup we have had since before I moved the laptop to Ubuntu. I open *it* and the machine pauses for a few moments and then gives me an error message:

**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of
"Windows Network:diablo".

Any idea why it's doing this? Or why it worked at first and is *now* doing this?

Thanks in advance for any help!

---

### Post by dmizer on 2006-11-07
i don't think it has anything to do with you going wireless.  i think that the recent modules update package changed some operations in network file sharing, i had several things go haywire on me after the last round of updates.

you can make your ubuntu machine connect to your windows box using cifs instead of smbfs.  try here ... [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by Howlin' Hobbit on 2006-11-10
> **dmizer said:**
> i don't think it has anything to do with you going wireless.  i think that the recent modules update package changed some operations in network file sharing, i had several things go haywire on me after the last round of updates.

you can make your ubuntu machine connect to your windows box using cifs instead of smbfs.  try here ... [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

Thanks for your reply. I checked out the how-to. Problem here is I don't want to have to install something else and then type a long command string in a terminal every time I want to access something on my LAN. I want to click on an icon and have it *just work*... like it did before the "update."

If an update broke something, shouldn't it go to the top of the fix list for the next time I get one of those little "you have updates" icons in my top panel?

Sorry if I sound harsh here, but this is exactly the kind of thing that is slowing down acceptance of Linux on your average person's desktop.

I realize that *no* OS is completely free of such issues, but networking (even home networking) is such a basic nowadays that I would think keeping it cooking along well would be a top priority.

The part that irks me the most is that the Windows box can see (and interact) with the Linux box just fine but the reverse isn't true anymore.

Thanks again for the response and I'll keep it in mind if I get to the point where I absolutely *have to* have networking happening from the Linux box... assuming there's no other fix by that time.

---

### Post by dmizer on 2006-11-11
it didn't necessarily break anything.  just changed how things work.

nautilus is a really bad way of mounting samba shares anyway.  not sure i understand the resistance to using cifs.  you're eventually going to be forced to use it anyway because smbfs is being phased out.  furthermore, if you make an entry in fstab, you'll never have to edit or type any commands again.  just do it once, and it will create an icon on your desktop and mount automatically every time you boot.

[http://www.ubuntuforums.org/showthread.php?t=212847](http://www.ubuntuforums.org/showthread.php?t=212847)

---

### Post by Howlin' Hobbit on 2006-11-11
> **dmizer said:**
> it didn't necessarily break anything.  just changed how things work.

It surely did change how things work. It changed from "I can click on my 'network servers' icon and get to the shares" to "now I can't see the shares at all." I call that kind of change broken.

> **dmizer said:**
> not sure i understand the resistance to using cifs.  you're eventually going to be forced to use it anyway because smbfs is being phased out.

Oh, terrific!

> **dmizer said:**
> furthermore, if you make an entry in fstab, you'll never have to edit or type any commands again.  just do it once, and it will create an icon on your desktop and mount automatically every time you boot.

This is on my laptop. It is not always in my house and even when it is the other machines may or may not be on at the time. I don't want it looking to automatically link to a share when the share isn't anywhere to be found, nor do I want to be hooked up to *all* the shared folders on each of the other two machines in my LAN *all* the time. That would be 8 or so icons cluttering up my desktop even though I only use a couple of them with any regularity and even those aren't an every day thing.

And what happens when there's a new share on one of the computers? Won't I have to go in and do all that stuff again for it?

If cifs is on a machine-by-machine basis it might be slightly easier but it doesn't appear so from the how-to I read, it looks like you have to do it for every share, not just once and for all.

Lastly, I'm reading through that long thread you linked to and I came across this:

> I think it's a matter of what everyone was raised on..it's not about being "easier" per se, but what has become "second nature" to most...MS has just plain made it easier for the masses...

**Linux needs to have that edge if it's going to attract and hold on to the end user in the future..**(*emphasis mine*)

Bingo! It may well just be what I'm used to but it also just makes more sense to me to use a share when you need it and not futz about with it when you don't. And having to go to the (admittedly better than Windows) terminal to do something you used to be able to do with a click or two just isn't easier or better.

Thanks again for your time. Despite my rant I appreciate you (and the other nice folks on this board) trying to help me out as I learn this thing.

---

### Post by dmizer on 2006-11-11
> **Howlin' Hobbit said:**
> This is on my laptop. It is not always in my house and even when it is the other machines may or may not be on at the time. I don't want it looking to automatically link to a share when the share isn't anywhere to be found, nor do I want to be hooked up to *all* the shared folders on each of the other two machines in my LAN *all* the time. That would be 8 or so icons cluttering up my desktop even though I only use a couple of them with any regularity and even those aren't an every day thing.
does your laptop choke every time you boot and there's not a cdrom in the drive?  there's an entry in fstab for that too.  the same thing will happen to your shares as what happens to the cdrom drive if there's no cd in it.  if there's some mounts you only want to use occasionally, set them to not auto mount.  then when you want to see the share just turn it on.

> And what happens when there's a new share on one of the computers? Won't I have to go in and do all that stuff again for it?
you'll have nice working examples in fstab to work against.

> If cifs is on a machine-by-machine basis it might be slightly easier but it doesn't appear so from the how-to I read, it looks like you have to do it for every share, not just once and for all.
just as you would have to through nautilus.

> Bingo! It may well just be what I'm used to but it also just makes more sense to me to use a share when you need it and not futz about with it when you don't. And having to go to the (admittedly better than Windows) terminal to do something you used to be able to do with a click or two just isn't easier or better.
actually, how can you call it easier or better if you've never used the command line way?
nautilus mounts are unstable at best, and makes an already slow connection even slower.
maybe this doesn't concern you, but it can't handle non-latin characters in your shares. 
you can't open a file directly from the server, you have to copy them to your local drive first.
you can't save a file directly to your network share, you have to drag and drop it to your nautilus folder.
no previews on nautilus "mounted" shares.
your shares are not chashed on your local machine, so you have to wait for them to appear every time you open the folder.

and actually i can continue this list. these and many other reasons are what caused me to search out the RIGHT way to mount network shares with linux.  and it's so much better now.

> Thanks again for your time. Despite my rant I appreciate you (and the other nice folks on this board) trying to help me out as I learn this thing.
it's no problem, just hope you can get over some of that resistence to the command line.  arcane commands may seem difficult at first, but in the long run it really does make things easier than gui interface.  particularly when you're working with a gui desktop that can be custom configured in any way.  for instance, i have no idea if you're using kde, gnome, or xfce.  also, if you're using gnome, are you using the same menu bar setup that ubuntu came installed with, or have you installed a custom menubar theme like osx look alikes.  are you using dapper or edgy (both current and supported versions of ubuntu)?  there's no way for me to tell, but the command line doesn't care what the gui looks like, and so we can help you fix problems even if we don't know what gui you're using.

---

