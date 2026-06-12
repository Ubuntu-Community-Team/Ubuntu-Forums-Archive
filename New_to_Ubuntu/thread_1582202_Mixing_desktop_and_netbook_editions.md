---
title: "Mixing desktop and netbook editions"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by sanjochris on 2010-09-26
I've been messing around a bit with Ubuntu for about a week, clueless aside from that. So I probably shouldn't have tried adding the netbook edition to the desktop edition, but I did.
The resulting crash was pretty awful. After an apparently normal start, I got my wallpaper and my panels as usual, which then attempted to turn into the netbook desktop, then vanished completely, leaving me with a screen that flickered and cycled between empty and a half-screen of vertical white lines. After trying a few reboots it was clear things were going to stay that way. Luckily I had a copy of Parted Magic, which I used to get back into the machine. I had no idea what to look for, but I found a file called .xsession-errors which was full of fatal-error stuff. Then I found a couple of files with "netbook" in the names, in /usr/share/xsessions, renamed them to .doc files, and rebooted. I got my desktop back and everything worked, except I had no cursor. On the second reboot though, my cursor came back. I renamed the files back to what they had been, and thoroughly removed them and everything else  associated with netbooks, using the software center. All appears to be well. Sheer luck, though.

I'd still like to try the lightweight desktop that apparently comes with the netbook edition. But I don't think I'm going to be that lucky twice, so how should I go about installing it, please? And if I don't like it for now, is there a way to keep it on the system but just not use it? Thanks!

---

### Post by spiky001 on 2010-09-26
why not run the live cd of netbook see if you like it

---

### Post by Paqman on 2010-09-26
> **sanjochris said:**
> 
I'd still like to try the lightweight desktop that apparently comes with the netbook edition. But I don't think I'm going to be that lucky twice, so how should I go about installing it, please? And if I don't like it for now, is there a way to keep it on the system but just not use it? Thanks!

The netbook interface isn't really lighter, it's just optimised for small screens.

You should have been fine having both interfaces on your machine. How did you go about trying to add one to the other? The netbook edition actually includes the normal interface anyway, you just pick which one you want to log into from the logon screen.

---

### Post by kerry_s on 2010-09-26
the netbook version has both netbook-launcher & gnome desktop, so you can pick what you want to use at the log in.

---

### Post by sanjochris on 2010-09-26
Thanks, everyone, for those comments and suggestions.

Installation - I looked for the netbook in the software center, ubuntu-netbook was the package as I recall. If I also installed any other related packages I don't recall.

Using a live disk - it's a good idea, but it would run slower than a full install so I wouldn't be able to judge performance fairly. And even if I preferred the environment, I wouldn't know how to install it without wrecking my current Ubuntu desktop installation.

Choosing desktops at login - Ah, now this is also a puzzle. I took a look at other relatively lightweight environments and decided to try out Xubuntu, after I'd got my Ubuntu install running stable again. I'd read in more than one place that on rebooting, I would be given the option to choose the Xfce desktop or Gnome. Not so. I installed from the software center, no problems, rebooted, and went straight to Xubuntu - no alternative on offer. And that's how it has stayed, I don't get the choice at boot as everyone I'd read had claimed. And I don't know why.

Not that it's a problem, as the new environment definitely runs faster and smoother than the standard Ubuntu one did. That was prone to locking up and had serious problems multitasking. Unless I can try out other environments safely, I think I may stick with it. However, it would be nice to be able to revert to the standard desktop if I enhanced the machine's performance, but I don't know why I can't do that if everyone else seems able to do so.

I'm definitely getting there, though :)

I'm using: IBM Thinkpad X30, 500Mb RAM

---

### Post by kerry_s on 2010-09-26
not choice at boot, choice a log in. after you select your name, select the session in the session menu on the bottom.
if you have your system set to auto log in you won't see that, but you can log out from your current session & change.

---

### Post by sanjochris on 2010-09-26
> **kerry_s said:**
> not choice at boot, choice a log in. after you select your name, select the session in the session menu on the bottom.
if you have your system set to auto log in you won't see that, but you can log out from your current session & change.


Aha! Yes, I wasn't seeing that. I am, now. And I picked up some misinformation elsewhere which led me to believe it was a boot option, so thanks a lot for putting me straight on this. It all works fine, and I also found the option to display the session chooser in Xubuntu.

Now then, to go back to my original question, if I deselect Auto-login and attempt to install ubuntu netbook and reboot, will the netbook session option appear in the sessions list alongside Xubuntu and Ubuntu?  Really from what I've read, the only part of the netbook edition I'm interested in trying is the desktop environment, because Ubuntu with GNOME  is really choppy on this laptop, Xubuntu is a lot better, but I'd like to try other environments too. Thanks for the help :)

---

### Post by snowpine on 2010-09-26
Yes, you will need to disable auto-login to see the GDM login screen where you can select different Sessions (netbook launcher, Gnome, Xfce, etc.) which are different desktop environments or "skins" on top of the underlying 'buntu system.

---

### Post by sanjochris on 2010-09-26
I have some more data now. Good news is it looks like I wasn't doing anything wrong, bad news is that netbook edition will not run on my hardware. Here's what I did:

I used the software center to install ubuntu-netbook. Nothing else. I made no changes to the existing configuration. I just did the download and logged off.

As you said, the login screen now shows the options for netbook and netbook 2D. However, when I selected netbook 2D and logged in, I got a new desktop, which I assume to be the netbook one, superimposed on my wallpaper from Ubuntu Desktop for a few seconds, and then the new desktop faded out and I was left in a full Ubuntu Desktop session (which I had not selected) complete with all my buttons and icons. Puzzling. So I logged out, and then logged back in having this time selected the 'netbook session' from the options. And I got exactly the same crash as I got before -- flickering screen, with cyclic vertical white lines, apparently a hardware issue. In between all the flickering I could just make out the words:

PulseAudio configured for per-user sessions
binary binfmt-support
Checking battery state

this was flashing past along with everything else and did not change as far as I could see, so I assume this (or more likely the very next procedure) is the point at which everything died.

This is a repeatable error. Luckily I know how to fix it now, just by renaming the offending netbook files in /usr/shared/xsessions whilst using a live CD. I've tested it twice now, and got the same error on trying to start a netbook session. It is **only** the netbook sessions that don't work, the Ubuntu and Xubuntu sessions work just fine.

As it's a repeatable error it suggests that the netbook edition simply doesn't like my hardware, in which case there's nothing I can do. But that does resolve my original question, and now I know about the auto-login and how to get to the sessions options, I am up and running happily with the other desktop options. 

Thanks for your help, it's nice to find a forum that treats a beginner like a human being!

---

